# Prominent Notice

These files have been changed, replaced, and customized for joyful use by Filestack, and this prominent notice has been added pursuant
to the terms and conditions of the Apache License Section 4 Article b. Many thanks to the DocuAPI team for their original work from
which this was forked and upon which this is based. While these changes are not intended to go upstream to the source project (as these
changes are largely branding related), still any parts of this customization that others may find useful are available also under the
terms of the Apache License.

Trademarks, brand marks, logos, and other properties of Filestack remain the property of Filestack and are copyrighted - not for use
by others without permission! This repository is the personal work of David Liedle, and is not an official Filestack project.

**DocuAPI** is a beautiful multilingual API documentation theme for [Hugo](http://gohugo.io/). This theme is built on top of the beautiful work of [Robert Lord](https://github.com/lord) and others on the [Slate](https://github.com/lord/slate) project ([Apache 2 License](https://github.com/lord/slate/blob/master/LICENSE)).

<br/>

> Visit the [demo site](https://docuapi.com/).

<br/>

![Screenshot DocuAPI Example site](https://raw.githubusercontent.com/bep/docuapi/master/images/screenshot.png)

## Use

See the [exampleSite](https://github.com/bep/docuapi/tree/master/exampleSite) and more specific its site [configuration](https://github.com/bep/docuapi/blob/master/exampleSite/config.toml) for the available options.

**Most notable:** This theme will use all the (non drafts) pages in the site and build a single-page API documentation. Using `weight` in the page front matter is the easiest way to control page order.

If you want a different page selection, please provide your own `layouts/index.html` template.

## Hooks

When the fix for [#2549](https://github.com/spf13/hugo/issues/2549) is released we may do this with blocks, but until then you can provide some custom partials:

* `partials/hook_head_end.html` is inserted right before the `head` end tag. Useful for additional styles etc.
* `partials/hook_body_end.html` which should be clear by its name.
* `partials/hook_left_sidebar_start.html` the start of the left sidebar
* `partials/hook_left_sidebar_end.html` the end of the left sidebar
* `partials/hook_left_sidebar_logo.html` the log `img` source

The styles and Javascript import are also put in each partial and as such can be overridden if really needed:

* `partials/styles.html`
* `partials/js.html`

## Develop the Theme

**Note:** In most situations you will be well off just using the theme and maybe in some cases provide your own template(s). Please refer to the [Hugo Documentation](http://gohugo.io/overview/introduction/) for that.

But you may find styling issues, etc., that you want to fix. Those Pull Requests are warmly welcomed!

**If you find issues that obviously belongs to  [Slate](https://github.com/lord/slate), then please report/fix them there, and we will pull in the latest changes here.**

This project provides a very custom asset bundler in [bundler.go](https://github.com/bep/docuapi/blob/master/bundler.go) written in Go.

It depends on `libsass` to build, so you will need `gcc` (a C compiler) to build it for your platform. If that is present, you can try:

* `go get -u -v .`
* `go run bundler.go` (this will clone Slate to a temp folder)
* Alternative  to the above if you already have Slate cloned somewhere: `go run bundler.go -slate=/path/to/Slate`

All options:

```bash
go run bundler.go -h
  -minify
    	apply minification to output Javascript, CSS etc. (default true)
  -slate string
    	the path to the Slate source, if not set it will be cloned from https://github.com/lord/slate.git
```

With `make` and `fswatch` (OSX only, I believe) available, you can get a fairly enjoyable live-reloading development experience for all artifacts by running:

* `hugo server` in your Hugo site project.
* `make serve` in the theme folder.
