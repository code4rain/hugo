---
comments: true
date: 2012-12-14T00:00:00Z
title: PUSH된 COMMIT내용 수정하기(Gerrit Review전)
url: /2012/12/14/pushdoen-commitnaeyong-sujeonghagi-gerrit-reviewjeon/
tags:
 - git
---

Git에서 수정하고 Gerrit에 Push를 하였으나 아직 Review가 끝나지 않아 Merge되지 않은 상태에서 Commit을 수정해서 다시 Gerrit에 Patch #2로 올리는 간단한 방법입니다.

아래 방법은 수정하고 싶은 commit이 현재 HEAD일 경우입니다.

# comit에 있는 일부 파일만 변경하고 싶을 때

1. 수정하고 싶은 파일(a.c) 편집
2. `git add a.c`
3. `git commit --amend -C HEAD` // -C옵션은 HEAD에 있는 commit 내용을 그대로 사용한다는 의미입니다. 고로 Change Id도 유지되겠죠.
4. `git push`

# commit에 있는 파일 중 하나를 이전으로 돌리고 싶을 떄

1. `git checkout HEAD^` -- <돌리고 싶은 파일명> // HEAD^는 현재 HEAD 바로 전 commit 내용을 기준으로 돌리겠다는 의미. HEAD^ 위치에 원하는 Commit의 SHA ID를 써주어도 됨.
2. `git add <돌리고 싶은 파일명>`
3. `git commit --amend -C HEAD`
4. `git push`
