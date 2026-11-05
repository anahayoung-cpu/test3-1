# 개발 워크스테이션 구축 프로젝트

## 1. 프로젝트 개요

### 1-1. 프로젝트 목적

본 프로젝트는 개발 환경 구축에 필요한 기본 도구인 Linux CLI, Docker, Git/GitHub의 사용 방법을 익히고, 직접 개발 워크스테이션을 구축하는 것을 목표로 한다.

터미널을 활용한 파일 및 디렉터리 관리부터 Linux 파일 권한 설정, Docker 이미지 및 컨테이너 관리, Dockerfile 기반 웹 서버 구축, 포트 매핑, 데이터 마운트 및 영속성 검증까지 수행한다.

마지막으로 Git과 GitHub를 연동하여 작업 결과물을 관리하고, 다른 사용자도 동일한 환경을 재현할 수 있도록 기술 문서와 실행 기록을 정리한다.

### 1-2. 프로젝트 주요 수행 내용

- Windows PowerShell 및 Linux CLI 기본 명령어 실습
- Linux 파일 및 디렉터리 권한 관리
- Docker 설치 및 기본 명령어 실습
- Dockerfile 기반 커스텀 이미지 제작
- 웹 서버 컨테이너 실행 및 포트 매핑
- 바인드 마운트 및 Docker 볼륨 영속성 검증
- Git 버전 관리 및 GitHub 저장소 연동
- 실행 기록 및 기술 문서 작성

---

## 2. 실행 환경

### 2-1. Windows 환경

| 항목 | 실행 환경 |
|---|---|
| OS | Windows 11 |
| OS Build | 10.0.26200.0 |
| Shell | Windows PowerShell |
| PowerShell Version | 5.1.26100.9711 |
| 작업 환경 | Windows PowerShell |

### 2-2. Linux 환경

| 항목 | 실행 환경 |
|---|---|
| Host OS | Windows 11 |
| Linux 실행 환경 | WSL2 |
| Linux 배포판 | Ubuntu 2 |
| Shell | Bash |
| Terminal | Ubuntu Terminal |

### 2-3. Docker 환경

| 항목 | 실행 환경 |
|---|---|
| Docker 실행 환경 | Docker Desktop |
| Docker Client Version | 29.9.2 |
| Docker Server Version | 29.9.2 |
| Docker Engine | 29.9.2 |

**Docker 버전 확인 명령어**

```powershell
docker --version
```

**실행 결과**

```text
PS C:\WINDOWS\System32>  docker --version
Docker version 29.9.2, build a82e528
```

### 2-4. Git 환경

| 항목 | 실행 환경 |
|---|---|
| Git Version | 2.56.0.windows.4 |
| 코드 편집기 | nano, Ubuntu Terminal |
| 원격 저장소 | GitHub |
| 기본 브랜치 | main |

**Git 버전 확인 명령어**

```powershell
git --version
```

**실행 결과**

```text
PS C:\WINDOWS\System32> git --version
git version 2.56.0.windows.4
```

---

## 3. 수행 항목 체크리스트

### 3-1. 터미널 및 Linux

- [x] PowerShell 현재 위치 확인
- [x] 파일 및 폴더 목록 확인
- [x] 숨김 파일 및 폴더 확인
- [x] 디렉터리 이동 및 생성
- [x] 빈 파일 생성
- [x] 파일 내용 입력 및 확인
- [x] 파일 복사
- [x] 파일 이동 및 이름 변경
- [x] 파일 삭제
- [x] Linux CLI 기본 명령어
- [x] 절대 경로 및 상대 경로 확인
- [x] 파일 권한 확인 및 변경
- [x] 디렉터리 권한 확인 및 변경

### 3-2. Docker

- [x] Docker 설치 및 기본 점검
- [x] Docker 이미지 다운로드 및 목록 확인
- [x] hello-world 실행
- [x] Ubuntu 컨테이너 실행
- [x] 컨테이너 실행 및 종료 실습
- [x] Docker 로그 확인
- [x] Docker 리소스 사용량 확인

### 3-3. Dockerfile 및 웹 서버

- [x] 웹 서버 소스코드 작성
- [x] Dockerfile 직접 작성
- [x] 커스텀 이미지 빌드
- [x] 커스텀 컨테이너 실행
- [x] 포트 매핑 설정
- [x] 브라우저 또는 curl 접속 확인
- [x] 서로 다른 호스트 포트로 2회 실행 및 접속 확인

### 3-4. 데이터 관리

- [x] 바인드 마운트 설정
- [x] 호스트 파일 변경 전후 비교
- [x] Docker 볼륨 생성
- [x] 컨테이너와 볼륨 연결
- [x] 컨테이너 삭제 전 데이터 확인
- [x] 새 컨테이너에서 데이터 유지 여부 확인

### 3-5. Git 및 GitHub

- [x] Git 사용자 정보 설정
- [x] Git 기본 브랜치 설정
- [x] Git 설정 확인
- [x] VS Code GitHub 로그인
- [x] GitHub Repository 생성
- [x] 로컬 프로젝트와 원격 저장소 연결
- [x] 프로젝트 업로드 및 확인

---

## 4. 터미널 기본 조작 실습

### 4-1. 현재 위치 및 파일 목록 확인

**수행 목적**

현재 작업 디렉터리를 확인하고 해당 위치의 파일과 폴더 목록을 조회한다.

**사용 명령어**

```powershell
pwd
ls
ls -Force
```

**실행 결과**

