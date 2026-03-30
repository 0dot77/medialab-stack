# /experiment — Systematic Experimentation

> **Role**: Researcher
> **Trigger**: User invokes `/experiment` or asks to systematically explore parameter space
> **Output**: `experiments/[date]-[name]/` directory + `EXPERIMENT-LOG.md` update

## Purpose

파라미터 공간을 정의하고, 조합 매트릭스를 생성하며, 실행 스크립트와 실험 로그를 만든다.

## Behavior

### 1. Context Check

실행 시 프로젝트 루트에서 `CONCEPT.md`, `REFERENCES.md`, `CATALOG.md`를 확인하고 있으면 읽는다. `EXPERIMENT-LOG.md`가 있으면 기존 실험 이력을 참조한다.

### 2. Base Sketch Selection

- 사용자가 파일을 지정하면 해당 파일
- 지정하지 않으면 가장 최근 스케치
- 코드를 분석하여 조절 가능한 파라미터를 자동 추출한다

### 3. Parameter Space Definition

코드 상단의 파라미터 섹션을 분석하여 실험 가능한 파라미터를 나열한다:

```
감지된 파라미터:
1. PARTICLE_COUNT — 현재값: 200, 타입: int
2. SPEED — 현재값: 2.0, 타입: float
3. COLOR_PALETTE — 현재값: ['#264653', ...], 타입: array
```

각 파라미터에 대해 사용자에게 실험 범위를 질문한다:
- Range: min, max, step
- 또는 이산적 값 목록

### 4. Combination Matrix

파라미터 조합을 생성한다:
- 전체 조합 (full grid) — 파라미터가 적을 때
- 라틴 하이퍼큐브 샘플링 — 파라미터가 많을 때
- 사용자 지정 조합

총 조합 수를 미리 알려주고 확인을 받는다. 너무 많으면 줄일 것을 제안.

### 5. Generate Experiment Files

`experiments/[YYYY-MM-DD]-[name]/` 디렉토리를 생성한다:
```
experiments/2026-03-30-particle-density/
├── config.json          — 파라미터 매트릭스
├── run-001.[ext]        — 조합 1
├── run-002.[ext]        — 조합 2
├── ...
├── run-all.sh           — 전체 실행 스크립트 (해당되는 경우)
└── log.md               — 실험 로그 (관찰 기록용)
```

각 `run-NNN` 파일:
- 독립 실행 가능
- 상단에 해당 실험의 파라미터 값 주석
- 원본 코드에서 파라미터만 다름

### 6. EXPERIMENT-LOG.md Update

프로젝트 루트의 `EXPERIMENT-LOG.md`에 이 실험 세션을 추가한다. 없으면 `templates/EXPERIMENT-LOG.md.tmpl` 기반으로 생성. 기존 내용은 보존.

### 7. Post-generation Guide

```
실험 세트가 생성되었습니다: experiments/2026-03-30-particle-density/
- N개 조합, N개 파일

각 파일을 실행하고 log.md에 관찰을 기록하세요.
흥미로운 결과를 발견하면 /vary 로 더 탐색할 수 있습니다.
```

## Core Principles

1. **체계적** — 무작위 시행착오가 아닌 구조화된 탐색.
2. **재현 가능** — config.json에 모든 파라미터가 기록된다.
3. **비파괴적** — 원본 스케치를 수정하지 않는다. 별도 디렉토리에 생성.
4. **언어를 따른다** — 사용자의 언어로 로그와 안내를 작성한다.
