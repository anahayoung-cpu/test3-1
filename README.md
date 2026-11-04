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
| 작업 환경 | [실제 사용한 터미널 및 편집기 입력] |

### 2-2. Linux 환경

| 항목 | 실행 환경 |
|---|---|
| Host OS | Windows 10 Pro 22H2 |
| Linux 실행 환경 | WSL2 |
| Linux 배포판 | Ubuntu [버전 입력] |
| Shell | Bash |
| Terminal | Windows Terminal / Ubuntu Terminal |

### 2-3. Docker 환경

| 항목 | 실행 환경 |
|---|---|
| Docker 실행 환경 | [Docker Desktop 등 실제 환경 입력] |
| Docker Client Version | [버전 입력] |
| Docker Server Version | [버전 입력] |
| Docker Engine | [확인된 정보 입력] |

**Docker 버전 확인 명령어**

```powershell
docker --version
```

**실행 결과**

```text
[실제 실행 결과 붙여넣기]
```

### 2-4. Git 환경

| 항목 | 실행 환경 |
|---|---|
| Git Version | [버전 입력] |
| 코드 편집기 | Visual Studio Code |
| 원격 저장소 | GitHub |
| 기본 브랜치 | main |

**Git 버전 확인 명령어**

```powershell
git --version
```

**실행 결과**

```text
[실제 실행 결과 붙여넣기]
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
- [ ] Linux CLI 기본 명령어
- [ ] 절대 경로 및 상대 경로 확인
- [ ] 파일 권한 확인 및 변경
- [ ] 디렉터리 권한 확인 및 변경

### 3-2. Docker

- [ ] Docker 설치 및 기본 점검
- [ ] Docker 이미지 다운로드 및 목록 확인
- [ ] hello-world 실행
- [ ] Ubuntu 컨테이너 실행
- [ ] 컨테이너 실행 및 종료 실습
- [ ] Docker 로그 확인
- [ ] Docker 리소스 사용량 확인

### 3-3. Dockerfile 및 웹 서버

- [ ] 웹 서버 소스코드 작성
- [ ] Dockerfile 직접 작성
- [ ] 커스텀 이미지 빌드
- [ ] 커스텀 컨테이너 실행
- [ ] 포트 매핑 설정
- [ ] 브라우저 또는 curl 접속 확인
- [ ] 서로 다른 호스트 포트로 2회 실행 및 접속 확인

### 3-4. 데이터 관리

- [ ] 바인드 마운트 설정
- [ ] 호스트 파일 변경 전후 비교
- [ ] Docker 볼륨 생성
- [ ] 컨테이너와 볼륨 연결
- [ ] 컨테이너 삭제 전 데이터 확인
- [ ] 새 컨테이너에서 데이터 유지 여부 확인

### 3-5. Git 및 GitHub

- [ ] Git 사용자 정보 설정
- [ ] Git 기본 브랜치 설정
- [ ] Git 설정 확인
- [ ] VS Code GitHub 로그인
- [ ] GitHub Repository 생성
- [ ] 로컬 프로젝트와 원격 저장소 연결
- [ ] 프로젝트 업로드 및 확인

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

- 644: 소유자는 읽기 및 쓰기, 그룹과 기타 사용자는 읽기 가능
- 755: 소유자는 읽기, 쓰기, 실행 가능. 그룹과 기타 사용자는 읽기 및 실행 가능

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
[실제 실행 결과 붙여넣기]
```

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
[실제 실행 결과 붙여넣기]
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
[실제 실행 결과 붙여넣기]
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
[실제 실행 결과 붙여넣기]
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
[실제 실행 결과 붙여넣기]
```

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
[실제 실행 결과 붙여넣기]
```

**컨테이너 종료 및 유지 관찰**

- exit 실행 후 컨테이너 상태: [관찰 결과 입력]
- 실행 중인 컨테이너에서 exec 사용 결과: [관찰 결과 입력]
- attach와 exec의 차이: [직접 관찰한 내용 입력]

**Docker 기본 실습 로그**

- [Docker 설치 및 운영 로그](logs/docker-practice.txt)

---

## 7. Dockerfile 기반 커스텀 웹 서버 제작

### 7-1. 프로젝트 개요

기존 Docker 베이스 이미지를 활용하여 웹 서버를 구성하고, 사용자 정의 콘텐츠를 적용한 커스텀 이미지를 제작한다.

**선택한 방식**

- [ ] A. NGINX / Apache 등 웹 서버 베이스 이미지 활용
- [ ] B. Ubuntu / Alpine 등 Linux 베이스 이미지 활용

**선택한 베이스 이미지**

[실제로 사용한 이미지 이름 및 버전 입력]

**커스텀 적용 내용**

| 커스텀 항목 | 적용 목적 |
|---|---|
| [항목 1] | [적용 이유] |
| [항목 2] | [적용 이유] |
| [항목 3] | [적용 이유] |

### 7-2. 웹 서버 소스코드

**파일 위치**

