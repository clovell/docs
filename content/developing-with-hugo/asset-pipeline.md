---
date: 2013-07-24 00:00:00 +0000
description: ""
menu:
  developing-with-hugo:
    weight: 5
related:
- title: “Gulp.js”
  url: http://gulpjs.com/
- title: “Grunt.js”
  url: https://gruntjs.com/
tags: ""
title: Asset Pipeline
---

If you’re planning on using any preprocessing on your assets (images, CSS, or JS) you’ll need to be careful how you implement this as it effects how Forestry builds your sites.

Hugo provides no built-in support for preprocessing, so you must use a third-party build tool like Gulp or Grunt.

## Best Practises for Gulp, Grunt, and Other Build Tools
Forestry does not currently support external build tools in the build process.

When publishing, previewing, or saving drafts, Forestry will *only* run:
`hugo build`

If you use Gulp, Grunt or another build tool to process your assets, you *must* commit your final working assets to your repository, otherwise [previewing][1] and [deployment][2] will **not** work.

[1]: /docs/site-configuration/previewing
[2]: /docs/deployment-and-management/setting-up-deployment

