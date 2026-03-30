---
name: survey
description: "Reference researcher for media art projects. Use when the user wants to collect references across prior works, technical resources, and inspiration sources. Triggers on /survey or requests to find art/tech references."
---

# /survey — Reference Research

> **Role**: Research assistant
> **Trigger**: User invokes `/survey` or asks to find references/precedents for a project
> **Output**: Entries appended to `REFERENCES.md` in the project root

## Purpose

프로젝트 관련 레퍼런스를 세 축으로 수집하여 REFERENCES.md에 누적한다.

## Behavior

### 1. Context Check

실행 시 프로젝트 루트에서 다음을 확인한다:
- `CONCEPT.md` — 있으면 읽어서 작품 의도·키워드를 기반으로 리서치
- `REFERENCES.md` — 있으면 기존 항목을 보존하고 새 항목을 추가. 없으면 `templates/REFERENCES.md.tmpl` 기반으로 새로 생성
- `CATALOG.md` — 있으면 기존 작업 맥락 파악

### 2. Research Scope

사용자가 주제를 지정하면 해당 주제로 조사한다. 지정하지 않으면 CONCEPT.md의 키워드를 기반으로 리서치 방향을 제안하고 확인을 받는다.

### 3. Three Axes

레퍼런스를 세 축으로 수집한다:

#### Axis 1 — Prior Works (선행 작품)
유사한 컨셉이나 매체를 사용한 미디어아트 작품:
- 작품명, 작가, 연도
- 한 줄 요약
- 현재 프로젝트와의 관련성
- 기술적 인사이트 (알려진 경우)

#### Axis 2 — Technical References (기술 레퍼런스)
관련 라이브러리, 프레임워크, 기법, 논문:
- 제목, 유형 (라이브러리/논문/튜토리얼/기법)
- URL (있는 경우)
- 한 줄 요약
- 프로젝트 적용 방법

#### Axis 3 — Inspiration Sources (영감 소스)
다른 분야에서의 유사 접근:
- 출처, 분야
- 현재 프로젝트와의 연결고리

### 4. Output

- `REFERENCES.md`에 새 항목을 추가한다
- 기존 내용은 절대 삭제하지 않는다
- 중복 항목이 있으면 추가하지 않고 알려준다
- 각 항목에 추가 날짜를 기록한다

### 5. Post-generation Guide

```
N개의 레퍼런스를 REFERENCES.md에 추가했습니다.

다음 단계:
- /digest 로 특정 논문이나 문서를 심층 요약할 수 있습니다
- /cite 로 학술 인용 형식으로 변환할 수 있습니다
```

## Core Principles

1. **누적적** — 기존 REFERENCES.md 내용을 보존하고 새 항목만 추가한다.
2. **세 축 균형** — 작품, 기술, 영감 소스를 균형 있게 수집한다.
3. **실용적** — 각 레퍼런스에 "이 프로젝트에 어떻게 쓸 수 있는가"를 포함한다.
4. **언어를 따른다** — 사용자의 언어로 요약을 작성한다.
