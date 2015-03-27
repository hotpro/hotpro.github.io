---
layout: post
title: "Docker Vagrant Octopress"
date: 2015-03-26 19:02:23 +0000
comments: true
categories: [Docker, Vagrant, Octopress] 
---
Heard Docker and Vagrant for a long time, but I haven't tried them until days ago. I was starting to build my github blog, so I used them to setup an isolated octopress environment.

Building a blog with github page and octopress is quite easy. Docker and Vagrant make it much easier. [Octopress](http://octopress.org/)

At the beginning, I used vagrant to setup it. Vagrant is an actual virtual machine base on virtualbox. [Vagrant](https://www.vagrantup.com/)

Docker, for me, is an application running on a computer, which provides you lots of isolated containers to run your applications. [Docker](https://www.docker.com/)

They both have some bugs for now. I like docker more. I am now using a docker image, which has builtin octopress. Very handy. [Docker Octopress](https://github.com/aratana/docker-octopress)

##Troubleshooting
###Vagrant
```
vagrant SSH Timeout - Cant connect via ssh
```
refer to [https://github.com/mitchellh/vagrant/issues/3860](https://github.com/mitchellh/vagrant/issues/3860)
###Octopress
```
gem install bundler
ERROR:  Loading command: install (LoadError)
    cannot load such file -- zlib
ERROR:  While executing gem ... (NameError)
    uninitialized constant Gem::Commands::InstallCommand
```
zlib1g-dev needs to be installed before ruby is installed.
`sudo apt-get install zlib1g-dev`

```
bundle install
Could not load OpenSSL.
You must recompile Ruby with OpenSSL support or change the sources in your Gemfile from 'https'
to 'http'. Instructions for compiling with OpenSSL using RVM are available at
http://rvm.io/packages/openssl.
```
This is another dependency problem.
Use this to solve both problems and some potential problems
`sudo apt-get -y install build-essential zlib1g-dev libreadline-dev libssl-dev libcurl4-openssl-dev`
###Docker
```
docker can't connect to boot2docker because of tcp timeout
```
solution:
```
boot2docker down # Shut down boot2docker VirtualBox bits
sudo route -nv add -net 192.168.56 -interface vboxnet0 # Add a static route
boot2docker up # Start up boot2docker, bring VirtualBox bits back up
$(boot2docker shellinit)
docker images # List images. This should just work.
```
refer to [https://github.com/boot2docker/boot2docker/issues/392#issuecomment-54588412](https://github.com/boot2docker/boot2docker/issues/392#issuecomment-54588412)
