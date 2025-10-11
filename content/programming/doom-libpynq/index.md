---
title: 'Rocking My Baby to Industrial Metal'
summary: "Ported DOOM to libpynq. It was mostly fun."
date: 2025-10-11
draft: false
ShowToc: true
cover:
   image: "/programming/doom-libpynq/cover.jpg"
   alt: "PYNQ running DOOM"
   relative: false
---

# Installation

## Prerequisites

1. Ensure you have run `make install` in the directory of your libpynq installation at least once.
2. Get yourself a `doom.wad` file or two. I had trouble running the shareware version, so feel free to try different files if one doesn't work.

## Steps

1. Download and extract the [repository](https://github.com/leekleak/DOOM_libpynq) into the home directory of your PYNQ.
2. Move your `doom.wad` file into the `DOOM_libpynq` directory.
3. Enter `DOOM_libpynq` and open `params.mk`.
4. Override the value of `LIB_PYNQ` according to your setup.
   1.  The preset value assumes that both your main libpynq folder and your `DOOM_libpynq` are in your home directory. If that is the case and the libpynq versions match, you may already be good to go.
5.  Run `make install`
6.  Run `make run`

# Troubleshooting

- I get errors
  - Maybe try different .wad files
- I get horrible performance
  - After I boot up my PYNQ, VSCode eats up 100% of the CPU time indexing stuff. If you're experiencing the same, try waiting for it to finish.

# I did not expect porting DOOM was *this* easy

Like yeah, the legend says that you can run DOOM on a toaster or on a microwave, but I always thought that that was at least a mild exaggeration. You know... It can't be that...

It's that easy.

For context, before attempting this, I thought it would take me at least a couple of days, maybe even a week or two, but no. This genuinely took half a day and most of that time was wasted just wrestling with makefiles. Considering that I'm a total C newbie, it's really incredible the amount of work the people behind [doomgeneric](https://github.com/ozkl/doomgeneric) did to make the dream of running DOOM literally anywhere a reality.

Seriously, I cannot stress this enough -- this entire porting process required me to write exactly **SIX** functions of which only **TWO** took more than 5 minutes. It's ludicrous.

The point behind this entire paragraph is that it's so easy it's a wonder it hasn't been ported to *more* platforms. So go ahead, do it. Be the change you want to see in the world. Port DOOM to your dishwasher and share it with the world.

# Performance and libpynq

## The first image
The very first thing I tried to do after getting my PYNQ board was display images on the cute little display. That was literally my first time touching C, but it was surprisingly easy and with the help of `stb_image` I got an image on the display within that very same day.

![](/programming/doom-libpynq/image.jpg "The image in question")

Having experienced great success, I set myself a slightly bigger challenge of getting Shrek to run. Obviously, I had no intention of working with video codecs and the like, so the second best option was a gif. Luckily the `stb_image` library already had some functions for dealing with gifs too, so the next day, in all my excitement, I plugged in the wires and...

There was a major problem. The performance wasn't great. By that I mean it ran at a whopping 0.25 FPS. Certainly not real-time and about 100 times less than what would be required to run DOOM without having the ambulance on the line.

Not sure what to do, I cleaned up my spaghetti code and while that did manage to improve the performance to maybe about 0.33 FPS, things were not looking good. My code was pretty much perfect, so in a desperate search for answers I dove into the libpynq source code.

## Expedition into the source

And oh my!

Here's some highlights (comments mine):

```
bool spi_master_write_command(display_t *display, uint8_t cmd) {
   gpio_set_level(display->_dc, spi_to_gpio(SPI_Command_Mode));
   spi0[0x68 / 4] = cmd;
   while (((spi0[0x64 / 4]) & 4) == 0) { //Sure, let's wait. We got time.
   }
   usleep(1); //Imagine setting a 1 usec delay for EACH PIXEL DRAWN
   return true;
}
```

```
bool spi_master_write_data_byte(display_t *display, uint8_t data) {
   gpio_set_level(display->_dc, spi_to_gpio(SPI_Data_Mode));
   spi0[0x68 / 4] = data;
   while (((spi0[0x64 / 4]) & 4) == 0) {
      //Guys, relax it's not like we've got a frame to render
   }
   return true;
}
```

```
bool spi_master_write_color(display_t *display, uint16_t color, uint16_t size) {
   gpio_set_level(display->_dc, spi_to_gpio(SPI_Data_Mode));
   for (int i = 0; i < size; i++) {
      while (((spi0[0x64 / 4]) & 8) == 8) { //Yo, Bobby, wanna grab some coffee?
      }
      spi0[0x68 / 4] = (color >> 8) & 0xFF;
      while (((spi0[0x64 / 4]) & 8) == 8) { //Sure man, we've been in this loop for hours
      }
      spi0[0x68 / 4] = (color)&0xFF;
   }
   while (((spi0[0x64 / 4]) & 4) == 0) { // One more for good measure
   }
   return -1;
}
```

And there's more.

Admittedly, there's *a* reason to do (some of) this. You wait to ensure that the data you've written has actually been passed through and received or whatever, but man that's slow. I want real-time rendering, I don't care if there's a pixel missing or something like that. I want pixels to move and I want them do to that fast.

During my excursion to the source files I:
- Commented out all that shit (It's fine, to my eye the picture's perfect even without the guardrails).
- Discovered a function to draw pixels in batches and adapted it to my codebase.

In the end that was enough to jump from 0.25 FPS to about 26 FPS. It's not often we get a 100x performance improvement by commenting out some lines, but we take those.

Most importantly, Shrek was happy.

![](/programming/doom-libpynq/shrek.jpg "Shrek being the cutest green goblin out there.")

## Why stop at 26 FPS?

Ehh, from what I looked, it seems that I've reached the maximum bandwidth SPI supports (protocol I'm using to communicate with the screen).

Currently each pixel requires two writes as I can only send 8 bits per write, so that's a possible route for further optimisation. During my testing I did manage to roughly double the result to 55 FPS by simply not sending the second write, which reinforced my belief that it's a bandwidth issue. However, I could not bear to downgrade from a beautiful 16-bit palette to 8-bit. Isn't that the difference between the NES and SNES?

Hell, I can just show the difference: 

![](/programming/doom-libpynq/comparison.jpg "8-bit vs 16-bit")

Oh.

Ok lol.

I honestly thought there would be a bigger difference.

Wait, how many bits was NES again?

*checks notes*

**6-bits!?!**

Ok, fine, I guess I'll have to make 8-bits work. 

