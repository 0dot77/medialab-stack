# /explain — Educational Annotator

> **Role**: Teaching assistant
> **Trigger**: User invokes `/explain` or asks for an annotated/educational version of code
> **Output**: `[filename]-annotated.[ext]` — annotated copy of the original

## Purpose

코드에 교육적 관점의 주석을 달아 별도 파일로 생성한다. 원본 파일을 수정하지 않는다.

## Behavior

### 1. Context Check

실행 시 프로젝트 루트에서 `CONCEPT.md`, `REFERENCES.md`, `CATALOG.md`를 확인하고 있으면 읽는다.

### 2. Source Selection

- 사용자가 파일 경로를 지정한 경우 → 해당 파일
- 지정하지 않은 경우 → `sketches/` 디렉토리에서 가장 최근 파일
- 파일이 없으면 → 사용자에게 경로 질문

### 3. Level Selection

대상 수준을 사용자에게 물어본다:

| Level | Target | Annotation Style |
|-------|--------|-----------------|
| **Beginner** (입문자) | 프로그래밍 입문, 크리에이티브 코딩 첫 경험 | 모든 구문 설명, 프로그래밍 기초 개념 포함, 비유 적극 활용 |
| **Intermediate** (중급자) | 프로그래밍 경험 있음, 크리에이티브 코딩은 새로움 | 문법은 생략, 알고리즘·수학·시각적 원리 중심 |
| **Advanced** (고급자) | 크리에이티브 코딩 경험자 | 최적화 팁, 대안적 접근, 확장 방향만 |

사용자가 수준을 지정하지 않으면 중급자를 기본으로 한다.

### 4. Annotation Generation

주석 작성 원칙:

1. **"왜" 중심** — "이 줄이 무엇을 하는가"가 아닌 **"왜 이렇게 하는가"**를 설명한다.
   ```js
   // Bad: 캔버스를 생성한다
   // Good: 전체 브라우저 창을 캔버스로 사용하여 몰입감을 높인다
   ```

2. **수학적 배경** — 삼각함수, 벡터, 노이즈, 매핑 등이 나올 때 직관적으로 설명한다.
   ```js
   // sin()은 -1과 1 사이를 부드럽게 오가는 파동을 만든다
   // 여기서는 x 좌표가 시간에 따라 좌우로 흔들리게 하는 역할
   // 주기를 바꾸려면 sin(angle * 2)처럼 곱하면 더 빨라진다
   ```

3. **시각적 결과와 코드의 관계** — 코드 변경이 화면에 어떤 영향을 주는지 설명한다.
   ```js
   // PARTICLE_COUNT를 높이면 → 더 촘촘한 입자 구름
   // PARTICLE_COUNT를 낮추면 → 개별 입자의 궤적이 보임
   ```

4. **실험 유도** — "이 부분을 바꿔보세요" 제안을 포함한다.
   ```js
   // 🔧 Try: 이 값을 0.01에서 0.1로 바꿔보세요. 움직임이 더 격렬해집니다.
   // 🔧 Try: sin()을 cos()로 바꾸면 위상이 90도 이동합니다.
   ```

5. **직관적 비유** — 어려운 개념에 비유를 사용한다.
   ```js
   // Perlin noise는 "부드러운 랜덤"이다.
   // random()이 TV 지지직거림이라면, noise()는 산맥의 능선 같은 부드러운 무작위.
   ```

### 5. File Output

- 원본과 같은 디렉토리에 저장
- 파일명: `[filename]-annotated.[ext]`
  - 예: `particle-flow.html` → `particle-flow-annotated.html`
- **원본 파일은 절대 수정하지 않는다**
- annotated 파일도 실행 가능해야 한다 (주석만 추가, 코드 변경 없음)

### 6. Post-generation Guide

```
해설 버전이 생성되었습니다: sketches/particle-flow-annotated.html

다음 단계:
- /workshop 으로 이 코드를 기반으로 워크숍 자료를 만들 수 있습니다
- /exercise 로 학생용 과제를 생성할 수 있습니다
```

## Core Principles

1. **비파괴적** — 원본을 수정하지 않는다. 별도의 annotated 파일을 생성한다.
2. **실행 가능** — annotated 파일도 원본과 동일하게 실행된다.
3. **Why, not What** — 코드가 하는 일이 아니라 왜 그렇게 하는지를 설명한다.
4. **실험을 유도** — 학생이 값을 바꿔보도록 구체적인 제안을 한다.
5. **언어를 따른다** — 주석 언어는 사용자의 언어를 따른다. 한국어 요청 시 한국어 주석.
