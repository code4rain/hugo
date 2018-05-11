---
comments: true
date: 2012-12-27T00:00:00Z
title: Change Outlook Subject with Python
url: /2012/12/27/change-outlook-subject-with-python/
tags:
 - outlook
 - python
---

## Introduction
직장에 다니게 되면서 e-mail은 뗄레야 뗄 수 없는 사이가 되었습니다. 업무지시부터 각종 정보에 이르기까지 모든 것이 e-mail을 통해서 전달되기 때문이죠. 그런데 회사 메일은 받은 편지함 공간에 제약이 있었습니다. 읽지 않은 메일은 2주간, 읽은 메일은 1주일간만 보관 가능했습니다. 워낙 많은 사람들이 쓰고 있어서 공간제약은 어쩔 수 없는 면이 있죠. 그래서 대부분 선배, 동료, 후배들은 백업 용도로 아웃룩을 사용하고 있습니다. 출장 나가서 본 많은 주재원분들이나 업체에서는 아웃룩을 메인으로 쓰지만 회사 내부 규정상 아웃룩 발신을 제한하고 있어서 우리 회사에서는 메인보다는 백업용도로 사용하고 있습니다.

아웃룩 2003까지는 뭐 그러려니 하고 search plugin을 설치해서 쓰고 있다가, 2010에 [conversation view(대화보기)](http://support.microsoft.com/kb/2274243/ko)라는 기능이 추가된 것을 알게 되었습니다. 메일 제목을 기준으로(엄밀히 이야기하면 메일 제목은 아닙니다만) 메일을 묶어주는 기능입니다.

하루에 오는 메일들이 대부분 Reply나 Foword 형식이기 때문에 이 기능을 쓰게 되면 하루에 오는 몇 백통의 메일을 몇 십개 Thread로 묶어서 보여주는 효과가 있습니다.

__오호라~!__

하지만 난관에 봉착합니다. 이 기능은 아웃룩에서 수발신한 메일들만 묶어줍니다. 회사메일에서 reply, foword를 하게되면 다른 conversation subject를 가진 메일로 인식하고 묶어주질 못하는 거죠.

SW engineer가 이대로 포기할 순 없어서 검색해보기 시작합니다.

우리의 친구 Google과 stackoverflow를 찾아보다가 [힌트][HINT]를 발견합니다.
Python으로 뭔가 쿵짝쿵짝하면 될 것같은 느낌이 듭니다. 오호~

열심히 스크립트도 만들고 수정해봅니다.

__뭔가 되는 듯하더니 안됩니다.ㅠㅠ__

음 다시 Google과 stackoverflow를 뒤져봅니다.
[MSDN]에 나온 걸 보니 conversationTopic을 변경이 안된다고 합니다. - READ Only attribute.

이런...

하지만 또 뒤져봅니다.

... (\_ \_) (- - ) ( - -)

걸렸습니다. Redemption DLL을 깔면 수정할 수 있답니다. (오예~)

그래서 기존에 온 메일을 일괄 정리하는 스크립트를 만듭니다. 쓱싹쓱싹 돌 때 심심하니 메일 하나를 처리하면 .하나를 찍어주도록 합니다.
다 되고 나서 Conversation View로 바꿔봅니다.

...

잘됩니다.ㅋㅋㅋㅋ

이제 매번 스크립트를 돌리기가 귀찮아집니다. 보통은 여기까지하고 그만두지만, 이번엔 아웃룩 VBA까지 건들여봅니다. 뚝딱뚝딱

__이힝~__

이제 메일이 오면 자동으로 정리해주도록 변경합니다. 아.. 내가 만든 VBA스크립트는 인증받지 않은 스크립트라 보안을 해제해줘야 합니다.
설마 회사에 스팸용 VBA 스크립트가 들어오진 않을테니, 보안담당자를 믿고 보안도 해제합니다.

길고긴 삽질이 끝났습니다.

## 설치 방법
1. Download and install
	* Windows용 Python을 설치합니다.
	* Python은 Outlook을 32bit을 설치했으면 32bit을, 64bit을 설치했으면 64bit을 설치합니다.
		* Python Download : [2.7.5 32bit](http://www.python.org/ftp/python/2.7.5/python-2.7.5.msi)
		* Python용 win32 library도 다운받습니다. : [pywin32-218.win32-py2.7.exe](http://sourceforge.net/projects/pywin32/files/pywin32/Build%20218/pywin32-218.win32-py2.7.exe/download)
	* Redemption DLL도 설치합니다. (설치가 잘 안되면 관리자 권한으로 설치합니다.) : [Redemption](http://www.dimastr.com/redemption/Redemption.zip)

2. 기존 메일을 정리하는 스크립트

스크립트를 작성합니다. 아래 내용을 복붙해서 conversation.py로 만듭니다.
python이 제대로 설치되었다면 conversation.py를 double click하면 잘 실행이 됩니다.
<script src="https://gist.github.com/code4rain/28057bc26d7ba343e59f.js"></script>

메일이 오면 자동으로 변경해주는 건 VBA스크립트를 만들어야 합니다.

[MSDN]: http://msdn.microsoft.com/en-us/library/office/ff869318.aspx
[HINT]: http://stackoverflow.com/questions/1440233/possible-to-intercept-and-rewrite-email-on-outlook-client-side-using-ironpython