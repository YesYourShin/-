---
layout: post
title: "[Git] subtree로 Commit과 같이 Repository 합치기"
date: 2022-09-19 19:57 +0900
categories: [Git]
tag: [Github, Git, subtree]
---
프로그래밍을 하면서 배웠던 걸 전부 Repository를 만들어 push 하다보니 Repository가 너무 많아졌다.

그래서 한 곳으로 모으는 정리를 하고 싶었다.

그런데 Repository의 파일들을 그냥 clone해서 새 Repository에 넣을 경우 이전에 했던 commit들이 다 사라져서 열심히 심어놓은 잔디도 없어진다.

그래서 commit 내역도 같이 합칠 수 있는 것을 찾아보니 git subtree를 사용하면 가능하다고 하여 사용해 보기로 하였다.

## 새로운 Repository 만들기

Repository를 한 곳에 모아야 하니 Github에서 새로운 Repository를 만들어 준다.

그리고 clone을 해준다.

```console
$ git clone (복사할 Repository)
```

그 후 commit을 한 번 해준다. 방금 만든 Repository라 commit 내역이 하나도 없는데 commit을 하지 않으면 후에 subtree를 할 때 에러가 난다.

간단하게 readme 파일 만들고 commit 하자.

clone한 폴더에 readme.md 파일을 만든다.
commit 한다.

```console
$ git add .
$ git commit -m "설명"
```

## subtree로 Repository 병합하기
```console
$ git subtree add --prefix=(합칠 Repository의 파일들을 담을 폴더명) (합칠 Repository 주소) (합칠 Repository Branch)
```

push를 한 후 Github에서 Repository를 확인해보면 commit 내역과 Repository가 잘 합쳐진 것을 볼 수 있다.

합친 후 기존 Repository는 다 삭제해주었다.
