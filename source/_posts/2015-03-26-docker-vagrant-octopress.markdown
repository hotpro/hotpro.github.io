---
layout: post
title: "Docker Vagrant Octopress"
date: 2015-03-26 19:02:23 +0000
comments: true
categories: [Docker, Vagrant, Octopress] 
---
Heard Docker and Vagrant for a long time, but I haven't tries them until days ago. I wanted to build my github blog, so I used them to setup an isolated octopress environment.

Building a blog with github page and octopress is quite easy. Docker or Vagrant makes it much easier. [Octopress](http://octopress.org/)

At the beginning, I used vagrant to setup it. Vagrant is an actual virtual machine base on virtualbox. [Vagrant](https://www.vagrantup.com/)

Docker, for me, is a application running on a computer, which provides you lots of container to run your applications. [Docker](https://www.docker.com/)

They both have some bugs for now. I like docker more. I am now using a docker image, which has builtin octopress. Very handy. [Docker Octopress](https://github.com/aratana/docker-octopress)
