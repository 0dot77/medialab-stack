# medialab-stack

미디어아트 창작 · 연구 · 교육을 위한 [Claude Code](https://claude.com/claude-code) 스킬팩.

**Imagine → Sketch → Explore → Refine → Document → Teach**

## 설치

```bash
git clone https://github.com/0dot77/medialab-stack.git
cd medialab-stack
./setup
```

설치 후, 미디어아트 프로젝트 디렉토리에서 슬래시 명령어로 사용한다:

```
/imagine    →  컨셉 발상, CONCEPT.md 생성
/sketch     →  즉시 실행 가능한 프로토타입 코드 생성
/vary       →  기존 스케치에서 N개 변형 탐색
/workshop   →  코드 기반 워크숍 자료 세트 생성
```

## 스킬 목록

### 창작

| 명령어 | 설명 |
|--------|------|
| `/imagine` | 예술적 의도를 파고들어 CONCEPT.md 생성 |
| `/sketch` | 최소 동작 코드를 빠르게 프로토타이핑 |
| `/vary` | 기존 스케치에서 N개 변형 생성 |
| `/experiment` | 파라미터 공간을 체계적으로 탐색 |
| `/glitch` | 규칙을 깨뜨려 우연의 미학 발견 |

### 연구

| 명령어 | 설명 |
|--------|------|
| `/survey` | 선행 작품 · 기술 · 영감 소스 수집 |
| `/digest` | 논문/기술 문서를 미디어아트 관점으로 요약 |
| `/cite` | REFERENCES.md를 학술 인용 형식으로 변환 |
| `/critique` | 형식 · 개념 · 관객 경험 관점의 미학적 리뷰 |

### 프로덕션

| 명령어 | 설명 |
|--------|------|
| `/optimize` | 퍼포먼스 최적화 (미학적 영향 설명 포함) |
| `/install` | 전시 배포 체크리스트 + 자동시작 스크립트 |

### 아카이브

| 명령어 | 설명 |
|--------|------|
| `/document` | 아티스트 스테이트먼트, 기술 문서, 전시 캡션 (국문/영문) |
| `/archive` | 프로젝트 정리와 카탈로그 생성 |

### 교육

| 명령어 | 설명 |
|--------|------|
| `/explain` | 코드에 교육적 주석을 달아 해설 버전 생성 |
| `/workshop` | 완전한 워크숍 자료 세트 생성 |
| `/exercise` | 3단계 과제 생성 (기초/응용/창작) |
| `/syllabus` | 주차별 커리큘럼 설계 |

## 워크플로우

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

## 사용 예시

### 전시 준비

```
/imagine                  # 컨셉 정립
/survey                   # 레퍼런스 수집
/sketch                   # 첫 프로토타입
/vary                     # 변형 탐색
/critique                 # 중간 리뷰
/optimize                 # 퍼포먼스 튜닝
/install                  # 전시 환경 배포
/document                 # 아티스트 스테이트먼트, 캡션
```

### 워크숍 준비

```
/sketch                   # 데모 코드 작성
/explain                  # 해설 버전 생성
/workshop                 # 슬라이드, 핸드아웃, 단계별 코드
/exercise                 # 과제 생성
```

### 학기 수업

```
/syllabus                 # 16주 커리큘럼 설계
/sketch + /explain        # 매주 예제 코드 + 해설
/exercise                 # 주간 과제
/workshop                 # 실습 자료
```

## 메타 문서

스킬들은 프로젝트 루트에 다음 문서를 생성하고, 다른 스킬이 이를 자동으로 참조한다:

| 문서 | 생성 스킬 | 내용 |
|------|----------|------|
| `CONCEPT.md` | `/imagine` | 예술적 의도, 컨셉, 기술 스택 |
| `REFERENCES.md` | `/survey`, `/digest` | 레퍼런스 누적 |
| `CATALOG.md` | `/archive` | 프로젝트 파일 카탈로그 |
| `TECHNICAL-RIDER.md` | `/install` | 전시 기술 사양서 |
| `EXPERIMENT-LOG.md` | `/experiment` | 실험 기록 |

## 지원 프레임워크

p5.js · Processing · openFrameworks · Three.js · Tone.js · TouchDesigner · Max/MSP · GLSL · Arduino

프로젝트 파일 구조에서 자동 감지한다.

## 라이선스

MIT
