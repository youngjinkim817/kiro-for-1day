# 준비사항

이 섹션에서는 Kiro IDE 기능을 적용할 코드 토대인 Spirit of Kiro 게임의 개발환경 설정 과정을 안내합니다.

---

## **환경 설정 옵션**

사용하는 AWS 계정 유형에 따라 적절한 가이드를 선택하세요.


### **선택지1: Workshop Event 계정 사용**

AWS Workshop Event에 참여하고 있다면, 사전 구성된 임시 계정을 사용할 수 있습니다.

- 필요한 권한이 사전 설정됨
- Amazon Bedrock 모델 접근 권한이 이미 활성화됨
- 임시 계정으로 워크샵 종료 후 접근 불가

**[→ Workshop Event 계정에서 개발환경 준비](02-workshop-event-account/README.md)**

AWS Workshop Event에 참여하는 경우, 먼저 Workshop Studio를 통해 임시 AWS 계정에 접속해야 합니다. Chrome 또는 Firefox 브라우저를 열고 이벤트 주최자가 제공한 **Workshop Studio 링크**로 이동하세요.

[**이벤트 대시보드 열기**](https://catalog.prod.workshops.aws/event/dashboard/ko-KR)

1. 로그인 페이지에서 `Email one-time password (OTP)`를 선택합니다. 이메일 주소로 9자리 이벤트 접속 코드를 수신하여 입력합니다.

2. 성공적으로 로그인하면 검토 및 참가 페이지로 이동합니다. 이용 약관을 주의 깊게 검토한 후 **Join event**를 클릭합니다.

축하합니다! 이제 워크샵을 위한 AWS 계정에 성공적으로 접속하셨습니다.

### **선택지2: 개인 AWS 계정 사용**

개인 AWS 계정을 보유하고 있다면, 개인 환경에서 개발환경을 설정할 수 있습니다.

- AWS Free Tier 사용 가능
- 개인 계정의 권한 설정 필요
- Amazon Bedrock 모델 접근 권한 요청 필요

**[→ 개인 환경에서 개발환경 준비](03-personal-environment/README.md)**

---

## **프로젝트 구조 이해**

개발환경 설정 전에 프로젝트의 전체 구조를 파악해보세요:

- [`architecture.md`](https://github.com/kirodotdev/kiro-demo-game/blob/main/docs/architecture.md) – 시스템 아키텍처 개요
- [`appsec-overview.md`](https://github.com/kirodotdev/kiro-demo-game/blob/main/docs/appsec-overview.md) – 게임 구성 요소 간 연결 방식
