---
layout: post
title: "[github 블로그 만들기] 1 - 테마를 사용하여 블로그 생성하기"
date: 2022-07-11 10:10 +0900
categories: [Github Blog]
tag: [Github, Ruby]
---

# 마음에 드는 github 블로그 테마를 선택해보자

테마는 직접 만들 수도 있고 아래의 사이트에서 찾을 수도 있다.

> <https://jamstackthemes.dev/ssg/jekyll/>
> <https://jekyllthemes.org/>
> <https://jekyllthemes.io/>
> <https://github.com/topics/jekyll/>

나는 github 검색창에서 jekyll-theme을 검색해서 나온 것들 중 chirpy라는 테마가 괜찮아 보여서 이 테마를 사용하기로 했다.

![image](https://user-images.githubusercontent.com/53047744/178199374-47bf4922-e362-4df4-8c3b-3a46dc308843.png)

테마 링크

> <https://github.com/cotes2020/jekyll-theme-chirpy>

이 테마의 설명 페이지

> <https://chirpy.cotes.page/>

설명 페이지의 HOME에서 Getting Started 포스팅을 읽으면 설치를 하고 어떻게 실행하면 되는지 설명이 나온다.

# 테마를 내 리포지토리로 가져와보자

잘 모르겠지만 레포지토리 url 뒤에 /generate를 붙이면 해당 레포지토리를 내 레포지토리로 가져오는 것 같다.

> <https://github.com/cotes2020/chirpy-starter/generate>

그 후 자신의 레포지토리의 프로젝트를 clone 하여 받는다.

# Ruby 설치

설치 사이트

> <https://www.ruby-lang.org/en/downloads/>

![image](https://user-images.githubusercontent.com/53047744/178209585-7ced788b-7031-42d3-9d32-371c20721ce4.png)

사이트에 들어가서 RubyInstaller을 누른다.

![image](https://user-images.githubusercontent.com/53047744/178209933-aacadc86-e300-4df4-8874-e016f3cc09ea.png)

빨간 Download 버튼을 누른다.

![image](https://user-images.githubusercontent.com/53047744/178212409-21358efa-0aa0-4e3e-b951-de776f2f01dc.png)

WITH DEVKIT 라고 적힌 것 중 버전이 2.5.0 이상인 것을 다운한다.

설치 방법은 구글에서 검색할 것.

설치가 잘 됐는지 cmd에서 확인해 볼 것

```powershell
$ ruby -v
```

# bundle 설치

gem은 node의 npm과 비슷하게 패키지를 설치할 수 있게 도와주는 툴이다.
Gemfile은 bundler에서 사용하는 의존성 파일이고, bundle은 Gemfile에 정의된 gem들의 의존성을 파악해 사용할 수 있게 해준다.

해당 테마 프로젝트를 Visual Studio Code를 열어서 패키지를 설치해주자.

```powershell
$ bundle
```

# \_config.yml 설정

yml파일에서 필요한 것들을 작성해주자.

- lang : 블로그 언어를 설정하는 곳이다. \_data 폴더 안에 있는 locales 폴더에서 해당되는 언어의 파일명을 그대로 적으면 된다. 해당 파일에서 한글로 표시될 단어들을 수정할 수도 있다.
- timezone : 포스팅 작성 등에 사용되는 시간 설정이다.
- title : 블로그의 제목이다.
- tagline : 타이틀 밑에 들어갈 부제목이다.
- url : 블로그 주소를 적어준다.

이 외에도 필요한 설정은 주석을 읽으면서 알아서 적어주자.

내 기준으로 위의 설정들을 변경하면 이렇게 된다.

> lang: ko-KR
> timezone: Asia/Seoul
> title: Shin
> tagline: 개발하면서 배운 것들을 올리는 블로그 입니다.
> url: "https://YesYourShin.github.io"

# 로컬에서 사이트 확인하기

루트 폴더에서 밑의 코드를 실행시킨다.

```powershell
$ bundle exec jekyll s
```

그러고 나면 <http://127.0.0.1:4000> 에서 사이트를 확인이 가능하다.

# github에서 배포

설명 페이지에서 플랫폼 목록을 업데이트해야 한다고 나와있다.

```powershell
$ bundle lock --add-platform x86_64-linux
```

github에 현재 프로젝트를 push한 다음 github의 리포지토리 이름을 `Github_Username.github.io`로 수정한다.

그 다음 해당 리포지토리의 설정에서 왼쪽 메뉴의 Pages를 눌러 들어간다.
거기서 Source의 Branch를 gh-pages로 변경 후 Save 버튼을 누른다.

![image](https://user-images.githubusercontent.com/53047744/178218744-ca89e658-6df1-4e3d-811a-1a5da817049a.png)

그 후 자신의 블로그 주소(`Github_Username.github.io`)로 가면 블로그가 만들어져 있는 것을 확인할 수 있다.