```text
site/
 └── index.html
```

**index.html 실제 코드**

```html
[실제 작성한 HTML 코드 붙여넣기]
```

### 7-3. Dockerfile 작성

**파일 위치**

```text
Dockerfile
```

**실제 Dockerfile 내용**

```dockerfile
[직접 작성한 Dockerfile 전체 내용 붙여넣기]
```

### 7-4. 커스텀 이미지 빌드

**수행 목적**

작성한 Dockerfile을 기반으로 사용자 정의 Docker 이미지를 생성한다.

**사용 명령어**

```bash
docker build -t [이미지명]:[태그] .
```

**실행 결과**

```text
[실제 빌드 결과 붙여넣기]
```

### 7-5. 커스텀 컨테이너 실행

**사용 명령어**

```bash
docker run -d --name [컨테이너명] -p [호스트포트]:[컨테이너포트] [이미지명]:[태그]
```

**실행 결과**

```text
[실제 실행 결과 붙여넣기]
```

**이미지 및 컨테이너 확인**

```bash
docker images
docker ps -a
```

**실행 결과**

```text
[실제 실행 결과 붙여넣기]
```

---

## 8. 포트 매핑 및 웹 서버 접속 검증

### 8-1. 포트 매핑 설정

**수행 목적**

호스트 컴퓨터의 포트와 Docker 컨테이너 내부의 포트를 연결하여 외부에서 웹 서버에 접근할 수 있도록 설정한다.

**실행 명령어**

```bash
docker run -d -p [호스트포트]:[컨테이너포트] --name [컨테이너명] [이미지명]:[태그]
```

**실행 결과**

```text
[실제 실행 결과 붙여넣기]
```

### 8-2. 웹 서버 접속 확인

**접속 주소**

```text
http://localhost:[호스트포트]
```

**curl 검증 명령어**

```bash
curl http://localhost:[호스트포트]
```

**실행 결과**

```text
[실제 웹 서버 응답 붙여넣기]
```

### 8-3. 포트 변경 후 추가 접속 확인

**두 번째 실행 명령어**

```bash
docker run -d -p [두 번째 호스트포트]:[컨테이너포트] --name [두 번째 컨테이너명] [이미지명]:[태그]
```

**접속 확인**

```bash
curl http://localhost:[두 번째 호스트포트]
```

**실행 결과**

```text
[실제 실행 결과 붙여넣기]
```

### 8-4. 브라우저 접속 증거

첫 번째 접속 화면:

![첫 번째 웹 서버 접속 화면](screenshots/web-browser-1.png)

두 번째 접속 화면:

![두 번째 웹 서버 접속 화면](screenshots/web-browser-2.png)

※ 실제 스크린샷을 screenshots 폴더에 저장한 뒤 파일명을 일치시킨다.

---

## 9. 바인드 마운트 변경 반영 검증

### 9-1. 바인드 마운트 설정

**수행 목적**

호스트 컴퓨터의 폴더와 컨테이너 내부 디렉터리를 연결하여 호스트에서 수정한 파일이 컨테이너에 반영되는지 확인한다.

**실행 명령어**

```bash
[실제로 사용한 docker run 명령어 붙여넣기]
```

**실행 결과**

```text
[실제 실행 결과 붙여넣기]
```

### 9-2. 변경 전 파일 내용

**호스트 파일 내용 확인**

```bash
[실제로 사용한 파일 확인 명령어]
```

**실행 결과**

```text
[변경 전 내용 붙여넣기]
```

### 9-3. 호스트 파일 수정

**파일 수정 방법 및 명령어**

```bash
[실제로 사용한 수정 명령어]
```

**변경 후 내용**

```text
[변경 후 내용 붙여넣기]
```

### 9-4. 컨테이너 반영 여부 확인

**검증 명령어**

```bash
[실제로 사용한 컨테이너 내부 확인 명령어]
```

**실행 결과**

```text
[변경된 내용이 반영된 결과 붙여넣기]
```

**검증 결과**

[호스트 파일을 수정한 결과 컨테이너 내부 또는 웹 브라우저에 어떻게 반영되었는지 설명]

**증거 자료**

