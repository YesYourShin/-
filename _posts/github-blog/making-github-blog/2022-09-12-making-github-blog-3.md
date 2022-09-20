---
layout: post
title: "[github 블로그 만들기] 3 - 댓글 기능 추가하기"
date: 2022-09-12 02:47 +0900
categories: [Github Blog]
tag: [Github, Comments, Giscus, Discussions]
---

## 댓글 플랫폼 정하기

댓글 플랫폼으로는 disqus, utterances, giscus가 있다.

> disqus: SNS 계정을 이용하여 댓글을 달 수 있다.  
> utterances: github의 issue 탭을 활용해서 댓글을 달 수 있다.  
> giscus: github의 discussions 탭을 활용해서 댓글을 달 수 있다.

disqus는 개발 블로그에 SNS 계정을 사용하여 댓글을 사용하는 게 마음에 들지 않았다.
그리고 광고가 자동으로 붙는다는 글을 보고 사용하지 않기로 했다.

utterances는 issue탭을 사용하는 것이 마음에 들지 않았고, 댓글에 필요한 대댓글이 없다고 하여 쓰고 싶지 않았다.

giscus는 토론이나 커뮤니티를 위해 만들어진 discussions를 댓글로 사용하게 해주고 대댓글도 사용 가능하다. 그래서 giscus를 쓰기로 하였다.

## 활성화 방법

1. 댓글을 사용할 레포지토리를 public으로 전환한다.

2. Github 계정에 giscus 앱을 설치
   https://github.com/apps/giscus
   위 링크를 들어가면 아래의 페이지가 뜬다.
   Install을 클릭

![image](https://user-images.githubusercontent.com/53047744/188343992-7695289c-7ab8-4310-a99f-de76861eb3fe.png)

3. 이 앱을 어디에 설치할 건지를 물어보고 있다.
   나는 특정 레포지토리에만 설치하기로 하였다.
   그 후 Install을 클릭하면 설치가 완료 된다.

![image](https://user-images.githubusercontent.com/53047744/188344250-eef96705-ca7b-42a3-9b89-76b6c0ecb26e.png)

![image](https://user-images.githubusercontent.com/53047744/188344455-301cb78e-cb86-4692-874b-ac6d5315d1f9.png)

4. 그 후 Discussions을 사용하기 위해서, 댓글을 저장할 레포지토리의 Settings탭의 Features에서 Discussions에 체크를 해준다.

![image](https://user-images.githubusercontent.com/53047744/188344821-3ac116a2-823e-4b33-8a9d-6018649395e9.png)

## giscus 댓글 커스텀하기

아래 링크로 들어가면 댓글 기능을 원하는 대로 커스텀 할 수 있다.

> https://giscus.app/ko

커스텀을 끝내고 나면 giscus 활성화에 스크립트가 있다.
![image](https://user-images.githubusercontent.com/53047744/189541513-437d79df-c7cf-4ff1-9334-50f26a26aa1c.png)

\_config.yml 파일 comments란의 giscus란에 입력해야 하는 것들을 스크립트를 확인하며 입력해준다.

![image](https://user-images.githubusercontent.com/53047744/188346600-7dd1bde2-316f-445e-b0cc-137987e7af9b.png)

그러면 post 아래에 comments란이 생성되는 것을 확인할 수 있다.

![image](https://user-images.githubusercontent.com/53047744/189540789-47401a88-fbcb-403f-8cf9-c180fe39bf66.png)

댓글을 남기면 이렇게 표시가 된다.

![image](https://user-images.githubusercontent.com/53047744/189540877-e70bdb6d-1de4-48c5-a990-84f595d0d059.png)

이 댓글은 해당 블로그의 repository의 Discussions 탭에서 확인할 수 있다.

![image](https://user-images.githubusercontent.com/53047744/189540952-3ce6cf7d-069e-4580-a5a5-222559bf25ef.png)
