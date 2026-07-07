---
title: "Markdown으로 블로그 글을 관리하는 흐름"
description: "frontmatter와 Markdown 본문을 이용해 글을 빠르게 추가하는 기본 운영 방식입니다."
slug: "markdown-blog-workflow"
date: "2026-07-07"
category: "콘텐츠"
tags: ["Markdown", "콘텐츠관리", "자동화"]
image: "/images/sample.jpg"
---

Markdown 기반 블로그는 글 파일 자체가 콘텐츠 데이터베이스 역할을 합니다. 제목, 설명, 날짜, 태그 같은 정보는 frontmatter에 넣습니다.

## 작성 흐름

1. 새 글 생성 스크립트를 실행합니다.
2. 생성된 Markdown 파일의 frontmatter를 확인합니다.
3. 본문을 작성하고 빌드합니다.

이 방식은 CMS 없이도 Git 기반으로 글의 변경 이력을 관리하기 좋습니다.
