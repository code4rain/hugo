---
comments: true
date: 2016-05-09T01:29:16Z
title: Posting to Tumblr With Emacs
url: /2016/05/09/posting-to-tumblr-with-emacs/
---

최근에 주력 에디터를 vi에서 emacs로 변경하였습니다. emacs를 쓰면서 다양한 부가기능들을 하나씩 사용해보던 중에 tumblr post도 emacs내에서 작성할 수 있는 방법을 찾게되어 공유하고자 합니다. tumblr에 썻던 글이라 영문으로 작성되어 있습니다.

# What is the tumblesocks

[tumblesocks](https://github.com/gcr/tumblesocks) is the one of emacs package. It helps to post tumblr via emacs editor. You can download it from melpa, gnu and github.

# How to setup

1. Download the package: simply use `M-x package-install tumblesocks`
2. Add the followings to your `.emcacs`:
<pre><code>(require 'tumblesocks)
(setq tumblesocks-blog "YourBlogName.tumblr.com")</code></pre>
3. Run `M-x tumblesocks-api-test-auth`
4. tumblesocks will open the browser and access to tumblr to get auth code.
5. Copy the auth code and paste it to emacs prompt

# How to post with tumblesocks

1. Make new post: `M-x tumblesocks-compose-new-post` or other commands.
2. Write the post - I recommnad *markdown* editor.
3. Finish writing: `M-x tumblesocks-compose-finish`
4. If you need to edit existing post, use `M-x tumblesocks-compose-edit-post` - **currently not working for me.**

# Some commands to make the post

* `tumblesocks-text-post-from-region`: Instantly create a post with the contents of region.
* `tumblesocks-text-post-from-buffer`: Instantly create a post from the entire buffer
* `tumblesocks-compose-new-from-region`: Open a buffer and start writing a new post. The contents of region will be copied over.
* `tumblesocks-compose-new-from-highlighted-region`: Open a buffer and start writing a new post. The contents of region will be syntax-highlighted and copied into the post as formatted HTML. This is super-useful for including source code into your tumbles.
* `tumblesocks-compose-insert-highlighted-region`: Insert the syntax-highlighted region at the end of post you're currently writing.
