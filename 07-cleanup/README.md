# 실습 환경 정리

## AWS 자원 정리

이 워크샵에서 생성한 AWS 자원들을 정리하여 불필요한 비용이 발생하지 않도록 합니다.

### 1. Amazon Q Developer 구독 해지

1. [Amazon Q Developer 콘솔](https://us-east-1.console.aws.amazon.com/amazonq/developer)로 이동합니다.
2. 탐색 창에서 **구독**을 선택합니다.
3. **사용자** 탭에서 생성한 사용자를 선택합니다.
4. **구독 해지**를 클릭합니다.

### 2. IAM Identity Center 정리

1. [IAM Identity Center 콘솔](https://console.aws.amazon.com/singlesignon)로 이동합니다.
2. **사용자** 섹션에서 워크샵용으로 생성한 사용자를 삭제합니다.
3. **설정** > **Identity Center 인스턴스 삭제**를 선택하여 전체 인스턴스를 삭제합니다.

### 3. Amazon Cognito 정리

1. [Amazon Cognito 콘솔](https://us-west-2.console.aws.amazon.com/cognito)로 이동합니다.
2. **사용자 풀**에서 워크샵용으로 생성한 사용자 풀을 선택합니다.
3. **삭제**를 클릭하여 사용자 풀을 삭제합니다.
4. **자격 증명 풀**에서 생성한 자격 증명 풀도 동일하게 삭제합니다.

### 4. 로컬 환경 정리


### 5. 정리 완료 확인

- [ ] Amazon Q Developer 구독 해지 완료
- [ ] IAM Identity Center 사용자 삭제 완료
- [ ] IAM Identity Center 인스턴스 삭제 완료
- [ ] Amazon Cognito 사용자 풀 삭제 완료

상기 항목을 수행하여 워크샵 환경을 정리하실 수 있습니다.
