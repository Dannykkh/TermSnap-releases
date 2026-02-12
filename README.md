<p align="center">
  <img src="images/termsnap-icon.png" width="120" alt="TermSnap Icon">
</p>

<h1 align="center">TermSnap</h1>
<p align="center"><strong>AI 기반 터미널 도우미</strong> — "PuTTY를 더 편하게"</p>

<p align="center">
  <img src="https://img.shields.io/badge/platform-Windows%2010+-blue" alt="Platform">
  <img src="https://img.shields.io/badge/.NET-8.0-purple" alt=".NET">
  <img src="https://img.shields.io/badge/license-Proprietary-red" alt="License">
</p>

---

## 왜 만들었나

서버를 다루다 보면 반복되는 불편함이 있습니다.

- **명령어를 매번 검색해야 한다** — nginx 재시작이 `systemctl restart nginx`인지, `service nginx restart`인지 헷갈린다.
- **PuTTY는 너무 단순하다** — 탭도 없고, 파일 전송하려면 WinSCP를 따로 열어야 한다.
- **서버가 여러 대면 관리가 복잡하다** — 프로필 저장, 빠른 전환, 상태 모니터링이 필요하다.
- **로컬 터미널도 따로 쓴다** — PowerShell은 여기, SSH는 저기. 하나로 합치고 싶다.

TermSnap은 이 문제들을 하나의 도구로 해결합니다. **자연어로 말하면 AI가 명령어를 만들어주고**, SSH와 로컬 터미널을 탭 하나로 통합하며, 파일 전송까지 한 화면에서 처리합니다.

---

## 스크린샷

### 세션 선택

앱을 열면 로컬 터미널과 SSH 서버 연결 중 선택할 수 있습니다.

![세션 선택](images/session-selector.png)

### 로컬 터미널

PowerShell, CMD, WSL, Git Bash를 지원합니다. Claude Code, Codex, Gemini CLI 같은 AI 도구도 바로 연동됩니다.

![로컬 터미널](images/local-terminal-welcome.png)

### SSH 서버 연결

저장된 서버 프로필로 한 번에 접속합니다. 비밀번호, .ppk, .pem 키 모두 지원합니다.

![SSH 연결](images/ssh-connection.png)

### 프로젝트 뷰

파일 탐색기와 여러 터미널을 한 화면에서 사용합니다. VS Code나 Cursor를 바로 열 수도 있습니다.

![프로젝트 뷰](images/file-viewer.png)

---

## 주요 기능

### AI 명령어 변환

서버 명령어를 몰라도 됩니다. 한국어로 "nginx 재시작해줘"라고 입력하면 AI가 `sudo systemctl restart nginx`로 변환합니다.

- **5가지 AI 제공자** — Gemini, OpenAI, Claude, Grok, Ollama(로컬)
- **Q&A 벡터 검색** — 한번 물어본 명령어는 저장되어 다음부터 AI 호출 없이 즉시 답변 (토큰 절약)
- **하이브리드 검색** — FTS5 키워드 검색 + Embedding 의미 검색을 결합
- **오류 자동 분석** — 명령어 실행에 실패하면 AI가 원인을 분석하고 수정된 명령어를 제안 (최대 3회 재시도)

### SSH 서버 세션

PuTTY의 불편함을 해결한 SSH 클라이언트입니다.

- **서버 프로필 저장** — 호스트, 포트, 인증 정보를 프로필로 저장하고 한 번에 접속
- **3가지 인증 방식** — 비밀번호, .ppk (PuTTY 형식), .pem (OpenSSH 형식)
- **SFTP 파일 전송** — 별도 프로그램 없이 드래그 앤 드롭으로 파일 업로드/다운로드
- **원격 파일 탐색기** — 서버 파일 구조를 트리로 탐색
- **서버 모니터링** — CPU, 메모리, 디스크, 업타임을 실시간 확인
- **Port Forwarding** — SSH 터널링으로 포트 포워딩 관리
- **비밀번호 암호화** — Windows DPAPI로 API 키와 비밀번호를 안전하게 저장

### 로컬 터미널 세션

Warp 스타일의 로컬 터미널입니다.

- **4가지 쉘** — PowerShell, CMD, WSL (Ubuntu 등), Git Bash
- **블록 UI** — 명령어와 출력을 블록 단위로 정리해서 보여주는 모드
- **AI CLI 연동** — Claude Code, Codex, Gemini CLI, Aider를 터미널 안에서 바로 실행
- **Git 브랜치 표시** — 현재 Git 브랜치를 자동 감지해서 표시
- **인터랙티브 모드** — vim, python, node 같은 인터랙티브 프로그램 지원

### 프로젝트 관리

하나의 프로젝트에 여러 터미널을 묶어서 관리합니다.

- **서브탭 시스템** — 프로젝트 안에 터미널 여러 개를 탭으로 관리
- **파일 탐색기 고정** — 서브탭을 전환해도 파일 탐색기는 그대로 유지
- **에디터 연동** — VS Code, Cursor를 감지해서 버튼 한 번으로 실행
- **최근 폴더** — 자주 쓰는 폴더를 웰컴 화면에서 바로 열기
- **Git 저장소 복제** — 웰컴 화면에서 바로 `git clone`

### 명령어 관리

자주 쓰는 명령어를 저장하고 빠르게 재사용합니다.

