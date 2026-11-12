🤖 텔레그램 AI 요약 비서: '핵심만 3줄' (Core-Summary-Bot)

1. 프로젝트 개요

바쁜 현대 사회에서 넘쳐나는 텍스트 정보를 모두 읽기란 불가능에 가깝습니다. 우리 팀은 사용자가 긴 글이나 기사 링크를 복사해서 붙여넣기만 하면, AI가 가장 중요한 핵심만 3줄로 요약해 주고 관련 키워드까지 추출해 주는 텔레그램 기반 AI 비서 서비스를 기획 및 개발했습니다.

2. 팀원 및 역할 분담

본 프로젝트는 4인의 팀원이 역할을 분담하여 유기적으로 협력했습니다.

노현우: 핵심 AI 로직 설계, Gemini API 연동 및 프롬프트 엔지니어링,실사용자 테스트(QA) 진행, 피드백 수집 및 개선안 도출 문서화

오승욱: 프로젝트 총괄 기획, 타겟 사용자 분석 및 서비스 아키텍처 설계

강민수: 노코드(Make.com) 기반 워크플로우 파이프라인 구축 및 버전 관리


💡 Commit 기록 관련 안내 (중요)
본 프로젝트는 빠르고 효율적인 개발을 위해 디스코드 화면 공유를 통한 '실시간 페어 프로그래밍(Pair Programming)' 방식으로 진행되었습니다. 기획, 프롬프트 테스트, 파이프라인 연결을 팀원들이 함께 화면을 보며 의논하여 실시간으로 수정했기 때문에, 깃허브 커밋 기록은 통합 및 관리를 위해 메인 담당자의 단일 계정으로 집중하여 업로드하였음을 알립니다.

3. 기술 스택 (Tech Stack)

AI Model: Google Gemini 1.5 Flash (빠른 응답 속도와 높은 요약 성능)

Platform: Telegram Bot API (서버 리소스 없이 사용자 접근성이 높은 메신저 플랫폼 채택)

Automation: Make.com (웹훅 기반 노코드 API 연동 및 데이터 파이프라인 구축)

Version Control: Git / GitHub

### 💡 Git 브랜치 전략 및 원격 리포지토리 관리 (Branch Strategy)
*   **원격 리포지토리 URL:** https://github.com/ghksl96/Mission-M2-1 (Public 운영)
*   **브랜치 전략 (GitHub Flow 변형):** 
    *   `main` 브랜치: 무중단 서비스가 돌아가는 최종 배포용 브랜치 (안정성 보장)
    *   `feature/prompt-update` (가상 브랜치): 프롬프트 엔지니어링 개선 및 테스트를 진행한 작업 환경. 디스코드 화면 공유를 통한 페어 프로그래밍 완료 후 `main`으로 즉시 병합(Merge)하는 전략을 취함.

4. 서비스 아키텍처 및 워크플로우
### 🖼️ 서비스 아키텍처 다이어그램
```mermaid
graph TD
    A[사용자 텔레그램] -->|텍스트 입력| B(Make.com: Watch Updates)
    B --> C{Google Gemini 1.5}
    C -->|3줄 요약 추출| D(Make.com: Send Message)
    D -->|결과 반환| A
본 서비스는 별도의 서버 구축 없이 노코드 툴과 웹훅을 활용한 Serverless 아키텍처로 구성되었습니다.

사용자 입력: 사용자가 텔레그램 봇에게 긴 텍스트 전송

이벤트 감지: Make.com의 Telegram 'Watch Updates' 모듈이 웹훅을 통해 메시지 수신

AI 처리: Gemini API로 메시지 전달 (사전 정의된 System Prompt에 따라 3줄 요약 및 키워드 추출 수행)

결과 반환: 처리된 결과물을 Telegram 'Send a Message' 모듈을 통해 사용자에게 전송

5. 주요 기능 및 개선 사항

정확한 3줄 요약: 긴 글을 문맥 파악 후 3문장으로 압축

가독성 개선: 텍스트만 나오는 밋밋한 형태에서, 이모지와 해시태그(#)를 활용하도록 프롬프트 고도화 (사용자 피드백 반영)

실시간 24시간 응답: Make.com 스케줄링 기능을 통해 24시간 상시 동작하는 서비스 배포 완료

6. 사용 방법

텔레그램 앱을 실행합니다.

검색창에 @본인의봇아이디를 검색하여 봇 채팅방에 입장합니다.

/start 를 누르거나 요약하고 싶은 긴 글을 채팅창에 전송합니다.

약 2~3초 후, AI가 깔끔하게 정리한 3줄 요약본을 확인합니다.

실행화면<BR>

<img width="1031" height="784" alt="Screenshot_2" src="https://github.com/user-attachments/assets/ea87b5ff-21af-4edf-af79-5d91d23abd98" /><BR>

<img width="556" height="677" alt="Screenshot_1" src="https://github.com/user-attachments/assets/6d902f46-a946-4694-9414-76a5fc2b6365" />

