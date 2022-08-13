---
layout: post
title: github 블로그 만들기 2
---

이제 블로그를 만들었으니 게시글을 작성하는 명령어를 알아보도록 하겠다.

## 게시글 관련 명령어 사용

아래의 사이트를 참고하여 작성하였다.

> https://github.com/jekyll/jekyll-compose

처음에 명령어를 사용하기 위해서 추가적으로 설치를 해줘야 한다.

루트 폴더에 `Gemfile` 이라는 파일이 있을 것이다. 그 파일 안에 밑에 적힌 것을 추가로 작성해주자.

> gem 'jekyll-compose', group: [:jekyll_plugins]

그 후 실행을 하면 설치가 완료된다.

```powershell
$ bundle
```

설치한 후 도움말을 확인하고 싶으면 아래 명령어를 입력하면 된다.

```powershell
$ bundle exec jekyll help
```

명령어를 사용할 때는 꼭 아래 형식으로 사용해야 한다.

```powershell
$ bundle exec jekyll <subcommand> [options]
```

여기서 우리가 쓸 것은 게시글을 작성하는데에 필요한 명령어 들이다.

```
draft      # 지정된 이름의 새 초안 게시물을 만든다.
post       # 지정된 이름의 새 게시물을 만든다.
publish    # 초안을 _posts 디렉토리로 이동시키고 날짜를 설정한다.
unpublish  # 게시물을 _drafts 디렉토리로 이동시킨다. (게시를 취소한다.)
page       # 지정된 이름의 새 페이지를 만든다. (사용을 안 해서 모르겠다. 찾아봐야겠다.)
rename     # 게시물의 이름과 제목을 변경한다.
compose    # 지정된 이름의 새 파일을 만든다.
```

## post

새 게시물을 만들 수 있다.  
예시

```powershell
$ bundle exec jekyll post "My New Post"
# or specify a custom format for the date attribute in the yaml front matter
$ bundle exec jekyll post "My New Post" --timestamp-format "%Y-%m-%d %H:%M:%S %z"
```

## compose

새 파일을 만든다.

```powershell
# or by using the compose command
$ bundle exec jekyll compose "My New Post"

# or by using the compose command with post specified
$ bundle exec jekyll compose "My New Post" --post

# or by using the compose command with the posts collection specified
$ bundle exec jekyll compose "My New Post" --collection "posts"
```

```powershell
# or by using the compose command with draft specified
$ bundle exec jekyll compose "My new draft" --draft

# or by using the compose command with the drafts collection specified
$ bundle exec jekyll compose "My new draft" --collection "drafts"
```

컬렉션에 새 파일을 만든다.

```powershell
$ bundle exec jekyll compose "My New Thing" --collection "things"
```

## draft

초안을 만든다.

```powershell
$ bundle exec jekyll draft "My new draft"
```

## rename

이름을 바꾼다.

게시글의 경우

```powershell
$ bundle exec jekyll rename _posts/2014-01-24-my-new-draft.md "My New Post"

# or specify a specific date
$ bundle exec jekyll rename _posts/2014-01-24-my-new-post.md "My Old Post" --date "2012-03-04"

# or specify the current date
$ bundle exec jekyll rename _posts/2012-03-04-my-old-post.md "My New Post" --now
```

초안의 경우

```powershell
$ bundle exec jekyll rename _drafts/my-new-draft.md "My Renamed Draft"

# or rename it back
$ bundle exec jekyll rename _drafts/my-renamed-draft.md "My new draft"
```

## publish

초안을 게시한다.

```powershell
$ bundle exec jekyll publish _drafts/my-new-draft.md

# or specify a specific date on which to publish it
$ bundle exec jekyll publish _drafts/my-new-draft.md --date 2014-01-24
# or specify a custom format for the date attribute in the yaml front matter
$ bundle exec jekyll publish _drafts/my-new-draft.md --timestamp-format "%Y-%m-%d %H:%M:%S %z"
```

## unpublish

게시물 게시를 취소한다.

```powershell
$ bundle exec jekyll unpublish _posts/2014-01-24-my-new-draft.md
```

## 기본 플러그인 구성

구성을 사용자 정의하려면 jekyll_compose 를 편집하면 된다.

## mark다운 문법

vscode 확장 프로그램 markdown