![바인드 마운트 변경 전후 비교](screenshots/bind-mount.png)

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
[실제 실행 결과 붙여넣기]
```

### 10-2. 볼륨 연결 및 데이터 저장

**사용 명령어**

```bash
docker run -d --name [첫 번째 컨테이너명] -v [볼륨명]:/data ubuntu sleep infinity
```

데이터 생성 및 확인:

```bash
docker exec -it [첫 번째 컨테이너명] bash -lc "echo '[저장할 내용]' > /data/hello.txt && cat /data/hello.txt"
```

**실행 결과**

```text
[실제 저장 내용 및 출력 결과 붙여넣기]
```

### 10-3. 첫 번째 컨테이너 삭제

**사용 명령어**

```bash
docker rm -f [첫 번째 컨테이너명]
```

**실행 결과**

```text
[실제 실행 결과 붙여넣기]
```

### 10-4. 새 컨테이너에서 데이터 확인

**사용 명령어**

```bash
docker run -d --name [두 번째 컨테이너명] -v [동일한 볼륨명]:/data ubuntu sleep infinity
```

이전 데이터 확인:

```bash
docker exec -it [두 번째 컨테이너명] bash -lc "cat /data/hello.txt"
```

**실행 결과**

```text
[이전 데이터가 확인된 실제 결과 붙여넣기]
```

### 10-5. 영속성 검증 결과

- 첫 번째 컨테이너에서 저장한 데이터: [내용 입력]
- 첫 번째 컨테이너 삭제 여부: [결과 입력]
- 두 번째 컨테이너 연결 여부: [결과 입력]
- 데이터 유지 여부: [확인 결과 입력]

**증거 자료**

![Docker 볼륨 영속성 검증](screenshots/docker-volume.png)

---

## 11. Git 설정 및 GitHub 연동

### 11-1. Git 버전 확인

**사용 명령어**

```bash
git --version
```

**실행 결과**

```text
[실제 실행 결과 붙여넣기]
```

### 11-2. Git 사용자 정보 및 기본 브랜치 설정

**사용 명령어**

```bash
git config --global user.name "[설정한 사용자 이름]"
git config --global user.email "[설정한 이메일]"
git config --global init.defaultBranch main
```

**설정 확인**

```bash
git config --list
```

**실행 결과**

```text
[민감정보를 제거하거나 마스킹한 실제 결과 붙여넣기]
```

### 11-3. Git 로컬 저장소 생성

**사용 명령어**

```bash
git init
git status
```

**실행 결과**

```text
[실제 실행 결과 붙여넣기]
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
[실제 실행 결과 붙여넣기]
```

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
[실제 실행 결과 붙여넣기]
```

### 11-6. VS Code 및 GitHub 연동 확인

**수행 내용**

- VS Code에서 GitHub 로그인
- 프로젝트 폴더 열기
- Git 저장소 연결 상태 확인
- 원격 저장소와 로컬 프로젝트 연동 확인

**증거 자료**

![VS Code GitHub 연동 화면](screenshots/github-vscode.png)

---

## 12. 트러블슈팅

실습 과정에서 발생한 문제와 해결 방법을 기록한다.

### 12-1. 문제 사례 1

**문제 상황**

[어떤 명령어를 실행했을 때 어떤 문제가 발생했는지 작성]

**원인 가설**

[문제가 발생한 원인으로 추정한 내용]

**확인 과정**

```bash
[문제 확인에 사용한 명령어]
```

**확인 결과**

```text
[실제 오류 메시지 또는 결과]
```

**해결 방법**

```bash
[수정한 명령어 또는 해결 방법]
```

**최종 결과**

[문제가 해결되었는지 작성]

### 12-2. 문제 사례 2

**문제 상황**

[문제 상황 작성]

**원인 가설**

[원인으로 추정한 내용]

**확인 과정**

```bash
[문제 확인에 사용한 명령어]
```

**확인 결과**

```text
[실제 오류 메시지 또는 결과]
```

**해결 방법**

```bash
[수정한 명령어 또는 해결 방법]
```

**최종 결과**

[문제 해결 결과 작성]

### 12-3. 추가 문제 사례 (선택)

**문제 상황**

[문제 상황 작성]

**원인 및 해결 방법**

[실제 수행 내용 작성]

---

## 13. 결과물 및 증빙 자료 위치

| 구분 | 파일 및 폴더 | 설명 |
|---|---|---|
| 기술 문서 | README.md | 프로젝트 전체 수행 내용 |
| 터미널 로그 | logs/ | PowerShell 및 Linux 실행 기록 |
| Docker 로그 | logs/ | Docker 설치 및 운영 기록 |
| 웹 소스코드 | site/ | 웹 서버 콘텐츠 |
| Docker 설정 | Dockerfile | 커스텀 이미지 빌드 설정 |
| 스크린샷 | screenshots/ | 포트 접속 및 데이터 검증 증거 |

### 주요 증빙 자료

- [PowerShell 실습 로그](logs/powershell-practice.txt)
- [Linux 실습 로그](logs/linux-practice.txt)
- [Docker 실습 로그](logs/docker-practice.txt)
- [Git 실습 로그](logs/git-practice.txt)

---

## 14. 최종 수행 결과

본 프로젝트를 통해 개발 환경 구축에 필요한 터미널 및 Linux CLI 기본 명령어, 파일 권한 관리, Docker 이미지 및 컨테이너 운영, Dockerfile 기반 웹 서버 구축, 포트 매핑 및 데이터 영속성의 개념을 실습하였다.

또한 Git과 GitHub를 이용하여 소스코드 및 작업 이력을 관리하고, 프로젝트 실행 과정과 검증 결과를 기술 문서로 정리하였다.

**GitHub Repository**

[최종 GitHub 저장소 링크 입력]
