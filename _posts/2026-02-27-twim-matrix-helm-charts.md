---
layout: post
title:  "This Week in Matrix (TWIM) Matrix Helm Charts"
date:   2026-02-27 17:00:25 +0000
categories: blog
---

**Update 2026-03-06**: The TWIM for [this week](https://matrix.org/blog/2026/03/06/this-week-in-matrix-2026-03-06/) is now live, you can check out this update there via [this link](https://matrix.org/blog/2026/03/06/this-week-in-matrix-2026-03-06/#matrix-helm-charts).

---

### Matrix Helm Charts

Over the course of 3 weeks whilst working from the Thailand island of Koh Phangan 🇹🇭 as part of the [Matrix Workation](https://matrix.org/blog/2026/02/13/this-week-in-matrix-2026-02-13/#matrix-workation-thailand-edition-th) - and 2 weeks back in reality - I've been working on creating a number of helm charts which can be used to deploy Matrix-related components into a Kubernetes cluster.

That's now available at [cyclikal94/matrix-helm-charts](https://github.com/cyclikal94/matrix-helm-charts)!

The idea is to create charts with example defaults that "Just Work" to deploy components with near-most all configuration deferring the the components' standard config file format

So far a few charts have been created for:

- `ntfy` a HTTP-based pub-sub notification service which can be used to provide Matrix push notifications on Android without Google via UnifiedPush. See [binwiederhier/ntfy](https://github.com/binwiederhier/ntfy).
    - Includes useful Matrix config defaults in an example `values.yaml`, so you don't have to "know" `ntfy`.
- `matrix-appservice-irc` an IRC bridge for Matrix. See [matrix-org/matrix-appservice-irc](https://github.com/matrix-org/matrix-appservice-irc)
- `mautrix-telegram` A Matrix-Telegram hybrid puppeting/relaybot bridge. See [mautrix/telegram](https://github.com/mautrix/telegram)

The work spent on `mautrix-telegram`, getting setup following the [Kubernetes](https://docs.mau.fi/bridges/general/docker-setup.html#kubernetes) guidiance, should mean I can get the remaining `mautrix` bridges as charts. The charts exist but are pending testing ... 🤖

#### Installing

Deploying should be as easy as:

1. Adding the Helm Repo:
```bash
helm repo add matrix-helm-charts https://cyclikal94.github.io/matrix-helm-charts
helm repo update
```
2. Setting up your `values.yaml` (just use the `values.matrix.example.yaml`) and plug in your homeserver details.
3. Deploy with:
```bash
helm upgrade --install matrix-appservice-irc matrix-helm-charts/matrix-appservice-irc -n matrix-appservice-irc --create-namespace --values matrix-appservice-irc-values.yaml
```
4. For App Service bridges (basically everything except `ntfy`) give Synapse the App Service Registration file - if you're using ESS Community it's just:
```yaml
synapse:
  appservices:
    - configMap: matrix-appservice-irc-registration
      configMapKey: appservice-registration-irc.yaml
```

Deploying `helm` charts / upgrades isn't exactly ... exciting, but here's a GIF anyway:

![Deploying ntfy, matrix-appservice-irc and mautrix-telegram](/assets/posts/2026-02-27-twim-matrix-helm-charts-install.gif)
