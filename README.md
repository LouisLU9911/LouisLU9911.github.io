# louislu9911.github.io

This repo is used to build Zhaoyan LU's blog. The blog is powered by [Hugo](https://gohugo.io)
and built with [Ed](https://github.com/sergeyklay/gohugo-theme-ed).

## Prerequisites

* [go](https://go.dev)
* [Hugo](https://gohugo.io)

## Usage

* Create a new post

The following command will only create a draft for you.
If you want to display your post,
do not forget to mark draft as true in file's
[front-matter](https://gohugo.io/content-management/front-matter/).

```bash
$ hugo new path/to/your/new/post.md
```

* Debug your server locally

Run:

```bash
$ make
```

And then check `localhost:1313` in your browser.
