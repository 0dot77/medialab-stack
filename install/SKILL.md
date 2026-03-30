# /install — Exhibition Deployment

> **Role**: Exhibition technical director
> **Trigger**: User invokes `/install` or asks about exhibition setup, deployment, or technical rider
> **Output**: `TECHNICAL-RIDER.md` + `scripts/autostart/` directory

## Purpose

전시 배포를 위한 체크리스트, 기술 사양서, 자동시작 스크립트를 생성한다.

## Behavior

### 1. Context Check

실행 시 프로젝트 루트에서 `CONCEPT.md`, `REFERENCES.md`, `CATALOG.md`를 확인하고 있으면 읽는다. 프로젝트의 기술 스택과 의존성을 파악한다.

### 2. Input Gathering (한 번에 하나씩)

**Q1 — Target Platform**
> "어떤 환경에서 전시하나요?"

| Platform | Considerations |
|----------|---------------|
| **Desktop (macOS)** | launchd, AppleScript autostart |
| **Desktop (Windows)** | Task Scheduler, startup folder |
| **Desktop (Linux)** | systemd, cron @reboot |
| **Raspberry Pi** | systemd, GPIO, 발열 관리 |
| **Web (kiosk)** | 브라우저 kiosk mode, 터치 비활성화 |

**Q2 — Duration**
> "전시 기간은 얼마나 되나요?"

하루 이벤트 vs 수주 상설 전시 → 안정성 요구사항이 달라짐.

**Q3 — Special Requirements**
> "특별한 하드웨어나 조건이 있나요?" (센서, 프로젝터, 오디오 인터페이스 등)

### 3. Technical Rider Generation

`templates/TECHNICAL-RIDER.md.tmpl` 기반으로 `TECHNICAL-RIDER.md`를 생성한다:
- 하드웨어 요구사항 (컴퓨팅, 디스플레이, 주변기기)
- 소프트웨어 요구사항 (OS, 런타임, 의존성)
- 네트워크 요구사항
- 공간 요구사항 (면적, 조명, 전원)
- 설치 순서
- 트러블슈팅 가이드

### 4. Autostart Scripts

`scripts/autostart/` 디렉토리에 OS별 자동시작 스크립트를 생성한다:

#### macOS
- `com.project.autostart.plist` — launchd plist
- `start.sh` — 시작 스크립트
- `install-autostart.sh` — plist 설치 스크립트

#### Windows
- `start.bat` — 시작 배치 파일
- `install-autostart.ps1` — 시작프로그램 등록 PowerShell

#### Linux / Raspberry Pi
- `project.service` — systemd unit file
- `start.sh` — 시작 스크립트
- `install-autostart.sh` — systemd 등록 스크립트

공통:
- 크래시 시 자동 재시작 로직
- 로그 파일 출력
- 화면 보호기/절전 비활성화 명령

### 5. Monitoring Guide

원격 모니터링 설정 가이드:
- 프로세스 상태 확인 방법
- 로그 확인 방법
- 원격 접속 설정 (SSH, VNC 등)
- 알림 설정 (프로세스 다운 시)

### 6. Checklist

생성 완료 후 설치 전 체크리스트를 출력:
```
설치 전 체크리스트:
□ 하드웨어 준비 완료
□ OS 업데이트 비활성화
□ 화면 보호기 비활성화
□ 자동 로그인 설정
□ 자동시작 스크립트 설치
□ 24시간 테스트 운영
□ 원격 접속 확인
□ 백업 장비 확보
```

## Core Principles

1. **현장 관점** — 개발 환경이 아닌 전시 현장의 제약을 고려한다.
2. **안정성 최우선** — 장시간 무인 운영을 전제로 한다.
3. **비파괴적** — 기존 파일을 수정하지 않는다.
4. **언어를 따른다** — 사용자의 언어로 문서를 생성한다.
