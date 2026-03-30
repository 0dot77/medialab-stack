# medialab-stack

미디어아트 창작 · 연구 · 교육을 위한 Claude Code 스킬팩

> gstack이 "Think → Plan → Build → Review → Test → Ship"이라면,
> medialab-stack은 **"Imagine → Sketch → Explore → Refine → Document → Teach"**이다.

## 이것은 무엇인가

medialab-stack은 미디어아트 개발자, 리서처, 교육자를 위한 [Claude Code](https://claude.com/claude-code) 스킬 모음이다. [gstack](https://github.com/garrytan/gstack)의 SKILL.md 기반 구조를 차용하되, 스타트업 소프트웨어 개발이 아닌 **미디어아트 창작-연구-교육 워크플로우**에 맞게 완전히 새로 설계했다.

## gstack과의 차이

| gstack | medialab-stack |
|--------|---------------|
| 소프트웨어 제품 개발 | 미디어아트 창작·연구·교육 |
| 기능 요구사항 중심 | 예술적 의도 중심 |
| 코드 품질·테스트 | 실험 가능성·미학적 탐색 |
| Ship it | Show it |

## Quick Start

```bash
# 1. 설치
git clone https://github.com/your-username/medialab-stack.git
cd medialab-stack
./setup

# 2. 새 프로젝트에서 사용
cd your-media-art-project
/imagine          # 컨셉 발상 → CONCEPT.md 생성
/sketch           # 즉시 프로토타이핑
/vary             # 변형 탐색
/workshop         # 워크숍 자료 생성
```

## 스킬 목록

### 🎨 창작 (Create)

| 명령어 | 역할 | 설명 |
|--------|------|------|
| `/imagine` | 큐레이터 + 드라마투르그 | 예술적 의도를 파고들어 CONCEPT.md 생성 |
| `/sketch` | 크리에이티브 코더 | 최소 동작 코드를 빠르게 생성 |
| `/vary` | 디자인 탐험가 | 기존 스케치에서 N개의 변형 생성 |
| `/experiment` | 연구원 | 파라미터 공간 탐색과 체계적 실험 |
| `/glitch` | 트릭스터 | 규칙을 깨뜨려 우연의 미학 발견 |

### 🔬 연구 (Research)

| 명령어 | 역할 | 설명 |
|--------|------|------|
| `/survey` | 리서치 어시스턴트 | 선행 작품·기술·영감 소스 수집 |
| `/digest` | 리서치 어시스턴트 | 논문/기술 문서를 미디어아트 관점으로 요약 |
| `/cite` | 서지 관리자 | REFERENCES.md를 학술 인용 형식으로 변환 |
| `/critique` | 미술 비평가 패널 | 형식·개념·관객 경험 관점의 미학적 리뷰 |

### 🛠 완성 (Production)

| 명령어 | 역할 | 설명 |
|--------|------|------|
| `/optimize` | 테크니컬 아티스트 | 퍼포먼스 최적화 (미학적 영향 포함) |
| `/install` | 전시 기술 감독 | 전시 배포 체크리스트와 자동시작 스크립트 |

### 📦 아카이브 (Archive)

| 명령어 | 역할 | 설명 |
|--------|------|------|
| `/document` | 아카이비스트 + 큐레이터 | 아티스트 스테이트먼트, 기술 문서, 전시 캡션 |
| `/archive` | 디지털 아카이비스트 | 프로젝트 정리와 카탈로그 생성 |

### 📚 교육 (Teach)

| 명령어 | 역할 | 설명 |
|--------|------|------|
| `/explain` | 교수 조교 | 코드에 교육적 주석을 달아 해설 버전 생성 |
| `/workshop` | 교육 설계자 | 완전한 워크숍 자료 세트 생성 |
| `/exercise` | 교육과정 설계자 | 3단계 과제 생성 (기초/응용/창작) |
| `/syllabus` | 커리큘럼 아키텍트 | 주차별 커리큘럼 설계 |

## Creative Sprint 사이클

```
  Imagine ──→ Sketch ──→ Vary
     ↑                    │
     │                    ↓
   Survey    Critique ←── Experiment
     │          │
     ↓          ↓
   Digest    Optimize ──→ Install
                            │
                            ↓
              Document ──→ Archive
                            │
                            ↓
              Workshop ──→ Exercise ──→ Syllabus
```

## 예시 시나리오

### 전시 준비 4주

1. **1주차**: `/imagine`로 컨셉 정립 → `/survey`로 레퍼런스 수집 → `/sketch`로 첫 프로토타입
2. **2주차**: `/vary`로 변형 탐색 → `/experiment`로 파라미터 실험 → `/critique`로 중간 리뷰
3. **3주차**: `/optimize`로 퍼포먼스 튜닝 → `/install`로 전시 환경 준비
4. **4주차**: `/document`로 문서화 → `/archive`로 아카이빙

### 워크숍 준비 1주

1. `/imagine`로 워크숍 주제 정립
2. `/sketch`로 데모 코드 작성
3. `/explain`으로 해설 버전 생성
4. `/workshop`으로 자료 세트 생성
5. `/exercise`로 과제 생성

### 학기 수업

1. `/syllabus`로 16주 커리큘럼 설계
2. 매주 `/sketch` + `/explain`으로 예제 코드 생성
3. `/exercise`로 과제 생성
4. `/workshop`으로 실습 자료 준비

## 메타 문서

medialab-stack은 프로젝트 루트에 다음 문서들을 생성하고 관리한다:

- **CONCEPT.md** — 작품의 예술적 의도, 컨셉, 기술 스택 (`/imagine`이 생성)
- **REFERENCES.md** — 레퍼런스 누적 (`/survey`, `/digest`가 추가)
- **CATALOG.md** — 프로젝트 카탈로그 (`/archive`가 생성)
- **TECHNICAL-RIDER.md** — 전시 기술 사양서 (`/install`이 생성)
- **EXPERIMENT-LOG.md** — 실험 기록 (`/experiment`가 생성)

## 라이선스

MIT
