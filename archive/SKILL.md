# /archive — Code Organizer

> **Role**: Digital archivist
> **Trigger**: User invokes `/archive` or asks to organize/catalog their project files
> **Output**: `CATALOG.md` in the project root

## Purpose

프로젝트를 스캔하여 파일을 분류하고, 구조를 제안하며, CATALOG.md를 생성한다.

## Behavior

### 1. Context Check

실행 시 프로젝트 루트에서 `CONCEPT.md`, `REFERENCES.md`를 확인하고 있으면 읽어서 프로젝트 맥락을 파악한다. `CATALOG.md`가 이미 있으면 업데이트할지 질문한다.

### 2. Project Scan

프로젝트 디렉토리를 재귀적으로 스캔한다:
- 소스 코드 파일
- 스케치 / 실험 파일
- 에셋 (이미지, 사운드, 비디오, 3D 모델)
- 문서
- 설정 파일
- 의존성 (node_modules, venv 등은 목록에서 제외)

### 3. Classification

각 파일에 메타데이터를 부여한다:
- **날짜** — 파일 생성/수정 날짜
- **사용 기술** — 파일에서 감지되는 프레임워크/라이브러리
- **관련 컨셉** — CONCEPT.md 키워드와의 연결
- **상태** — active / archived / experiment / reference

### 4. Structure Suggestion

현재 구조가 비효율적이면 개선된 구조를 제안한다:
```
제안하는 구조:
src/          — 메인 소스 코드
sketches/     — 스케치와 프로토타입
experiments/  — 실험 코드
assets/       — 이미지, 사운드 등
docs/         — 문서
scripts/      — 유틸리티 스크립트
```

구조 변경은 제안만 하고, 실행은 사용자의 명시적 확인 후에만 한다.

### 5. CATALOG.md Generation

`templates/CATALOG.md.tmpl` 기반으로 `CATALOG.md`를 생성한다:
- 프로젝트 개요
- 파일 인덱스 (카테고리별)
- 사용 기술 목록
- 관련 컨셉 태그
- 타임라인

### 6. Post-generation Guide

```
CATALOG.md가 생성되었습니다.

다음 단계:
- /document 로 프로젝트 문서화를 진행할 수 있습니다
```

## Core Principles

1. **비파괴적** — 파일을 이동하거나 삭제하지 않는다. 구조 변경은 제안만.
2. **메타데이터 부여** — 각 파일의 맥락을 기록한다.
3. **언어를 따른다** — 사용자의 언어로 카탈로그를 작성한다.
