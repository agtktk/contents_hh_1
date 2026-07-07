# SEO Static Blog

WordPress 없이 운영할 수 있는 Markdown 기반 정적 블로그입니다. Astro로 정적 HTML을 생성하며 Cloudflare Pages, GitHub Pages, Netlify에 배포할 수 있습니다.

## 설치

```bash
npm install
```

## 개발 서버 실행

```bash
npm run dev
```

기본 주소는 `http://localhost:4321`입니다.

## 새 글 추가

```bash
npm run new-post "글 제목" "카테고리" "태그1,태그2"
```

`content/posts/` 안에 `날짜-슬러그.md` 파일이 생성됩니다. 각 글은 frontmatter를 사용합니다.

```md
---
title: "글 제목"
description: "메타 설명"
slug: "post-slug"
date: "2026-07-07"
category: "카테고리"
tags: ["태그1", "태그2"]
image: "/images/sample.jpg"
---
```

## 빌드

```bash
npm run build
```

빌드 결과는 `dist/` 폴더에 생성됩니다. `index.html`, 글 상세 페이지, 카테고리/태그 페이지, `rss.xml`, `robots.txt`, `sitemap.xml` 파일이 포함됩니다.

## site.config 수정

사이트 공통 설정은 `site.config.js`에서 한 번에 수정합니다.

- `siteName`: 사이트 이름
- `siteUrl`: 배포될 실제 URL
- `siteDescription`: 기본 메타 설명
- `author`: 작성자 이름
- `defaultImage`: 기본 Open Graph 이미지
- `naverVerificationCode`: 네이버 소유 확인 코드
- `googleVerificationCode`: 구글 소유 확인 코드

배포 전 `siteUrl`을 실제 도메인으로 바꾸세요.

## Cloudflare Pages 배포

1. GitHub에 이 프로젝트를 푸시합니다.
2. Cloudflare Dashboard에서 Pages 프로젝트를 생성합니다.
3. GitHub 저장소를 연결합니다.
4. Build command에 `npm run build`를 입력합니다.
5. Build output directory에 `dist`를 입력합니다.
6. Node.js 버전은 20 이상을 권장합니다.
7. 배포 후 발급된 도메인 또는 연결한 커스텀 도메인을 `site.config.js`의 `siteUrl`에 반영합니다.

## 네이버 서치어드바이저 등록

1. `site.config.js`의 `siteUrl`을 실제 사이트 주소로 설정합니다.
2. 네이버 서치어드바이저에서 사이트를 등록합니다.
3. HTML 파일 방식이면 `naverVerificationCode`에 네이버가 제공한 코드를 입력합니다.
4. 메타태그 방식도 같은 값이 `<meta name="naver-site-verification">`에 자동 출력됩니다.
5. 배포 후 `/robots.txt`, `/sitemap.xml`, `/rss.xml`에 접속해 정상 출력되는지 확인합니다.
6. 서치어드바이저에 sitemap URL을 제출합니다.

## 파일 구조

```text
content/posts/              Markdown 글
public/images/sample.jpg    샘플 이미지 경로
scripts/new-post.js         새 글 생성 스크립트
src/components/             재사용 컴포넌트
src/layouts/                공통 HTML/SEO 레이아웃
src/pages/                  정적 페이지와 동적 라우트
site.config.js              사이트 설정
astro.config.mjs            Astro 설정
```

## 운영 메모

- 대표 이미지는 `public/images/`에 넣고 글 frontmatter의 `image` 경로를 수정하세요.
- 광고 배너나 CTA는 레이아웃의 `.ad-slot` 위치에 쉽게 삽입할 수 있습니다.
- sitemap은 Astro 빌드 과정에서 자동 생성됩니다.
