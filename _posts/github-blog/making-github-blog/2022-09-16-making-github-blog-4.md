---
layout: post
title: "[github 블로그 만들기] 4 - Google Analytics를 사용하여 Page View 구현하기"
date: 2022-09-16 15:17 +0900
categories: [Github Blog]
tag: [Github, Google Analytics, Google Cloud, Page View, Google Analytics superProxy]
---
## Google Analytics 설정

Google Analytics 계정 및 속성 만들기

아래의 Google Analytics 홈페이지로 이동하여 `측정 시작`을 클릭한다.

> Google Analytics : https://analytics.google.com/

![image](https://user-images.githubusercontent.com/53047744/189783909-aa76b12b-8ede-4bcc-b17c-20025863ca2e.png)

`계정 설정`, `속성 설정`, `비즈니스 정보`를 입력하고 만들기 버튼을 누른다.

![image](https://user-images.githubusercontent.com/53047744/189789432-cfbbb808-8f2c-4a35-b966-713ffa7418b4.png)

속성을 설정할 때 고급 옵션에서 유니버설 애널리틱스 속성 만들기를 체크하여 자신의 블로그 링크를 넣고 `Google 애널리틱스 4 속성과 유니버설 애널리틱스 속성 둘 다 만들기`와 `Google 애널리틱스 4 속성에 대해 향상된 측정 사용 설정`을 체크한다.

![image](https://user-images.githubusercontent.com/53047744/190383008-e2b89487-89bc-40eb-a9a6-9be32828d467.png)

왼쪽 위의 `모든 계정 > @@@` 이라고 적힌 탭을 눌러보면 아래의 창이 나타난다.

![제목 없음](https://user-images.githubusercontent.com/53047744/190530619-2ba2d14a-4170-4b6c-8e11-2c7de0eae196.png)

만약 속성 이름을 blog로 했다면 저 사진에 있는 것 처럼 blog 와 blog-GA4 두 개가 생성된다.

그냥 blog는 `유니버설 애널리틱스(UA)` 속성이고 GA4가 써진 blog 속성이 `구글 애널리틱스4(GA4)` 속성이다.

GA4 속성을 선택하여 `관리` > `데이터 스트림`으로 이동하면 생성되어 있는 스트림을 확인할 수 있다.

![1](https://user-images.githubusercontent.com/53047744/190531958-b1713088-5ef2-4895-a955-2c0c579ec07e.png)

스트림을 클릭하면 `웹 스트림 세부정보` 창이 뜨는데 여기서 `스트림 세부정보`의 `측정 ID`를 복사한다.

![2](https://user-images.githubusercontent.com/53047744/190532367-0168dc74-561b-47e1-866e-2ca176e98b7a.png)

`_config.yml` 파일에서 `google_analytics`의 `id`란에 복사한 측정 ID를 입력한다.

![3](https://user-images.githubusercontent.com/53047744/190532889-61c82d1e-52d4-48c6-9c4a-15ef06d4edea.png)

이렇게 하여 github에 push하면 실시간으로 트래픽을 모니터링할 수 있다.

![image](https://user-images.githubusercontent.com/53047744/189792157-c977b1a9-40a6-4e92-993c-7e3b64e8b7e5.png)


## Page Views 설정

아래의 `Google Cloud` 홈페이지로 이동하여 `애플리케이션 만들기`를 클릭 한다.

> Google Cloud : https://console.cloud.google.com/appengine

![image](https://user-images.githubusercontent.com/53047744/189792066-3665ea90-bad3-4002-b99a-b8a9d971d20a.png)

위치를 설정한다.
나는 한국에 있기 때문에 asia-northeast3로 위치를 설정하였다.

![image](https://user-images.githubusercontent.com/53047744/189792265-8e57a271-6b94-425f-8695-6e35562748b9.png)

리소스의 `Language`를 `Python`으로 선택하고 `Environment`를 `표준`으로 선택한다.

![image](https://user-images.githubusercontent.com/53047744/189792847-1af03c4d-1b43-4d75-9fe5-f9c7f76267bf.png)

왼쪽 상단 메뉴 버튼을 눌러서 `API 및 서비스 이동` 탭의 `사용 설정된 API 및 서비스`로 이동한다.

![4](https://user-images.githubusercontent.com/53047744/190533884-38b55043-683b-493f-8a70-b9b8842987ff.png)

왼쪽에서 `OAuth 동의 화면`을 클릭한다.

![image](https://user-images.githubusercontent.com/53047744/189794374-3370ebda-a9b9-4ad5-8313-0952b1cc122f.png)

블로그가 공개적으로 호스팅 될거니 `외부`를 선택하여 `만들기 버튼`을 클릭한다.

![image](https://user-images.githubusercontent.com/53047744/189794559-fc587f3f-310f-41ab-9b14-ba7e0c499cf8.png)

`OAuth 동의 화면`에서 `앱 이름`, `사용자 지원 이메일`, `개발자 연락처 정보`를 입력한다.

![image](https://user-images.githubusercontent.com/53047744/189794895-1f2bbd41-ae4f-48d9-a4c4-3d99aad03407.png)

![6](https://user-images.githubusercontent.com/53047744/190535132-3596d7f0-6efd-4670-8fd5-f770213fcbe4.png)

왼쪽의 `API 및 서비스`에서 `사용자 인증 정보`로 이동해 `사용자 인증 정보 만들기`의 `OAuth 클라이언트 ID`를 클릭한다.

![5](https://user-images.githubusercontent.com/53047744/190534869-01377e6d-e843-40c4-87a4-865bce9cced0.png)

`애플리케이션 유형`은 `웹 애플리케이션`을 선택한다.

이름도 입력해준다.

![7](https://user-images.githubusercontent.com/53047744/190535721-4cf25aed-6503-4b4f-b578-68e7b3b169eb.png)

`승인된 리디렉션 URI`에는 아래의 형식으로 입력한다.
> `https://<project-id>.<region>.r.appspot.com/admin/auth`

`project-id`는 상단의 프로젝트 타이틀을 클릭하면 `ID` 컬럼에 적혀있다.

![8](https://user-images.githubusercontent.com/53047744/190536463-a17eb300-b015-48ad-8c3d-5ae934a6311d.png)

`region`은 어디서 확인 하는지 찾지 못했다.

나는 앞에서 애플리케이션을 만들 때 설정한 위치를 입력하는 거라고 생각했는데 안 되어서 시간을 날렸다.

이 URI는 `superProxy`에서 로그인을 한 후에 이동되는 경로이다. 실제로 로그인을 했을 때 `region` 부분에 du라고 적힌 경로로 이동을 한 것을 보고 일단은 du로 작성하였다.

~~혹시 아시는 분은 댓글로 알려주시면 감사하겠습니다.~~

> 예시: https://civil-sprite-123456.du.r.appspot.com/admin/auth

이렇게 해서 만들면 `클라이언트 ID`와 `클라이언트 보안 비밀번호`를 알려주는 창이 나온다.

이 번호들은 방금 만든 `클라이언트 ID`를 클릭하면 다시 확인할 수 있다.

![9](https://user-images.githubusercontent.com/53047744/190537817-6044d04b-8e85-47f4-b27b-763bc8490554.png)

![10](https://user-images.githubusercontent.com/53047744/190538094-ae828351-d051-4bba-954b-c3bfbd0302b0.png)

`클라이언트 ID`와 `클라이언트 보안 비밀번호`를 복사한다.

아래의 링크로 들어가 플랫폼용 클라우드 SDK를 설치한다.

> https://cloud.google.com/sdk/docs/quickstart

`Google Cloud CLI 설치 프로그램`을 다운로드해서 설치한다.

![image](https://user-images.githubusercontent.com/53047744/190538297-8e128776-b946-42a3-8071-48aded096727.png)

`Google Cloud SDK shell`을 실행하여 다음 명령을 실행한다.

~~정확하게 기억이 안 나지만 대충 로그인 어쩌고 뜨고 픽업 프로젝트 나오면 아까 프로젝트 ID에 해당하는 것을 선택해주면 된다.~~

```console
# gcloud init

~snip~

You are logged in as: [blah_blah@gmail.com].

Pick cloud project to use:
[1] chirpy-test-300716
[2] Create a new project
Please enter numeric choice or text value (must exactly match list
item): 1
```

superProxy를 사용하기 위해 `결제`와 `Google Analytics API`를 설정할 것이다.

왼쪽 위 메뉴 버튼을 눌러서 `결제`로 들어가 결제 계정을 만든다.

![12](https://user-images.githubusercontent.com/53047744/190539267-5525ac89-62ad-4d24-80dc-250b33a54775.png)

`API 및 서비스`의 `라이브러리`를 클릭하여 `API 및 서비스 검색`에 `Google Analytics API`를 검색하여 사용 버튼을 클릭한다.

![11](https://user-images.githubusercontent.com/53047744/190538748-78a64fb0-dde9-44ca-b45e-e860b5e3c607.png)

![image](https://user-images.githubusercontent.com/53047744/189794173-04888aed-43a2-4b81-a3d0-ef852301933c.png)


## Google Analytics superProxy 설정

아래 깃허브 링크에 있는 프로젝트에서 `Google Analytics superProxy` 프로젝트를 Google Cloud CLI가 깔린 폴더 안에 있는 `google-cloud-sdk`에 붙여넣기 한다.

> Github Link : https://github.com/googleanalytics/google-analytics-super-proxy

나의 경우에는 아래 경로에 있었다.

> C:\Users\사용자이름\AppData\Local\Google\Cloud SDK\google-cloud-sdk

`google-cloud-sdk`의 `src/app.yaml`파일 에서 첫 두 줄을 제거한다.

```diff
- application: your-project-id
- version: 1
```

`src/config.py`파일에 `AUTH_CONFIG`와 `XSRF_KEY`를 입력한다.

`OAUTH_CLIENT_ID`와 `OAUTH_CLIENT_SECRET`는 아까 복사했던 것을 그대로 입력하면 되고 `OAUTH_REDIRECT_URI`는 `api 및 서비스` > `사용자 인증 정보` > `클라이언트 ID`에 입력했던 `승인된 리디렉션 URI`를 입력하면 된다.

`XSRF_KEY`는 자신이 적고 싶은대로 적어주면 된다. 어렵게 적어주자.

![13](https://user-images.githubusercontent.com/53047744/190540888-a605d8c8-a618-4fb7-bfb4-a859fb384515.png)

다시 `Google Cloud SDK Shell`을 실행하여 `google-cloud-sdk/src` 위치에서 아래 명령을 실행한다.

```console
# gcloud app deploy
```

deploy해서 배포된 서비스 주소 뒤에 /admin을 붙여서 접속하면 아래와 같은 페이지가 나온다.

주소는 콘솔에서 `target url`이라고 출력된 란에 있다.

![image](https://user-images.githubusercontent.com/53047744/189834800-2124d5c3-2fd4-4133-ae74-8ab7e8f8ad52.png)

`Authorize Access` 버튼을 눌러 자신을 관리자로 추가한다.

![image](https://user-images.githubusercontent.com/53047744/189874698-c3fac5b7-6a24-47ce-a8f3-131581787a43.png)

`Continue`를 누르면 아래 화면이 나온다.

![image](https://user-images.githubusercontent.com/53047744/189876500-184d6b69-6be7-48d3-bd2a-4708bcebb9d3.png)

## Google Analytics Query 만들기
위 사진의 `Create Query` 버튼을 누르면 아래 페이지로 이동된다.

![image](https://user-images.githubusercontent.com/53047744/190543314-f00315aa-4509-46bb-8c23-77d0de913685.png)

`Refresh Interval`는 아래 URI를 몇 초마다 실행할 것인가를 설정하는 곳이다. 초 기준으로 입력해주면 된다. 나는 5분(600)으로 설정하였다.

이제 `Encoded URi for the query`에 들어갈 URI를 만들어보자.

아래 링크에 접속하면 아래 페이지로 이동된다.

> Google Analytics Query Explorer : https://ga-dev-tools.web.app/ga4/query-explorer/

![image](https://user-images.githubusercontent.com/53047744/190543598-3f05127d-2397-45cb-82ab-7abb6f8c451c.png)

`UA Query Explorer`에서 필요한 매개변수를 입력해주고 `RUN QUERY` 버튼을 누르면 API Request URI이 나온다.

입력해야 할 매개변수는 다음과 같다.

* start-date : 블로그에 처음으로 포스팅 한 날짜 `YYYY-MM-DD`
* end-date : `today`
* metrics : `ga:pageviews`
* dimentions : `ga:pagePath`

Chirpy 테마 블로그에서는 필터도 설정하라고 적어놨는데 필터는 잘 모르겠다.

난 적혀져 있는대로 했는데 나중에 다시 알아봐야겠다.

* filter : `ga:pagePath=~^/posts/.*/$;ga:pagePath!@=`

이렇게 해서 Run Query를 클릭해 API Request URI를 `Encoded URI for the query`에 입력한 후 Save Query를 클릭한다.

쿼리가 저장되면 이렇게 나타난다.

![14](https://user-images.githubusercontent.com/53047744/190546003-ef3e5822-6c68-48dd-ab79-94477d036445.png)

`Manage` 버튼을 클릭하면 아래의 페이지가 나타난다.

![15](https://user-images.githubusercontent.com/53047744/190567175-9fa99053-e59a-470c-a28a-5a6655769c8e.png)

`Enable Endpoint`와 `Start Scheduling`을 클릭해서 활성화 시켜준다.

그 후 `_config.yml` 파일에서 `google_analytics`의 `proxy_endpoint`에 위 화면의 `Public Request Endpoint`에 있는 `URL`을 복사 붙여넣기 한다.

이렇게 하면 조회수가 활성화가 된다!

![16](https://user-images.githubusercontent.com/53047744/190568951-c21f82e2-99e4-46d7-b5be-7f1d5a2e27a1.png)

이 테마를 만든 사람의 블로그에 있는 설명을 보면서 했는데 superProxy 부분에서 4일이나 걸렸다...
