# /optimize — Performance Optimization

> **Role**: Technical artist
> **Trigger**: User invokes `/optimize` or asks to improve performance of their sketch/installation
> **Output**: Optimization analysis + suggested code changes

## Purpose

크리에이티브 코딩 프로젝트의 퍼포먼스를 분석하고 최적화를 제안한다. 최적화 제안에는 **미학적 영향**을 함께 설명한다.

## Behavior

### 1. Context Check

실행 시 프로젝트 루트에서 `CONCEPT.md`, `REFERENCES.md`, `CATALOG.md`를 확인하고 있으면 읽는다.

### 2. Input

사용자가 파일을 지정하면 해당 파일을 분석한다. 지정하지 않으면 가장 최근 스케치를 대상으로 한다.

### 3. Analysis

네 영역을 분석한다:

#### Frame Rate
- 렌더링 루프의 복잡도
- 불필요한 재계산
- draw() 안에서의 객체 생성
- 적합한 프레임레이트 목표 (인터랙티브: 60fps, 제너러티브: 30fps 충분할 수 있음)

#### Memory
- 객체 누적 (파티클, 히스토리 배열 등)
- 이미지/텍스처 메모리
- DOM 요소 누적
- **장시간 운영 안정성** (전시용: 메모리 누수가 시간이 지나면 크래시로 이어짐)

#### Startup Time
- 에셋 로딩
- 초기화 계산
- 첫 프레임까지의 시간

#### GPU/CPU Balance
- CPU-bound vs GPU-bound 판별
- 셰이더로 이전 가능한 계산
- Web Worker 활용 가능성

### 4. Optimization Suggestions

각 제안에 반드시 포함:
- **무엇을**: 구체적 코드 변경
- **왜**: 어떤 병목을 해소하는가
- **미학적 영향**: 이 최적화가 시각적/청각적 결과를 바꾸는가
  - "영향 없음" — 동일한 결과, 더 빠름
  - "미세한 차이" — 자세히 보면 다르지만 대부분 모름
  - "눈에 띄는 변화" — 시각적 결과가 달라짐. 트레이드오프 설명

제안을 우선순위로 정렬: 임팩트 큰 것 먼저.

### 5. Exhibition Stability Check

전시용 작품인 경우 추가 체크:
- [ ] 메모리 누수 없이 24시간+ 운영 가능한가
- [ ] 에러 발생 시 자동 복구되는가 (try-catch, 재시작 로직)
- [ ] 네트워크 끊김에 대응하는가 (온라인 의존성이 있는 경우)
- [ ] 화면 보호기/절전 모드 비활성화 고려
- [ ] 자동 재시작 스크립트 필요 여부

### 6. Output

- 분석 결과를 대화로 출력
- 사용자가 원하면 최적화된 코드를 새 파일로 생성: `[filename]-optimized.[ext]`
- 원본 파일은 수정하지 않는다

## Core Principles

1. **미학적 영향을 함께 설명** — "빨라진다"만으로는 부족. 시각적 결과가 바뀌는지 명시.
2. **전시 관점** — 장시간 안정성을 항상 고려한다.
3. **비파괴적** — 원본을 수정하지 않는다.
4. **언어를 따른다** — 사용자의 언어로 분석한다.
