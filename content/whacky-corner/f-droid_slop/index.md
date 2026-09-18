---
title: "How much of F-Droid is LLM generated?"
summary: "Investigating the use of LLMs in the Android FOSS community"
date: 2026-09-15
draft: false
tags:
  - Open Source
cover:
  image: "/whacky-corner/f-droid_slop/header.png"
  alt: "F-Droid robot looking very sad"
  relative: false
ShowToc: true
---

# Preamble

So for better and for **worse** this blog post has gotten some traction. Most of it rather tribal, unfortunately. So I have 2 points I want to front-load to anyone reading this.

1. LLM usage does not make the project *"slop"*. A big part of the projects using LLMs are overseen and guided by skilled people who review the output and ensure code quality. I think there are many valid uses for this technology even if I think it is largely harmful.

2. The results of the investigation are not to be taken *too* seriously. This was done mostly for fun and out of curiousity and I apologize to the couple of creators whose projects I have mislabeled for the distress seeing this post may have caused.

To extend on point 2, I have since taken a second look at the apps list and re-categorized around 9-10 apps, all towards being **more** human coded than I had thought at first. I have been rather been nice to the apps on re-review, so one or two "Mostly LLM" projects may have slipped into "Mostly Human" category, but that's a sacrifice I am willing to make.

If you have any other corrections feel free to reach out.


# Intro

I love F-Droid. I love what F-Droid stands for and I like the freedom that it gives its users. As a FOSS app maintainer I also have **nothing** but good things to say about the people behind the project. Maybe they're even a bit *too* nice, considering how many times repro has failed due to me forgetting to commit before building 😅.

But **my god** is it hard to find human-written software now.

## The problem
Sometimes I open F-Droid just to browse. You know, maybe I'll find an app that solves a problem I didn't know I had, or maybe I'll find a better alternative to something I already use.

And one day, while browsing, I noticed an app with an obvious and ugly *AI generated icon.* It's not on the list and I will not shame it, but it got me thinking. How much of F-Droid is AI?

As someone who does programming for fun and is only a student, untarnished by honest work, I get my knowledge of what the coding world is like mostly from clickbaity YT videos and Reddit posts of CS professionals. They either describe LLMs as god reincarnate or as glorified autocomplete.

Both are, *obviously*, wrong, but that's not really helpful in determining what I want to know. What is the *actual* state of programming nowadays? Whenever I use FOSS software, how likely it is that it has been vibe-coded by a rando in an afternoon? 

## How to know if an app is vibe-coded?

That's the trick—you can't. Text just doesn't carry enough meta information for any kind of assessments to be even close to accurate. However, just as that em-dash I used in the first sentence probably triggered an alarm in your brain, **there are signs.**

While that does make the task at hand sound fickle and dependent on happenstance, the signs, especially concerning LLM code repositories, are never too hard to find.

You see, the main allure of LLMs is that they allow the developer to be more lazy. That's kind of the whole point! You just prompt, sit back and relax. So it should not surprise you to hear that this attitude is then reflected in everything the vibe-coder touches.

Why write a README from scratch? Lol, just let the LLM do it.

Do code-review? Naw, just let the LLM review its own changes and then also give it access to the repo so you don't even need to press the commit button.

If a project was concerned with looking legitimate, it would be trivial to do such things by hand. But it's low effort all the way down.

## My biases

This part can be skipped if you don't care about my stance on LLMs, but I need to make my position clear to avoid contributing to the circlejerk too much.

To begin with, I'd like to acknowledge that LLMs are incredibly useful and capable. As 2026 has progressed, this has become more and more visible, but people being able to one-shot medium scale games and software in half an hour is ridiculously impressive, even if the end product is usually not very good.

I also am very much in favor of software getting faster and more secure. The story of the Linux kernel development has shown that LLMs are capable of finding and sometimes even solving many types of code issues.

With the pleasantries out of the way though, I have to admit I really hate LLMs and what they have done to programming, related engineering fields, and society as a whole.

Their mere existence makes educating yourself and going on fun side projects much less rewarding. Like *yeah*, I did something, but with an LLM I could have done this in a quarter of the time. And when you *do* take the black pill and vibe-code, it's even worse. It's not like you did anything. The machine did that.

Then there's the atrophying effects on human brains, their unfathomable capability for serving plausibly sounding misinformation and the climate disaster that we're just kinda ignoring. All very fun things to think about.

## Criteria / The experiment

As mentioned before, there's **no way** to effectively detect slop, so I propose a rough 3 tier system based on the aesthetics of the repo:

- {{<bad>}} Mostly AI {{</bad>}}
  - This is mostly for projects that have significant LLM smells and means I expect >50% of the code is LLM authored. Any kind of agentic infrastructure automatically lands an app in this tier as I do not believe it is possible to use AI responsibly from within a coding harness.
- {{<ok>}} Hard to say / Mostly human / Other {{</ok>}}
  - Occasional LLM commits either by maintainers or contributors, but mostly looks human. May have an LLM policy which permits certain uses. This tag means I expect <50% of the code is LLM authored.
- {{<good>}} No signs of AI {{</good>}}
  - Could not find anything suspicious/Has a strict LLM policy.

Note that my rating will still be quite superficial and the tiers quite loose. I did not build a "slop detector" or anything like that, so my decisions are based on looking at recent commits and their content along with the project's branding.

Also note that since I have no way of knowing for sure, there may be errors. I still believe most of my findings to be accurate however.

I will also not look at the history of the app. If it has existed since 2014 but recent commits are LLM authored it will be categorized as "mostly AI"

The apps chosen were the batch of updates pushed to F-Droid on September 12, 2026. That amounted to 102 apps, which was quite a lot of work for me to go through.😅

