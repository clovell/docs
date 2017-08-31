---
date: 2013-07-24 00:00:00 +0000
description: ""
menu:
  developing-with-hugo:
    weight: 2
related:
- title: “Hugo Structure Reference”
  url: https://gohugo.io/overview/source-directory/
- title: “Hugo Support File Formats”
  url: https://gohugo.io/content/supported-formats/
- title: “Hugo Sections Reference”
  url: https://gohugo.io/content/sections/
- title: “Hugo Content Types Reference”
  url: https://gohugo.io/content/types/
- title: “Hugo Archetypes Reference”
  url: https://gohugo.io/content/archetypes/
tags: ""
title: Project Structure
---

In Hugo, project structure and naming is fairly rigid other than content structure. You must follow the Hugo guidelines for where content, layouts, data, and static assets must be stored.

Inside your content folder, you create the structure and organization that works for you.

For example, a Hugo site may look like this:

```
.
├── archetypes/ 
├── config.yml
├── data/
|   └── members.yml
├── layouts/
|   ├── footer.html
|   └── header.html
├── content/
|   ├── 2007-10-29-why-every-programmer-should-play-nethack.md
|   └── _index.md
├── public/
├── static/
|   ├── screen.css
|   └── main.js
├── themes/
|   └── example-theme

```

For a full breakdown on how this directory structure works, [see the Hugo docs](https://gohugo.io/overview/source-directory/).

## How Forestry Parses Hugo

Based on the example structure above, let’s explain how Forestry parses your site.

## Content

Forestry parses the `content/` folder for any applicable content.

Any content in the root of the content folder with be added to the "Pages" content type.

Any content in a subfolder will be added to a content type with the same name as that folder. *For example, `content/posts/`* would become the "Posts" content type.

## Data Files

Any files found inside the `_data/` folder are parsed as data files and are displayed individually in the CMS under the "Data" section.

## Front Matter Templates

Upon initial import, we will parse your site to generate [Front Matter Templates][1]. More details found in the [Front Matter Templates][1] doc.

## Themes

We will also parse the Archetypes of your theme folder when importing your site.

[1]: /docs/site-configuration/front-matter-templates