```text
PS C:\Users\김동환> pwd

Path
----
C:\Users\김동환


PS C:\Users\김동환> ls


    디렉터리: C:\Users\김동환


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2022-07-01   오전 7:56                .ms-ad
d-r---      2021-05-04  오후 12:25                3D Objects
d-----      2026-11-03   오후 2:31                codyssey
d-r---      2021-05-04  오후 12:25                Contacts
d-r---      2026-11-04   오전 9:04                Desktop
d-r---      2026-08-14  오전 10:31                Documents
d-r---      2026-11-04   오전 8:18                Downloads
d-r---      2025-01-23   오후 3:40                Favorites
d-r---      2021-05-04  오후 12:25                Links
d-r---      2021-05-04  오후 12:25                Music
d-r---      2026-05-11   오후 2:29                OneDrive
d-r---      2024-02-26   오전 8:54                Pictures
d-r---      2021-05-04  오후 12:25                Saved Games
d-r---      2021-05-04  오후 12:25                Searches
d-r---      2024-04-01   오전 8:31                Videos
-a----      2026-08-20   오전 8:38             29 Foxit Reader SDK ActiveX.ini
-a----      2024-06-25   오전 9:48          21663 KCase.log
-a----      2026-03-27   오후 4:12            185 totalmines.ini


PS C:\Users\김동환> ls -Force


    디렉터리: C:\Users\김동환


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2022-07-01   오전 7:56                .ms-ad
d-r---      2021-05-04  오후 12:25                3D Objects
d--h--      2021-05-04  오후 12:19                AppData
d--hsl      2021-05-04   오전 8:55                Application Data
d-----      2026-11-03   오후 2:31                codyssey
d-r---      2021-05-04  오후 12:25                Contacts
d--hsl      2021-05-04   오전 8:55                Cookies
d-r---      2026-11-04   오전 9:04                Desktop
d-r---      2026-08-14  오전 10:31                Documents
d-r---      2026-11-04   오전 8:18                Downloads
d-r---      2025-01-23   오후 3:40                Favorites
d--hs-      2026-11-04   오전 7:28                IntelGraphicsProfiles
d-r---      2021-05-04  오후 12:25                Links
d--hsl      2021-05-04   오전 8:55                Local Settings
d-r---      2021-05-04  오후 12:25                Music
d--hsl      2021-05-04   오전 8:55                My Documents
d--hsl      2021-05-04   오전 8:55                NetHood
d-r---      2026-05-11   오후 2:29                OneDrive
d-r---      2024-02-26   오전 8:54                Pictures
d--hsl      2021-05-04   오전 8:55                PrintHood
d--hsl      2021-05-04   오전 8:55                Recent
d-r---      2021-05-04  오후 12:25                Saved Games
d-r---      2021-05-04  오후 12:25                Searches
d--hsl      2021-05-04   오전 8:55                SendTo
d--hsl      2021-05-04   오전 8:55                Templates
d-r---      2024-04-01   오전 8:31                Videos
d--hsl      2021-05-04   오전 8:55                시작 메뉴
-a----      2026-08-20   오전 8:38             29 Foxit Reader SDK ActiveX.ini
-a----      2024-06-25   오전 9:48          21663 KCase.log
-a-h--      2026-11-03   오후 7:09       19398656 NTUSER.DAT
-a-hs-      2021-05-04   오전 8:55         393216 ntuser.dat.LOG1
-a-hs-      2021-05-04   오전 8:55        5181440 ntuser.dat.LOG2
-a-hs-      2021-05-04   오전 8:55          65536 NTUSER.DAT{53b39e88-18c4-11ea-a811-000d3aa4692b}.TM.blf
-a-hs-      2021-05-04   오전 8:55         524288 NTUSER.DAT{53b39e88-18c4-11ea-a811-000d3aa4692b}.TMContainer000000000
                                                  00000000001.regtrans-ms
-a-hs-      2021-05-04   오전 8:55         524288 NTUSER.DAT{53b39e88-18c4-11ea-a811-000d3aa4692b}.TMContainer000000000
                                                  00000000002.regtrans-ms
---hs-      2021-05-04  오후 12:25             20 ntuser.ini
-a----      2026-03-27   오후 4:12            185 totalmines.ini
```

### 4-2. 디렉터리 이동 및 생성

**수행 목적**

작업 디렉터리를 이동하고 새로운 프로젝트 폴더를 생성한다.

**사용 명령어**

```powershell
cd Desktop
cd ..
mkdir codyssey
cd codyssey
pwd
```

**실행 결과**

```text
PS C:\Users\김동환> cd Desktop
PS C:\Users\김동환\Desktop> cd ..
PS C:\Users\김동환> mkdir codyssey


    디렉터리: C:\Users\김동환


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2026-11-04   오후 3:24                codyssey


PS C:\Users\김동환> cd codyssey
PS C:\Users\김동환\codyssey> pwd

Path
----
C:\Users\김동환\codyssey
```

### 4-3. 빈 파일 생성 및 파일 내용 입력

**수행 목적**

빈 파일을 생성하고 파일에 내용을 기록한 뒤 저장된 내용을 확인한다.

**사용 명령어**

```powershell
New-Item hello.txt -ItemType File
Set-Content hello.txt "Hello, Docker!"
Get-Content hello.txt
```

**실행 결과**

```text
PS C:\Users\김동환\codyssey> New-Item hello.txt -ItemType File


    디렉터리: C:\Users\김동환\codyssey


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----      2026-11-04   오후 3:25              0 hello.txt


PS C:\Users\김동환\codyssey> Set-Content hello.txt "Hello, Docker!"
PS C:\Users\김동환\codyssey> Get-Content hello.txt
Hello, Docker!
```

### 4-4. 파일 복사 및 이름 변경

**수행 목적**

기존 파일을 복사하고 복사한 파일의 이름을 변경한다.

**사용 명령어**

```powershell
Copy-Item hello.txt hello-copy.txt
Rename-Item hello-copy.txt hello-backup.txt
ls
```

**실행 결과**

```text
PS C:\Users\김동환\codyssey> Copy-Item hello.txt hello-copy.txt
PS C:\Users\김동환\codyssey> ls


    디렉터리: C:\Users\김동환\codyssey


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----      2026-11-04   오후 3:25             16 hello-copy.txt
-a----      2026-11-04   오후 3:25             16 hello.txt


PS C:\Users\김동환\codyssey> Rename-Item hello-copy.txt hello-backup.txt
PS C:\Users\김동환\codyssey> ls


    디렉터리: C:\Users\김동환\codyssey


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----      2026-11-04   오후 3:25             16 hello-backup.txt
-a----      2026-11-04   오후 3:25             16 hello.txt
```

### 4-5. 파일 이동 및 삭제

**수행 목적**

파일을 다른 디렉터리로 이동하고 삭제 작업을 수행한다.

**사용 명령어**

```powershell
mkdir moved
Move-Item hello.txt .\moved\
ls .\moved\
Get-Content .\moved\hello.txt
Move-Item .\moved\hello.txt .\
Remove-Item hello-backup.txt
ls
```

**실행 결과**

```text
PS C:\Users\김동환\codyssey> mkdir moved


    디렉터리: C:\Users\김동환\codyssey


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2026-11-04   오후 3:31                moved


PS C:\Users\김동환\codyssey> Move-Item hello.txt .\moved\
PS C:\Users\김동환\codyssey> ls .\moved\


    디렉터리: C:\Users\김동환\codyssey\moved


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----      2026-11-04   오후 3:25             16 hello.txt


PS C:\Users\김동환\codyssey> Get-Content .\moved\hello.txt
Hello, Docker!
PS C:\Users\김동환\codyssey> Move-Item .\moved\hello.txt .\
PS C:\Users\김동환\codyssey> Remove-Item hello-backup.txt
PS C:\Users\김동환\codyssey> ls


    디렉터리: C:\Users\김동환\codyssey


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----      2026-11-04   오후 3:32                moved
-a----      2026-11-04   오후 3:25             16 hello.txt

```

**전체 터미널 실행 기록**

- [PowerShell 실습 로그](logs/powershell-practice.txt)

---

## 5. Linux CLI 및 파일 권한 실습

### 5-1. Linux 실행 환경 확인

**사용 목적**

Ubuntu Linux 환경에서 현재 위치, 운영체제 정보 및 파일 목록을 확인한다.

**사용 명령어**

```bash
pwd
cat /etc/os-release
ls -la
```

