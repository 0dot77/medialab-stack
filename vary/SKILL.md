---
name: vary
description: "Variation generator for creative code. Use when the user wants to create multiple variations of an existing sketch by changing color, motion, scale, algorithm, or other axes. Triggers on /vary or requests to explore variations."
---

# /vary — Variation Generator

> **Role**: Design explorer
> **Trigger**: User invokes `/vary` or asks to create variations of a sketch
> **Output**: N variation files alongside the original

## Purpose

기존 스케치에서 N개의 변형을 빠르게 생성하여 디자인 공간을 탐색한다. 원본은 절대 수정하지 않는다.

## Behavior

### 1. Context Check

실행 시 프로젝트 루트에서 `CONCEPT.md`, `REFERENCES.md`, `CATALOG.md`를 확인하고 있으면 읽는다.

### 2. Source Selection

입력 스케치를 결정한다:
- 사용자가 경로를 지정한 경우 → 해당 파일
- 지정하지 않은 경우 → `sketches/` 디렉토리에서 가장 최근 수정된 파일
- `sketches/`가 없거나 비어있으면 → 사용자에게 파일 경로를 질문

원본 파일을 읽고 내용을 파악한다.

### 3. Variation Axis

사용자가 변형 축을 지정하지 않은 경우, 코드를 분석하여 적합한 변형 축을 제안한다:

| Axis | Description | Example |
|------|-------------|---------|
| **Color/Palette** | 색상 체계 변형 | 모노크롬, 보색, 자연색, 네온 |
| **Motion/Physics** | 움직임·물리 법칙 변형 | 중력, 반발, 유체, 진자 |
| **Scale/Density** | 스케일·밀도 변형 | 파티클 수, 크기, 간격 |
| **Algorithm** | 알고리즘 변형 | Perlin → Simplex, sin → triangle wave |
| **Time/Speed** | 시간·속도 변형 | 슬로모션, 가속, 역재생, 펄스 |
| **Geometry** | 형태 변형 | 원→사각, 2D→3D, 곡선→직선 |
| **Interaction** | 인터랙션 변형 | 마우스→키보드, 클릭→드래그 |

사용자에게 축을 제안하고 선택을 받는다. 복수 축 선택 가능.

### 4. Generate Variations

- 기본 3개 변형 생성. 사용자가 수를 지정하면 그에 따름.
- 각 변형 파일의 코드 상단에 주석으로 원본 대비 변경사항을 명시:
  ```
  // === VARIATION ===
  // Original: sketches/2026-03-30-particle-flow.html
  // Axis: Color/Palette
  // Changes: Replaced warm palette with cold monochrome blue gradient
  // ==================
  ```
- 파라미터 섹션의 값만 바꾸는 단순 변형이 아닌, 미학적으로 의미 있는 차이를 만든다.

### 5. File Output

- 원본과 같은 디렉토리에 저장
- 파일명: `[원본명]-v1.[ext]`, `[원본명]-v2.[ext]`, ...
  - 예: `sketches/2026-03-30-particle-flow-v1.html`
- **원본 파일은 절대 수정하지 않는다**

### 6. Summary

생성 완료 후 각 변형의 한 줄 요약 테이블을 출력:

```
| File | Axis | What Changed |
|------|------|-------------|
| -v1  | Color | Cold monochrome blue gradient |
| -v2  | Motion | Fluid simulation with viscosity |
| -v3  | Scale | 10x particle count, micro-scale |
```

## Core Principles

1. **비파괴적** — 원본 코드는 절대 수정하지 않는다. 모든 변형은 새 파일이다.
2. **의미 있는 차이** — 파라미터 하나 바꾸는 수준이 아닌, 미학적으로 다른 결과를 만든다.
3. **추적 가능** — 각 변형이 원본에서 무엇을 바꿨는지 주석으로 명확히 기록한다.
4. **언어를 따른다** — 주석과 안내는 사용자의 언어를 따른다.
