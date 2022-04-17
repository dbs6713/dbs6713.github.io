---
title: "Personal CDN for Free"
description: Use Google Apps for a free personal CDN.
tags: [cdn,google,web]
date: 2014-12-17T16:56:24-07:00
---
Use Google Apps for a free personal CDN:

So with some personal branding on a few websites it became apparent that my life would be much simpler if I had a personal CDN to store and share common files.  After a little bit of research some CDN providers it became obvious that there are not many simple or FREE personal CDN solutions out there.  So I googled "personal cdn" and the first [link](https://brandonb.io/use-google-app-engine-as-your-own-personal-cdn) was magical!  A simple posting by Brandon Brown explained how the Google App Engine can be used for your very own personal CDN.  You can read his blog post but here I will describe the process I went through.

After following Brandon's advice in the `app.yaml` file I added a `files/` and `img/` directory as well as and `index
.html` if someone actually hits [http://donbstringham-cdn.appspot.com/](http://donbstringham-cdn.appspot.com/).  So now the
configuration file looks like this:

```
application: donbstringham.us
version: 1
api_version: 1
threadsafe: true
runtime: python27

handlers:
- url: /css
static_dir: css
mime_type: text/css

- url: /js
static_dir: js
mime_type: text/javascript

- url: /img
static_dir: img

- url: /files
static_dir: files

- url: /.*
static_files: index.html
upload: index.html
```

It took me about one hour to setup and configure Google Apps as a personal CDN.  So now I use this personal CDN for
static content on a couple of personal websites as well as fonts and images for my various email signatures.