**실행 결과**

```text
donghwan@localhost:~$ pwd
/home/donghwan
donghwan@localhost:~$ cat /etc/os-release
PRETTY_NAME="Ubuntu 26.04.1 LTS"
NAME="Ubuntu"
VERSION_ID="26.04"
VERSION="26.04.1 LTS (Resolute Raccoon)"
VERSION_CODENAME=resolute
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=resolute
LOGO=ubuntu-logo
donghwan@localhost:~$ ls -la
total 32
drwxr-x--- 4 donghwan donghwan 4096 Nov  4 15:21 .
drwxr-xr-x 3 root     root     4096 Nov  3 14:55 ..
-rw------- 1 donghwan donghwan   27 Nov  4 15:21 .bash_history
-rw-r--r-- 1 donghwan donghwan  220 Nov  3 14:55 .bash_logout
-rw-r--r-- 1 donghwan donghwan 3771 Nov  3 14:55 .bashrc
drwxr-x--- 4 donghwan donghwan 4096 Nov  3 14:58 .cache
drwxr-x--- 3 donghwan donghwan 4096 Nov  3 14:58 .config
-rw-rw-r-- 1 donghwan donghwan    0 Nov  4 12:44 .motd_shown
-rw-r--r-- 1 donghwan donghwan  807 Nov  3 14:55 .profile
```

### 5-2. 절대 경로 및 상대 경로 실습

**사용 목적**

현재 디렉터리를 기준으로 상대 경로와 절대 경로의 차이를 확인한다.

**사용 명령어**

```bash
pwd
cd ..
cd ~
cd /
cd /home/위치
```

**실행 결과**

```text
donghwan@localhost:~$ pwd
/home/donghwan
donghwan@localhost:~$ cd ..
donghwan@localhost:/home$ pwd
/home
donghwan@localhost:/home$ cd ~
donghwan@localhost:~$ pwd
/home/donghwan
donghwan@localhost:~$ cd /
donghwan@localhost:/$ pwd
/
donghwan@localhost:/$ cd /home/donghwan
donghwan@localhost:~$ pwd
/home/donghwan
```

-절대경로는 `/`부터 시작하는 전체 경로로, 설정파일이나 시스템 자원처럼 항상 고정된 위치를 정확하게 참조해야 하는 경우에 적합하다. 예를 들어 `/etc/docker/daemon.json`과 같은 파일은 절대경로로 지정하는 것이 안전하다. 반면 상대경로는 현재 작업 디렉터리를 기준으로 파일 위치를 표현하며, 프로젝트 내부의 스크립트나 문서처럼 구조가 유지되는 범위에서 간단하고 이식성 있게 참조해야 하는 경우에 유용하다. 예를 들어 `./script/start.sh`, `../README.md`와 같은 방식이 이에 해당한다. 정리하면, 시스템 설정이나 고정 위치는 절대경로, 프로젝트 내부 파일 참조는 상대경로를 사용하는 것이 적절하다.

### 5-3. 파일 권한 확인 및 변경

**사용 목적**

파일의 읽기(r), 쓰기(w), 실행(x) 권한을 확인하고 chmod 명령어로 권한을 변경한다.

**사용 명령어**

```bash
touch permission-test.txt
ls -l permission-test.txt
chmod 644 permission-test.txt
ls -l permission-test.txt
chmod 755 permission-test.txt
ls -l permission-test.txt
```

**권한 변경 전후 결과**

```text
donghwan@localhost:~/linux-test$ touch perm.txt
donghwan@localhost:~/linux-test$ ls -l perm.txt
-rw-r--r-- 1 donghwan donghwan 0 Nov  4 16:20 perm.txt
donghwan@localhost:~/linux-test$ chmod u+x perm.txt
donghwan@localhost:~/linux-test$ ls -l perm.txt
-rwxr--r-- 1 donghwan donghwan 0 Nov  4 16:20 perm.txt
donghwan@localhost:~/linux-test$ chmod u-x perm.txt
donghwan@localhost:~/linux-test$ ls -l perm.txt
-rw-r--r-- 1 donghwan donghwan 0 Nov  4 16:20 perm.txt
donghwan@localhost:~/linux-test$ chmod u+x perm.txt
donghwan@localhost:~/linux-test$ ls -l perm.txt
-rwxr--r-- 1 donghwan donghwan 0 Nov  4 16:20 perm.txt
donghwan@localhost:~/linux-test$ chmod 644 perm.txt
donghwan@localhost:~/linux-test$ ls -l perm.txt
-rw-r--r-- 1 donghwan donghwan 0 Nov  4 16:20 perm.txt
donghwan@localhost:~/linux-test$ chmod 755 perm.txt
donghwan@localhost:~/linux-test$ ls -l perm.txt
-rwxr-xr-x 1 donghwan donghwan 0 Nov  4 16:20 perm.txt
```

**권한 변경 내용**

- 파일 권한 변경은 파일 소유자(user), 그룹(group), 기타 사용자(other) 가 해당 파일에 대해 읽기(r), 쓰기(w), 실행(x) 할 수 있는 범위를 조정하여 보안과 사용 목적에 맞게 접근 권한을 설정하기 위해 수행한다.
- 644로 변경 : 일반 문서 파일처럼 소유자만 수정 가능하게 하고, 그룹과 기타 사용자는 내용만 읽을 수 있도록 제한하기 위함이다
- 755로 변경: 실행이 필요한 파일처럼 소유자는 수정과 실행이 가능하고, 그룹과 기타 사용자는 읽기와 실행만 가능하도록 설정하기 위함이다


### 5-4. 디렉터리 권한 확인 및 변경

**사용 목적**

디렉터리의 접근 권한을 확인하고 권한 변경을 수행한다.

**사용 명령어**

```bash
mkdir permission-dir
ls -ld permission-dir
chmod 755 permission-dir
ls -ld permission-dir
```

**실행 결과**

```text
donghwan@localhost:~/linux-test$ mkdir testdir
donghwan@localhost:~/linux-test$ ls -ld testdir
drwxr-xr-x 2 donghwan donghwan 4096 Nov  4 16:27 testdir
donghwan@localhost:~/linux-test$ chmod 755 testdir
donghwan@localhost:~/linux-test$ ls -ld testdir
drwxr-xr-x 2 donghwan donghwan 4096 Nov  4 16:27 testdir
donghwan@localhost:~/linux-test$ chmod 700 testdir
donghwan@localhost:~/linux-test$ ls -ld testdir
drwx------ 2 donghwan donghwan 4096 Nov  4 16:27 testdir
```

**Linux 실습 로그**

- [Linux 실행 및 권한 실습 로그](logs/linux-practice.txt)

---

## 6. Docker 설치 및 기본 운영 실습

### 6-1. Docker 설치 및 버전 확인

**수행 목적**

Docker가 정상적으로 설치되었는지 확인한다.

**사용 명령어**

```bash
docker --version
docker info
```

**실행 결과**

