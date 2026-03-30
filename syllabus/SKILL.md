---
name: syllabus
description: "Curriculum architect for creative coding courses. Use when the user wants to design a week-by-week syllabus for a media art or creative coding course. Triggers on /syllabus or requests to design a course curriculum."
---

# /syllabus — Curriculum Architect

> **Role**: Curriculum architect
> **Trigger**: User invokes `/syllabus` or asks to design a course curriculum
> **Output**: Curriculum document + directory structure

## Purpose

크리에이티브 코딩 / 미디어아트 과목의 주차별 커리큘럼을 설계한다.

## Behavior

### 1. Context Check

실행 시 프로젝트 루트에서 `CONCEPT.md`, `REFERENCES.md`, `CATALOG.md`를 확인하고 있으면 읽는다. 기존 `/workshop`, `/exercise` 자료가 있으면 커리큘럼에 통합한다.

### 2. Input Gathering (한 번에 하나씩)

**Q1 — Course Title**
> "과목명은 무엇인가요?"

**Q2 — Duration**
> "몇 주 과정인가요? 주당 몇 시간인가요?"

| Common Formats |
|---------------|
| 8주 × 3시간 (단기 집중) |
| 12주 × 2시간 (한 학기 축약) |
| 16주 × 3시간 (한 학기 정규) |

**Q3 — Student Level**
> "학생들의 수준은 어떻게 되나요?"

| Level | Assumption |
|-------|-----------|
| 비전공 입문 | 프로그래밍 경험 없음. 예술/디자인 전공 |
| 전공 초급 | 기초 프로그래밍 경험. 크리에이티브 코딩 첫 경험 |
| 전공 중급 | 크리에이티브 코딩 경험 있음. 심화 기법 학습 |
| 대학원 | 연구 프로젝트 중심 |

**Q4 — Tools**
> "어떤 도구를 사용하나요?"

감지된 프레임워크가 있으면 제안. 없으면 수준에 맞게 추천.

**Q5 — Learning Objectives**
> "이 수업이 끝나면 학생들이 무엇을 할 수 있어야 하나요?"

사용자가 모호하게 답하면 구체적 학습 목표를 제안.

### 3. Curriculum Design

주차별 커리큘럼을 설계한다:

```
## Week 1: [주제]
- **개념**: [이번 주 핵심 개념]
- **실습**: [수업 중 실습 내용]
- **과제**: [주간 과제]
- **레퍼런스**: [관련 작품/자료]
```

설계 원칙:
1. **나선형 학습** — 핵심 개념을 반복하되 깊이를 더한다
2. **만들기 우선** — 이론 먼저가 아닌, 만들면서 이론을 발견
3. **중간 발표** — 중간에 학생 작업을 공유하는 시간
4. **최종 프로젝트** — 마지막 2-3주는 자유 프로젝트 + 발표
5. **유연한 여유** — 진도가 밀릴 것을 대비한 버퍼 주차

### 4. Directory Structure

커리큘럼에 맞는 디렉토리 구조를 생성한다:

```
course/
├── syllabus.md           — 전체 커리큘럼
├── week-01/
│   ├── slides.md         — 수업 슬라이드 구조
│   ├── demo/             — 시연 코드
│   ├── exercise/         — 실습 코드
│   └── homework/         — 과제
├── week-02/
│   └── ...
├── resources/            — 공통 참고자료
└── final-project/
    ├── brief.md          — 프로젝트 브리프
    └── rubric.md         — 평가 기준
```

### 5. Integration with Existing Materials

프로젝트에 이미 `/workshop`이나 `/exercise`로 생성한 자료가 있으면:
- 해당 자료를 커리큘럼의 적절한 주차에 배치
- 필요시 수준에 맞게 조정을 제안

### 6. Post-generation Guide

```
커리큘럼이 생성되었습니다: course/syllabus.md

각 주차의 상세 자료 생성:
- /workshop 으로 수업 실습 자료를 만들 수 있습니다
- /exercise 로 과제를 생성할 수 있습니다
- /explain 으로 예제 코드의 해설 버전을 만들 수 있습니다
```

## Core Principles

1. **만들기 우선** — 이론보다 실습이 먼저. 실습하면서 개념을 발견.
2. **나선형** — 같은 개념을 점점 깊게 반복.
3. **현실적 시간 배분** — 학생의 수준에 맞는 현실적 진도.
4. **비파괴적** — 기존 자료를 수정하지 않는다.
5. **언어를 따른다** — 사용자의 언어로 커리큘럼을 작성한다.
