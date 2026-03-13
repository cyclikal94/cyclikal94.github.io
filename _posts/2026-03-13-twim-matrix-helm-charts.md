---
layout: post
title:  "This Week in Matrix (TWIM) Matrix Helm Charts v1.0.0"
date:   2026-02-27 17:00:25 +0000
categories: blog
---

### Matrix Helm Charts

**tl;dr** 10 new bridges and a new Installation Guide! Visit [cyclikal94/matrix-helm-charts](https://github.com/cyclikal94/matrix-helm-charts) to find helm charts to quickly deploy `ntfy`, `matrix-appservice-irc` and `mautrix-*` bridges.

[Matrix Helm Charts](https://github.com/cyclikal94/matrix-helm-charts) is a collection of... well... Helm Charts for Matrix! Easy to use charts designed to be deployed into Kubernetes to make setting up Bridges, Integrations and other related Matrix Ecosystem things simple.

#### What's new!

Previously `ntfy` an alternative push notification provider for Android; `matrix-appservice-irc` an IRC bridge; and the two Python-based `mautrix` bridges, `telegram` and `googlechat`; had been implemented.

This time, work on the Go-based `mautrix` bridges has been completed, with all 10 updated bridges now having accompanying helm charts!
- These all use a shared base chart, so when new Go bridges appear / changes occur, updates will be simple!
- Double puppetting is enabled by default and uses a shared App Service registration across all charts using the same base chart version.
- Let the charts automatically setup required postgres in namespace, or point them at your own.

Somehow theres been 300+ downloads of the `mautrix-whatsapp` chart already, with a smattering of love for the others, awesome that people are trying these out / hopefully finding useful! 😁

I plan to work through the matrix.org Ecosystem page for ideas on new charts to add, but suggestions very welcome!

#### Want to try yourself?

Deploying is as easy as:

1. Downloading the config `values.yaml` and configuring it to your setup:
    ```bash
    export CHART=mautrix-whatsapp
    curl -L "https://raw.githubusercontent.com/cyclikal94/matrix-helm-charts/main/charts/${CHART}/values.matrix.example.yaml" -o "${CHART}-values.yaml"
    ```
2. Installing the chart:
    ```bash
    helm upgrade --install "${CHART}" "oci://ghcr.io/cyclikal94/matrix-helm-charts/${CHART}" \
      --namespace "${CHART}" \
      --create-namespace \
      --values "./${CHART}-values.yaml"
    ```
3. For App Service bridges (basically everything except `ntfy`) give Synapse the App Service Registration file - if you're using ESS Community it's just:
    ```yaml
    synapse:
      appservices:
        - configMap: mautrix-whatsapp-registration
          configMapKey: appservice-registration-whatsapp.yaml
    ```

For more info, I've created an [Installation](https://github.com/cyclikal94/matrix-helm-charts/blob/main/INSTALLATION.md) guide!