```text
ahy@DESKTOP-OO963F5:~$ docker --version
Docker version 29.9.2, build a82e528
ahy@DESKTOP-OO963F5:~$ docker info
Client:
 Version:    29.9.2
 Context:    default
 Debug Mode: false
 Plugins:
  agent: Docker AI Agent Runner (Docker Inc.)
    Version:  v1.152.0
    Path:     /usr/local/lib/docker/cli-plugins/docker-agent
  ai: Docker AI Agent - Ask Gordon (Docker Inc.)
    Version:  v1.33.0
    Path:     /usr/local/lib/docker/cli-plugins/docker-ai
  buildx: Docker Buildx (Docker Inc.)
    Version:  v0.38.1
    Path:     /usr/local/lib/docker/cli-plugins/docker-buildx
  compose: Docker Compose (Docker Inc.)
    Version:  v5.6.1
    Path:     /usr/local/lib/docker/cli-plugins/docker-compose
  debug: Get a shell into any image or container (Docker Inc.)
    Version:  0.49.0
    Path:     /usr/local/lib/docker/cli-plugins/docker-debug
  desktop: Docker Desktop commands (Docker Inc.)
    Version:  4.98.0
    Path:     /usr/local/lib/docker/cli-plugins/docker-desktop
  dhi: CLI for managing Docker Hardened Images (Docker Inc.)
    Version:  v0.0.9
    Path:     /usr/local/lib/docker/cli-plugins/docker-dhi
  extension: Manages Docker extensions (Docker Inc.)
    Version:  v0.2.32
    Path:     /usr/local/lib/docker/cli-plugins/docker-extension
  init: Creates Docker-related starter files for your project (Docker Inc.)
    Version:  v1.4.1
    Path:     /usr/local/lib/docker/cli-plugins/docker-init
  mcp: Docker MCP Plugin (Docker Inc.)
    Version:  v0.44.2
    Path:     /usr/local/lib/docker/cli-plugins/docker-mcp
  model: Docker Model Runner (Docker Inc.)
    Version:  v1.2.9
    Path:     /usr/local/lib/docker/cli-plugins/docker-model
  offload: Docker Offload (Docker Inc.)
    Version:  v0.7.35
    Path:     /usr/local/lib/docker/cli-plugins/docker-offload
  pass: Docker Pass Secrets Manager Plugin (beta) (Docker Inc.)
    Version:  v0.3.2
    Path:     /usr/local/lib/docker/cli-plugins/docker-pass
  sandbox: "docker sandbox" is deprecated, use Docker Sandboxes instead (Docker Inc.)
    Version:  v0.13.0
    Path:     /usr/local/lib/docker/cli-plugins/docker-sandbox
  scout: Docker Scout (Docker Inc.)
    Version:  v1.27.0
    Path:     /usr/local/lib/docker/cli-plugins/docker-scout

Server:
 Containers: 7
  Running: 3
  Paused: 0
  Stopped: 4
 Images: 4
 Server Version: 29.9.2
 Storage Driver: overlayfs
  driver-type: io.containerd.snapshotter.v1
 Logging Driver: local
 Cgroup Driver: cgroupfs
 Cgroup Version: 2
 Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gcplogs gelf journald json-file local splunk syslog
 CDI spec directories:
  /etc/cdi
  /var/run/cdi
 Discovered Devices:
  cdi: docker.com/gpu=webgpu
 Swarm: inactive
 Runtimes: runc io.containerd.runc.v2 nvidia
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: b7a25261e029d68978bbf290df0a62fc819b3c51
 runc version: v1.5.2-0-g29dd3dc2
 init version: de40ad0
 Security Options:
  seccomp
   Profile: builtin
  cgroupns
 Kernel Version: 6.18.54.1-microsoft-standard-WSL2
 Operating System: Docker Desktop
 OSType: linux
 Architecture: x86_64
 CPUs: 16
 Total Memory: 15.18GiB
 Name: docker-desktop
 ID: 2ce103e4-2f13-40d9-950f-662d2d44b602
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 HTTP Proxy: http.docker.internal:3128
 HTTPS Proxy: http.docker.internal:3128
 No Proxy: hubproxy.docker.internal
 Labels:
  com.docker.desktop.address=unix:///var/run/docker-cli.sock
 Experimental: false
 Insecure Registries:
  hubproxy.docker.internal:5555
  127.0.0.0/8
  ::1/128
 Live Restore Enabled: false
 Firewall Backend: iptables
```

 *Docker daemon은 정상 실행(running) 중이며, Swarm 상태는 inactive이다.

### 6-2. Docker 이미지 확인

**수행 목적**

Docker 이미지를 다운로드하고 현재 보유한 이미지 목록을 확인한다.

**사용 명령어**

```bash
docker pull nginx:alpine
docker images
```

**실행 결과**

```text
ahy@DESKTOP-OO963F5:~$ docker pull nginx:alpine
docalpine: Pulling from library/nginx
b9b388a21ecf: Pull complete
9b0f7dfe35b2: Pull complete
12b85cff06fd: Pull complete
26185d08a3ec: Pull complete
7cc330898115: Pull complete
7b229517ed22: Pull complete
657023555a2a: Pull complete
2ec5fb117ffa: Pull complete
acc2d54c3743: Download complete
a4d5b1f57abc: Download complete
Digest: sha256:785835ea65db4bba6f021acc0f3be91b0fef76a53fe41f8588c6698d2aed0606
Status: Downloaded newer image for nginx:alpine
docker.io/library/nginx:alpine
ahy@DESKTOP-OO963F5:~$ docker images
                                                                                  i Info →   U  In Use
IMAGE                ID             DISK USAGE   CONTENT SIZE   EXTRA
hello-world:latest   c567b231f656       25.9kB         9.49kB    U
my-web:v1            985aa7ce8e0e        241MB         63.9MB
nginx:alpine         785835ea65db       94.5MB         27.2MB
nginx:latest         5ab5b0b01097        243MB         66.8MB
ubuntu:latest        6a06111c3b0a        163MB         45.9MB    U
```

### 6-3. Docker 컨테이너 상태 확인

**사용 목적**

실행 중인 컨테이너 및 종료된 컨테이너 목록을 확인한다.

**사용 명령어**

```bash
docker ps
docker ps -a
```

**실행 결과**

```text
ahy@DESKTOP-OO963F5:~$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
ahy@DESKTOP-OO963F5:~$ docker ps -a
CONTAINER ID   IMAGE         COMMAND    CREATED         STATUS                          PORTS     NAMES
8f66caa56b9d   ubuntu        "bash"     2 minutes ago   Exited (0) About a minute ago             blissful_grothendieck
68b248d3862a   hello-world   "/hello"   3 minutes ago   Exited (0) 3 minutes ago                  cranky_haibt
```

### 6-4. Docker 로그 및 리소스 확인

**사용 목적**

컨테이너의 실행 로그와 리소스 사용량을 확인한다.

**사용 명령어**

