---
layout: post
title: "使用github pages和octopress搭建blog"
date: 2013-06-29 23:19
comments: true
categories: [Github, Octopress, Octoflat] 
footer: true
---

第一篇blog简单介绍下使用octopress在github pages上搭建blog的步骤。

*    首先参看Octopress官方文档 [Octopress Setup](http://octopress.org/docs/setup/)
*    我使用的主题是 [Octoflat](https://github.com/alexgaribay/octoflat)  具体的[demo](http://alexgaribay.com/index.html)
*    博客正文是使用 [Markdown](http://wowubuntu.com/markdown/)
*    comment使用的是Disqus。只需要在octopress的`_config.yml`里配置一下就行了。
```
 disqus_short_name: your_disqus_short_name
 disqus_show_comment_count: true
```

