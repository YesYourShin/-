---
layout: post
title: "[github 블로그] comments 란이 생성되지 않는 문제"
date: 2022-09-12 02:59 +0900
categories: [Github Blog, Error]
tag: [Github, Comments, Giscus]
---
# 문제
github 블로그를 만들면서 댓글 기능을 추가하려고 하였다.

_config.yml에서 comments 란에 giscus 설정을 하였는데 post 아래에 giscus comments 란이 생성 되지 않았다.

# 원인 찾기

giscus를 사용하려면 _config.yml 파일에서 comments 부분의 giscus 설정 란을 채우고 active에 giscus를 적어주면 comments 란이 표시가 되어야 한다.

![image](https://user-images.githubusercontent.com/53047744/188346600-7dd1bde2-316f-445e-b0cc-137987e7af9b.png)

하지만 무슨 이유인지 이 방법이 먹히지 않았다.

giscus에서 출력되는 활성화 코드를 직접 post 파일에 넣으면 comments란이 표시가 되는 걸로 봐서 giscus 설정의 문제는 아닐 것이라 생각하였다. (사진은 예시일 뿐 진짜로 이렇게 적지는 않았다.)

![image](https://user-images.githubusercontent.com/53047744/189542827-82d92a38-901c-467d-8520-2fa8df2db84e.png)

구글링으로 comments를 넣는 방법을 찾아보았는데 위 방법 이외에 다른 방법으로는 layout 폴더에서 양식을 만들어 추가하는 그런 방법이 있는 거 같긴 했지만 내가 만드는 블로그에는 그런 게 필요가 없었다. 그리고 아마도 그 문제가 아닐 거란 생각이 들었다.

구글링으로 아무리 찾아봐도 원인을 알 수가 없어서 같은 테마를 쓰고 comments 기능을 사용하고 있는 다른 개발자의 블로그 repository를 찾아보았다.

그리고 _config.yml 파일의 설정을 봤는데 giscus가 아니라 utterances를 사용하는 것 말고는 설정이나 파일이 내 블로그와 다른 게 없었다.

테스트를 해보려고 그 개발자의 블로그를 clone해서 post 생성을 해보았더니 comments 부분의 코드가 너무나도 잘 들어가 있는 것을 확인할 수 있었다...

설마 giscus는 설정란이 있긴 하지만 사용할 수 없는 건가 라는 생각이 들어서 utterances를 giscus로 변경했는데 너무나도 코드가 잘 들어가 있었다.

![image](https://user-images.githubusercontent.com/53047744/189542911-3be9c61c-33c8-4043-a3f1-21f98834d823.png)

모든 게 똑같은데 왜 내 블로그는 comments란이 생성이 되지 않는 건지 전혀 알 수가 없었다.

# 해결

내 블로그의 comments 설정을 giscus에서 utterances로 변경해보았더니 정말 놀랍게도 코드가 들어가 있었다.

다시 giscus로 변경했더니 정상적으로 giscus comments 란이 생성되는 것을 확인할 수 있었다.

그 전에 내가 어떤 걸 했는지 잘 생각해보니 실행을 다시 했었다...

이런 걸로 일주일을 날렸다... 제발 설정 변경 후에는 다시 실행하는 것을 까먹지 말자...