```bash
docker logs [컨테이너 이름]
docker stats --no-stream
```

**실행 결과**

```text
ahy@DESKTOP-OO963F5:~$ docker logs myubuntu
root@c2aee663817a:/# echo "this is myubuntu" > myfile.txt
root@c2aee663817a:/# cat myfile.txt
this is myubuntu
root@c2aee663817a:/# pwd
/
root@c2aee663817a:/# exit
exit
root@c2aee663817a:/# cat myfile.txt
this is myubuntu
root@c2aee663817a:/# exit
exit

ahy@DESKTOP-OO963F5:~$ stats --no-stream
Command 'stats' not found, did you mean:
  command 'statfs' from deb gocryptfs (2.6.1-1)
  command 'kstats' from deb aircrack-ng (1:1.7+git20230807.4bf83f1a-2ubuntu2)
  command 'stat' from deb coreutils-from-gnu (0.0.0~ubuntu25)
  command 'stat' from deb coreutils-from-uutils (0.0.0~ubuntu25)
  command 'stat' from deb coreutils-from-busybox (0.0.0~ubuntu25)
  command 'stat' from deb coreutils-from-toybox (0.0.0~ubuntu25)
  command 'states' from deb enscript (1.6.5.90-3.2build1)
  command 'sats' from deb mpdtoys (0.26-1build1)
Try: sudo apt install <deb name>
```

### 6-5. hello-world 컨테이너 실행

**사용 목적**

Docker가 정상적으로 이미지를 다운로드하고 컨테이너를 실행하는지 확인한다.

**사용 명령어**

```bash
docker run hello-world
```

**실행 결과**

```text
ahy@DESKTOP-OO963F5:~$ docker run hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```

 *hello-world 컨테이너 실행 결과
  -`docker run hello-world` 명령 실행 후 Docker가 `hello-world` 이미지를 Docker Hub에서 내려받고, 이를 기반으로 컨테이너를 생성·실행하여 안내 메시지를 정상적으로 출력하였다. 이를 통해 Docker 클라이언트와 Docker daemon 간 통신, 이미지 pull, 컨테이너 생성 및 실행 기능이 정상적으로 동작함을 확인하였다. 즉, 이미지는 변경되지 않는(불변) 실행 템플릿이고, 컨테이너는 그 이미지를 기반으로 실제 실행되며 상태 변화가 발생할 수 있는(가변) 실행 인스턴스이다.

### 6-6. Ubuntu 컨테이너 실행 및 내부 명령어 실습

**사용 목적**

Ubuntu 이미지를 이용해 컨테이너를 실행하고 컨테이너 내부에서 기본 Linux 명령어를 수행한다.

**사용 명령어**

```bash
docker run -it --name ubuntu-practice ubuntu bash
```

**컨테이너 내부 실행 명령어**

```bash
ls
echo "Docker container practice"
```

**실행 결과**

```text
ahy@DESKTOP-OO963F5:~$ docker run -it ubuntu bash
root@8f66caa56b9d:/# pwd
/
root@8f66caa56b9d:/# ls
bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
root@8f66caa56b9d:/# cat /etc/os-release
PRETTY_NAME="Ubuntu 26.04.1 LTS"
NAME="Ubuntu"
VERSION_ID="26.04"
VERSION="26.04.1 LTS (Resolute Raccoon)"
VERSION_CODENAME=resolute
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=resolute
LOGO=ubuntu-logo
root@8f66caa56b9d:/# echo "hello docker" > test.txt
root@8f66caa56b9d:/# cat test.txt
hello docker
```

**컨테이너 종료 및 유지 관찰**

- exit 실행 후 컨테이너 상태: [컨테이너는 종료되 docker ps -a 실행 시 컨테이너 목록 확인 가능]
- 실행 중인 컨테이너에서 exec 사용 결과: [메인 프로세스에 직접 영향을 미침]
- attach와 exec의 차이: [attach는 메인 프로세스에 직접 영향을 미침. exec는 메인 프로세스는 건드리지 않지만 컨테이너 내부 작업 결과는 남길 수 있음]

**Docker 기본 실습 로그**

- [Docker 설치 및 운영 로그](logs/docker-practice.txt)

---

## 7. Dockerfile 기반 커스텀 웹 서버 제작

### 7-1. 프로젝트 개요

기존 Docker 베이스 이미지를 활용하여 웹 서버를 구성하고, 사용자 정의 콘텐츠를 적용한 커스텀 이미지를 제작한다.

**선택한 방식**

- NGINX / Apache 등 웹 서버 베이스 이미지 활용

**선택한 베이스 이미지**

[nginx:alpine]

**커스텀 적용 내용**

| 커스텀 항목 | 적용 목적 |
|---|---|
| index.html | 기본 NGINX 시작 페이지 대신 직접 만든 웹 페이지를 표시하기 위해 |
| 웹 페이지 제목(My NGINX Web Server) 설정 | 브라우저 탭에서 페이지를 식별하기 쉽게 하기 위해 |
| 본문 내용(Hello Docker + NGINX!, 한글 안내 문구) 추가 | Docker와 NGINX를 활용한 커스텀 웹 서버임을 명확히 보여주기 위해
 |

### 7-2. 웹 서버 소스코드

**파일 위치**

```text
site/
 └── index.html
```


**index.html 실제 코드**

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>My NGINX Web Server</title>
</head>
<body>
  <h1>Hello Docker + NGINX!</h1>
  <p>내가 만든 커스텀 웹서버입니다.</p>
</body>
</html>
```

### 7-3. Dockerfile 작성

**파일 위치**

```text
Dockerfile
```

**실제 Dockerfile 내용**

```dockerfile
FROM nginx:alpine
COPY site/index.html /usr/share/nginx/html/index.html
```

 -웹 파일(`site/`)과 이미지 빌드 설정(`Dockerfile`)을 분리하여 관리 편의성을 높이고, 향후 정적 파일 추가 및 환경 확장에 유리하도록 디렉터리 구조를 구성하였다.

### 7-4. 커스텀 이미지 빌드

**수행 목적**

작성한 Dockerfile을 기반으로 사용자 정의 Docker 이미지를 생성한다.

**사용 명령어**

```bash
docker build -t my-nginx-web:v1 .
```

**실행 결과**

```text
[+] Building 3.3s (7/7) FINISHED                                                       docker:default
 => [internal] load build definition from Dockerfile                                             0.0s
 => => transferring dockerfile: 109B                                                             0.0s
 => [internal] load metadata for docker.io/library/nginx:alpine                                  2.1s
 => [internal] load .dockerignore                                                                0.0s
 => => transferring context: 2B                                                                  0.0s
 => [internal] load build context                                                                0.0s
 => => transferring context: 281B                                                                0.0s
 => CACHED [1/2] FROM docker.io/library/nginx:alpine@sha256:785835ea65db4bba6f021acc0f3be91b0fe  0.0s
 => => resolve docker.io/library/nginx:alpine@sha256:785835ea65db4bba6f021acc0f3be91b0fef76a53f  0.0s
 => [2/2] COPY site/index.html /usr/share/nginx/html/index.html                                  0.0s
 => exporting to image                                                                           1.0s
 => => exporting layers                                                                          0.1s
 => => exporting manifest sha256:f24cf0812afaf3dae7af529621577b0dbef69db208e5a6e59ad04931e9ddf5  0.0s
 => => exporting config sha256:7e36ceb50c8161e4c3331aabe16ef9bda69f9177029e8ca4c86f497d36d20a66  0.0s
 => => exporting attestation manifest sha256:d55eb222636f296df69f202499127ae28336c4ea24e1491ee0  0.0s
 => => exporting manifest list sha256:cc185ab54764e4026d332836b52a965311cae79628a8142670faaeeca  0.0s
 => => naming to docker.io/library/my-nginx-web:v1                                               0.0s
 => => unpacking to docker.io/library/my-nginx-web:v1    
