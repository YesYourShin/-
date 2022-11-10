---
layout: post
title: dll 사용안됨
---

파이썬으로 매크로를 만들려고 할 때 문제 발생
```python
windll.LoadLibrary('C:\myfile\MECRO\DD94687.64.dll')
```
해당 코드에 대해 에러가 발생한다.
```console
OSError: [WinError 1114] DLL 초기화 루틴을 실행할 수 없습니다
```

해결과정
1. 배터리를 최고성능으로 향상시켜보라는 방법은 먹히지 않았다.
