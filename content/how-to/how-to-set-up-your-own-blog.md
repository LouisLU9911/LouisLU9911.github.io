---
title: "How to Set Up Your Own Blog"
date: 2023-05-21T14:47:25+08:00
draft: false
featuredImage: ""
description: ""
author: Louis LU
type: post
tags:
  - blog
  - hugo
  - hugo-theme
  - gohugo-theme-ed
  - github
  - github-actions
  - github-pages
  - latex
toc: false  # enable it if you want to show the contents in the sidebar
---

{{< toc >}}

## Overview

If you want to quickly set up your own blog without spending a lot of time
on tedious tasks such as deployment and server operations :neutral_face:,
[Hugo](https://gohugo.io) +
[GitHub Actions](https://github.com/features/actions) +
[GitHub Pages](https://pages.github.com/) is a great solution.
[Ed](https://github.com/sergeyklay/gohugo-theme-ed) is the theme I used.

## Prerequisites

### Basic Dependencies

* [Hugo](https://gohugo.io)
* Terminal
* Your Github account
* git (Maybe a 
[quickstart](https://docs.github.com/en/get-started/quickstart) would help :smirk:)

### (Optional) Ed's Dependencies

* [go >= 1.12](https://go.dev)

### (Optional) Katex

* [Katex](https://katex.org/)

## Create a new repo

At the beginning, you need to create a new Github repo to store your website.

Depending on the name of the repository you create, the domain name required to
access the final website will also vary. View details at
[Github Pages](https://pages.github.com).

Assuming that your account name is `foo`.

| Type              | Repo Name | Website Domain Name |
|:-----------------:|:---------:|:-------------------:|
| User/Organization | foo       | foo.github.io       |
| Project           | bar       | foo.github.io/bar   |

## Create a new site

```bash
$ hugo new site YourSiteName
Congratulations! Your new Hugo site is created in /path/to/your/YourSiteName.

Just a few more steps and you're ready to go:

1. Download a theme into the same-named folder.
   Choose a theme from https://themes.gohugo.io/ or
   create your own with the "hugo new theme <THEMENAME>" command.
2. Perhaps you want to add some content. You can add single files
   with "hugo new <SECTIONNAME>/<FILENAME>.<FORMAT>".
3. Start the built-in live server via "hugo server".

Visit https://gohugo.io/ for quickstart guide and full documentation.
```

Just follow the instruction above and build your own blog **locally**.

If you want to use the same theme (i.e.,
[Ed](https://gohugo-theme-ed.netlify.app)) as me,
you could refer to its official
[docs](https://gohugo-theme-ed.netlify.app/documentation). :point_left:

## Set up Github Actions

Next is to correctly set up GitHub Actions so that the website can
be automatically built and deployed on GitHub.

Hugo provides its own
[action](https://gohugo.io/hosting-and-deployment/hosting-on-github/) for you.
Just use it! :stuck_out_tongue_closed_eyes:

If you have set it up correctly, the website will automatically update every
time you push a new commit. :sunglasses: Enjoy it!

## Add Latex support with Katex

To add LaTeX support to your website using KaTeX, create a file
named `katex.html` in your `layouts/partials` folder.

The following code snippet is taken from [the KaTeX documentation](https://katex.org/docs/browser.html#starter-template).

* `layouts/partials/katex.html`

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.16.7/dist/katex.min.css"
    integrity="sha384-3UiQGuEI4TTMaFmGIZumfRPtfKQ3trwQE2JgosJxCnGmQpL/lJdjpcHkaaFwHlcI" crossorigin="anonymous">

<!-- The loading of KaTeX is deferred to speed up page rendering -->
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.16.7/dist/katex.min.js"
    integrity="sha384-G0zcxDFp5LWZtDuRMnBkk3EphCK1lhEf4UEyEM693ka574TZGwo4IWwS6QLzM/2t"
    crossorigin="anonymous"></script>

<!-- To automatically render math in text elements, include the auto-render extension: -->
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.16.7/dist/contrib/auto-render.min.js"
    integrity="sha384-+VBxd3r6XgURycqtZ117nYw44OOcIax56Z4dCRWbxyPt0Koah1uHoK0o4+/RRE05" crossorigin="anonymous"
    onload="renderMathInElement(document.body);"></script>
```

You can include this file in your `layouts/partials/footer.html` file like this:

```html
<!-- Your original footer.html (It may come from the theme you used) -->

{{ if .Params.katex }}{{ partial "katex.html" . }}{{ end }}
```

To enable KaTeX on a specific post, add the following to its
[front matter](https://gohugo.io/content-management/front-matter/):

```markdown
---
# other settings in the front matter
katex: true
---
```

## References

* [Hugo](https://gohugo.io)
* [Ed](https://gohugo-theme-ed.netlify.app)
* [Katex](https://katex.org/)
* [GitHub Actions](https://github.com/features/actions)
* [GitHub Pages](https://pages.github.com/)
* [How to build personal blog using GitHub Pages and Hugo](https://blog.hellohuigong.com/en/posts/how-to-build-personal-blog-with-github-pages-and-hugo/)
* [Start a blog using Hugo and Github Pages](https://matimacazaga.github.io/posts/hugo_tutorial/)
