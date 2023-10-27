---
layout: single
title: "깃헙 블로그 만드는 방법"
categories: github
tags: blog
toc: false
---

# 깃헙 블로그 만드는 방법

## [블로그 구축하기](https://www.youtube.com/watch?v=ACzFIAOsfpM)

* 마음에 드는 [테마](https://github.com/topics/jekyll-theme)를 선택합니다.
* Fork합니다.
  - [도큐먼트](https://mmistakes.github.io/minimal-mistakes/docs/configuration)를 꼼꼼히 확인합니다.
* Settings에서 저장소 이름을 변경합니다.
  - 반드시 이름을 "(내 계정 이름).github.io"라고 해야 합니다.
* _config.yml 파일에서 URL을 수정합니다.
  - 블로그의 주소: "https://(내 계정 이름).github.io"
  - 대부분의 설정은 여기서 할 수 있습니다.
* 테마도 변경해 볼 수 있습니다.
  - _config.yml 에 테마 있음
* 새로운 포스팅을 [생성](https://jekyllrb.com/docs/posts)합니다.
  - 저장소에서 Add file > Create new file을 선택합니다.
  - 만약 처음 포스팅을 하는 것이라면 "(내 계정 이름).github.io/_posts/2023-10-23-first.md" 라는 식으로 작성합니다. (first는 후에 포스트 주소가 됨)
  - md 파일 첫 부분에 다음 속성을 넣으세요.
    ```
    ---
    layout: single
    title: "첫 포스팅 입니다. 설레네요."
    categories: coding    # 카테고리 설정을 했을 경우 적용됨 (EP07)
    tags: python          # 태그 설정을 했을 경우 적용됨 (EP07), 복수형의 경우 [python, blog, jekyll]
    toc: true             # Heading을 이용하여 자동으로 목차가 생성됨
    ---
    "포스팅 내용"
    ```
* jupyter notebook 파일을 다운로드 받아 업로드하는 방법도 있습니다.
  - 다운로드 받은 .md 파일명을 변경합니다. (예시: "2023-10-23-second.md")
* images 업로드 방법
  - images 폴더 만들어서 이미지 업로드
* 자세한 내용은 [Quick-Start Guide](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)를 보세요.

# 깃헙 블로그 만들기 시즌 1

## [EP01. 개발환경 설치하기](https://www.youtube.com/watch?v=--MMmHbSH9k)

## [EP02. 이미지 매우 간단하게 추가하기](https://www.youtube.com/watch?v=1UEOWcKcVdk)

## [EP03. 업데이트 내역을 실시간 확인하기](https://www.youtube.com/watch?v=0TeHUqSAb6Q)

## [EP04. 블로그 설정 매우 쉽게 변경하기*](https://www.youtube.com/watch?v=c-h3XcDjHtQ)

## [EP05. 댓글 & 구글 애널리틱스 추가하기](https://www.youtube.com/watch?v=anXaW9xhgcU)

## [EP06. 테마변경, SNS 링크 삽입, Pagination 설정*](https://www.youtube.com/watch?v=Wi1W3hpfvZc)

## [EP07. 카테고리 기능, #태그 기능 추가하기*](https://www.youtube.com/watch?v=3UOh0rKlxjg)

## [EP08. 글 목차, 404 페이지 에러 구현*](https://www.youtube.com/watch?v=OoeGqYu8JFQ)

## [EP09. 구글, 네이버 검색엔진 등록하기*](https://www.youtube.com/watch?v=OxRZrg0u6h4)

## [EP10. 블로그 내 글 검색기능 추가하기*](https://www.youtube.com/watch?v=AONVKTeeaWY)

## [EP11. 블로그에 설정된 폰트(글씨체) 변경하기](https://www.youtube.com/watch?v=k7DjQ1JF9rY)

## [EP12. 공지사항(Notice), 버튼, YouTube 영상 추가하기*](https://www.youtube.com/watch?v=q0P3TSoVNDM)

## [주피터 노트북(.ipynb)을 블로그 콘텐츠로 1분만에 변환하기](https://www.youtube.com/watch?v=g4TgmY5VK-A)

# 깃헙 블로그 만들기 시즌 2

## [EP14. 주요 내용 안내](https://www.youtube.com/watch?v=p1cdQPw-JME)

## [EP15. 최신 업데이트 내역 블로그에 적용하기(최신 기능 적용)*](https://www.youtube.com/watch?v=zoZ4LF-8j2E)

## [EP16. 메인 페이지에 사진 추가, 유튜브 아이콘/링크 추가하기*](https://www.youtube.com/watch?v=PODVNQI6QL0)

## [EP17. 포스트 왼쪽 영역 확장, TOC 스타일 수정하기(CSS 스타일 수정하는 법)](https://www.youtube.com/watch?v=GIsCf9_jboM)

## [EP18. 이미지 추가시 오류 해결](https://www.youtube.com/watch?v=ndJ5B-DyBnA)

## [EP19. 사이트 주소가 바뀌었을 때 redirect_from 플러그인으로 해결하기](https://www.youtube.com/watch?v=aVhu5CEpkSI)

## [EP20. 나만의 커스텀 CSS 스타일을 마크다운 형식으로 적용하기*](https://www.youtube.com/watch?v=monQhJMsGi4)

## [EP21. LaTeX 수식 문법을 지원하는 mathjax를 블로그에 적용하기](https://www.youtube.com/watch?v=3O08iA_BFbM)

## [EP22. 연도별 포스팅 아카이브 생성하기*](https://www.youtube.com/watch?v=251YUs2FGfI)

## [EP23. 블로그 배포 더이상 기다리지 마세요~ 배포 브랜치 설정 & 배포 시점 확인하기](https://www.youtube.com/watch?v=5aoIeNvquOE)

## [EP24. 사이드바에 카테고리 & 태그 숫자 카운트와 함께 추가하기*](https://www.youtube.com/watch?v=FDFBJ_86sF4)

## [EP25. 블로그에 상단 배너 추가하기*](https://www.youtube.com/watch?v=fo3tpjxZbZQ)

