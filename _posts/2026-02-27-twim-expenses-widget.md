---
layout: post
title:  "This Week in Matrix (TWIM) Expenses Widget"
date:   2026-02-27 08:40:00 +0000
categories: blog
---

I'm making a habit of writing TWIM posts perhaps, it's now 2 weeks in a row ... and perhaps I'll have two things to share this week. We'll see how the work on [Matrix Helm Charts](https://github.com/cyclikal94/matrix-helm-charts) shakes out.

This week the work I did on a UI update to the [matrix-community/expenses-matrix-widget](https://codeberg.org/matrix-community/expenses-matrix-widget), alongside better link parsing and CI is the subject of the post - including a fancy video to demonstrate the update and general functionality of the widget.

Why video creation / editing keeps coming up for me recently I'm not sure, but I need to find a better workflow. A tool I found perfect for these sorts of things [ScreenToGif](https://www.screentogif.com/) regrettably doesn't work on my current setup and it feels like doing basic things is so much harder - perhaps I'll find something better!

Anyway, once again, I'm including the post below:

### Expenses Widget

The Expense Widget is something you can add to your room to share expenses with your family and friends simply by sending lightweight, human-readable messages like so:

```
1000 nice dinner $ @me / @me @myfriend:example.com @myotherfriend:example.com
```

If you've been following along recent TWIMs you'll remember the [last TWIM update](https://matrix.org/blog/2026/02/13/this-week-in-matrix-2026-02-13/#expenses-widget) for the Expenses Widget a couple weeks ago where we shared some progress.

That update included work on a PR for Element Web, making the widget fully reactive, and adding support for room history exports. This time round the expense widget has gotten a whole new look courtesy of some shiny CSS, better link parsing to handle user mentions from more clients and some CI to automate the deployment of updates!

Check out the experience of using the updated widget in-room below:

<video controls preload="metadata" playsinline style="width: 100%; height: auto;">
  <source src="/assets/posts/2026-02-27-twim-expenses-widget-demo.mp4" type="video/mp4">
  Your browser does not support HTML video. <a href="/assets/posts/2026-02-27-twim-expenses-widget-demo.mp4">Download the video</a>.
</video>

**Interested?** Visit the repo at [matrix-community/expenses-matrix-widget](https://codeberg.org/matrix-community/expenses-matrix-widget) or add the widget now to your room by pasting the below command:

```bash
/addwidget https://matrix-expenses-widget-nightly.netlify.app/#/?widgetId=$matrix_widget_id&userId=$matrix_user_id&roomId=$matrix_room_id&baseUrl=$org.matrix.msc4039.matrix_base_url&deviceId=$org.matrix.msc3819.matrix_device_id
```

