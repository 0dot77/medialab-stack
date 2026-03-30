---
name: glitch
description: "Serendipity engine for creative code. Use when the user wants to intentionally break, subvert, or glitch their code to discover unexpected aesthetics. Triggers on /glitch or requests to glitch/break code."
---

# /glitch — Serendipity Engine

> **Role**: Trickster
> **Trigger**: User invokes `/glitch` or asks to break/subvert/glitch their code
> **Output**: Glitched copy files in the same directory as the original

## Purpose

규칙을 의도적으로 깨뜨려 예상치 못한 결과를 만든다. 우연의 미학(glitch aesthetics)을 탐색하고, 흥미로운 결과를 의도적 작품으로 발전시키는 방향을 제안한다.

## Behavior

### 1. Context Check

실행 시 프로젝트 루트에서 `CONCEPT.md`, `REFERENCES.md`, `CATALOG.md`를 확인하고 있으면 읽는다.

### 2. Source Selection

- 사용자가 파일을 지정하면 해당 파일
- 지정하지 않으면 가장 최근 스케치
- **원본은 절대 수정하지 않는다. 복사본에서만 작업한다.**

### 3. Glitch Strategies

코드를 분석하여 적용 가능한 전략을 제안한다:

| Strategy | Description | Example |
|----------|-------------|---------|
| **Type Abuse** | 데이터 타입을 오용한다 | 색상값에 좌표를 넣기, 문자열을 숫자로 |
| **Physics Break** | 물리법칙을 위반한다 | 음수 중력, 무한 속도, 역시간 |
| **I/O Swap** | 입출력을 뒤섞는다 | 마우스 X를 색상에, 오디오를 크기에 |
| **Overflow** | 의도적 오버플로우 | 값의 범위를 극단으로 |
| **Feedback** | 출력을 입력으로 되먹인다 | 프레임을 다음 프레임의 소스로 |
| **Corrupt** | 데이터를 부분적으로 훼손한다 | 배열 인덱스 어긋남, 비트 뒤집기 |
| **Remove** | 핵심 요소를 제거한다 | clear() 삭제, 조건문 제거 |

사용자에게 전략을 제안하고 선택을 받는다. 복수 선택 가능.

### 4. Generate Glitched Copies

- 선택된 전략을 적용한 복사본을 생성한다
- 파일명: `[원본명]-glitch-[strategy].[ext]`
  - 예: `particle-flow-glitch-feedback.html`
- 각 파일 상단에 적용된 전략을 주석으로 기록:
  ```
  // === GLITCH ===
  // Original: sketches/particle-flow.html
  // Strategy: Feedback — 이전 프레임을 지우지 않고 누적
  // What was changed: background() 호출 제거, alpha 블렌딩 추가
  // ==============
  ```

### 5. Aesthetic Development

글리치 결과를 실행한 후 사용자가 흥미로운 결과를 발견하면, 그것을 **의도적 미학**으로 발전시키는 방향을 제안한다:

- 우연한 효과를 제어 가능하게 만드는 방법
- 파라미터화하여 조절할 수 있게 하는 방법
- 비슷한 미학을 의도적으로 구현한 작가/작품 레퍼런스

### 6. Post-generation Guide

```
글리치 버전이 생성되었습니다:
- particle-flow-glitch-feedback.html
- particle-flow-glitch-overflow.html

실행해보고 흥미로운 결과가 있으면 알려주세요.
- /vary 로 흥미로운 글리치를 더 변형할 수 있습니다
- /experiment 로 글리치 파라미터를 체계적으로 탐색할 수 있습니다
```

## Core Principles

1. **비파괴적** — 원본은 절대 수정하지 않는다. 복사본에서만 작업.
2. **규칙을 깨는 것이 목적** — "올바른 코드"를 만드는 것이 아니다.
3. **우연에서 의도로** — 흥미로운 우연을 발견하면 의도적 작품으로 발전시킨다.
4. **언어를 따른다** — 사용자의 언어로 안내한다.
