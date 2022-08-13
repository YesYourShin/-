---
layout: post
title: github 블로그를 리포지토리 비공개했더니 블로그가 안 뜬다
---

github 블로그 리포지토리를 비공개 시켰더니 블로그 페이지가 나오지 않았다.

리포지토리를 확인해보니 비공개 상태에서 pages를 사용하려면 pro를 써야했다...

![image](https://user-images.githubusercontent.com/53047744/184500410-136f9314-bb7d-43f0-b832-0d59d4c4504f.png)

학생 인증으로 pro를 사용해보려 했으나 우리 학교 학생증을 인증하는 것으로는 안 되는 거 같았다. 그래서 그냥 포기하고 다시 공개로 전환하기로 했다.

그런데 리포지토리를 공개로 전환한 후에도 블로그를 들어갔더니 블로그 페이지가 표시되지 않았다.

커밋을 해보았더니

![image](https://user-images.githubusercontent.com/53047744/184499453-d1c8424c-a4c9-4425-9fce-218ee83ac15d.png)

이렇게 나왔다.

어떤 부분이 문제인가 생각해보다 pages가 생각났다.

github pages는 github repository에서 웹사이트를 호스팅
할 수 있게 해준다. 블로그를 만들 때도 사용했던 기능.

github repository에서 page에 들어가니 branch 부분이 main 으로 되어있었다.
main을 gh-pages로 바꿔줬더니 정상적으로 뜨는 것을 확인했다.