```

### 7-5. 커스텀 컨테이너 실행

**사용 명령어**

```bash
docker run -d --name my-nginx-container -p 8081:80 my-nginx-web:v1
```

**실행 결과**

```text
6a41cb6773216cf6a6a764af9b393d0fc2b40102cf1a438d74854e806c60f662
```

**이미지 및 컨테이너 확인**

```bash
docker images
docker ps -a
```

**실행 결과**

```text
ahy@DESKTOP-OO963F5:~/my-web-project$ docker images
                                                                                  i Info →   U  In Use
IMAGE             ID             DISK USAGE   CONTENT SIZE   EXTRA
my-nginx-web:v1   cc185ab54764       93.6MB         26.3MB    U
ahy@DESKTOP-OO963F5:~/my-web-project$ docker ps -a
CONTAINER ID   IMAGE             COMMAND                  CREATED         STATUS         PORTS                                     NAMES
6a41cb677321   my-nginx-web:v1   "/docker-entrypoint.…"   9 minutes ago   Up 9 minutes   0.0.0.0:8081->80/tcp, [::]:8081->80/tcp   my-nginx-container
```

---

## 8. 포트 매핑 및 웹 서버 접속 검증

**재현 절차**

1. 커스텀 이미지 `my-nginx-web:v1`가 준비되어 있는지 확인한다.
2. 첫 번째 컨테이너를 실행하여 호스트 8082번 포트를 컨테이너 80번 포트에 매핑한다.
3. `curl` 명령으로 `http://localhost:8082` 접속 결과를 확인한다.
4. 두 번째 컨테이너를 실행하여 호스트 8083번 포트를 컨테이너 80번 포트에 매핑한다.
5. `curl` 명령으로 `http://localhost:8083` 접속 결과를 확인한다.
6. 브라우저에서 두 포트에 접속하여 화면이 정상 출력되는지 확인한다.

### 8-1. 포트 매핑 설정

**수행 목적**

호스트 컴퓨터의 포트와 Docker 컨테이너 내부의 포트를 연결하여 외부에서 웹 서버에 접근할 수 있도록 설정한다.

**실행 명령어**

```bash
docker run -d -p 8082:80 --name web-review1 my-nginx-web:v1
```

**실행 결과**

```text
6d98317c4b88989d38c930792fed56b71afcbaf38c08ea3f697a552017fa884c
```

 -컨테이너가 백그라운드에서 실행되었으며, 호스트의 8082번 포트가 컨테이너의 80번 포트와 연결되도록 설정되었다.
 -Docker 컨테이너는 네트워크 네임스페이스(network namespace)를 통해 서로 독립된 네트워크 환경에서 동작한다. 각 컨테이너는 자체적인 IP 주소, 포트, 네트워크 인터페이스를 가지므로 다른 컨테이너 및 호스트와 분리된다. 이러한 구조는 포트 충돌을 방지하고 서비스 간 격리와 보안성을 높이는 데 필요하다. 그러나 분리된 환경에서는 컨테이너 내부 서비스에 호스트가 직접 접근할 수 없으므로 포트 포워딩이 필요하다. 예를 들어 `-p 8082:80` 옵션을 사용하면 호스트의 8082번 포트 요청이 컨테이너의 80번 포트로 전달된다. 따라서 네트워크 네임스페이스는 격리를 위해, 포트 포워딩은 호스트와 컨테이너 간 통신을 위해 필요하다.


### 8-2. 웹 서버 접속 확인

**접속 주소**

```text
http://localhost:8082
```

**curl 검증 명령어**

```bash
curl http://localhost:8082
```

**실행 결과**

```text
ahy@DESKTOP-OO963F5:~/docker-web$ curl http://localhost:8082
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>My NGINX Web Server</title>
</head>
<body>
  <h1>Hello Docker + NGINX!</h1>
  <p>내가 만든 커스텀 웹서버입니다.</p>
</body>
</html>
```



### 8-3. 포트 변경 후 추가 접속 확인

**두 번째 실행 명령어**

```bash
docker run -d -p 8083:80 --name web-review2 my-nginx-web:v1
```

**접속 확인**

```bash
curl http://localhost:8083
```

**실행 결과**

```text
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>My NGINX Web Server</title>
</head>
<body>
  <h1>Hello Docker + NGINX!</h1>
  <p>내가 만든 커스텀 웹서버입니다.</p>
</body>
</html>
```

### 8-4. 브라우저 접속 증거

첫 번째 접속 화면:

<img width="802" height="306" alt="8082" src="https://github.com/user-attachments/assets/5306fd7a-87b5-491a-b4a1-73287d78c856" />

두 번째 접속 화면:

<img width="814" height="340" alt="8083" src="https://github.com/user-attachments/assets/c5d1a067-7302-45e0-a1a1-1c5556044de6" />

---

## 9. 바인드 마운트 변경 반영 검증

### 9-1. 바인드 마운트 설정

**수행 목적**

호스트 컴퓨터의 폴더와 컨테이너 내부 디렉터리를 연결하여 호스트에서 수정한 파일이 컨테이너에 반영되는지 확인한다.

**실행 명령어**

```bash
docker run -d --name web-bind -p 8084:80 -v $(pwd)/site:/usr/share/nginx/html nginx:alpine
```

**실행 결과**

```text
ahy@DESKTOP-OO963F5:~/docker-web$ docker run -d --name web-bind -p 8084:80 -v $(pwd)/site:/usr/share/nginx/html nginx:alpine
Unable to find image 'nginx:alpine' locally
alpine: Pulling from library/nginx
Digest: sha256:785835ea65db4bba6f021acc0f3be91b0fef76a53fe41f8588c6698d2aed0606
Status: Downloaded newer image for nginx:alpine
91c5c59178755ebf968c16412189ad69bf604c10af0a7e29e7ec7ec23509520e
```

### 9-2. 변경 전 파일 내용

**호스트 파일 내용 확인**

```bash
cat ~/docker-web/site/index.html
```

**실행 결과**

