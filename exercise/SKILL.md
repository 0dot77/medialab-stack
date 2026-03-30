# /exercise — Assignment Generator

> **Role**: Curriculum designer
> **Trigger**: User invokes `/exercise` or asks to create assignments/homework from code
> **Output**: Exercise package in `exercises/[name]/`

## Purpose

기존 코드를 기반으로 3단계 과제를 생성한다: 기초(파라미터 수정) → 응용(기능 추가) → 창작(새 작품).

## Behavior

### 1. Context Check

실행 시 프로젝트 루트에서 `CONCEPT.md`, `REFERENCES.md`, `CATALOG.md`를 확인하고 있으면 읽는다.

### 2. Input

- 사용자가 코드 파일을 지정하면 해당 파일
- 지정하지 않으면 가장 최근 스케치 또는 워크숍 코드
- 대상 수준을 질문: 입문 / 중급 / 고급

### 3. Three-Tier Exercises

#### Tier 1 — Foundation (기초: 파라미터 수정)
- 기존 코드의 파라미터를 변경하여 결과를 관찰하는 과제
- 명확한 지시: "SPEED 값을 0.5, 2.0, 10.0으로 바꿔보고 차이를 설명하세요"
- 정답이 있는 것이 아닌, 관찰과 설명이 평가 대상
- 시작 코드: 원본 그대로 제공

#### Tier 2 — Application (응용: 기능 추가)
- 기존 코드에 새 기능을 추가하는 과제
- 구체적 요구사항: "마우스 클릭 시 파티클 색상이 변하도록 수정하세요"
- 힌트를 3단계로 제공 (힌트 1: 방향, 힌트 2: 접근법, 힌트 3: 거의 답)
- 시작 코드: 주석으로 수정 위치를 표시

#### Tier 3 — Creative (창작: 새 작품)
- 배운 기법을 활용한 자유 창작 과제
- 열린 프롬프트: "이 기법을 사용하여 '시간의 흐름'을 표현하는 작품을 만드세요"
- 제약 조건 (기법, 캔버스 크기, 색상 수 등)으로 창의성 유도
- 시작 코드: 최소 보일러플레이트만

### 4. Output Structure

```
exercises/[name]/
├── README.md              — 과제 개요
├── tier-1/
│   ├── prompt.md          — 과제 설명
│   ├── starter.[ext]      — 시작 코드
│   └── example.[ext]      — 예시 결과 (교수자용)
├── tier-2/
│   ├── prompt.md          — 과제 설명
│   ├── starter.[ext]      — 시작 코드
│   ├── hints.md           — 3단계 힌트
│   └── solution.[ext]     — 풀이 (교수자용)
└── tier-3/
    ├── prompt.md          — 과제 설명
    ├── starter.[ext]      — 최소 보일러플레이트
    ├── rubric.md          — 평가 기준
    └── examples.[ext]     — 예시 작품 (교수자용)
```

### 5. Rubric

각 과제에 평가 기준을 포함한다:

| Criterion | Description |
|-----------|-------------|
| **기술적 완성도** | 코드가 실행되는가, 요구사항을 충족하는가 |
| **실험 정신** | 기본 요구를 넘어 탐색을 시도했는가 |
| **미학적 고려** | 시각적/청각적 결과에 의도가 있는가 |
| **문서화** | 자신의 과정과 발견을 설명할 수 있는가 |

Tier 1은 기술적 완성도 중심, Tier 3으로 갈수록 미학적 고려와 실험 정신의 비중이 커진다.

### 6. Post-generation Guide

```
과제가 생성되었습니다: exercises/[name]/

다음 단계:
- /workshop 으로 이 과제를 포함한 워크숍 자료를 만들 수 있습니다
- /syllabus 로 학기 커리큘럼에 배치할 수 있습니다
```

## Core Principles

1. **3단계 scaffolding** — 관찰 → 수정 → 창작의 자연스러운 학습 곡선.
2. **모든 코드가 실행 가능** — 시작 코드도, 풀이도 실행 가능해야 한다.
3. **비파괴적** — 원본 코드를 수정하지 않는다.
4. **언어를 따른다** — 사용자의 언어로 과제를 작성한다.
