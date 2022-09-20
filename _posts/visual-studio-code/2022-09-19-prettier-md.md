---
layout: post
title: VSCode로 markdown 작성 시 줄 끝의 공백이 제거되는 현상 해결 방법
date: 2022-09-19 20:36 +0900
categories: [Visual Studio Code]
tag: [Visual Studio Code, Prettier, .editorconfig, Markdown]
---

VSCode로 블로그 글을 작성하려고 하였는데 저장을 하게 되면 줄 끝에 있는 공백이 제거되는 현상이 있어서, 줄 끝에 있는 공백 2칸이 없어져서 개행을 할 때 곤란했다.

그래서 해결방법을 찾아보았다.

## Prettier 사용 중일 시 Markdown파일에 적용되지 않도록 하기

Prettier는 정해진 규칙에 따라 자동으로 코드를 정리해주는 VSCode 확장 프로그램이다.

이 프로그램을 사용하고 있다면 Markdown 파일이 있는 폴더 또는 루트 폴더에 `.prettierignore` 파일을 만든다.

그 후 아래처럼 작성한다.

```plaintext
*.md
```

이렇게 하면 해당폴더와 하위 폴더의 Markdown 파일은 전부 Prettier 기능이 적용되지 않게 된다.

## .editorconfig 파일 수정하기
editorconfig 파일도 Prettier와 비슷하게 자동으로 코드를 정리해주는 설정 파일이다.

이 파일에서 `trim_trailing_whitespace` 라고 적힌 줄을 찾아 값을 false로 바꾼다.

`trim_trailing_whitespace`는 줄 끝의 공백 제거 여부를 나타낸다. 그래서 false로 설정하면 작동하지 않게 된다.

## VSCode의 텍스트 편집기 설정 수정하기

VSCode의 설정에서 텍스트 편집기의 `Trim Trailing Whitespace`의 체크를 해제한다.

이것도 마찬가지로 줄 끝의 공백 제거 여부를 나타내는 것이기 때문에 체크를 해제해야 한다.

이렇게 설정하면 저장을 했을 때 줄 끝의 공백이 없어지는 현상을 해결할 수 있다.
