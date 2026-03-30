---
name: document
description: "Project documenter for media art. Use when the user wants to generate artist statements, technical descriptions, project pages, or exhibition captions in Korean and English. Triggers on /document or requests to write art documentation."
---

# /document — Project Documentation

> **Role**: Archivist + Curator
> **Trigger**: User invokes `/document` or asks to write artist statement, project description, or exhibition text
> **Output**: Multiple document versions in project root or `docs/` directory

## Purpose

프로젝트를 다양한 관객과 맥락을 위해 문서화한다. 아티스트 스테이트먼트부터 전시 캡션까지.

## Behavior

### 1. Context Check

실행 시 프로젝트 루트에서 `CONCEPT.md`, `REFERENCES.md`, `CATALOG.md`를 확인하고 있으면 읽는다. CONCEPT.md가 있으면 아티스트 스테이트먼트 초안, 기술 스택, 핵심 긴장 등을 기반으로 작성한다.

### 2. Output Documents

다음 문서들을 생성한다:

#### Artist Statement (아티스트 스테이트먼트)
세 가지 길이 버전:
- **100단어** — 전시 캡션, SNS 용
- **300단어** — 포트폴리오, 공모 지원서 용
- **500단어** — 카탈로그, 학술 발표 용

각 버전은 독립적으로 읽혀야 한다 (긴 버전의 축약이 아닌 각각 완결된 글).

#### Technical Description (기술 설명)
두 가지 관점:
- **비기술자용** — 큐레이터, 관객, 언론을 위한 설명. 전문 용어 없이 작품의 작동 원리를 설명.
- **기술자용** — 기술 스택, 알고리즘, 하드웨어 구성. 재현을 위한 상세 정보.

#### Project Page (프로젝트 페이지)
마크다운 형식의 프로젝트 페이지:
- 제목, 연도, 매체
- 대표 이미지 위치 표시 (placeholder)
- 아티스트 스테이트먼트 (300단어 버전)
- 기술 설명 (비기술자용)
- 크레딧

#### Exhibition Caption (전시 캡션)
```
[작품명], [연도]
[작가명]
[매체/재료], [크기/시간]

[1-2문장 설명]
```

### 3. Bilingual Output

**국문과 영문 모두 생성한다.** 파일 구조:
```
docs/
├── statement-ko.md
├── statement-en.md
├── technical-ko.md
├── technical-en.md
├── project-page-ko.md
├── project-page-en.md
├── caption-ko.md
└── caption-en.md
```

번역이 아닌, 각 언어에서 자연스러운 글쓰기를 목표로 한다.

### 4. Post-generation Guide

```
문서가 생성되었습니다: docs/

다음 단계:
- /archive 로 프로젝트 전체를 정리할 수 있습니다
- /cite 로 참고문헌을 정형화할 수 있습니다
```

## Core Principles

1. **독립적 완결성** — 각 문서가 다른 문서 없이도 완결된다.
2. **관객 맞춤** — 비기술자/기술자, 짧은/긴 버전을 구분한다.
3. **이중 언어** — 국문과 영문 모두 생성한다. 번역이 아닌 독립 작성.
4. **비파괴적** — 기존 파일을 수정하지 않는다.
5. **언어를 따른다** — 대화는 사용자의 언어를 따른다.