```text
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>My NGINX Web Server</title>
</head>
<body>
  <h1>Hello Docker + NGINX!</h1>
  <p>내가 만든 커스텀 웹서버입니다.</p>
</body>
</html>
```

### 9-3. 호스트 파일 수정

**파일 수정 방법 및 명령어**

```bash
nano ~/docker-web/site/index.html
```

**변경 후 내용**

```text
ahy@DESKTOP-OO963F5:~/docker-web$ cat ~/docker-web/site/index.html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>My NGINX Web Server</title>
</head>
<body>
  <h1>Hello Docker + NGINX!</h1>
  <p>바인드 마운트 수정 반영 테스트입니다.</p>
</body>
</html<!DOCTYPE html>
<html>
```

### 9-4. 컨테이너 반영 여부 확인

**검증 명령어**

```bash
docker exec web-bind cat /usr/share/nginx/html/index.html
```

**실행 결과**

```text
ahy@DESKTOP-OO963F5:~/docker-web$ docker exec web-bind cat /usr/share/nginx/html/index.html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>My NGINX Web Server</title>
</head>
<body>
  <h1>Hello Docker + NGINX!</h1>
  <p>바인드 마운트 수정 반영 테스트입니다.</p>
</body>
</html<!DOCTYPE html>
<html>
```

**검증 결과**

호스트의 ~/docker-web/site/index.html 파일을 수정한 후, 컨테이너 내부의 /usr/share/nginx/html/index.html 파일 내용도 동일하게 변경된 것을 확인하였다. 또한 브라우저 및 curl 명령어를 통해 localhost:8084 접속 시 수정된 내용이 즉시 반영되는 것을 확인하였다. 이를 통해 바인드 마운트를 사용하면 호스트 파일 변경 사항이 컨테이너에 실시간으로 반영됨을 검증하였다.

**증거 자료**

<img width="822" height="306" alt="8084-1" src="https://github.com/user-attachments/assets/fb55b714-ed9d-4c6b-a3a9-d0bacdc81a5e" />
<img width="836" height="332" alt="8084" src="https://github.com/user-attachments/assets/ebee33cc-9610-4aec-846f-b96a8e393f9c" />


---

## 10. Docker 볼륨 영속성 검증

### 10-1. Docker 볼륨 생성

**수행 목적**

컨테이너가 삭제되더라도 데이터를 유지할 수 있도록 별도의 Docker 볼륨을 생성한다.

**사용 명령어**

```bash
docker volume create [볼륨명]
docker volume ls
```

**실행 결과**

```text
ahy@DESKTOP-OO963F5:~/docker-web$ docker volume create mydata-vol
mydata-vol
ahy@DESKTOP-OO963F5:~/docker-web$ docker volume ls
DRIVER    VOLUME NAME
local     my-data-volume
local     mydata-vol
```

### 10-2. 볼륨 연결 및 데이터 저장

**사용 명령어**

```bash
docker run -d --name vol-test1 -v mydata-vol:/data ubuntu sleep infinity
```

데이터 생성 및 확인:

```bash
docker exec -it vol-test1 bash -lc "echo 'Docker volume persistence test' > /data/hello.txt && cat /data/hello.txt"
```

**실행 결과**

```text
ahy@DESKTOP-OO963F5:~/docker-web$ docker run -d --name vol-test1 -v mydata-vol:/data ubuntu sleep infinity
Unable to find image 'ubuntu:latest' locally
latest: Pulling from library/ubuntu
f3f25b84a7d7: Pull complete
edafa32f5d9e: Pull complete
21594acc2d8b: Download complete
Digest: sha256:6a06111c3b0a8600feadb270aec771dc239bf407b25625f93f44ab00e11f4d3c
Status: Downloaded newer image for ubuntu:latest
511339c9a673e468bfe90b21e51c2869b284431a5579869f465f7417c9d803df
ahy@DESKTOP-OO963F5:~/docker-web$ docker exec -it vol-test1 bash -lc "echo 'Docker volume persistence test' > /data/hello.txt && cat /data/hello.txt"
Docker volume persistence test
```

### 10-3. 첫 번째 컨테이너 삭제

**사용 명령어**

```bash
docker rm -f docker rm -f vol-test1
```

**실행 결과**

```text
ahy@DESKTOP-OO963F5:~/docker-web$ docker rm -f vol-test1
vol-test1
```

### 10-4. 새 컨테이너에서 데이터 확인

**사용 명령어**

```bash
docker run -d --name [두 번째 컨테이너명] -v [동일한 볼륨명]:/data ubuntu sleep infinity
```

이전 데이터 확인:

```bash
docker exec -it vol-test2 bash -lc "cat /data/hello.txt"
```

**실행 결과**

```text
ahy@DESKTOP-OO963F5:~/docker-web$ docker exec -it vol-test2 bash -lc "cat /data/hello.txt"
Docker volume persistence test
```

### 10-5. 영속성 검증 결과

- 첫 번째 컨테이너에서 저장한 데이터: Docker volume persistence test
- 첫 번째 컨테이너 삭제 여부: docker rm -f vol-test1 명령으로 삭제 완료
- 두 번째 컨테이너 연결 여부: mydata-vol 볼륨을 연결한 vol-test2 컨테이너 실행 완료
- 데이터 유지 여부: 유지됨. vol-test2에서 /data/hello.txt 내용을 확인했을 때 동일한 데이터가 출력됨

**증거 자료** 

<img width="598" height="118" alt="image" src="https://github.com/user-attachments/assets/6b57f7f7-f440-4632-915f-714d8bb7f512" />

<img width="940" height="250" alt="image" src="https://github.com/user-attachments/assets/b6ebe2c7-8420-4b01-89b4-f348cb3c659e" />

<img width="928" height="130" alt="image" src="https://github.com/user-attachments/assets/5a0152fe-bb32-4111-b154-4961091dba4e" />

---

## 11. Git 설정 및 GitHub 연동

### 11-1. Git 버전 확인

**사용 명령어**

```bash
git --version
```

**실행 결과**

```text
ahy@DESKTOP-OO963F5:~/docker-web$ git --version
git version 2.53.0
```

### 11-2. Git 사용자 정보 및 기본 브랜치 설정

**사용 명령어**

```bash
git config --global user.name "anahayoung-cpu"
git config --global user.email "a*****ng@gmail.com"
git config --global init.defaultBranch main
```

**설정 확인**

```bash
git config --list
```

**실행 결과**

```text
ahy@DESKTOP-OO963F5:~/docker-web$ git config --global user.name "anahayoung-cpu"
ahy@DESKTOP-OO963F5:~/docker-web$ git config --global user.email "a*****ng@gmail.com"
ahy@DESKTOP-OO963F5:~/docker-web$ git config --global init.defaultBranch main
ahy@DESKTOP-OO963F5:~/docker-web$ git config --list
user.email=a*****ng@gmail.com
user.name=anahayoung-cpu
init.defaultbranch=main
core.repositoryformatversion=0
core.filemode=true
core.bare=false
core.logallrefupdates=true
remote.origin.url=https://github.com/anahayoung-cpu/test3-1.git
remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*
branch.main.remote=origin
branch.main.merge=refs/heads/main
```

