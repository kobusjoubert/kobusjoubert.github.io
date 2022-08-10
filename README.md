# GitHub Page

GitHub page where I'll add Ruby, Rails and Hotwire mistakes I've made with ideas, conventions, good practices and syntax sugar to improve it all. 🤓

## Usage

Start the server.

```
bin/dev
```

Now browse to <http://localhost:4000>

## Creating Posts

To [create a post](https://jekyllrb.com/docs/posts/#creating-posts), add a file to your `_posts` directory with the following format:

```
YEAR-MONTH-DAY-title.MARKUP
```

Where `YEAR` is a four-digit number, `MONTH` and `DAY` are both two-digit numbers, and `MARKUP` is the file extension representing the format used in the file. For example, the following are examples of valid post filenames:

```
2011-12-31-new-years-eve-is-awesome.md
2012-09-12-how-to-write-a-blog.md
```

All blog post files must begin with [front matter](https://jekyllrb.com/docs/front-matter/) which is typically used to set a [layout](https://jekyllrb.com/docs/layouts/) or other meta data. For a simple example this can just be empty:

```
---
layout: post
title:  "Welcome to Jekyll!"
---

# Welcome

**Hello world**, this is my first Jekyll blog post.

I hope you like it!
```

## Publishing

Commit to the `main` and push to GitHub.

```
git add .
git commit -m 'New post title'
git push origin main
```
