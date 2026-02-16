---
layout: post
title:  "From FloorIt Ipsum to Godot Matrix RTC"
date:   2026-02-16 11:00:00 +0700
categories: blog
---

Greetings from Koh Phangan 🇹🇭 and the [Matrix Workation](https://matrix.org/blog/2026/02/13/this-week-in-matrix-2026-02-13/#matrix-workation-thailand-edition-th).

It's been a busy two weeks so far, with one left to go before heading back home. As part of the workcation, we've been working on various Matrix-related side projects.

One of mine being [Godot Matrix RTC](https://cyclikal.dev/godot-matrix-rtc/), which initially started with looking at [@toger5's Keyboard Kart](https://github.com/toger5/Godot-MatrixRTC-Keyboard-Kart) aka **FloorIt Ipsum** game.

Initially the plan was just to update the Godot project to bring the `join()` and `leave()` logic into the Godot application itself - instead of as html overlay elements.

I then planned to create a Pong-variant with an arena of `n + 1` sides, where `n` is the number of members in the RTC session. However I ended up adjusting *FloorIt Ipsum's** Game / UI to suit any orientation and sizing.

With that done, it kinda felt like the bones were there to make making more Godot Matrix RTC games easier by creating an add-on that handled all this for you - with a sample project to show potential UI setup.

So the plan for `godot-matrix-rtc-pong` was dropped and today I finished up the work for the `godot-matrix-rtc` plugin! 🎉

By the end, the original bridge code has been statically typed, generalised, documented and more. The plugin merges in the required export template, CI does all the Element Call SDK `dist` building for you while a Godot `EditorExportPlugin` handles putting it in the right place.

It's hard to know when to "stop", but if I didn't spend time polishing it now, it probably would never have been finished. Though I still think it'd be cool to add a lobby of joined members, and who knows what else!

So despite never really writing all that much, I figured I'd dust off (and bug fix!) this domains' site generation and put it up - to mark a completed project.

Special thanks goes to:
- [@toger5](https://github.com/toger5) and [FloorIt Ipsum](https://github.com/toger5/Godot-MatrixRTC-Keyboard-Kart)
- The FOSDEM'26 talk by Timo Kandra, Valere Fedronic and Robin Townsend - [MatrixRTC x Godot - A Battle Royale](https://fosdem.org/2026/schedule/event/UW9GKA-matrixrtc-godot-battle-royale/)
- Everyone on the [Matrix Workation](https://matrix.org/blog/2026/02/13/this-week-in-matrix-2026-02-13/#matrix-workation-thailand-edition-th)