If you just want the results, feel free to skip to [the results](#statistics--conclusion)

# Apps

<!---
Couple of notes:
1. I add comments between apps to add a bit of spacing so as to not get lost mentally.
2. Some justifications are copy pasted as I don't expect anyone to read the entire list one by one. The colors are the important part.
-->

<!--
1.
-->

{{< icon src="https://f-droid.org/repo/com.greenart7c3.nostrsigner/en-US/icon_GZCnTG4XMU5dhZlyqLj_Jqq0XZAtLTxd-65FCcmhGTI=.png" >}}Amber{{< /icon >}}

**Description:** Nostr event signer for Android 

**Repository:** https://github.com/greenart7c3/Amber

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** All recent commits were done with LLM, PRs accepted from agents, Claude Code and Codex infrastructure present.


<!--
2.
-->

{{< icon src="https://f-droid.org/repo/com.poppingmoon.aria/en-US/icon_nKGYjQuir4PxWAkdmuR1hbe9QAaUXGe0y2SR3dcTMv8=.png" >}}Aria for Misskey {{< /icon >}}
**Description:** Dive into the interplanetary microblogging platform 🚀

**Repository:** https://github.com/poppingmoon/aria

{{<good>}}<b>Rating:</b> No signs of AI {{</good>}}<br>

**Justification:** This is a hard one as commit naming and structure felt a bit suspicious, but I did not see anything else and decided to err on the side of caution

<!--
3.
-->

{{< icon src="https://f-droid.org/repo/com.saad_khan_rind.atmosphere_effect/en-US/icon_zn4JfT94J57Iy4F_OC1yqg_sCMK1yK63gA-bl1nncbE=.png" >}}Atmo Engine{{< /icon >}}
**Description:** Animated wallpapers with Atmosphere, Glass, Canvas Sketch and playlists. 

**Repository:** https://github.com/saad-khan-rind/nosatmosphereeffect

{{<good>}}<b>Rating:</b> No signs of AI {{</good>}}<br>

**Justification:** Heavy emoji usage in the README, but otherwise nothing looks suspicious.

<!--
4.
-->

{{< icon src="https://f-droid.org/repo/deckers.thibault.aves.libre/en-US/icon_GH5gV0fwEdeDoKaG3fRGgig1tdXzVQ9W7ULgoCprtEg=.png" >}}Aves Libre{{< /icon >}}
**Description:** Gallery and metadata explorer 

**Repository:** https://github.com/deckerst/aves

{{<good>}}<b>Rating:</b> No signs of AI {{</good>}}<br>

**Justification:** Nothing looked suspicious

<!--
5.
-->

{{< icon src="https://f-droid.org/repo/com.ashkanrafiee.balance/en-US/icon_wce8C-_r5q2DySbH7r8lr4Se78_kXuSFapenQNtd6IE=.png" >}}Balance{{< /icon >}}
**Description:** Private offline bank balance dashboard

**Repository:** https://github.com/AshkanRafiee/balance

{{<bad>}}<b>Rating:</b> Mostly AI {{</bad>}}<br>

**Justification:** Code and commits exhibit various AI smells.

<!--
6.
-->

{{< icon src="https://f-droid.org/repo/com.baly_groceries_tracker.app/en-US/icon_Ox4zvd1J_FjmuC3uB2tUG1pgXJgjJzvheVWWYIWuKUc=.png" >}}Baly Groceries Tracker {{< /icon >}}
**Description:** Track your groceries, without worrying about running out.

**Repository:** https://github.com/rw-account/baly_groceries_tracker

{{<ok>}}<b>Rating:</b> Mostly human {{</ok>}}<br>

**Justification:** Some inconsistent code styles, suspiciously formatted README and a very "AI-type" UI style. Otherwise, nothing concrete.

<!--
7.
-->

{{< icon src="https://f-droid.org/repo/com.guiforge.bati/en-US/icon_2yUxMAqWJSWncbEQytCu6o34VKihA6O_rYTd_B5h8Eg=.png" >}}Bati: Fitness RPG {{< /icon >}}
**Description:** Turn workouts into quests, boss fights and a village built by your training. 

**Repository:** https://github.com/Guiforge/bati

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** AI disclosure in README (Thanks for making it easy :D)

<!--
8.
-->

{{< icon src="https://f-droid.org/repo/io.github.derweh.bayesianbahn/en-US/icon_0DfMXPWL8CARvikM2heJQrUQvjP-xynK5WKDMSRQnhs=.png" >}}BayesianBahn {{< /icon >}}
**Description:** Empirical arrival-time distributions for Deutsche Bahn trains 

**Repository:** https://github.com/DerWeh/BayesianBahn

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** All commits are Claude co-authored. Though it's really funny how Deutsche Bahn sucks so hard it has enticed people to vibe-code unofficial timetables.

<!--
9.
-->

{{< icon src="https://f-droid.org/repo/com.beatbridge/en-US/icon_xkxSOe14huX18OAsEfJxwfkIYEPYSbWbixzhtMd3XgU=.png" >}}BeatBridge: Bluetooth Music{{< /icon >}}
**Description:** Auto-play music when your Bluetooth car, headphones, or speakers connect. 

**Repository:** https://github.com/brandonp2412/BeatBridge

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** Includes Claude Code contributions, quite a lot of the commits look to be at least AI

<!--
10.
-->

{{< icon src="https://f-droid.org/repo/de.markusfisch.android.binaryeye/en-US/icon_JCQAH6daJAEg6038ZyKnweYEAYfbht0wrM_VejEpLxg=.png" >}}Binary Eye{{< /icon >}}
**Description:** QR code and barcode scanner with no ads 

**Repository:** https://github.com/markusfisch/BinaryEye

{{<good>}}<b>Rating:</b> No signs of AI{{</good>}}<br>

**Justification:** Nothing suspicious

<!--
11.
-->

{{< icon src="https://f-droid.org/repo/com.blockdrop.game/en-US/icon_R7byf9tq_bbXkI9cIvjnnyTqL-olhrG2QdyCOVb1YzE=.png" >}}BlockDrop: Block Puzzle{{< /icon >}}
**Description:** Free and open source block-stacking puzzle game. Arrange falling shapes to clear 

**Repository:** https://github.com/brandonp2412/BlockDrop

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** Has infrastructure for LLMs, Claude co-authored commits.

<!--
12. 
-->

{{< icon src="https://f-droid.org/repo/com.inspiredandroid.braincup/en-US/icon_ztWvt7sbgVZVcq8e_YkBfgSc3BFjvKwEGZRyGwgtAQk=.png" >}}Braincup - Brain Training {{< /icon >}}
**Description:** Train your focus, memory and math skills. 

**Repository:** https://github.com/SimonSchubert/Braincup

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** All recent commits are Claude co-authored

<!--
13
-->

{{< icon src="https://f-droid.org/repo/cc.kafuu.bilidownload/en-US/icon_CQ3B9pPSHorTct4vGlrWxSuP3kgAwB-YSoRM_cjraRw=.png" >}}BVD{{< /icon >}}
**Description:** bilibili video resource downloader 

**Repository:** https://github.com/KafuuNeko/BiliDownload

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** All recent commits look LLM authored

<!--
14
-->

{{< icon src="https://f-droid.org/repo/com.yepgoryo.CaptureCap/en-US/icon_RNoeN1UIc2LfP3maIkifINMg5F3VawqiaAaMTivlwm8=.png" >}}CaptureCap{{< /icon >}}
**Description:** Record and Stream Audio and/or Screen 

**Repository:** https://github.com/yepgoryo/CaptureCap

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** Has an AI disclosure listing files written with LLM help

<!--
15
-->

{{< icon src="https://f-droid.org/repo/org.avmedia.gshockGoogleSync/en-US/icon_ACZLCCNVH-iUZaYaR7VREkB_WFwCMQjmbyGgxtnNCf4=.png" >}}Casio G-Shock Smart Sync {{< /icon >}}
**Description:** Add smart functions to your Casio square BT G-Shock Watch. 

**Repository:** https://github.com/izivkov/CasioGShockSmartSync

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** AI artifacts such as planning .md files pushed to repo.

<!--
16
-->

{{< icon src="https://f-droid.org/repo/app.chompass/en-US/icon_tf1GtLGXCMMC-57N73q7zOuwTu_gNDNTTNI5xl8Dv5U=.png" >}}Chompass - Calorie Tracker {{< /icon >}}
**Description:** Ad-free AI calorie tracker. Snap, speak, or type meals. Open source.

**Repository:** https://codeberg.org/fitguy/chompass

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** Recent commits look AI authored. Note that this repository is hosted on Codeberg and likely violates their terms of use.

<!--
17.
-->

{{< icon src="https://f-droid.org/assets/ic_repo_app_default_KNN008Z2K7VNPZOFLMTry3JkfFYPxVGDopS1iwWe5wo=.png" >}}DeltaSync {{< /icon >}}
**Description:** Encrypted KeePass sync — requires your own self-hosted server.

**Repository:** https://gitlab.com/Star95/keepass-deltasync

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** All recent commits co-authored by Claude Opus 5

<!--
18.
-->

{{< icon src="https://f-droid.org/repo/duress.keyboard/en-US/icon_5i5gWHSJE_aBhzYGneHzKysVUDk7-3k8b0MoqDFwd3s=.png" >}}DuressKeyboard{{< /icon >}}
**Description:** Keyboard that reacts to triggers and performs security actions

**Repository:** https://github.com/pofesk0/lastcodeduresskeyboard

{{<ok>}}<b>Rating:</b> ???{{</ok>}}<br>

**Justification:** This may be the most confusing repo I've ever seen lol. Has been in development since November of 2025, but the owner doesn't seem to know how to use git??? All the commits have seemingly been done by copy pasting the change code by hand through the GitHub web file editor. Quite bizarre!

<!--
19.
-->

{{< icon src="https://f-droid.org/repo/com.app.equran/en-US/phoneScreenshots/icon_qMOnmrt1nUZO-81YcT0zNfn43PTBFbpIe6GPb3CmAdI=.png" >}}eQuran {{< /icon >}}
**Description:** Read, listen, choose from 5 reciters, and track your Quran journey. 

**Repository:** https://github.com/ya27hw/equran_app

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** Has infrastructure for agents; most recent commit looks LLM generated.

<!--
20.
-->

{{< icon src="https://f-droid.org/repo/io.evcc.android/en-US/icon_wFhC9Y6ybuk49qSVCvFXc6DcRBb5g9QGKeKZ-Vi9OWc=.png" >}}
evcc - solar charging {{< /icon >}}
**Description:** charge your EV when the sun is shining or electricity is cheap and clean 

**Repository:** https://github.com/evcc-io/app

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** Agent infrastructure; Claude co-authorship of commits; even commits without explict co-authorship look largely LLM generated.

<!--
21
-->

{{< icon src="https://f-droid.org/repo/at.j0s.meyercard.app/en-US/icon_PnlVJrNHmsJHlCrg0B0M99Qru255zdcFGDPoW73yfk4=.png" >}}Fechtkarte{{< /icon >}}
**Description:** Warm-up drill card generator using notation credited to Joachim Meyer 

**Repository:** https://github.com/J0s3f/Fechtkarte

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** Agent infrastructure; commits and code look LLM generated

<!--
22
-->

{{< icon src="https://f-droid.org/repo/com.nononsenseapps.feeder/en-US/icon_Ab31f6rFiG70NRqjyOH87znJd2y38yiEg2Tz_lY791w=.png" >}}Feeder{{< /icon >}}
**Description:** An awesome Libre and Open Source RSS feed reader

**Repository:** https://github.com/spacecowboy/Feeder

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** Agentic infrastructure, most recent code commits look LLM generated, accepted PRs from agents.

<!--
23
-->

{{< icon src="https://f-droid.org/repo/app.simple.felicity/en-US/icon_wzX06hvULCl40mEvloaq9He6kIrgIAvirVFvagl8E_M=.png" >}}Felicity Music Player{{< /icon >}}
**Description:** Advance audiophile grade offline music player. 

**Repository:** https://github.com/Hamza417/Felicity

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** Several commits I checked exhibit signs of heavy LLM use.

<!--
24
-->

{{< icon src="https://f-droid.org/repo/com.fixupxer/en-US/icon_2jYJIM-2DrT24oOFBAkXsMOGHDtm5U_dRQes1KQaodc=.png" >}}FixupXer - URL Enhancer {{< /icon >}}
**Description:** Clean URL tracking, fix embeds (X, IG, FB, TikTok, Bluesky), catch link leaks 

**Repository:** https://github.com/NeatCode-Labs/fixupxer

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** AI generated icon + all recent commits look LLM generated.

<!--
25.
-->

{{< icon src="https://f-droid.org/repo/com.presley.flexify/en-US/icon_BBeJtKPePtGO8WiLmL6LHNQKPk9RX3_wjR-NipOxmNw=.png" >}}Flexify: Gym Workout Log {{< /icon >}}
**Description:** Log workouts, reps, cardio, and rest timers. Track strength offline.

**Repository:** https://github.com/brandonp2412/Flexify

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** Lot of LLM infrastructure; code looks almost entirely AI.

<!--
26
-->

{{< icon src="https://f-droid.org/repo/app.crossword.yourealwaysbe.forkyz/en-US/icon_9RC0QqpRkXPPUGy-rA-Mx9gDUvu7pF_qp44KtVq1lCw=.png" >}}Forkyz{{< /icon >}}
**Description:** Crossword puzzles application, download and play.

**Repository:** https://gitlab.com/Hague/forkyz

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** LLM infrastructure; recent commits look entirely LLM generated.

<!--
27
-->

{{< icon src="https://f-droid.org/repo/icons/com.gemwallet.android.836.png" >}}Gem Wallet: Bitcoin, USDT, BNB{{< /icon >}}
**Description:** Secure crypto wallet for 100+ blockchains: Bitcoin, USDT, ETH, Solana, and more. 

**Repository:** https://github.com/gemwalletcom/wallet

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** LLM infrastructure; recent commits look entirely LLM generated.

<!--
28
-->

{{< icon src="https://f-droid.org/repo/com.freetime.geoweather/en-US/icon_gMVPFW5a0RYLMrVigsfRnDmgsWlQCpyCUT6_waoOMyw=.png" >}}GeoWeather {{< /icon >}}
**Description:** Modern weather app with 16-day forecast for multiple cities 

**Repository:** https://github.com/FreetimeMaker/GeoWeather

{{<ok>}}<b>Rating:</b> Mostly Human{{</ok>}}<br>

**Justification:** Signs of heavy LLM use in the README and the website, however nothing too concrete in the code to be considered mostly AI

<!--
29
-->

{{< icon src="https://f-droid.org/repo/whl.trending.ai/en-US/icon_OMcBkXr0Hl2hgFFtzl1ShhzXqy2M1CCTi66I1YSoJZU=.png" >}}GitHub Trending & Hacker News {{< /icon >}}
**Description:** Daily AI picks from GitHub Trending, Hacker News & Product Hunt. 

**Repository:** https://github.com/HarlonWang/TrendingAI

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** All recent commits Claude co-authored.

<!--
30
-->

{{< icon src="https://f-droid.org/repo/dev.chungjungsoo.gptmobile/en-US/icon_xC52Uy3HV9fWm-FjuFMNMpF4B6LlcSTPbWSZJDZxeoU=.png" >}}GPTMobile{{< /icon >}}
**Description:** Your all in one chat assistant - Chat with multiple LLMs at once! 

**Repository:** https://github.com/Taewan-P/gpt_mobile

{{<ok>}}<b>Rating:</b> Mostly human{{</ok>}}<br>

**Justification:** Has LLM Infrastructure, however a decent amount of contributions look human, so I'm giving the benefit of the doubt.

<!--
31
-->

{{< icon src="https://f-droid.org/repo/com.gymmane.app/en-US/icon_ce_NtWH4KDZ11zN7TxmGuthD1EW4l48BZffQUtX46zk=.png" >}}GymMane {{< /icon >}}
**Description:** Dark, offline gym log. Tap the muscle, log your sets, watch your numbers move. 

**Repository:** https://github.com/InlitX/GymMane

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** README got that LLM emoji vomit; very high inbound code frequency. UI looks like what LLMs like to generate.

<!--
32
-->

{{< icon src="https://f-droid.org/repo/xyz.lepisma.harp/en-US/icon_N54xD3hrsvQLHhcItDbBOGyX_Af8QoImaoye3jRbmR8=.png" >}}
Harp{{< /icon >}}
**Description:** Private on-device Personal Health Record Application 

**Repository:** https://git.sr.ht/~lepisma/harp-kmp

{{<ok>}}<b>Rating:</b> Not sure {{</ok>}}<br>

**Justification:** My browser could not get through the sourcehut bot-detection test for some reason, so I was unable to check code. Saw one commit co-authored by Claude, status of others remains unknown.

<!--
33
-->

{{< icon src="https://f-droid.org/repo/com.sidhant.huespill/en-US/icon_NiuiaUFYQcnqu9FdSFKujDwWgljWToPr0i6TP2bmsmw=.png" >}}Hue Spill {{< /icon >}}
**Description:** Fill the entire board with a single color. 

**Repository:** https://github.com/sidhant947/HueSpill

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** Very new, only few commits. UI looks vibe-coded though and UI is all this game has.

<!--
34
-->

{{< icon src="https://f-droid.org/repo/com.a4a.g8invoicing/en-US/icon_KljiCtpx75APEIWy45knYOWNO5oyqEz7uFw2m_7Tn4I=.png" >}}
invoice, quote, delivery note {{< /icon >}}
**Description:** Invoice in 10 seconds — bundle quotes and delivery notes into invoices! 

**Repository:** https://github.com/gatesuperapp/g8-invoicing

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** All recent commits co-authored by Claude.

<!--
35.
-->

{{< icon src="https://f-droid.org/repo/com.seiko.keystoreviewer/en-US/icon_TBqQdKR9l_zLhwAi-MxRBxQ6gaAntkjXOr3aMYZQ5rA=.png" >}}KeyStoreViewer {{< /icon >}}
**Description:** Quickly view MD5, SHA1, and Public Keys for App Signatures. 

**Repository:** https://github.com/qdsfdhvh/KeyStoreViewer

{{<bad>}}<b>Rating:</b> Mostly AI {{</bad>}}<br>

**Justification:** Recent commits look entirely AI generated.

<!--
36
-->

{{< icon src="https://f-droid.org/repo/de.kitshn.android/en-US/icon_KDwu4yHOCStyP2LD4Lj90QVwS9UscFzFcGCjEp_YSlY=.png" >}}
kitshn (for Tandoor) {{< /icon >}}
**Description:** An unofficial client for the self-hosted Tandoor recipe management software. 

**Repository:** https://github.com/kitshn-app/kitshn

{{<good>}}<b>Rating:</b> No signs of AI{{</good>}}<br>

**Justification:** Nothing looks suspicious

<!--
37
-->

{{< icon src="https://f-droid.org/repo/com.buzbuz.smartautoclicker/en-US/icon_z13taPHqDPZUJ6Cmi4D4-mJ7jZUDODEPNZobLcArC-w=.png" >}}Klick'r - Smart AutoClicker{{< /icon >}}
**Description:** Automating clicks based on what is displayed 

**Repository:** https://github.com/Nain57/Smart-AutoClicker

{{<good>}}<b>Rating:</b> No signs of AI{{</good>}}<br>

**Justification:** Nothing looks suspicious

<!--
38
-->

{{< icon src="https://f-droid.org/repo/com.lenshrv.foss/en-US/icon_aTwP8VkkgfOh70xOR8QHSHqJH-zMrDPNpRsHaSSJzy0=.png" >}}Lens HRV {{< /icon >}}
**Description:** Measure heart-rate variability with your phone camera, no extra sensors 

**Repository:** https://github.com/LensHRV/lenshrv-app

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** Born from one +10k LOC "init" commit. 2 remaining commits look LLM authored and so does the UI.

<!--
39
-->

{{< icon src="https://f-droid.org/repo/com.svenjacobs.app.leon/en-US/icon_0TpKYOySnqGg3Zf5j2DvaPsQPvwixVKjjeUnG5gMJZ4=.png" >}}Léon – The URL Cleaner {{< /icon >}}
**Description:** Removes tracking & other redundant parameters from web links for sharing 

**Repository:** https://github.com/leon-cleaning-services/leon

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** LLM infrastructure; recent commits look entirely LLM generated.

<!--
40
-->

{{< icon src="https://f-droid.org/repo/ch.cryptobit.letterbox/en-US/icon_zoGHBNEY5CWnViAJjPbeT-CQf9folgBwdJyKN7nzpFw=.png" >}}
LetterBox {{< /icon >}}
**Description:** LetterBox is a simple kids game for learning letters 

**Repository:** https://gitlab.com/muelli/letterbox

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** Recent commits look entirely AI generated.

<!--
41
-->

{{< icon src="https://f-droid.org/repo/com.ashkanrafiee.librecontactsbackup/en-US/icon_FvbwDtiVkt-65ACbL-v-ZcVMgDbsppkdGQ74cTcCZ-g=.png" >}}Libre Contacts Backup {{< /icon >}}
**Description:** Offline and encrypted contact backups 

**Repository:** https://github.com/AshkanRafiee/Libre-Contacts-Backup

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** All recent commits look entirely AI generated.

<!--
42
-->

{{< icon src="https://f-droid.org/repo/org.grakovne.lissen/en-US/icon_k3qflE2tlusghVDchLiwAQtD1ThlIwF3RcDyw1-hA3A=.png" >}}Lissen: Audiobookshelf client {{< /icon >}}
**Description:** Clean Audiobookshelf Player

**Repository:** https://github.com/GrakovNe/lissen-android/

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** Most recent commits look AI generated.

<!--
43
-->

{{< icon src="https://f-droid.org/repo/com.kapoue.maintask/en-US/icon_yyxfO6WgnGlaC02592zIzR8c8nNdwgePq3C_Gp2GzSs=.png" >}}MainTask {{< /icon >}}
**Description:** Reminders for your recurring tasks: filters, plants, backups, car checks… 

**Repository:** https://codeberg.org/kapoue/MainTask

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** All recent commits co-authored by Claude Sonnet 5. Note that this repository is hosted on Codeberg and likely violates their terms of use.

<!--
44
-->

{{< icon src="https://f-droid.org/repo/com.rama.mako/en-US/icon_Bj9HdZXSbsWpqM22LhtmRWj-iaAhfrRAb7I8L260JVo=.png" >}}Mako {{< /icon >}}
**Description:** Privacy-first Android launcher designed for focus, speed, and simplicity. 

**Repository:** https://github.com/rama-io/mako

{{<good>}}<b>Rating:</b> No signs of AI{{</good>}}<br>

**Justification:** Nothing too suspicious.

<!--
45
-->

{{< icon src="https://f-droid.org/repo/com.codesail.market_monk/en-US/icon_Qu3fnN5fH1Now8Jow43psqTT3EkD9i4MKMizBRo2m6A=.png" >}}MarketMonk: Stock Tracker{{< /icon >}}
**Description:** Track stocks, build a portfolio, and view performance charts. 

**Repository:** https://github.com/brandonp2412/MarketMonk

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** LLM infrastructure; recent commits look entirely LLM generated.

<!--
46
-->

{{< icon src="https://f-droid.org/repo/com.markleaf.notes/en-US/icon_iKCUvFem5MW77aWy-F-iP04PrOqkRiDmwbUQBU98Wj4=.png" >}}
Markleaf{{< /icon >}}
**Description:** Local-first Markdown notes with tags, search, and file export 

**Repository:** https://github.com/jeiel85/markleaf-android

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** LLM infrastructure; recent commits look entirely LLM generated.

<!--
47
-->

{{< icon src="https://f-droid.org/repo/com.matedroid/en-US/icon_2GiNj_nCJ4fimLLj7gx266bmvz9VyQ3psUA12aCEXwE=.png" >}}MateDroid {{< /icon >}}
**Description:** View Tesla vehicle data from your self-hosted Teslamate instance 

**Repository:** https://github.com/vide/matedroid

{{<bad>}}<b>Rating:</b> Mostly AI {{</bad>}}<br>

**Justification:** LLM infrastructure; recent commits look entirely LLM generated.

<!--
48
-->

{{< icon src="https://f-droid.org/repo/us.materialio.app/en-US/icon_quZ7RZQvMLI9N63aMc-9T-o7xp0QTQUUw8mYE21KXe4=.png" >}}
Materialious {{< /icon >}}
**Description:** Modern material design for YouTube and Invidious. 

**Repository:** https://github.com/Materialious/Materialious

{{<good>}}<b>Rating:</b> No signs of AI {{</good>}}<br>

**Justification:** Only a brief look, but nothing jumped out as suspicious.

<!--
49
-->

{{< icon src="https://f-droid.org/repo/de.metager.metagerapp.fdroid/en-US/icon_9aiPOGzOgkgpP7Ho9ASWceZ22Kr0oR5O5j0gZqHh4sw=.png" >}}MetaGer: Search & Browser{{< /icon >}}
**Description:** Anonymous search and tab groups, private browsing with tracker and ad blocking. 

**Repository:** https://gitlab.metager.de/metager/metager-app

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** LLM infrastructure; recent commits look entirely LLM generated.

<!--
50
-->

{{< icon src="https://f-droid.org/repo/com.prayer_times/en-US/icon_sfJSGlR4HZXhltyTaYj85NDwX7ub5k5pMOLi2PjP9Ys=.png" >}}Mihrab: Prayer Times & Quran {{< /icon >}}
**Description:** Adhan alarms, qibla compass, the Madinah mushaf, widgets. No trackers. 

**Repository:** https://github.com/Hassan-PS/Mihrab

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** LLM infrastructure; recent commits look entirely LLM generated.

<!--
51
-->

{{< icon src="https://f-droid.org/repo/io.github.johnathan.minesweeper/en-US/icon_w64bbni9FlmRvNy0Ydwds11cHCRz2frr0zB-g4sl15Y=.png" >}}
Minesweeper {{< /icon >}}
**Description:** Beautiful Minesweeper. No ads, no trackers, no permissions. 

**Repository:** https://github.com/john-athan/minesweeper

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** Most recent commits look entirely AI generated. So does the UI.

<!--
52
-->

{{< icon src="https://f-droid.org/repo/com.katoaapps.openminilaunch/en-US/icon_Krfk5dFvldkdnTATbfaEA2VV-wOaoA7kjVfVb6WEpLo=.png" >}}MinkLauncher OpenSource {{< /icon >}}
**Description:** A minimal, keyboard-first Android home-screen launcher 

**Repository:** https://github.com/katoaapps/openminilaunch

{{<good>}}<b>Rating:</b> No signs of AI {{</good>}}<br>

**Justification:** Was suspicious about the incredibly verbose README, but could not find anything else.

<!--
53
-->

{{< icon src="https://f-droid.org/repo/io.github.trevarj.motd/en-US/icon_yEpE9BzrO4KCXV-Wa2h9lBtARJ56IdOx9V-G4CLmU04=.png" >}}
motd {{< /icon >}}
**Description:** Native IRC client with a modern chat interface 

**Repository:** https://github.com/trevarj/motd

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** LLM infrastructure; recent commits look entirely LLM generated.

<!--
54
-->

{{< icon src="https://f-droid.org/repo/com.nevar.nzik.foss/en-US/icon_jwU6JfMRHnizN7jEYsDhxb-aQVfBhsrc5SiB_D0v9eY=.png" >}}N-Zik {{< /icon >}}
**Description:** A modern, multilingual YouTube Music client for Android with offline support. 

**Repository:** https://github.com/N-Zik-Group/N-Zik

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** LLM infrastructure; recent commits look entirely LLM generated.

<!--
55
-->

{{< icon src="https://f-droid.org/repo/com.appmindlab.nano/en-US/icon_7HRkBQqHPzRcKtLnmnZsktsCmOq5s3LfkpQp7nBT-Dg=.png" >}}neutriNote CE{{< /icon >}}
**Description:** A hub of written thoughts in fast searchable plain text

**Repository:** https://github.com/appml/neutrinote

{{<good>}}<b>Rating:</b> No signs of AI {{</good>}}<br>

**Justification:** Found nothing.

<!--
56
-->

{{< icon src="https://f-droid.org/repo/com.nextcloud.client/en-US/icon_uMFXKXpFQnnVroYp_Oxtrb4w_rVoRJ4Zi85v0NPY1ZY=.png" >}}Nextcloud {{< /icon >}}
**Description:** Synchronization client 

**Repository:** https://github.com/nextcloud/android

{{<ok>}}<b>Rating:</b> Mostly Human{{</ok>}}<br>

**Justification:** Has LLM infrastructure, but most commits look human.

<!--
57
-->

{{< icon src="https://f-droid.org/repo/dev.casraf.pantry/en-US/icon_9ocRMprNlRQ9litxrxk0dkGaNs0gQYnojP0iUk7vm08=.png" >}}Nextcloud Pantry {{< /icon >}}
**Description:** Shared household lists, photos & notes on your own server — and on your watch. 

**Repository:** https://github.com/chenasraf/pantry-flutter

{{<bad>}}<b>Rating:</b> Mostly AI {{</bad>}}<br>

**Justification:** Most recent commits look entirely AI generated. So does the UI.

<!--
58
-->

{{< icon src="https://f-droid.org/repo/com.nfcalarmclock/en-US/icon_6daA89N1TIb1DI5jcVke-47OBb-xVEdET_eS4LLtLAs=.png" >}}NFC Alarm Clock {{< /icon >}}
**Description:** Customizable and feature-rich alarm clock app. 

**Repository:** https://github.com/gabeg805/NFC-Alarm-Clock

{{<good>}}<b>Rating:</b> No signs of AI{{</ok>}}<br>

**Justification:** Nothing looks suspicious.

<!--
59
-->

{{< icon src="https://f-droid.org/repo/jp.nonbili.noutube/en-US/icon_A1nC0BkAzsvNhws7y1thjfhF8LJJReXVUORApHsstDE=.png" >}}NouTube {{< /icon >}}
**Description:** YouTube and YouTube Music in a single app. No ads, plays in the background. 

**Repository:** https://github.com/nonbili/NouTube

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** Most recent commits look AI generated.

<!--
60
-->

{{< icon src="https://f-droid.org/repo/com.novadial.phone/en-US/icon_5sXOpMpB9B-kKWorT65-6F-Cg8cKpT6TsjDVcXyyb_s=.png" >}}
NovaDial {{< /icon >}}
**Description:** Unlock a secure, open-source calling experience with NovaDialer 

**Repository:** https://github.com/dhilipmpms/NovaDial

{{<good>}}<b>Rating:</b> No signs of AI{{</good>}}<br>

**Justification:** Nothing looks off at a quick glance.

<!--
61
-->

{{< icon src="https://f-droid.org/repo/dev.davidv.translator/en-US/icon_GEAckWVv4ZVJ9tzqlXEm1CJ2LgDy-mhWQipIBE5m4P8=.png" >}}Offline Translator {{< /icon >}}
**Description:** On-device translation of text, images and pdf/odt files, with TTS

**Repository:** https://github.com/DavidVentura/offline-translator

{{<good>}}<b>Rating:</b> No signs of AI{{</good>}}<br>

**Justification:** Nothing looks off at a quick glance.

<!--
62
-->

{{< icon src="https://f-droid.org/repo/icons/com.dt.opnsense_manager.163.png" >}}
OPNsense Manager {{< /icon >}}
**Description:** Manage OPNsense firewall: monitor, configure rules, view logs & services 

**Repository:** https://github.com/Etregin/OPNsense_Manager

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** Most recent commits look AI generated.

<!--
63
-->

{{< icon src="https://f-droid.org/repo/com.emanuelef.remote_capture/en-US/icon_TJT256J_Rd4v-6FCoLNzys-8hkM0nt5ayiphLs5CEN0=.png" >}}PCAPdroid {{< /icon >}}
**Description:** No-root network monitor, firewall and PCAP dumper for Android

**Repository:** https://github.com/emanuele-f/PCAPdroid

{{<good>}}<b>Rating:</b> Almost no signs of AI {{</good>}}<br>

**Justification:** Some commits include LLM created translations, however they are disclosed and few and far between 

<!--
64
-->

{{< icon src="https://f-droid.org/repo/m.co.rh.id.a_personal_stuff/en-US/icon_ksxV4Iw6cEKktJ74LSwPauCL0m-GzdrimXdceeLPSgU=.png" >}}
Personal Stuff {{< /icon >}}
**Description:** App used to track, manage and remind you of your own stuff. 

**Repository:** https://github.com/rh-id/a-personal-stuff

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** A lot of recent commits look AI generated.

<!--
65
-->

{{< icon src="https://f-droid.org/repo/com.asksakis.freegate/en-US/icon_Oje0h96pLEiukZaeYfRjZBBOjCW59kbJk26NSSC-P8I=.png" >}}Phylax{{< /icon >}}
**Description:** Viewer for Frigate NVR with smart URL switching and notifications

**Repository:** https://github.com/sfortis/phylax

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** Most recent commits look AI generated.

<!--
66
-->

{{< icon src="https://f-droid.org/repo/com.jarsilio.android.pingoff/en-US/icon_JukW7ha2_SyD55UdQA2y2pjqNNe84zJaZX-euGsUZbk=.png" >}}PingOff{{< /icon >}}
**Description:** Silence your phone automatically when using selected apps. 

**Repository:** https://gitlab.com/juanitobananas/ping-off

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** LLM infrastructure; most commits look entirely LLM generated.

<!--
67
-->

{{< icon src="https://f-droid.org/repo/InfinityLoop1309.NewPipeEnhanced/en-US/icon_CWQFN3-pZavxIDWYPYl4GHg-v7k6uCvk6PkmD9S8gSo=.png" >}}PipePipe{{< /icon >}}
**Description:** A FLOSS Android app to let you browse YouTube, NicoNico and BiliBili freely. 

**Repository:** https://github.com/InfinityLoop1308/PipePipe

{{<ok>}}<b>Rating:</b> Mostly Human{{</ok>}}<br>

**Justification:** Originally I marked this as "Mostly LLM" due to some commits being suspicious and translations being added manually whenever adding features. On reflection, the commits in question were mostly made by outside contributors and the translations I've confirmed to be basic MTL, not AI.

<!--
68
-->

{{< icon src="https://f-droid.org/repo/com.ismartcoding.plain/en-US/icon_mg0Jp4Y1WFWVDsM3Hn84dZejuiMUunbKxAfx2CzjrZ4=.png" >}}PlainApp: Phone Web Portal {{< /icon >}}
**Description:** Manage your phone on the web! Access files, contacts, videos, music & more. 

**Repository:** https://github.com/plainhub/plain-app

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** Most recent commits look AI generated and so does the README.

<!--
69
-->

{{< icon src="https://f-droid.org/repo/io.github.dorumrr.privacyflip/en-US/icon_BSCWtcVzqrd0Wm1YvxBLBqt8dO2Km7qnQl65Cz88x_E=.png" >}}Privacy Flip{{< /icon >}}
**Description:** Manage your device privacy based on lock/unlock state 

**Repository:** https://github.com/dorumrr/privacyflip

{{<bad>}}<b>Rating:</b> Mostly AI {{</bad>}}<br>

**Justification:** Most recent commits look AI generated and so does the README.

<!--
70
-->

{{< icon src="https://f-droid.org/repo/com.sidhant.queens/en-US/icon_YR31byh1Qe3h22ESJHgL0_HcpSpqRAVgEa8JtQtAAPI=.png" >}}Queens {{< /icon >}}
**Description:** Challenging crown-placement logic puzzle. Infinite levels. No tracking & ads. 

**Repository:** https://github.com/sidhant947/queens

{{<ok>}}<b>Rating:</b> Mostly human{{</ok>}}<br>

**Justification:** Some AI smells, but maintainer has refused some LLM generated PRs and has contacted to confirm it's mostly human.

<!--
71
-->

{{< icon src="https://f-droid.org/repo/icons/dev.tulis.readbear.15.png" >}}ReadBear{{< /icon >}}
**Description:** A cute&chill CBZ, PDF, EPUB reader that's ridiculously configurable!

**Repository:** https://github.com/Tulis12/ReadBear

{{<good>}}<b>Rating:</b> No signs of AI{{</good>}}<br>

**Justification:** Some commits look a bit suspicious, but at a glance I did not see any obvious signs of explicit LLM usage.

<!--
72
-->

{{< icon src="https://f-droid.org/repo/icons/com.saadibra.graymatter.9.png" >}}Relatrix{{< /icon >}}
**Description:** An active knowledge-management and multi-modal note-taking platform. 

**Repository:** https://github.com/saad-ibra/gray-matter

{{<bad>}}<b>Rating:</b> Mostly AI {{</bad>}}<br>

**Justification:** Most recent commits look AI generated + found some stray undeleted LLM thinking comments. UI has that AI look.

<!--
73
-->

{{< icon src="https://f-droid.org/repo/com.reteclock/en-US/icon_KipeS4dGUow1Qf7eGufH_SMo8D7TT9xUH8DlA0C9S4U=.png" >}}ReteClock{{< /icon >}}
**Description:** Full-screen digital clock and dock screensaver for old Android phones. 

**Repository:** https://github.com/rubidus-api/reteclock_apk

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** All recent commits are co-authored by Claude.

<!--
74
-->

{{< icon src="https://f-droid.org/repo/com.retekey/en-US/icon_NzTFfQz5QbbrCATxGOZg9CxCTYUgsAc6uLn_RnTWUD0=.png" >}}ReteKey{{< /icon >}}
**Description:** Hangul keyboard with Esc, Tab, Ctrl and F-keys. 470 KB, one permission. 

**Repository:** https://github.com/rubidus-api/retekey_apk

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** All recent commits are co-authored by Claude.

<!--
75
-->

{{< icon src="https://f-droid.org/repo/me.hackerchick.sharetoinputstick/en-US/icon_ARDbiOm9r-IkhyTpKY99tEz-E0M58zQhbYHQkXfK3Kw=.png" >}}
Share To InputStick {{< /icon >}}
**Description:** Send text to your InputStick straight from the Share menu 

**Repository:** https://github.com/TheLastProject/ShareToInputStick

{{<good>}}<b>Rating:</b> No signs of AI{{</good>}}<br>

**Justification:** Nothing suspicious

<!--
76
-->

{{< icon src="https://f-droid.org/repo/com.shatteredpixel.shatteredpixeldungeon/en-US/icon_sGrA1aakL86yLytAeV0fds7P_nAq5FZvoABR78V9p0Y=.png" >}}
Shattered Pixel Dungeon {{< /icon >}}
**Description:** A roguelike game based on Pixel Dungeon 

**Repository:** https://github.com/00-Evan/shattered-pixel-dungeon

{{<good>}}<b>Rating:</b> No signs of AI {{</good>}}<br>

**Justification:** Some stuff looks a bit sus, but found nothing serious.

<!--
77
-->

{{< icon src="https://f-droid.org/repo/dev.halim.shelfdroid/en-US/icon_SgZffFAbBzshy-mehtEyBEcBVO5C4p4tVtRNXtrZJfI=.png" >}}ShelfDroid{{< /icon >}}
**Description:** Audiobookshelf Android client with playback, downloads, and server management 

**Repository:** https://github.com/100nandoo/shelfdroid

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** LLM infrastructure; recent commits look entirely LLM generated.

<!--
78
-->

{{< icon src="https://f-droid.org/repo/com.arslan.shizuwall/en-US/icon_bdge3hq1qJXtWFm1kMPmYgD8Ipfp1Jv7iHGjF3kHQx0=.png" >}}
ShizuWall {{< /icon >}}
**Description:** Lightweight no root, no vpn firewall solution powered by Shizuku

**Repository:** https://github.com/AhmetCanArslan/ShizuWall

{{<ok>}}<b>Rating:</b> Mostly Human{{</ok>}}<br>

**Justification:** Found some evidence of AI usage, however nothing that looks too widespread.

<!--
79
-->

{{< icon src="https://f-droid.org/repo/dev.dettmer.simplenotes/en-US/icon_PupcRr_ROR0RHB-SWaQTP5PkkTa_UKW4qfjzGUzd0Sg=.png" >}}Simple Notes Sync{{< /icon >}}
**Description:** Offline notes & checklists, self-hosted sync. Under 5 MB, no ads, no tracking. 

**Repository:** https://github.com/inventory69/simple-notes-sync

{{<bad>}}<b>Rating:</b> Mostly AI {{</bad>}}<br>

**Justification:** Most recent commits look AI generated.

<!--
80
-->

{{< icon src="https://f-droid.org/repo/com.google.android.stardroid/en-US/icon_sjDgvxgimqjLph9kXRyxjeSAy18B30TXnwSp1OPwYl8=.png" >}}Sky Map{{< /icon >}}
**Description:** Sky Map turns your phone into a window on the night sky. 

**Repository:** https://github.com/sky-map-team/stardroid

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** LLM infrastructure; recent commits look entirely LLM generated.

<!--
81
-->

{{< icon src="https://f-droid.org/repo/icons/site.remlit.snowdrop.8.png" >}}Snowdrop{{< /icon >}}
**Description:** Multiplatform Mastodon API client using Compose 

**Repository:** https://github.com/ihateblueb/snowdrop

{{<good>}}<b>Rating:</b> No signs of AI{{</ok>}}<good>

**Justification:** Authors have confirmed no LLM usage + .noai file present

<!--
82
-->

{{< icon src="https://f-droid.org/repo/com.forrestguice.suntimescalendars/en-US/icon_X2cjb2yh-S0bOQYBMHwLzGBgqv1MjagF5PVseZz8m_U=.png" >}}
Suntimes Calendars {{< /icon >}}
**Description:** A calendar provider add-on for Suntimes. 

**Repository:** https://github.com/forrestguice/SuntimesCalendars

{{<good>}}<b>Rating:</b> No signs of AI{{</good>}}<br>

**Justification:** Nothing looks suspicious

<!--
83
-->

{{< icon src="https://f-droid.org/repo/com.tacticmaster/en-US/icon_6ajdMZpML86PFICBN-AavwtK6TJ5pPP3pgSUans0JE8=.png" >}}TacticMaster{{< /icon >}}
**Description:** Chess tactic trainer based on https://database.lichess.org/#puzzles. 

**Repository:** https://github.com/jazzm0/tactic-master

{{<good>}}<b>Rating:</b> No signs of AI{{</good>}}<br>

**Justification:** Nothing looks suspicious

<!--
84
-->

{{< icon src="https://f-droid.org/repo/icons/io.github.herrerad85.tallybook.86.png" >}}Tallybook{{< /icon >}}
**Description:** Private, offline-first expense and budget tracker, no account required

**Repository:** https://github.com/herrerad85/tallybook

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** Most recent commits look AI generated.

<!--
85
-->

{{< icon src="https://f-droid.org/repo/org.tasks/en-US/icon_hj4Uw7qW4b2sruhcSPVU6kuNoHV4QGWgIXjyUqJ36KA=.png" >}}Tasks.org: Open-source To-Do Lists & Reminders {{< /icon >}}
**Description:** Private, ad-free task lists! Optional sync with Google Tasks, CalDAV or EteSync!

**Repository:** https://github.com/tasks/tasks

{{<good>}}<b>Rating:</b> No signs of AI{{</good>}}<br>

**Justification:** Nothing looks suspicious

<!--
86
-->

{{< icon src="https://f-droid.org/repo/com.terminator.app/en-US/icon_RcNSQQqE3o-wxe8MfjdmV30rfqdQkPq_PGQztH7HhTU=.png" >}}Terminator{{< /icon >}}
**Description:** Multi-session terminal emulator with Material UI theming and root support

**Repository:** https://github.com/8dmusichannels-star/terminator

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** Most recent commits look AI generated.

<!--
87
-->

{{< icon src="https://f-droid.org/repo/org.ntust.app.tigerduck.fdroid/en-US/icon_QvM-s4jf536w1jQqonyN-sCDE84ZiV6h8bSBcCzc3sI=.png" >}}TigerDuck{{< /icon >}}
**Description:** NTUST campus assistant for courses, assignments, and more

**Repository:** https://github.com/tigerduck-app/tigerduck-app-android

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** LLM infrastructure; recent commits look entirely LLM generated.

<!--
88
-->

{{< icon src="https://f-droid.org/repo/io.timelimit.android.aosp.direct/en-US/icon_PaxylMiI-rzWjB0htPOybrteCvWUw53r2aMbnCc10FA=.png" >}}
TimeLimit.io {{< /icon >}}
**Description:** Flexibly limit the usage duration 

**Repository:** https://codeberg.org/timelimit/timelimit-android

{{<good>}}<b>Rating:</b> No signs of AI{{</good>}}<br>

**Justification:** Nothing looks suspicious

<!--
89
-->

{{< icon src="https://f-droid.org/repo/io.github.benji377.timety/en-US/icon_MbyiMimHJQhjlPgV0cxgLLuu4H635xNsfmc1sH-u2UQ=.png" >}}Timety{{< /icon >}}
**Description:** Offline-first productivity, focus, and habit tracking. 

**Repository:** https://github.com/Benji377/Timety

{{<bad>}}<b>Rating:</b> Mostly AI {{</bad>}}<br>

**Justification:** Most recent commits look AI generated.

<!--
90
-->

{{< icon src="https://f-droid.org/repo/de.quantumphysique.trale/en-US/icon_PRm7zDLDtSy3gjvyMQJ2xEvnMkr8S6rWkDLPouBjwCo=.png" >}}trale{{< /icon >}}
**Description:** privacy-respecting body weight-diary 

**Repository:** https://github.com/QuantumPhysique/trale

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** LLM infrastructure; recent commits look mostly LLM generated.

<!--
91
-->

{{< icon src="https://f-droid.org/repo/com.omaawr.tuisku/en-US/icon_EAUK0Lj7rqo7FHXoJmDdpH6AfXLpGsBhKXYPQI0WKhY=.png" >}}Tuisku{{< /icon >}}
**Description:** A simple and lightweight encrypted notes app 

**Repository:** https://github.com/omaawr/tuisku

{{<good>}}<b>Rating:</b> No signs of AI{{</good>}}<br>

**Justification:** Explicit no-AI policy.

<!--
92
-->

{{< icon src="https://f-droid.org/repo/com.unciv.app/en-US/icon_sZApOXTOdudh1zFJUN27SZ-DHeo2Pf1WHAKLDWBB4oA=.png" >}}Unciv{{< /icon >}}
**Description:** Open source 4X civilization-building game 

**Repository:** https://github.com/yairm210/Unciv

{{<ok>}}<b>Rating:</b> Mostly Human{{</ok>}}<br>

**Justification:** Some commits co-authored by Claude, but a bunch of others look human.

<!--
93
-->

{{< icon src="https://f-droid.org/repo/app.pwhs.universalinstaller/en-US/icon_p-rH0BQeCPDezlzb9mJ4WVIsPTFcXL3KqUZN64ulZbs=.png" >}}Universal Installer {{< /icon >}}
**Description:** APK/XAPK installer with silent installs via Shizuku, Root or Dhizuku.

**Repository:** https://github.com/pass-with-high-score/universal-installer

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** LLM infrastructure; recent commits look mostly LLM generated.

<!--
94
-->

{{< icon src="https://f-droid.org/repo/unlicense.launcher/en-US/icon_bk3BgkgNTOQVVMdl3m7ncHnEFl9Y3-CLO1bvzP9xWx4=.png" >}}UnlicenseLauncher {{< /icon >}}
**Description:** Simple and secure FOSS launcher with fully FREE🐍 license 

**Repository:** https://github.com/sirdeepsleep/UnlicenseLauncher

{{<ok>}}<b>Rating:</b> ???{{</ok>}}<br>

**Justification:** Looks to be a repeat of "DuressKeyboard". Quite a bizarre repo, but it looks like the accounts are different.

<!--
95
-->

{{< icon src="https://f-droid.org/repo/dev.victorialauncher/en-US/icon_YWVha_IBczQuyk93VAKcS6tGYJBjv6T1LfoXnaE0ezA=.png" >}}Victoria Launcher {{< /icon >}}
**Description:** A minimal, list-based home screen and open source Niagara Launcher alternative 

**Repository:** https://github.com/adelmonte/victoria-launcher

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** Most recent commits look AI generated.

<!--
96
-->

{{< icon src="https://f-droid.org/repo/org.y20k.voxscribe/en-US/icon__SHucbtS8Lcd9o94BAnClKcbpIOOwpo6gzleTqn4OxE=.png" >}}Voxscribe - Offline Voice Input {{< /icon >}}
**Description:** Voxscribe is an offline voice keyboard that transcribes speech on-device. 

**Repository:** https://codeberg.org/y20k/voxscribe

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** Most recent commits look AI generated. Note that this repository is hosted on Codeberg and likely violates their terms of use.

<!--
97
-->

{{< icon src="https://f-droid.org/repo/com.sidhant.watersort/en-US/icon__Hx3ALGVyL66fo2t2nhkM4FWsEIqqcXAaoN787StznY=.png" >}}
Water Sort {{< /icon >}}
**Description:** Relaxing color-sorting puzzle. Infinite levels. Zero tracking. No ads.

**Repository:** https://github.com/sidhant947/water-sort

{{<ok>}}<b>Rating:</b> Not sure{{</ok>}}<br>

**Justification:** README shows lots of AI signs, but I did not see anything too suspicious in code.

<!--
98
-->

{{< icon src="https://f-droid.org/repo/com.jarsilio.android.waveup/en-US/icon_y0Mvvnrd7wU8OXpYqk4iTLE-Al_8oIwyR1tY7AS3aII=.png" >}}WaveUp{{< /icon >}}
**Description:** Turn on the display by waving 

**Repository:** https://gitlab.com/juanitobananas/wave-up/tree/HEAD

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** LLM infrastructure; most commits look entirely LLM generated.

<!--
99
-->

{{< icon src="https://f-droid.org/repo/org.wikipedia/en-US/icon_Z9wprwa6ZGVuIVGDvXIrqKTMPNP-9xliVcQ9RN9eOvs=.png" >}}Wikipedia{{< /icon >}}
**Description:** The official app for Wikipedia, the world’s largest source of information. 

**Repository:** https://github.com/wikimedia/apps-android-wikipedia

{{<ok>}}<b>Rating:</b> Mostly Human{{</ok>}}<br>

**Justification:** Most commits look human made, but there's quite a lot of claude infrastructure. I know! I thought Wikipedia would be an easy pass too!

<!--
100
-->

{{< icon src="https://f-droid.org/repo/com.lazydevs.wristotle/en-US/icon_fgLvtXomFB2sOHLVZ5RukPpJFfsbFnpIVuoKG7itO1w=.png" >}}Wristotle Companion {{< /icon >}}
**Description:** Voice control for Pebble watches — on-device by default, no account. 

**Repository:** https://codeberg.org/wristotle/wristotle-companion

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** Most recent commits look AI generated. Note that this repository is hosted on Codeberg and likely violates their terms of use.

<!--
101
-->

{{< icon src="https://f-droid.org/repo/com.kingzcheung.xime/en-US/icon_HP39r4s1__qnRhAuLvDEaGRSTTTxjJDNBZ3X7E-pQMA=.png" >}}Xime IME{{< /icon >}}
**Description:** A Rime-based Chinese IME for Wubi and Pinyin input 

**Repository:** https://github.com/ximeiorg/Xime

{{<bad>}}<b>Rating:</b> Mostly AI{{</bad>}}<br>

**Justification:** LLM infrastructure; recent commits look mostly LLM generated.

<!--
102
-->

{{< icon src="https://f-droid.org/repo/com.yubico.yubioath/en-US/icon_n1gfcqvpep4h5S24_2j1ixPAH3k3RxE08gglmBTR63c=.png" >}}Yubico Authenticator {{< /icon >}}
**Description:** Generate OATH codes with YubiKey NEO over NFC 

**Repository:** https://github.com/Yubico/yubioath-flutter

{{<bad>}}<b>Rating:</b> Mostly AI {{</bad>}}<br>

**Justification:** Most recent commits look AI generated.

# Some interesting observations

## brandonp2412
While going through the apps I noticed one user named **brandonp2412** maintaining quite a few in this update cycle. Of course, all entirely vibe-coded.

That wouldn't be that much of a surprise, however they all seem to be under widely different namespaces. Some are just the app name, but some are quite confusing: "com.presley.\*" or "com.codesail.\*".

Either they're just a very avid vibe-coder, or they're one of those agents that have been given a GitHub account for some reason.

## Codeberg
Out of the 5 apps hosted on Codeberg, 4 are mostly AI generated and thus likely violate Codeberg's AI policy.

## The "Don't tread on me" apps
I also noticed a pair of very bizarre apps, both branded with the yellow "Don't tread on me" flag. 

DuressKeyboard & UnlicenseLauncher

What's most curious is that they have been in development for quite some time, yet all the changes are done not with git but through the GitHub web file editor!

Someone go find that person and teach them to use git😭😭.

# Statistics & Conclusion

Out of 102 apps:
```
{{<bad>}}<b>66</b> were largely written by AI <b>(64.7%)</b>{{</bad>}}
{{<ok>}}<b>13</b> were hard to categorize one way or another <b>(12.7%)</b>{{</ok>}}
{{<good>}}<b>24</b> showed little to no signs of AI involvement <b>(23.5%)</b>{{</good>}}
```

Really not sure how to cope with these numbers though.

On one hand, some seem to have quite a *few* users. And if people are having their lives improved by using said software, who am I to say "no"?

On the other hand, I'm really concerned about what the data means for the FOSS community as a whole.

I explicitly did not do any code quality analysis as that would have taken much more time and would have probably been out of my skill level anyway, but I am curious about the robustness and maintainability of the 72%.

Just for fun I also checked a few of the FOSS apps I actually use and quite a few showed signs of heavy LLM usage.

I'll still use them, as I find them useful, but this whole experiment has left me feeling quite conflicted.

I know how to fix this though:

Hey Claude, make a load-bearing time machine set to 2016 -- a time when I was a happy kid, nothing bad ever happened and all was good in FOSS-land.

Make no mistakes
