---
title: FoundryVTT Header Authentication
description: OpenSource Contribution.
slug: foundry-vtt-header-auth
date: 2025-09-02 01:00:00+0000
# image: cover.jpg
categories:
  - personal_projects
tags:
  - PR
  - SSO
weight: 1 # You can add weight to some posts to override the default sorting (date descending)
---

It was mostly a learning experience as I never touched header-based authentication before, but I needed this to work and the plugin didn't support it.

I've added the documentation on how to make it work with Authentik, both Authentik, Traefik and FoundryVTT plugin configurations. The owner of the plugin was very kind and added support for configuring the `separator` that Authentik needed.

- [Project Repo](https://github.com/MaienM/foundry-vtt-header-auth)
- [PR Link](https://github.com/MaienM/foundry-vtt-header-auth/pull/1)
