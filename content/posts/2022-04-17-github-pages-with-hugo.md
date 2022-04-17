+++ 
draft = false
date = 2022-04-17T09:47:56-06:00
title = "GitHub Pages with Hugo"
tags = ["go", "github", "markdown"]
categories = []
thumbnail = "images/tn.png"
description = "How to create and publish a static web site with GitHub Pages and Hugo."
+++

{{< rawhtml >}}
    <img src="https://blog.leonprasetya.my.id/p/how-i-made-hugo/hugo_huf7630602c9bedf706ad0ded87d4ffc01_56751_1600x0_resize_box_3.png" alt="hugo static site generator" width="300" />
{{< /rawhtml >}}

This year (2022) I have put together major updates to two web sites. Liking [Go](https://go.dev/), therefore Hugo was used to generate the static content site and [GitHub Pages](https://pages.github.com/) to host both of them. [Namecheap.com](https://www.namecheap.com/) is my domain registrar. I used two different methods to host and deploy them.

## METHOD 1 (TWO REPOSITORIES)

A little background about the content of the first site [Daoyin Chuan](https://daoyinchuan.com) which uses the two repository method.  It is a web site that honors my mentor and sifu [Fong Ha](https://fongha.com).  I used is a very Zen like theme named [Dimension](https://github.com/your-identity/hugo-theme-dimension).

This method requires two repositories.  The first one is *private* and the other *public*.  The *private* repository contains the sources used to generate the static web site. I named the *private* repository 'daoyinchuan.source'. The *public* repository I named [daoyinchuan.github.io](https://github.com/daoyinchuan/daoyinchuan.github.io). **NOTE:** I put these two repositories into my GitHub Organization "Daoyin Chuan".

{{< rawhtml >}}
    <img src="/images/daoyinchuan_dns.jpg" width="600"/>
{{< /rawhtml >}}

## METHOD 2 (SINGLE REPOSITORY)

{{< rawhtml >}}
    <img src="/images/dbs67_dns.jpg" width="600" />
{{< /rawhtml >}}
