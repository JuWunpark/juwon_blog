# 블로그 구조 가이드

## 📁 디렉토리 구조

```
myblog/
├── _config.yml          # 블로그 전역 설정
├── _posts/              # 📝 포스트 작성 폴더
├── _pages/              # 정적 페이지 템플릿 (about, archive, tags 등)
├── _layouts/            # 레이아웃 템플릿 (default, post, home-page, menu-page)
├── _includes/           # 재사용 가능한 컴포넌트 (header, footer, sidebar 등)
├── assets/              # 정적 파일 (CSS, JS, 이미지, 폰트)
│   ├── css/
│   ├── js/
│   └── img/             # 이미지 저장 폴더
├── about.markdown       # About 페이지 (수정 가능)
├── index.html           # 홈페이지
└── tags/                # 태그 페이지들
```

## 📄 About 페이지 수정 방법

### 위치
- **파일**: `/home/ubuntu/myblog/about.markdown`
- **URL**: `https://blog.juwonpark.me/project/about/`

### 현재 내용
```markdown
---
layout: menu-page
title: About me
permalink: /about/
---

## 안녕하세요, 주원입니다 👋

- 관심사: AI 앱 개발(Django), DevOps, 자동화, 데이터 분석  
- 지금 하는 일: 웹 서버 운영, devops공부, 그 외 이것저것 하고 있습니다   
- 깃허브: [JuWunpark](https://github.com/JuWunpark)  
- 이메일: <hello@juwonpark.me>

이 블로그에는 개발 메모, 배포 팁, 에러 해결 기록을 짧게 남깁니다.
```

### 수정 방법
1. `about.markdown` 파일을 직접 편집
2. 또는 `_config.yml`의 `author`, `about-author`, `email`, `github` 등을 수정하면 About 페이지 하단의 연락처 정보가 자동 반영됨

### About 페이지에 표시되는 정보
- **작성자 이름**: `_config.yml`의 `author` 필드
- **작성자 소개**: `_config.yml`의 `about-author` 필드  
- **작성자 사진**: `_config.yml`의 `author-pic` 필드 (이미지는 `assets/img/` 폴더에 저장)
- **연락처 링크**: `_config.yml`의 `email`, `github`, `linkedin`, `twitter` 등

## 📝 포스트 작성 가이드

### 파일 위치
- **폴더**: `_posts/`
- **파일명 형식**: `YYYY-MM-DD-제목.md` 또는 `YYYY-MM-DD-제목.markdown`

### 필수 Front Matter 필드

```yaml
---
layout: post          # 또는 "default" (post 권장)
title: "포스트 제목"   # 필수
date: 2025-11-13 10:00:00 +0000  # 필수 (ISO 8601 형식)
tags: jekyll github devops  # 권장 (공백으로 구분)
---
```

### 선택 Front Matter 필드

```yaml
---
layout: post
title: "포스트 제목"
date: 2025-11-13 10:00:00 +0000
tags: jekyll github devops

# 이미지 (홈페이지 카드와 포스트 상단에 표시)
img: posts/my-image.jpg  # assets/img/posts/my-image.jpg 경로

# 설명 (SEO 및 미리보기용)
description: "이 포스트는 Jekyll 블로그 설정에 대한 가이드입니다."

# 읽기 시간 표시 여부
read_time: true  # 기본값: false

# 날짜 표시 여부
show_date: true  # 기본값: false

# 목차(Table of Contents) 표시 여부
toc: true  # 기본값: false

# 작성자 (기본값: _config.yml의 author)
author: Juwon

# 카테고리 (태그와 유사하지만 다른 용도)
categories: tutorial
---
```

### 포스트 작성 예시

```markdown
---
layout: post
title: "Jekyll 블로그 시작하기"
date: 2025-11-13 10:00:00 +0000
tags: jekyll tutorial getting-started
img: posts/jekyll-logo.png
description: "Jekyll을 사용하여 정적 블로그를 만드는 방법을 소개합니다."
read_time: true
show_date: true
toc: true
---

## 소개

이 포스트는 Jekyll 블로그를 시작하는 방법에 대해 설명합니다.

## 설치

...

## 마무리

...
```

### 이미지 사용 방법

1. **이미지 저장 위치**: `assets/img/posts/` 폴더에 저장
2. **Front Matter에 지정**: `img: posts/my-image.jpg`
3. **마크다운에서 사용**: `![설명](/assets/img/posts/my-image.jpg)`

### 태그 시스템

- **태그 지정**: `tags: jekyll github devops` (공백으로 구분)
- **태그 페이지**: 자동으로 `/tag/jekyll/`, `/tag/github/` 등 생성
- **모든 태그 보기**: `/tags/` 페이지에서 확인 가능

## 🎨 주요 레이아웃

- **`post`**: 포스트 상세 페이지 (권장)
- **`default`**: 기본 레이아웃 (포스트에도 사용 가능)
- **`home-page`**: 홈페이지 레이아웃
- **`menu-page`**: 메뉴/정적 페이지 레이아웃 (About, Archive 등)

## ⚙️ _config.yml 주요 설정

```yaml
# 사이트 정보
title: Juwon Blog
description: 'Juwon의 블로그'
url: "https://blog.juwonpark.me"
baseurl: /project

# 작성자 정보
author: Juwon
author-pic: Myself_Neon_grey.jpg  # assets/img/ 폴더에 저장
about-author: Juwon의 블로그입니다.

# 연락처
email: hello@juwonpark.me
github: JuWunpark
linkedin: 
twitter: 

# 페이지네이션
paginate: 6  # 홈페이지에 표시할 포스트 수

# 읽기 속도
words_per_minute: 200  # 읽기 시간 계산 기준
```

## 📌 참고사항

1. **포스트 이미지**: `img` 필드가 없어도 포스트는 정상 작동하지만, 홈페이지 카드와 포스트 상단 커버 이미지가 표시되지 않음
2. **태그**: 태그를 지정하지 않으면 태그 페이지에서 해당 포스트가 표시되지 않음
3. **날짜 형식**: ISO 8601 형식 권장 (`YYYY-MM-DD HH:MM:SS +0000`)
4. **파일명**: 한글 파일명 사용 가능하지만, URL에는 영문이 더 적합
