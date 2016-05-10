---
categories:
- computer
comments: true
date: 2016-05-09T04:11:32Z
tags:
- octoress
- jekyll
- script
title: Scripts for Jekyll and Octopress
url: /2016/05/09/scripts-for-jekyll-and-octopress/
---

기존에 사용하던 octopress의 version 3가 개발되면서 동작 방식이 변경되었습니다. 기존에는 jekyll을 base로 추가적인 기능을 넣는 방식으로 개발이 되었지만 version 3에서는 jekyll을 설치하고 octopress를 추가적으로 설치하여 jekyll을 좀더 편하게 사용할 수 있는 방향으로 개발되고 있습니다.
 이와 동시에 기존에 사용하던 `rake`류의 command가 모두 `octopress`로 시작되는 command로 변경이 되어서 기존에 쓰던 script들을 사용할 수 없게 되었습니다.
 이를 개선하기 위해서 새로 만든 스크립트를 공유하고자 합니다~

Post를 새로 작성하는 경우,
title을 입력하면 emacsclient로 해당 파일을 열어줍니다.
<script src="https://gist.github.com/code4rain/717c4900d5b6c6fd7cc6fe9879fec420.js"></script>
작성된 post를 github에 반영하고, 원본 소스 파일도 upload합니다.
<script src="https://gist.github.com/code4rain/17b4b134919d3132ff1f9258fff71d55.js"></script>
