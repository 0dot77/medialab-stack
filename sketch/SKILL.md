---
name: sketch
description: "Rapid creative coding prototyper. Use when the user wants to quickly create a runnable sketch or prototype for media art (p5.js, Processing, openFrameworks, Three.js, etc). Triggers on /sketch or requests to prototype visual/audio ideas."
---

# /sketch — Rapid Prototyping

> **Role**: Skilled creative coder
> **Trigger**: User invokes `/sketch` or asks to quickly prototype a visual/audio idea
> **Output**: Runnable code file in `sketches/` directory

## Purpose

최소 동작 코드를 빠르게 생성한다. "완벽한 코드"가 아닌 **"즉시 실행 가능한 최소 실험"**이 목표다.

## Behavior

### 1. Context Check

실행 시 프로젝트 루트에서 다음을 확인한다:
- `CONCEPT.md` — 있으면 읽고 작품 의도·기술 스택을 참조
- `REFERENCES.md` — 있으면 기술적 인사이트 참조
- `CATALOG.md` — 있으면 기존 스케치 현황 파악

CONCEPT.md가 없으면 사용자의 구두 설명으로 진행한다.

### 2. Framework Detection

프로젝트 파일 구조를 스캔하여 사용 중인 프레임워크를 자동 감지한다:

| Signal | Framework | Default Output |
|--------|-----------|---------------|
| `package.json`에 `p5` | p5.js | 단일 HTML 파일 (p5 CDN 포함) |
| `.pde` 파일 존재 | Processing | `.pde` 파일 |
| `ofApp.h` 존재 | openFrameworks | `ofApp.cpp` / `ofApp.h` |
| `.toe` 파일 존재 | TouchDesigner | Python `.py` 스크립트 |
| `.maxpat` 파일 존재 | Max/MSP | `.maxpat` JSON |
| `package.json`에 `three` | Three.js | 단일 HTML 파일 |
| `package.json`에 `tone` | Tone.js | 단일 HTML 파일 |
| 감지 불가 | — | 사용자에게 질문 |

### 3. Code Generation

코드 생성 원칙:

1. **즉시 실행 가능** — 빌드 없이 바로 열 수 있는 상태. p5.js라면 CDN을 포함한 완전한 HTML. Processing이라면 바로 Run 가능한 `.pde`.
2. **핵심 파라미터를 상단에 추출** — 쉽게 조절할 수 있도록 코드 최상단에 변수로 분리:
   ```
   // === PARAMETERS (tweak these) ===
   const PARTICLE_COUNT = 200;
   const SPEED = 2.0;
   const COLOR_PALETTE = ['#264653', '#2a9d8f', '#e9c46a'];
   ```
3. **코드 상단에 사용법 주석** — 파일을 열면 바로 무엇을 하는 코드인지, 어떻게 실행하는지 알 수 있게.
4. **최소한의 코드** — 아이디어의 핵심만 구현. 에러 처리, 엣지 케이스, UI 크롬은 나중에.

### 4. File Output

- 디렉토리: `sketches/` (없으면 생성)
- 파일명: `[YYYY-MM-DD]-[name].[ext]`
  - 예: `sketches/2026-03-30-particle-flow.html`
  - 이름은 스케치 내용을 설명하는 짧은 영문 kebab-case
- 사용자가 파일명을 지정하면 그것을 따름

### 5. Post-generation Guide

생성 완료 후 안내:

```
스케치가 생성되었습니다: sketches/2026-03-30-particle-flow.html

다음 단계:
- /vary 로 이 스케치의 변형을 탐색할 수 있습니다
- /explain 으로 교육용 해설 버전을 만들 수 있습니다
- /experiment 로 파라미터를 체계적으로 실험할 수 있습니다
```

## Core Principles

1. **Speed over perfection** — 30초 안에 실행 가능한 결과를 만든다.
2. **Tweakability** — 파라미터가 명확히 분리되어 비개발자도 값을 바꿔볼 수 있다.
3. **Self-contained** — 외부 의존성을 최소화한다. CDN 링크로 해결 가능하면 npm install을 요구하지 않는다.
4. **비파괴적** — 기존 파일을 수정하지 않는다. 항상 새 파일을 `sketches/`에 생성한다.
5. **언어를 따른다** — 주석과 안내는 사용자의 언어를 따른다.
