+++
date = "2016-06-05T19:35:16-06:00"
description = "Development With Docker"
tags = ["dev"]
title = "Development With Docker"
+++

Being a developer for over two decades I am always looking for new ways to improve and simplify my workflow.  Recently, I've moved to [Vagrant](https://www.vagrantup.com/) which is a wrapper around virtual machine players such as [Virtual Box](https://www.virtualbox.org/wiki/Downloads), [VMWare Fusion](http://www.vmware.com/products/fusion.html) and such.  The most current tool that fits the bill, though is [Docker](https://www.docker.com/).  It is such a great tool that I have removed Vagrant and all virtual machine players from my development Macbook Pro!

Docker allows you to develop, build, deploy/ship and run applications all in the same container across all of your environments no matter what type they are.  It is a tool for your whole organization.  As a developer here are a few reasons I use it:

- Consistent development environments for the entire team.  Everyone uses the same OS, libraries, languages, runtimes no matter what host operating system they are using.
- Less *"It works on my machine"* because the development environment is the exact same as production.  Meaning it'll *"just work"* in production because you deploy containers!
- You only need Docker and an IDE or editor to develop.  No need to install many language environments on your machine.  For example, want to run a PHP script but don't have a PHP version installed?  Run it in a PHP image.
- QA can test the application with multiple language versions without have to resort to hacks for the language (python, php, ruby, java, node.js, golang).
- Deployment is simplified.  If it runs in the container on the build machine it will run on the production server just the same.  Package the application with the Docker image and push the image to the production server to run the new image.
- Developers can still use their favorite editor/IDE and tools one would normally do.  No more need for running a VM in VirtualBox and SSHing and developing from the shell.

There are plenty of websites on how to use Docker for Developerment.  Here are two of them [Why and How to Use Docker for Development](https://medium.com/iron-io-blog/why-and-how-to-use-docker-for-development-a156c1de3b24#.14iw16utk) and [Supercharge Your Development Environment (Using Docker)](https://denibertovic.com/talks/supercharge-development-env-using-docker/#/)!  If you prefer books the only one I can really suggest is (Docker for Developers)[https://leanpub.com/dockerfordevs] by [Chris Tankersley](https://leanpub.com/u/ctankersley).  It is a very well written book at a great price.

I guarantee that one you add/switch your development workflow with **Docker** you wonder how you ever got along with out it.

