---
layout: post
title:  "Getting a self-contained python 3.5 environment in Ubuntu Hirsute"
date:   2021-05-21 13:30:17 +0100
categories: blog
tags: python python35 ubuntu
---

Today I found myself needing to work on an old Python 3.5 codebase, which
refused to install its requirements in any later Python version. My first
idea was to install the Python 3.5 package from the [deadsnakes](https://launchpad.net/~deadsnakes/+archive/ubuntu/ppa) repos, but
they're only available for LTS releases, which my currently installed OS - Ubuntu 21.04, aka Hirsute Hippo - is not one of.

Here's (approximately) what I did to get a usable and fairly self-contained python 3.5 environment.

Build python 3.5:

    cd
    git clone git@github.com:python/cpython.git
    cd cpython
    git checkout 3.5
    ./configure --prefix=$HOME/python35 --with-ssl  # you probably want ssl so you can download packages
    make
    make install

Create a python 3.5 virtualenv within my project. I initially tried this with the virtualenv package
and had some minor issues that didn't occur when using the venv module instead:

    cd ~/my_crufty_old_project
    ~/python35/bin/python3.5 -m venv venv
    . venv/bin/activate

Upgrade pip and install my project's requirements:

    pip install -U pip
    pip install -r requirements.pip
