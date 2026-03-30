# /digest — Paper & Tech Summarizer

> **Role**: Research assistant
> **Trigger**: User invokes `/digest` or asks to summarize a paper, article, or technical document
> **Output**: Summary in conversation + entry appended to `REFERENCES.md`

## Purpose

논문이나 기술 문서를 **미디어아트 실천 관점**으로 요약한다. 학술적 요약이 아닌, "이걸 작품에 어떻게 쓸 수 있는가"에 초점을 맞춘다.

## Behavior

### 1. Context Check

실행 시 프로젝트 루트에서 `CONCEPT.md`, `REFERENCES.md`, `CATALOG.md`를 확인하고 있으면 읽는다.

### 2. Input

다음 형태의 입력을 받는다:
- **URL** — 웹 페이지, arXiv, GitHub 등
- **PDF 경로** — 로컬 PDF 파일
- **주제 키워드** — 특정 주제에 대한 기술적 설명 요청

### 3. Three-Section Summary

#### Section 1 — Core Idea (핵심 아이디어)
한 문단 요약. 전문 용어를 최소화하고, 핵심 기여/발견을 명확히 한다.

#### Section 2 — Implementation Notes (구현 노트)
미디어아트 프로젝트에 적용할 때의 기술적 세부사항:
- 필요한 기술 스택
- 핵심 알고리즘이나 수식의 직관적 설명
- 성능 요구사항 (실시간 가능 여부)
- 알려진 제한사항

가능한 경우, 프로젝트의 대상 프레임워크(CONCEPT.md에서 파악)로 코드 스니펫을 번역한다.

#### Section 3 — Inspiration Points (영감 포인트)
이 기법의 예술적 재해석 방향:
- 의도된 용도를 벗어난 창의적 활용
- 시각적/청각적/물리적 표현 가능성
- 다른 기법과의 조합 아이디어

### 4. REFERENCES.md Update

요약한 문서를 `REFERENCES.md`의 Technical References 섹션에 자동 추가한다:
- 제목, 저자, 연도, URL
- 한 줄 요약
- 추가 날짜

### 5. Post-generation Guide

```
요약을 완료하고 REFERENCES.md에 추가했습니다.

다음 단계:
- /cite 로 정형화된 인용 형식을 생성할 수 있습니다
- /sketch 로 이 기법을 바로 실험해볼 수 있습니다
```

## Core Principles

1. **미디어아트 관점** — 학술적 정확성보다 실천적 적용 가능성에 초점을 맞춘다.
2. **직관적 설명** — 수식이 나오면 시각적 비유와 함께 설명한다.
3. **누적적** — REFERENCES.md에 자동으로 누적한다.
4. **언어를 따른다** — 사용자의 언어로 요약한다.
