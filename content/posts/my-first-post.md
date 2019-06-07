---
title: "Hugo Syntax Highlighting"
date: 2019-06-02T16:54:24-06:00
---

A quick tutorial on how to add syntax highlighting to a [Hugo](https://www.gohugo.io)
site using [Chroma](https://github.com/alecthomas/chroma).

<!--more-->

## Prerequisites
* Hugo 0.28+

## Step 1. Choose a style

Visit the [Chroma Style Gallery](https://github.com/alecthomas/chroma) and pick
out the style that you prefer (Example: `xcode`).

## Step 2. Update config

You can get syntax highlighting one of two ways: Inline css or with a stylesheet.

### Inline CSS

The quickest way to get syntax highlighting is to set `pygmentsStyle` to `true`
in your `config.[toml|yml]` file.

{{% highlight yaml %}}
// config.toml
pygmentsStyle = "xcode"
{{% /highlight %}}

### Stylesheet

Inline css styles can be a bit cumbersome, especially if you want to override styles.
For this reason you might prefer to use a stylesheet for syntax styles.

First, replace `pygmentsStyle` with `pygmentsUseClasses = true`.

{{% highlight yaml %}}
// config.toml
pyghmentsUseClasses = true
{{% /highlight %}}

Then, generate the stylesheet from the command line like so:

{{% highlight bash %}}
$ hugo gen chromastyles --style=xcode > static/css/syntax.css
{{% /highlight %}}

You must then add a reference to the stylesheet, probably from a head.html
file.

{{% highlight html %}}
<!-- head.html -->
<link type="text/css" rel="stylesheet" href="{{ .Site.BaseURL }}css/syntax.css">
{{% /highlight %}}

## Step 3. Using the syntax highlighting

Wrap your code around the `highlight` shortcode passing in the desired language
(eg `swift`).

```
{{%/* highlight swift */%}}
func sayHi() {
  print("hello")
}
{{%/* /highlight */%}}
```

Here's the 
[full list of supported languages](https://gohugo.io/content-management/syntax-highlighting/#list-of-chroma-highlighting-languages).

## References
* [Hugo - Syntax Highlighting](https://gohugo.io/content-management/syntax-highlighting/)
* Thanks to [this post](https://discourse.gohugo.io/t/a-way-to-mark-plain-text-and-stop-hugo-from-interpreting/1325/4) for explaining how to escape hugo commands in markdown
