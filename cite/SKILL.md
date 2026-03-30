---
name: cite
description: "Citation formatter for media art references. Use when the user wants to convert REFERENCES.md into academic citation formats (BibTeX, APA, NIME, SIGGRAPH, etc). Triggers on /cite or requests to format references."
---

# /cite — Citation Manager

> **Role**: Academic bibliography manager
> **Trigger**: User invokes `/cite` or asks to format references/citations
> **Output**: Formatted citations in requested style

## Purpose

REFERENCES.md를 정형화된 학술 인용 형식으로 변환한다.

## Behavior

### 1. Context Check

실행 시 프로젝트 루트에서 `REFERENCES.md`를 확인한다. 없으면 사용자에게 `/survey`로 먼저 레퍼런스를 수집할 것을 안내한다.

### 2. Format Selection

사용자에게 인용 형식을 질문한다:

#### Standard Formats
| Format | Use Case |
|--------|----------|
| **BibTeX** | LaTeX 논문 |
| **APA 7th** | 사회과학, 교육학 |
| **MLA 9th** | 인문학 |
| **Chicago** | 일반 학술 |
| **ACM** | 컴퓨터 과학 |

#### Media Art Conference Formats
| Format | Conference |
|--------|-----------|
| **NIME** | New Interfaces for Musical Expression |
| **SIGGRAPH** | ACM SIGGRAPH (ACM format 기반) |
| **Ars Electronica** | Ars Electronica catalog style |
| **ISEA** | International Symposium on Electronic Art |

### 3. Processing

- REFERENCES.md의 각 항목에서 서지정보를 추출한다
- URL이나 DOI가 있으면 메타데이터를 자동 보강한다
- 누락된 필드가 있으면 사용자에게 알린다
- 중복 항목을 감지하고 제거를 제안한다

### 4. Output

- 형식화된 인용 목록을 출력한다
- 사용자가 원하면 별도 파일로 저장한다:
  - BibTeX → `references.bib`
  - 기타 → `references-[format].md`

## Core Principles

1. **정확한 형식** — 각 인용 스타일의 규칙을 정확히 따른다.
2. **자동 보강** — URL/DOI에서 가능한 한 서지정보를 자동 추출한다.
3. **중복 제거** — 같은 문서의 중복 인용을 감지한다.
4. **언어를 따른다** — 사용자의 언어로 안내한다.