### 11-3. Git 로컬 저장소 생성

**사용 명령어**

```bash
git init
git status
```

**실행 결과**

```text
ahy@DESKTOP-OO963F5:~/docker-web$ git init
Reinitialized existing Git repository in /home/ahy/docker-web/.git/
ahy@DESKTOP-OO963F5:~/docker-web$ git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

### 11-4. 변경 파일 등록 및 커밋

**사용 명령어**

```bash
git add .
git commit -m "Initial project setup"
git status
```

**실행 결과**

```text
ahy@DESKTOP-OO963F5:~/docker-web$ git add .
ahy@DESKTOP-OO963F5:~/docker-web$ git commit -m "Initial project setup"
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
ahy@DESKTOP-OO963F5:~/docker-web$ git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```
 * 현재 프로젝트는 이미 Git 저장소로 초기화되어 있었으며, git status 확인 결과 working tree clean 상태임.
   즉, 모든 파일이 이미 커밋되어 있어 추가 커밋할 변경사항은 없음.
   

### 11-5. GitHub 원격 저장소 연결

**GitHub Repository**

[실제 GitHub 저장소 주소 입력]

**사용 명령어**

```bash
git branch -M main
git remote add origin [GitHub Repository 주소]
git push -u origin main
```

**실행 결과**

```text
ahy@DESKTOP-OO963F5:~/docker-web$ git remote -v
origin  https://github.com/anahayoung-cpu/test3-1.git (fetch)
origin  https://github.com/anahayoung-cpu/test3-1.git (push)
ahy@DESKTOP-OO963F5:~/docker-web$ git branch -vv
* main effc9c8 [origin/main] Merge branch 'main' of https://github.com/anahayoung-cpu/test3-1
```

 * 현재 연결된 상태로 저장소 및 브랜치 추적 상태 확인용으로 실행.

   
### 11-6. VS Code 및 GitHub 연동 확인

**수행 내용**

- VS Code에서 GitHub 로그인
- 프로젝트 폴더 열기
- Git 저장소 연결 상태 확인
- 원격 저장소와 로컬 프로젝트 연동 확인

**증거 자료**

<img width="922" height="872" alt="image" src="https://github.com/user-attachments/assets/d3c96afd-d670-4ab6-ad38-4dbe4a4d512a" />
<img width="386" height="584" alt="image" src="https://github.com/user-attachments/assets/971d0b81-ffe7-4139-ab61-9da024c14d5e" />
<img width="848" height="96" alt="image" src="https://github.com/user-attachments/assets/3c6ed86d-9b54-4f36-a9d1-cfa6d6385687" />




---

## 12. 트러블슈팅

실습 과정에서 발생한 문제와 해결 방법을 기록한다.

### 12-1. 문제 사례 1

**문제 상황**

Docker 컨테이너를 실행하면서 8081 포트를 사용하려고 했는데, 컨테이너가 정상적으로 실행되지 않거나 같은 포트를 사용하는 과정에서 충돌이 발생하였다.

**원인 가설**

이미 실행 중인 다른 컨테이너가 8081 포트를 사용하고 있어서 포트 바인딩 충돌이 발생한 것으로 추정하였다.

**확인 과정**

```bash
docker run -d --name my-nginx-container -p 8081:80 my-nginx-web:v1
docker ps
sudo ss -ltnp | grep 8081
```

**확인 결과**

```text
Error response from daemon: driver failed programming external connectivity on endpoint ...
Bind for 0.0.0.0:8081 failed: port is already allocated
```

**해결 방법**

```bash
docker stop my-nginx-container
docker rm my-nginx-container
docker run -d --name my-nginx-container -p 8082:80 my-nginx-web:v1
```

 -해당 포트를 사용 중인 컨테이너가 있다면 `docker stop my-nginx-container` 명령으로 중지한 뒤, `docker rm my-nginx-container` 명령으로 삭제하고 충돌을 피하기 위해 다른 포트 번호로 변경하여 다시 실행하였다.

**최종 결과**

포트 충돌 문제를 해결한 후 컨테이너가 정상 실행되었고, 브라우저에서 http://localhost:8082 변경한 포트 번호로 접속하여 웹 페이지가 정상적으로 출력되는 것을 확인하였다.

### 12-2. 문제 사례 2

**문제 상황**

바인드 마운트 실습에서 호스트의 site 폴더를 컨테이너에 연결한 후, 파일 수정이 제대로 반영되지 않거나 권한 관련 문제가 발생하였다.

**원인 가설**

호스트 디렉터리의 소유자 또는 권한 설정이 현재 사용자와 맞지 않아, 파일 접근 또는 수정에 문제가 생긴 것으로 추정하였다.

**확인 과정**

```bash
ls -la
```

**확인 결과**

```text
ahy@DESKTOP-OO963F5:~/docker-web$ ls -la ~/docker-web/site
total 8
drwxr-xr-x 2 root root 4096 Nov  4 23:21 .
```

 -확인 결과 site 디렉터리의 소유자가 root:root로 설정되어 있어, 현재 사용자가 자유롭게 수정하기 어려운 상태임을 확인하였다.

**해결 방법**

```bash
ahy@DESKTOP-OO963F5:~/docker-web$ mkdir -p ~/docker-web/site
ahy@DESKTOP-OO963F5:~/docker-web$ nano ~/docker-web/site/index.html
ahy@DESKTOP-OO963F5:~/docker-web$ ls -ld ~/docker-web/site
drwxr-xr-x 2 root root 4096 Nov  4 23:21 /home/ahy/docker-web/site
ahy@DESKTOP-OO963F5:~/docker-web$ ls -l ~/docker-web/site
total 0
ahy@DESKTOP-OO963F5:~/docker-web$ sudo chown -R $USER:$USER ~/docker-web/site
[sudo: authenticate] Password:
ahy@DESKTOP-OO963F5:~/docker-web$ ls -ld ~/docker-web/site
**drwxr-xr-x 2 ahy ahy 4096 Nov  4 23:21 /home/ahy/docker-web/site**
```

**최종 결과**

권한 문제를 해결한 후 site 폴더의 파일을 수정하면 컨테이너 내부 웹 페이지에도 정상적으로 반영되었고, 브라우저에서 변경 사항을 확인할 수 있었다.


---

## 13. 최종 수행 결과

본 프로젝트를 통해 개발 환경 구축에 필요한 터미널 및 Linux CLI 기본 명령어, 파일 권한 관리, Docker 이미지 및 컨테이너 운영, Dockerfile 기반 웹 서버 구축, 포트 매핑 및 데이터 영속성의 개념을 실습하였다.

또한 Git과 GitHub를 이용하여 소스코드 및 작업 이력을 관리하고, 프로젝트 실행 과정과 검증 결과를 기술 문서로 정리하였다.
