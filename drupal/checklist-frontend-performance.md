# Frontend Performance Checklist for Drupal websites
> A checklist & guide to make sure you (Drupal 8.x+) website will be fast! Made for Drupal frontend developers and site builders.

# Table of Contents
- [Frontend Performance Checklist for Drupal websites](#frontend-performance-checklist-for-drupal-websites)
- [1. Checklist](#1-checklist)
  * [1.1 HTML](#11-html)
  * [1.2 Images](#12-images)
  * [1.3 CSS](#13-css)
  * [1.4 JS](#14-js)
  * [1.5 Assets](#15-assets)
  * [1.6 Fonts](#16-fonts)
  * [1.7 PWA](#17-pwa)
  * [1.8 Network](#18-network)
  * [1.9 Server](#19-server)
- [2. Drupal modules](#2-drupal-modules)
  * [2.1 Development related](#21-development-related)
  * [2.2 Caching related](#22-caching-related)
  * [2.3 Image optimmizations](#23-image-optimmizations)
  * [2.4 Other](#24-other)
- [3. Tools](#3-tools)
  * [3.1 Performance scoring - Online](#31-performance-scoring---online)
  * [3.2 Performance scoring - Offline (local installed)](#32-performance-scoring---offline-local-installed)
  * [3.3 Sprite Generators](#33-sprite-generators)
  * [3.4 Unused CSS - Online](#34-unused-css---online)
  * [3.5 Unused CSS - Offline](#35-unused-css---offline)
  * [3.6 Critical CSS/AboveTheFold CSS - Online](#36-critical-css-abovethefold-css---online)
  * [3.7 Critical CSS/AboveTheFold CSS - Offline](#37-critical-css-abovethefold-css---offline)
  * [3.8 Image optimization - Online](#38-image-optimization---online)
  * [3.9 Image optimization - Offline CLI](#39-image-optimization---offline-cli)
  * [3.10 Image optimization - Offline GUI](#310-image-optimization---offline-gui)
  * [3.11 Minify CSS/JS](#311-minify-css-js)
  * [3.12 CDN with free tiers](#312-cdn-with-free-tiers)
  * [3.13 Other tools](#313-other-tools)
- [4. Guides & Resources](#4-guides---resources)
  * [4.1 Collections of tools, posts etc](#41-collections-of-tools--posts-etc)
  * [4.2 Image Optimization](#42-image-optimization)
  * [4.3 Drupal related articles](#43-drupal-related-articles)
- [5. Similar projects](#5-similar-projects)
- [6. Licence](#6-licence)

<small><i><a href='http://ecotrust-canada.github.io/markdown-toc/'>Table of contents generated with markdown-toc</a></i></small>


# 1. Checklist
## 1.1 HTML

- [ ] Core theme [Classy](https://git.drupalcode.org/project/drupal/tree/8.8.x/core/themes/classy) is your friend. Most of the times you could use this a the **base theme** and its templates to make overrides.
- [ ] Mobile first design except if there is no need
- [ ] Critical link (aka css) tags are in head
- [ ] Less critical link tags are end of body
- [ ] Less critical link tags lazy load
  - [ ] `<link rel="preload" as="style" onload="this.rel='stylesheet'" id='dashicons-css' >`
- [ ] JS loads with the async property
  - [ ] `<script async src="https://hi.js"></script>`
  - [ ] or `defer` when scripts need to be loaded in order, or require the DOMContentLoaded Event
- [ ] Keep DOM simple and small (Maximum DOM Depth < 12). Must "kill" some of the default Drupal wrappers
- [ ] Create custom and simple 404, 403 error pages using twig template suggestions

## 1.2 Images

- [ ] Always use next gen formats
  - [ ] webp -> chrome/firefox (Also use https://modernizr.com to inspect WebP support)
  - [ ] jpeg xr -> ie11/edge
  - [ ] jpeg 2000 -> safari
- [ ] Use jpg for photography, not png
- [ ] Size images properly
- [ ] Use srcsets for multiple image sizes
- [ ] Use the `<picture>` element to let the browser select the right image for a scenario
- [ ] Lazy load images below the fold (see [1](https://developers.google.com/web/fundamentals/performance/lazy-loading-guidance/images-and-video), [2](https://imagekit.io/blog/lazy-loading-images-complete-guide))

## 1.3 CSS

- [ ] Avoid using `!important`
- [ ] Use svg instead of icon fonts like fontawesome
- [ ] Create svg sprites (or png sprites if svg are not available)
- [ ] Do not support olb browsers (remove too old prefixes)
- [ ] Avoid expensive selectors when possible
  - [ ]  `border-radius`
  - [ ]  `box-shadow`
  - [ ]  `transform`
  - [ ]  `filter`
  - [ ]  `:nth-child`
  - [ ]  `position: fixed;`
  - [ ]  Partial matching: `[class^="wrap"]`
- [ ]  Don't use universal selectors
  - [ ]  Avoid universal selectors like `*, [disabled], [type=“text”]`, etc. They are very expensive for the browser to match, as every element in the DOM must be checked.
- [ ]  Avoid deeply nested dependent selectors
  - [ ]  The descendant selector is very costly, as the browser must check for a match with every descendant element. On a complex web page, this can result in thousands and thousands (perhaps even more) of descendant selector searches.
- [ ]  Use media queries to load files based on use case
  
```css 
<link href="style.css" rel="stylesheet" media="all">
<link href="portrait.css" rel="stylesheet" media="orientation:portrait">
<link href="print.css" rel="stylesheet" media="print">
<link href="desktop.css" rel="stylesheet" media="(min-width: 720px)">
```
- [ ] Investigate using functional css instead of custom styles (eg [Tailwind](https://tailwindcss.com), [Tachyons](https://tachyons.io) etc. See more at https://css-tricks.com/need-css-utility-library)
- [ ] If you are able to run (automated) builds do not include compiled css or js in your vcs code but only their sources


## 1.4 JS

- [ ] Bundles should always be minified
- [ ] Bundles should have 0 comments, and all license text extracted to a separate file
- [ ] Use [Google Tag Manager](https://tagmanager.google.com) for 3rd party scripts like Google Analytics, FB Pixel etc
- [ ] Move js on bottom of the html page

## 1.5 Assets

- [ ]  All assets should be fingerprinted
- [ ]  All assets should have `Cache-Control: max-age=365000000, immutable` as a header
- [ ]  Assets should be served over http/2
- [ ]  Assets should only be served on a cookieless domain
- [ ]  All files should be cached by a CDN
- [ ]  Support Brotli compression if able
  - [ ]  15-30% smaller than gzip
- [ ]  Compress with gzip, or zopfli as a fallback to brotli
- [ ]  Do not ship unused css, js
- [ ]  Try to clone external js/css to local server and load them from there (eg Google Analytics script)

## 1.6 Fonts

- [ ] Fonts should always load `woff2` first
- [ ] `woff` for fallback
- [ ] Use `font-display: swap;` to allow the browser to use a fallback font while custom font files are being downloaded.
- [ ] eot or truetype is only needed for `IE < 10`

## 1.7 PWA

- [ ] Use a service worker to cache assets
- [ ] Use a service worker to prefetch pages users will most likely navigate to next
- [ ] Support offline, and spotty networks
- [ ] Make sure that the tracking or other third party js/css files (eg Google Analytics etc) are not included on the PWA

## 1.8 Network

- [ ] Test site with Network Throttling. See a [list of common Network speed](https://gist.github.com/theodorosploumis/fd4086ee58369b68aea6b0782dc96a2e)

## 1.9 Server
- [ ] Prefer Nginx over Apache2 (at least as a proxy)


---

# 2. Drupal modules
## 2.1 Development related
- https://www.drupal.org/project/seo_checklist
- https://www.drupal.org/project/html_checker
- https://www.drupal.org/project/healthcheck
- https://www.drupal.org/project/blackfire
- https://www.drupal.org/project/devel (webprofiler)
- https://www.drupal.org/project/performance_budget
- https://www.drupal.org/project/perfmon

## 2.2 Caching related
- **https://www.drupal.org/project/advagg**
- https://www.drupal.org/project/http_cache_control
- https://www.drupal.org/project/big_pipe_sessionless
- https://www.drupal.org/project/prefetch_cache
- https://www.drupal.org/project/cdn (and other CDN related modules)
- https://www.drupal.org/project/fastly
- https://www.drupal.org/project/stackpath

## 2.3 Image optimizations
- https://www.drupal.org/docs/8/mobile-guide/responsive-images-in-drupal-8
- https://www.drupal.org/project/lazy
- https://www.drupal.org/project/blazy
- https://www.drupal.org/project/lazyloader
- https://www.drupal.org/project/fancyload
- https://www.drupal.org/project/drimage
- https://www.drupal.org/project/imageapi_optimize
- https://www.drupal.org/project/imageapi_optimize_webp
- https://www.drupal.org/project/imageapi_optimize_binaries
- https://www.drupal.org/project/imagemagick
- https://www.drupal.org/project/webp

## 2.4 Other
- **https://www.drupal.org/project/quicklink**
- **https://www.drupal.org/project/minifyhtml**
- https://www.drupal.org/project/critical_css
- https://www.drupal.org/project/amp
- https://www.drupal.org/project/amp_cts
- https://github.com/Drupal-Jedi/css-tree-shaking
- https://www.drupal.org/project/pwa
- https://www.drupal.org/project/fast_404
- https://www.drupal.org/project/refreshless

---

# 3. Tools
## 3.1 Performance scoring - Online
- https://developers.google.com/speed/pagespeed/insights
- https://www.thinkwithgoogle.com/feature/testmysite
- https://yellowlab.tools
- https://www.webpagetest.org
- https://tools.pingdom.com
- https://search.google.com/test/mobile-friendly
- https://web.dev/measure
- https://gtmetrix.com
- https://www.uptrends.com/tools/website-speed-test
- https://gf.dev/website-audit
- https://www.giftofspeed.com
- https://varvy.com/pagespeed
- https://www.gumlet.com/analyzer
- https://www.dareboost.com
- https://www.checkbot.io
- https://whatdoesmysitecost.com
- https://compare.sitespeed.io (Beta)
- https://www.drupalaudit.com
- https://webhint.io
- https://waterfaller.dev

## 3.2 Performance scoring - Offline (local installed)
- https://www.sitespeed.io
- https://github.com/sitespeedio/coach
- https://www.sitespeed.io/documentation/throttle
- https://developers.google.com/web/tools/lighthouse
- https://github.com/gmetais/YellowLabTools
- https://github.com/sitespeedio/browsertime
- http://devbridge.github.io/Performance
- https://github.com/GoogleChromeLabs/psi
- https://github.com/paulirish/pwmetrics
- https://github.com/desktoppr/wbench
- http://yslow.org/command-line-har

## 3.3 Sprite Generators
- https://instantsprite.com (online - png/gif export)
- https://github.com/frexy/svg-sprite-generator
- https://github.com/sprity/sprity
- https://github.com/itsjavi/spritesheet-generator
- https://github.com/selaux/node-sprite-generator

## 3.4 Unused CSS - Online
- https://unused-css.com
- https://uncss-online.com
- https://www.jitbit.com/unusedcss
- https://purifycss.online
- https://cssstats.com

## 3.5 Unused CSS - Offline
- **https://github.com/Drupal-Jedi/css-tree-shaking**
- https://github.com/uncss/uncss
- https://www.purgecss.com
- https://github.com/probosckie/cssTreeShaking
- https://github.com/AlanJenkinsVS/css-tree-shaking
- https://github.com/purifycss/purifycss
- https://github.com/leeoniya/dropcss

## 3.6 Critical CSS/AboveTheFold CSS - Online
- https://criticalcss.com
- https://jonassebastianohlsson.com/criticalpathcssgenerator
- https://www.sitelocity.com/critical-path-css-generator

## 3.7 Critical CSS/AboveTheFold CSS - Offline
- **https://github.com/stefspakman/drupal-critical**
- https://github.com/addyosmani/critical
- https://github.com/filamentgroup/criticalCSS
- https://github.com/pocketjoso/penthouse
- https://github.com/finkinfridom/kant.io
- https://github.com/bezoerb/inline-critical
- https://github.com/hummal/crittr
- https://github.com/GoogleChromeLabs/critters
- https://github.com/theKashey/used-styles
- https://github.com/filamentgroup/loadCSS

## 3.8 Image optimization - Online
- https://resmush.it
- https://convertio.co/jpg-webp
- https://kraken.io
- https://www.gumlet.com
- https://imageoptim.com
- https://imagekit.io
- https://tinypng.com
- https://tinyjpg.com
- https://compressjpeg.com
- https://compresspng.com
- https://way2enjoy.com/compress-jpeg
- https://shortpixel.com
- https://imagify.io
- https://optimole.com
- https://compressor.io/compress
- https://squoosh.app
- https://imageengine.io
- https://blinkloader.com
- https://www.jpegmini.com
- http://thumborize.me
- https://rokka.io

## 3.9 Image optimization - Offline CLI
**WebP**
- https://github.com/imagemin/imagemin-webp

**JPEG**
- https://github.com/tjko/jpegoptim
- https://github.com/danielgtaylor/jpeg-archive
- https://github.com/technopagan/adept-jpg-compressor
- https://github.com/imagemin/jpeg-recompress-bin
- https://github.com/mozilla/mozjpeg
- https://github.com/google/butteraugli
- https://github.com/google/guetzli

**PNG**
- https://pngquant.org
- https://github.com/shssoichiro/oxipng

**SVG**
- https://github.com/svg/svgo
- https://github.com/jkphl/svg-sprite

**GIF**
- https://github.com/kohler/gifsicle

**General**
- https://github.com/ravgeetdhillon/create-optimize-images (bash wrapper)
- https://github.com/libvips/libvips
- https://github.com/imagemin/imagemin
- https://github.com/imagemin/imagemin-cli
- https://github.com/lovell/sharp
- https://github.com/google/zopfli
- https://github.com/charlyie/resmushit-cli
- https://github.com/psliwa/image-optimizer (PHP library)
- https://github.com/avalanche123/Imagine (PHP library)
- https://glide.thephpleague.com (PHP library)
- http://image.intervention.io (PHP library)
- https://github.com/joedicastro/img4web (Python script)
- https://fengyuanchen.github.io/compressorjs (JS library)

## 3.10 Image optimization - Offline GUI
- https://www.xnview.com/en/xnconvert
- https://trimage.org
- https://pnggauntlet.com
- https://jakearchibald.github.io/svgomg
- https://hvdwolf.github.io/pyExifToolGUI
- https://github.com/imagemin/imagemin-app

## 3.11 Minify CSS/JS
- https://github.com/mishoo/UglifyJS2
- https://github.com/cssnano/cssnano

## 3.12 CDN with free tiers
- https://anyone.cdn.biz.id
- https://jetpack.com/pricing
- https://www.cloudflare.com/plans
- https://shift8cdn.com
- https://www.coralcdn.org
- https://cloudinary.com
- **https://github.com/thumbor/thumbor** (OS, self-hosted)

## 3.13 Other tools
- **https://instant.page**
- https://github.com/turbolinks/turbolinks
- https://polyfill.io
- [CodePen - Performance Budget Builder](https://codepen.io/bradfrost/pen/EPQVBp)
- https://github.com/tkadlec/grunt-perfbudget
- https://micmro.github.io/PerfCascade
- https://github.com/filamentgroup/glyphhanger

---

# 4. Guides & Resources
## 4.1 Collections of tools, posts etc
- https://github.com/fabkrum/web-performance-resources
- https://developer.yahoo.com/performance/rules.html
- https://perf.rocks
- https://www.perf-tooling.today
- https://web.dev 
- https://browserdiet.com
- https://css-tricks.com/tools-for-optimizing-svg
- https://moz.com/learn/seo/page-speed

## 4.2 Image Optimization
- https://images.guide
- https://css-tricks.com/converting-and-optimizing-images-from-the-command-line
- https://jeremy.codes/blog/bulk-image-optimization-in-bash
- https://jeremy.codes/blog/faster-bulk-image-optimization-in-bash
- https://guides.wp-bullet.com/batch-optimize-jpg-lossy-linux-command-line-with-jpeg-recompress

## 4.3 Drupal related articles
- https://www.drupal.org/docs/8/modules/advanced-cssjs-aggregation/advanced-aggregates
- https://www.drupal.org/docs/8/mobile/front-end-performance
- https://www.fourkitchens.com/blog/article/use-grunt-and-advagg-inline-critical-css-drupal-7-theme
- https://pantheon.io/docs/guides/frontend-performance
- https://thinktandem.io/blog/2020/02/04/drupal-8-performance-tips-and-tricks-for-2020
- https://www.srijan.net/blog/performance-optimization-for-drupal-websites-intermediate-level
- [Debug Site Performance Using Web Profiler in Drupal 8 - Youtube, 2016](https://www.youtube.com/watch?v=pHf128w-1QQ)

---

# 5. Similar projects
- https://frontendchecklist.io
- https://github.com/thedaviddias/Front-End-Performance-Checklist
- https://web.dev/fast
- https://www.taskade.com/v/H1XaaoP0Ab
- https://jonyablonski.com/designers-wpo-checklist
- https://github.com/TerribleDev/WebPerformanceChecklist
- https://docs.google.com/spreadsheets/d/1PQTsn_A24CCSXtp8NcXg3ciL6IVa9LVJ_fG_e9oEH_0

--- 
# 6. Licence
[MIT](LICENSE.txt)
