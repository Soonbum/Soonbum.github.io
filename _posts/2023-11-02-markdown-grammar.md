---
layout: single
title: "마크다운(Markdown) 문법"
categories: script
tags: [markdown, github, documentation]
toc: false
---
1. 주석 처리 문법은 다음과 같습니다.
```
<!-- 주석 -->
```

2. 헤딩 처리는 다음과 같습니다. 목차를 만들거나 내부 링크를 걸 때 꼭 있어야 합니다.
```
# 머릿말 1
## 머릿말 2
### 머릿말 3
#### 머릿말 4
##### 머릿말 5
###### 머릿말 6
```

3. 수평선을 만드는 방법은 다음과 같습니다.
```
--- (하이픈 3개 이상)
___ (언더스코어 3개 이상)
*** (애스터리스크 3개 이상)
```

4. 텍스트 속성은 3가지가 있습니다.
```
**강조체** 또는 __강조제__ (애스터리스크 또는 언더스코어를 양쪽에 2개씩) 또는 <b>강조체</b>
*이탤릭체* 또는 _이탤릭체_ (애스터리스크 또는 언더스코어를 양쪽에 1개씩) 또는 <i>이탤릭체</i>
~~취소선~~ (틸드를 양쪽에 2개씩)
```

5. 인용구는 다음과 같습니다. (중첩도 사용 가능함)
```
> 인용문
>> 인용문 (중첩1)
>>> 인용문 (중첩2)
```
> “Everyone has a plan until they get hit. Then, like a rat, they stop in fear and freeze.” - Mike Tyson

6. 불릿 리스트는 다음과 같습니다.
```
* Apple
* Pear
  - Orange
  - Banana
```
* Apple
* Pear
  - Orange
  - Banana

7. 숫자 리스트는 다음과 같습니다.
```
1. 첫번째
2. 두번째
3. 세번째
```

8. HTML 링크는 이렇게 걸 수 있습니다.
```
<링크 주소>
또는
[링크 설명](링크 주소)
```

9. 이미지는 이렇게 걸 수 있습니다.
```
![대체 텍스트](이미지 주소)
또는
![대체 텍스트](이미지 주소 "툴팁텍스트")
```
![image](https://github.com/Soonbum/Qt_for_Python/assets/16474083/24d3c325-2737-4baa-994e-41f5ca3ec324 "Qt for Python")

10. 이미지 HTML 링크는 이렇게 걸 수 있습니다.
```
[![대체 텍스트](이미지 주소)](링크 주소)
```
[![텍스트](http://cfile24.uf.tistory.com/image/2444873B57E257821FA2AE)](https://unity3d.com/kr)

11. 동영상은 이렇게 걸 수 있습니다. (이미지 HTML 링크와 같은 형태)
```
[![대체 텍스트](썸네일 주소)](동영상 주소)

썸네일 이미지 링크는 동영상 주소의 접미사를 활용하면 됩니다.
- 0.jpg : 480*360 ( Player background ) 
- 1.jpg : 120*90 ( start )
- 2.jpg : 120*90 ( middle )
- 3.jpg : 120*90 ( end ) 
- hqdefault.jpg : 480*360 ( Player background )
- mqdefault.jpg :320*180 ( Player background )
- default.jpg :120*90  ( Player background )
- sddefault.jpg : 640*480 (480p의 경우)
- maxresdefault.jpg : 1920*1080 (1080p의 경우)
```
[![Video Label](http://img.youtube.com/vi/kMEb_BzyUqk/0.jpg)](https://youtu.be/kMEb_BzyUqk)

12. 표(테이블) 만들기

```
|헤더|설명|
|--|--|
|Cell1|Cell2|
|Cell1|Cell2|
|Cell1|Cell2|

|--:| --> 오른쪽 정렬
|:--| --> 왼쪽 정렬
|:--:| --> 가운데 정렬
```
|헤더|설명|
|--|--|
|Cell1|Cell2|
|Cell1|Cell2|
|Cell1|Cell2|

13. 코드 블럭 (싱글)
```
<!-- 코드의 경우 `(백틱) 문자로 감싸기 -->
`console.log('message')`
```

14. 코드 블럭 (멀티 라인)

![image](https://github.com/Soonbum/Markdown_Grammar/assets/16474083/150b965a-c405-43a5-9491-a9385676511e)

* 코드 블럭의 경우 백틱 3개로 위아래 감싸면 됩니다.
  -  백틱 3개 + 코드 + 백틱 3개
* 처음 나오는 백틱 3개 바로 뒤에 프로그래밍 언어 약자를 입력하면 그에 맞는 테마가 적용됩니다.
  - bash, cs, cpp, css, diff, html, http, ini, json, java, js 또는 javascript, php, perl, python, ruby, sql

15. 각주
```
이것은 간단한 각주[^1]입니다.
또 이것은 두번째 각주[^2]입니다.
각주는 문자[^한글각주]로도 가능합니다.

[^1]: 1번째 각주
[^2]: 2번째 각주
[^한글각주]: 3번째 각주
```
이것은 간단한 각주[^1]입니다.
또 이것은 두번째 각주[^2]입니다.
각주는 문자[^한글각주]로도 가능합니다.

[^1]: 1번째 각주
[^2]: 2번째 각주
[^한글각주]: 3번째 각주

16. Todo 리스트 (깃허브 전용)
```
- [x] 해야 할 일 1
- [x] 해야 할 일 2
- [x] 해야 할 일 3
- [ ] 해야 할 일 4
```
- [x] 해야 할 일 1
- [x] 해야 할 일 2
- [x] 해야 할 일 3
- [ ] 해야 할 일 4

17. 목차 만들기
```
목차
[1.개발을 하고 싶어요](#개발을-하고-싶어요)
[2.코딩을 잘하고 싶어요](#coding을-잘하고-싶어요)

본문
## 개발을 하고 싶어요
## Coding을 잘하고 싶어요

주의사항:
1. 띄어쓰기는 - 문자로 대체하면 됩니다.
2. 영어는 소문자로 바꾸세요.
```

