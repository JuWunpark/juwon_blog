# GitHub Secrets 설정 가이드

## Repository secrets에 추가하기

GitHub 저장소 → **Settings** → **Secrets and variables** → **Actions** → **Repository secrets** → **New repository secret**

다음 3개의 Secret을 추가하세요:

### 1. SERVER_HOST
- **Name**: `SERVER_HOST`
- **Value**: 서버의 공인 IP 주소
  - AWS EC2를 사용하는 경우: EC2 인스턴스의 Public IPv4 주소
  - 또는 도메인: `blog.juwonpark.me` (도메인이 서버를 가리키는 경우)

### 2. SERVER_USER
- **Name**: `SERVER_USER`
- **Value**: `ubuntu`

### 3. SERVER_SSH_KEY
- **Name**: `SERVER_SSH_KEY`
- **Value**: 서버의 SSH 개인 키 전체 내용
  - 아래 명령어로 확인:
  ```bash
  cat ~/.ssh/id_ed25519
  ```
  - 또는:
  ```bash
  cat ~/.ssh/id_rsa
  ```
  - **전체 내용**을 복사 (-----BEGIN부터 END까지 모두)

## 중요 사항

⚠️ **SSH 개인 키는 절대 공개하지 마세요!**
- GitHub Secrets에만 안전하게 저장됩니다
- 다른 사람과 공유하지 마세요

## 서버 IP 확인 방법

AWS EC2를 사용하는 경우:
1. EC2 콘솔 → Instances
2. 인스턴스 선택 → Details 탭
3. Public IPv4 address 확인

또는 서버에서:
```bash
curl -s ifconfig.me
```
