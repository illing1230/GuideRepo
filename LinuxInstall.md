## 윈도우 노트북을 리눅스 서버로 완전 교체하는 상세 가이드

### 1단계: 사전 준비
**백업 및 준비사항:**
- 중요한 데이터를 외부 저장장치에 백업
- 노트북 하드웨어 사양 확인 (CPU, RAM, 네트워크 카드 등)
- 8GB 이상 USB 드라이브 준비
- 인터넷 연결 확인

**리눅스 배포판 선택:**
- **Ubuntu Server**: 초보자에게 가장 친화적, 풍부한 문서
- **CentOS Stream/Rocky Linux**: 기업환경에 적합, RedHat 계열
- **Debian**: 안정성 중시, 서버용으로 매우 인기

### 2단계: 부팅 USB 만들기
**필요한 도구:**
- Rufus (윈도우용) 또는 Etcher
- 선택한 리눅스 ISO 파일

**과정:**
1. 리눅스 배포판 공식 사이트에서 Server 버전 ISO 다운로드
2. Rufus 실행 → USB 선택 → ISO 파일 선택
3. 파티션 방식: GPT, 파일시스템: FAT32 선택
4. "시작" 클릭하여 부팅 USB 생성

### 3단계: BIOS/UEFI 설정
**부팅 설정 변경:**
1. 노트북 재시작 시 F2, F12, Del 키 등으로 BIOS 진입
2. Boot 메뉴에서 USB를 최우선 부팅으로 설정
3. Secure Boot 비활성화 (필요시)
4. Legacy/UEFI 모드 확인

### 4단계: 리눅스 설치 과정
**Ubuntu Server 기준 설치:**

1. **언어 및 키보드 설정**
   - 한국어 또는 영어 선택
   - 키보드 레이아웃 설정

2. **네트워크 설정**
   - 유선/무선 네트워크 설정
   - 고정 IP 설정 권장 (나중에도 변경 가능)

3. **디스크 파티션**
   - "Guided - use entire disk" 선택 (전체 디스크 사용)
   - 또는 수동 파티션 설정:
     - `/` (루트): 최소 20GB 
     - `/home`: 나머지 공간
     - `swap`: RAM 크기와 동일 또는 2배

4. **사용자 계정 생성**
   - 관리자 계정 생성
   - 강력한 비밀번호 설정

5. **SSH 서버 설치**
   - "Install OpenSSH server" 체크 (원격 접속용)

6. **추가 소프트웨어**
   - Docker, 웹서버 등 필요한 패키지 선택

### 5단계: 설치 후 초기 설정

**시스템 업데이트:**
```bash
sudo apt update && sudo apt upgrade -y  # Ubuntu/Debian
sudo yum update -y                       # CentOS/RHEL
```

**SSH 보안 설정:**
```bash
sudo nano /etc/ssh/sshd_config
# Port 22 → 다른 포트로 변경 (보안)
# PasswordAuthentication yes → 키 인증 설정 시 no
sudo systemctl restart ssh
```

**방화벽 설정:**
```bash
sudo ufw enable                    # Ubuntu
sudo ufw allow ssh                 # SSH 포트 허용
sudo ufw allow 80                  # HTTP (필요시)
sudo ufw allow 443                 # HTTPS (필요시)
```

**전원 관리:**
```bash
# 노트북 덮개를 닫아도 계속 실행되도록 설정
sudo nano /etc/systemd/logind.conf
# HandleLidSwitch=ignore 추가
sudo systemctl restart systemd-logind
```

### 6단계: 서버 환경 구성

**웹서버 설치 (예시):**
```bash
# Apache
sudo apt install apache2 -y
sudo systemctl enable apache2

# 또는 Nginx
sudo apt install nginx -y
sudo systemctl enable nginx
```

**데이터베이스 설치 (필요시):**
```bash
sudo apt install mysql-server -y
sudo mysql_secure_installation
```

### 주의사항
- **데이터 손실**: 기존 윈도우와 모든 데이터가 완전히 삭제됨
- **하드웨어 호환성**: 일부 노트북 고유 기능(밝기 조절, Fn 키 등)이 제한될 수 있음
- **드라이버**: 그래픽카드, Wi-Fi 등의 드라이버 추가 설치 필요할 수 있음
- **전력 소모**: 서버용으로 24시간 운영 시 전력 및 발열 관리 필요

설치 중 특정 단계에서 문제가 발생하거나 더 자세한 설명이 필요한 부분이 있으시면 언제든 문의하세요.
