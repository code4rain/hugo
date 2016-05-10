---
categories:
- computer
comments: true
date: 2016-05-09T03:07:24Z
tags:
- git
- gtags
- gnu
title: Update/Generate GTAGS With Git Update
url: /2016/05/09/update-generate-gtags-with-git-update/
---

Tumblr에 작성했던 내용을 옮겨왔습니다. 기존에는 vi와 cscope를 활용해서 tag를 관리하다가 gnu에서 만든 global(gtags)를 알게되서 이를 활용할 수 있는 방법을 찾아보던 중에 ctags와 git을 활용하는 방법이 있어 이를 개선해서 gtags용으로 변경한 방법을 공유합니다.

# Why GTAGS([GNU Global](https://www.gnu.org/software/global/))?

* Find better than ctags
* Find faster than ctags/cscope
* Build faster thant ctags/cscope
* Integrate better with emacs

# Why git and gtags

* git is good scm tool used everywhere :)
* gtags made good reference with many languages
* git only maintains original source code
* gtags can update partially - git use diff for commit!

# How to setup

1. Instatll git and gnu global(gtags) to your system
2. make `~/.git_template/hooks` directory
3. move directory: `cd ~/.git_template/hooks`
3. make `gtags` file include below contents
   <script src="https://gist.github.com/code4rain/6934e4c29163f4f7e04e286db26e890a.js"></script>
4. make `post-checkout`, `post-commit`, `post-merge` as below (same contents)
   <script src="https://gist.github.com/code4rain/3104edb17699948ab829314bfce23708.js"></script>
5. make `post-rewrite` as below
   <script src="https://gist.github.com/code4rain/66ac28c0b4256308808a351d71d1aed0.js"></script>
6. run below command to add default git template.
   <script src="https://gist.github.com/code4rain/23f3217d2e784bc18e662ec7bf3f549f.js"></script>

refer from [Effortless Ctags with Git](http://tbaggery.com/2011/08/08/effortless-ctags-with-git.html)

