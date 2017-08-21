---
date: 2013-07-24 00:00:00 +0000
description: ""
menu:
  developing-with-jekyll:
    weight: 6
related:
- title: Jekyll Build Command Options
  url: https://jekyllrb.com/docs/configuration/#build-command-options
tags: ""
title: Environments
---

There are three unique developer environments when working with a Jekyll site in Forestry:

* **Local environment** this is your local development environment on your own machine. See [Local Development](/docs/developing-with-jekyll/local-development) for more info.

* **Staging environment** this is the environment Forestry creates when we generate a preview for you. See [Previewing](/docs/deployment-and-management/previewing) for more info.

* **Production environment** this is the environment Forestry publishes your site to. See [Setting Up Deployment](/docs/deployment-and-management/setting-up-deployment) for more info.

In order to make development easier, Forestry sets the environment variable `JEKYLL_ENV` based on the environment you’re in.

This allows you to set up conditional code in your layouts in order to handle paths, content, or functionality dependant on a specific environment.

This variable is accessible in your templates as `{{ jekyll.environment }}`.

The values are:

```
Local environment: "development"
Staging environment: "staging"
Production environment: "production"

```