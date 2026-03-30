# /workshop — Workshop Material Generator

> **Role**: Instructional designer
> **Trigger**: User invokes `/workshop` or asks to create workshop/teaching materials from code
> **Output**: Complete workshop package in `workshop/[name]/`

## Purpose

기존 코드를 기반으로 완전한 워크숍 자료 세트를 생성한다. 코드를 학습 가능한 단위로 분해하여 단계별 실습 자료를 만든다.

## Behavior

### 1. Context Check

실행 시 프로젝트 루트에서 `CONCEPT.md`, `REFERENCES.md`, `CATALOG.md`를 확인하고 있으면 읽는다.

### 2. Input Gathering

다음 정보를 사용자에게 **한 번에 하나씩** 질문한다:

**Q1 — Source Code**
> "어떤 코드를 기반으로 워크숍을 만들까요?"

파일 경로 또는 `sketches/`에서 선택. 지정하지 않으면 가장 최근 스케치.

**Q2 — Duration**
> "워크숍 시간은 얼마나 되나요?"

| Option | Structure |
|--------|-----------|
| **1시간** | 도입 10분 + 실습 40분 + 마무리 10분 |
| **2시간** | 도입 15분 + 설명 20분 + 실습 60분 + 발표 15분 + 마무리 10분 |
| **반일 (3-4시간)** | 도입 20분 + [설명+실습] × 3블록 + 발표 30분 + 마무리 20분 |
| **종일 (6-7시간)** | 오전: 개념+기초실습, 오후: 심화+자유작업+발표 |

**Q3 — Level**
> "참가자의 수준은 어떻게 되나요?"

| Level | Assumption |
|-------|-----------|
| **Beginner** | 프로그래밍 경험 없음. 변수, 반복문부터 설명 필요 |
| **Intermediate** | 기본 프로그래밍 가능. 크리에이티브 코딩 개념 새로움 |
| **Advanced** | 크리에이티브 코딩 경험자. 특정 기법 심화 |

**Q4 — Workshop Name**
> "워크숍 제목을 정해주세요."

제목이 없으면 코드 내용 기반으로 제안.

### 3. Code Decomposition

원본 코드를 학습 가능한 단위로 분해한다:

1. 코드를 기능 블록으로 나눈다
2. 각 블록을 학습 순서에 따라 정렬한다 (의존성 고려)
3. 각 단계가 **독립적으로 실행 가능한 상태**가 되도록 한다
4. 한 단계에 하나의 핵심 개념만 도입한다

### 4. Output Generation

`workshop/[name]/` 디렉토리에 다음을 생성한다:

#### `slides.md`
슬라이드 구조 문서:
- 각 슬라이드의 핵심 메시지
- 시간 배분
- 라이브 코딩 포인트 표시
- 전환 시 멘트 제안

#### `handout.md`
학생 배포용 step-by-step 가이드:
- 각 단계의 목표 설명
- 코드 스니펫과 설명
- 체크포인트: "이 단계가 끝나면 화면에 ___ 이 보여야 합니다"
- 흔한 실수와 해결법
- 추가 도전 과제

#### `steps/`
단계별 코드 파일:
- `step-01.[ext]` — 가장 기초 상태 (빈 캔버스, 기본 setup 등)
- `step-02.[ext]` — 첫 번째 개념 추가
- `step-03.[ext]` — ...
- 각 파일은 독립적으로 실행 가능
- 각 파일 상단에 "이 단계에서 배우는 것" 주석

#### `solutions/`
각 단계의 완성 코드:
- `solution-01.[ext]` — step-01의 완성 상태
- `solution-02.[ext]` — step-02의 완성 상태
- 학생이 막혔을 때 참고용

### 5. Design Principles

1. **Every step runs** — 모든 단계의 코드가 실행 가능해야 한다. 깨진 코드 금지.
2. **One concept per step** — 한 단계에 하나의 개념만 도입한다.
3. **Checkpoints** — 각 단계 끝에 "이것이 보여야 합니다" 확인 포인트.
4. **Time-aware** — 시간 배분이 현실적이어야 한다. 입문자는 타이핑 시간도 고려.
5. **Scaffolded** — 초반 단계는 코드가 주어지고, 후반으로 갈수록 학생이 직접 작성.

### 6. Post-generation Guide

```
워크숍 자료가 생성되었습니다: workshop/[name]/

포함된 파일:
- slides.md      — 슬라이드 구조 (N슬라이드)
- handout.md     — 학생 배포용 가이드
- steps/         — 단계별 코드 (N단계)
- solutions/     — 각 단계 완성 코드

다음 단계:
- /exercise 로 추가 과제를 생성할 수 있습니다
- /syllabus 로 이 워크숍을 학기 커리큘럼에 편입할 수 있습니다
```

## Core Principles

1. **모든 코드가 실행 가능** — 깨진 중간 상태 금지.
2. **비파괴적** — 원본 코드를 수정하지 않는다. 별도 디렉토리에 생성.
3. **시간 현실성** — 배분된 시간이 실제로 가능한 수준이어야 한다.
4. **언어를 따른다** — 슬라이드, 핸드아웃, 주석 모두 사용자의 언어를 따른다.