- **스니펫** — 명령어를 저장하고 카테고리별로 정리
- **매개변수 템플릿** — `docker run -p {{port:8080:포트번호}} {{image}}` 형태로 실행 시 값 입력
- **실행 이력** — 모든 명령어 실행 이력을 SQLite에 저장하고 전문 검색 (FTS5)
- **명령어 팔레트** — 단축키로 명령어를 빠르게 검색하고 실행

### 안전장치

위험한 명령어를 실행하기 전에 자동으로 차단합니다.

- **즉시 차단** — `rm -rf /`, `dd if=`, `mkfs`, Fork bomb, `curl | sh` 등 시스템을 파괴하는 명령어
- **확인 후 실행** — `rm`, `sudo`, `reboot`, `kill`, `iptables` 등은 확인 팝업 후 실행

### 모바일 접속

외부에서 스마트폰으로 서버에 접속할 수 있습니다.

- **내장 웹서버** — HTTPS (Kestrel) 웹서버 내장
- **QR 코드 접속** — QR을 스캔하면 모바일 브라우저에서 터미널 사용
- **PIN 인증** — 6자리 PIN으로 로그인 (5분 만료, 5회 시도 제한)
- **JWT 토큰** — Access Token + Refresh Token 기반 인증
- **WebSocket** — 실시간 터미널 출력 스트리밍

### AI 에이전트 시스템

단순 명령어 변환을 넘어, 전문 분야별 AI 에이전트가 작업을 도와줍니다.

- **DevOps Agent** — 배포, 인프라, 모니터링 전문
- **Backend Engineer Agent** — API, DB, 서버 로직 전문
- **Frontend Engineer Agent** — UI/UX, 웹 개발 전문
- **Librarian Agent** — 문서 검색, 학습 자료 정리
- **Oracle Agent** — 복잡한 아키텍처 질문 대응
- **Smart Router** — 질문 난이도에 따라 Fast/Balanced/Powerful 모델 자동 선택

### 기타

- **다국어** — 한국어, 영어 UI 지원
- **테마** — 다크 모드, 라이트 모드
- **세션 복원** — 앱을 재시작해도 마지막 탭 상태 그대로 복원
- **자동 업데이트 확인** — 새 버전이 있으면 알림
- **통계 대시보드** — 사용 패턴, 명령어 빈도 등 통계 시각화

---

## 비즈니스 모델 캔버스

<table>
<tr>
<td rowspan="2" width="20%">

### 8. 핵심 파트너십
- Google (Gemini API)
- OpenAI (GPT API)
- Anthropic (Claude API)
- xAI (Grok API)
- Renci.SshNet (오픈소스)
- MaterialDesignThemes

</td>
<td width="20%">

### 7. 핵심 활동
- AI 명령어 변환 엔진 개발
- 터미널 에뮬레이션 (ConPTY)
- SSH/SFTP 연결 관리
- 보안 (DPAPI 암호화, 위험 명령어 차단)
- Q&A 벡터 검색 최적화

</td>
<td rowspan="2" width="20%">

### 2. 가치 제안
- 자연어 → 명령어 변환
- SSH + 로컬 터미널 통합
- 위험 명령어 자동 차단
- Q&A 캐싱으로 비용 절약
- 모바일 원격 접속
- 프로젝트 단위 관리
- 5가지 AI 에이전트

</td>
<td width="20%">

### 4. 고객 관계
- GitHub Issues 피드백
- 자동 업데이트 알림
- 사용 통계 대시보드
- 다국어 지원 (한/영)

</td>
<td rowspan="2" width="20%">

### 1. 고객 세그먼트
- Linux 서버 관리자
- 명령어에 익숙하지 않은 개발자
- 여러 서버를 관리하는 DevOps
- 로컬+원격 통합이 필요한 프리랜서
- 서버 교육을 받는 학생

</td>
</tr>
<tr>
<td>

### 6. 핵심 자원
- WPF / .NET 8.0
- ConPTY (로컬 터미널)
- Renci.SshNet (SSH)
- SQLite + FTS5 (검색)
- ONNX 로컬 임베딩 모델
- Kestrel 웹서버

</td>
<td>

### 3. 채널
- GitHub Releases
- 기술 블로그/커뮤니티
- QR 코드 모바일 접속

</td>
</tr>
<tr>
<td colspan="2">

### 9. 비용 구조
- AI API 사용료 (Gemini, OpenAI, Claude, Grok)
- 개발 시간 (1인 개발)
- 코드 서명 인증서 (배포 시)

</td>
<td colspan="3">

### 5. 수익원
- **Freemium** — 기본 기능 무료, Pro 기능 유료
- **Pro 라이선스** — AI 에이전트, 모바일 접속, 고급 모니터링
- **기업용 라이선스** — 팀 관리, 중앙 설정, 볼륨 라이선스

</td>
</tr>
</table>

---

## 다운로드

[Releases](https://github.com/Dannykkh/TermSnap-releases/releases) 페이지에서 최신 버전을 다운로드하세요.

## 시스템 요구사항

- Windows 10 이상
- .NET 8.0 Runtime

## 라이선스

이 소프트웨어는 독점 소프트웨어입니다. 소스 코드는 비공개이며, 바이너리 재배포는 허용되지 않습니다.

Copyright (c) 2026 Dannykkh. All rights reserved.
