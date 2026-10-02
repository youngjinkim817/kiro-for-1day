## **게임 실행 단계**

### **1. 저장소 클론**

```bash
git clone https://github.com/kirodotdev/spirit-of-kiro.git
cd spirit-of-kiro
git checkout challenge
```

### **2. 의존성 확인**
 
설치된 도구들이 올바르게 작동하는지 확인합니다. 모든 의존성이 올바르게 설치되었다면 성공 메시지가 표시됩니다.

```bash
./scripts/check-dependencies.sh
```

> [!WARNING]
> **Windows 에서 sh 실행**
>
> Windows 실습 환경일 경우, Git 도구에서 제공하는 Git bash 를 활용하여 워크샵 내 쉘 스크립트를 수행하시기 바랍니다.


### **3. AWS 리전 설정**

이 실습은 **오리건(us-west-2) 리전**에서 진행됩니다. AWS CLI 기본 리전을 확인하고 필요시 변경하세요.

```bash
# 현재 리전 확인
aws configure get region

# 오리건 리전으로 설정 (권장)
aws configure set region us-west-2
```

### **4. Amazon Cognito 사용자 풀 배포**

AWS Free Tier로 제공되는 Cognito 사용자 풀을 배포합니다.

```bash
./scripts/deploy-cognito.sh game-auth
```

배포가 완료되면 AWS 콘솔에서 생성된 리소스를 확인할 수 있습니다.

### **5. 게임 스택 빌드 및 실행**

#### Podman 사용


<details><summary>코드 보기</summary>

```bash
# Podman 초기 설정 (처음 사용하는 경우)
podman machine init && podman machine start

# 게임 스택 빌드 및 실행
podman compose build && \
podman compose up \
  --watch \
  --remove-orphans \
  --timeout 0 \
  --force-recreate
```

</details>


#### Docker 사용

Docker를 사용하는 경우, 다음 별칭을 설정하면 앞선 Podman 명령어를 그대로 사용할 수 있습니다:

```bash
# 별칭 설정 (선택사항)
alias podman='docker'
```

또는 직접 Docker 명령어를 사용하시면 됩니다.


<details><summary>코드 보기</summary>

```bash
docker compose build && \
docker compose up \
  --watch \
  --remove-orphans \
  --timeout 0 \
  --force-recreate
```

</details>



> [!NOTE]
> **참고**
>
> 게임 서버, 클라이언트 컨테이너의 실행을 지속 유지하기 위해 다음 작업부터는 별개 터미널에서 진행하기 바랍니다.


### **6. 데이터베이스 초기화**

게임 유저 및 아이템의 상태 정보를 저장할 때는 여러분 로컬 환경에서 실행할 수 있는 [DynamoDB Local](https://docs.aws.amazon.com/ko_kr/amazondynamodb/latest/developerguide/DynamoDBLocal.html) 테이블을 이용할 것입니다.


> [!WARNING]
> **중요**
>
> Workshop Studio 환경이라면, Local DynamoDB 파일 생성을 위해 아래와 같은 파일 권한 설정 명령어를 먼저 입력해 주세요.
>
> ```bash
> sudo chmod 755 ./docker/dynamodb
> sudo chown -R $(id -u):$(id -g) ./docker/dynamodb
> ```


#### Podman 사용


<details><summary>코드 보기</summary>

```bash
podman exec server mkdir -p /app/server/iac &&
podman cp scripts/bootstrap-local-dynamodb.js server:/app/ &&
podman cp server/iac/dynamodb.yml server:/app/server/iac/ &&
podman exec server bun run /app/bootstrap-local-dynamodb.js
```

</details>


#### Docker 사용 


<details><summary>코드 보기</summary>


```bash
docker exec server bash -c "mkdir -p /app/server/iac" &&
docker cp scripts/bootstrap-local-dynamodb.js server:/app/ &&
docker cp server/iac/dynamodb.yml server:/app/server/iac/ &&
docker exec server bash -c "bun run /app/bootstrap-local-dynamodb.js"
```

</details>


### **7. 서버 상태 확인**

게임 서버와 클라이언트를 잘 구동하였는지 확인합니다.

먼저 게임서버가 정상 동작하는지 확인해 보세요. `OK` 응답이 반환되면 서버가 정상 작동 중입니다.
```bash
curl localhost:8080
```

웹 브라우저에서 게임 클라이언트에 접속이 가능한지 확인하세요.
```
http://localhost:5173
```
