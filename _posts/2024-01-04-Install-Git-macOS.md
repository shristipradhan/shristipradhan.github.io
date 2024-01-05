---
layout: post
title:  "How to install Git on macOS"
date:   2024-01-04
excerpt: "Install Git on macOS"
tag: false 
comments: false
---

Install Git using Homebrew:

Easy steps to get git running on your macOS using [Homebrew] (https://brew.sh/), a popular package manager for macOS.

1. Open Terminal on your macOS.
2. If you don't have Homebrew, install using:
`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`
3. Once Homebrew is installed, you need to add /opt/homebrew/bin to your PATH. Run the following commands to add Homebrew to your PATH:
`(echo; echo 'eval "$(/opt/homebrew/bin/brew shellenv)"') >> /Users/shristipradhan/.zprofile`
 `eval "$(/opt/homebrew/bin/brew shellenv)"`
4. You can verify the version of Homebrew using:
`brew --version`
5. Install git using:
`brew install git`
6. Once git is installed, check the version using:
`git --version`

Install Git using MacPorts:

Another easy steps to get git running on your masOS using [MacPorts](https://www.macports.org/), which is an open source initiative. 

1. Open Terminal on your macOS.
2. If you don't have MacPorts, first install command line tools using:
`xcode-select --install`
If command line tools are already installed, you might have to add PATH to your bash profile using:
`touch ~/.bash_profile`
`export PATH="/opt/local/bin:/opt/local/sbin:$PATH"`
`source ~/.bash_profile`
3. Install git using:
`sudo port install git`
6. Once git is installed, check the version using:
`git --version`


