# 개발 워크스테이션 구축 미션

## 1. 프로젝트 개요

### 1-1. 프로젝트 목적

Linux CLI, Docker, Git/GitHub 등 개발 환경 구축에 필요한 기본 도구를 익히고, 직접 개발 워크스테이션을 구성하는 것을 목표로 한다. 실습 결과와 실행 기록을 README에 정리하여 작업 과정과 결과를 재현할 수 있도록 한다.

### 1-2. 주요 수행 내용

- Windows PowerShell 및 Linux CLI 기본 명령어 실습
- Linux 파일 및 디렉터리 권한 관리
- Docker 이미지·컨테이너 실행 및 관리
- Dockerfile 기반 커스텀 웹 서버 제작
- 포트 매핑 및 웹 서버 접속 검증
- 바인드 마운트 및 Docker 볼륨 영속성 검증
- Git/GitHub 연동 및 프로젝트 관리

---

## 2. 실행 환경

| 구분 | 실행 환경 |
|---|---|
| OS | Windows 11 |
| Linux | WSL2 (Ubuntu 26.04.1 LTS) |
| Shell | Windows PowerShell 5.1 / Bash |
| Docker | Docker Desktop 29.9.2 |
| Git (WSL) | 2.53.0 |


**Doker 환경 버전 확인**

```powershell
PS C:\WINDOWS\System32> docker --version
Docker version 29.9.2, build a82e528
```

**Git 환경 버전 확인**

```text
ahy@DESKTOP-OO963F5:~/docker-web$ git --version
git version 2.53.0
```

---

## 3. 수행 항목 체크리스트

### 3-1. Linux CLI

- [x] 파일 및 폴더 목록 확인
- [x] 숨김 파일 및 폴더 확인
- [x] 디렉터리 이동 및 생성
- [x] 빈 파일 생성
- [x] 파일 내용 입력 및 확인
- [x] 파일 복사
- [ ] 파일 이동 및 이름 변경 (실행 로그 추가 필요)
- [x] 파일 삭제
- [x] 절대 경로 및 상대 경로 확인
- [x] 파일 권한 확인 및 변경
- [x] 디렉터리 권한 확인 및 변경

### 3-2. Docker

- [x] Docker 설치 및 기본 점검
- [x] Docker 이미지 다운로드 및 목록 확인
- [x] hello-world 실행
- [x] Ubuntu 컨테이너 실행
- [x] 컨테이너 실행 및 종료 상태 확인
- [x] Docker 로그 확인
- [ ] Docker 리소스 사용량 확인 (명령어 재실행 및 결과 추가 필요)

### 3-3. Dockerfile 및 웹 서버

- [x] 웹 서버 소스코드 작성
- [x] Dockerfile 작성
- [x] 커스텀 이미지 빌드
- [x] 커스텀 컨테이너 실행
- [x] 포트 매핑 설정
- [x] curl 및 브라우저 접속 확인
- [x] 서로 다른 호스트 포트로 2회 실행 및 접속 확인

### 3-4. 데이터 관리

- [x] 바인드 마운트 설정
- [x] 호스트 파일 변경 전후 비교
- [x] Docker 볼륨 생성
- [x] 컨테이너와 볼륨 연결
- [x] 컨테이너 삭제 후 데이터 확인
- [x] 새 컨테이너에서 볼륨 데이터 유지 여부 확인

### 3-5. Git 및 GitHub

- [x] Git 사용자 정보 설정
- [x] Git 기본 브랜치 설정
- [x] Git 설정 확인
- [x] VS Code GitHub 로그인
- [x] GitHub Repository 생성
- [x] 로컬 프로젝트와 원격 저장소 연결 상태 확인
- [x] 원격 저장소 및 브랜치 추적 상태 확인

---

## 4. Linux CLI 실습

### 4-1. Linux 실행 환경 및 파일 목록 확인

**실행 명령어 및 결과**

```text
donghwan@localhost:~$ pwd
/home/donghwan

donghwan@localhost:~$ cat /etc/os-release
PRETTY_NAME="Ubuntu 26.04.1 LTS"
NAME="Ubuntu"
VERSION_ID="26.04"
VERSION="26.04.1 LTS (Resolute Raccoon)"

donghwan@localhost:~$ ls -la
total 32
drwxr-x--- 4 donghwan donghwan 4096 Nov  4 15:21 .
drwxr-xr-x 3 root     root     4096 Nov  3 14:55 ..
-rw-r--r-- 1 donghwan donghwan 3771 Nov  3 14:55 .bashrc
-rw-r--r-- 1 donghwan donghwan  807 Nov  3 14:55 .profile
```

`ls -la`로 숨김 파일을 포함한 목록과 파일 권한을 확인하였다.

### 4-2. 파일 및 디렉터리 생성·복사·삭제

**실행 명령어 및 결과**

```text
ahy@DESKTOP-OO963F5:~$ mkdir test_folder
ahy@DESKTOP-OO963F5:~$ cd test_folder
ahy@DESKTOP-OO963F5:~/test_folder$ pwd
/home/ahy/test_folder

ahy@DESKTOP-OO963F5:~/test_folder$ cd ..
ahy@DESKTOP-OO963F5:~$ touch test_file.txt
ahy@DESKTOP-OO963F5:~$ echo "Hello Linux" > test.txt
ahy@DESKTOP-OO963F5:~$ cat test.txt
Hello Linux

ahy@DESKTOP-OO963F5:~$ cp test.txt copy_test.txt
copy_test.txt test.txt
ahy@DESKTOP-OO963F5:~$ rm copy_test.txt
test.txt
```

### 4-3. 절대 경로 및 상대 경로

**실행 명령어 및 결과**

```text
donghwan@localhost:~$ pwd
/home/donghwan

donghwan@localhost:~$ cd ..
donghwan@localhost:/home$ pwd
/home

donghwan@localhost:/home$ cd ~ #HOME 디렉터리
donghwan@localhost:~$ pwd
/home/donghwan

donghwan@localhost:~$ cd /
donghwan@localhost:/$ pwd
/

donghwan@localhost:/$ cd /home/donghwan
donghwan@localhost:~$ pwd
/home/donghwan
```

절대 경로는 `/`부터 시작하는 전체 경로이며, 상대 경로는 현재 작업 디렉터리를 기준으로 파일이나 디렉터리 위치를 지정한다.

### 4-4. 파일 권한 확인 및 변경

**실행 명령어 및 결과**

```text
donghwan@localhost:~/linux-test$ touch perm.txt
donghwan@localhost:~/linux-test$ ls -l perm.txt
-rw-r--r-- 1 donghwan donghwan 0 Nov  4 16:20 perm.txt

donghwan@localhost:~/linux-test$ chmod 755 perm.txt
donghwan@localhost:~/linux-test$ ls -l perm.txt
-rwxr-xr-x 1 donghwan donghwan 0 Nov  4 16:20 perm.txt
```

- `644`(rw-r--r--): 소유자는 읽기·쓰기, 그룹과 기타 사용자는 읽기만 가능하다.
- `755`(rwxr-xr-x): 소유자는 읽기·쓰기·실행, 그룹과 기타 사용자는 읽기·실행이 가능하다.

### 4-5. 디렉터리 권한 확인 및 변경

**실행 명령어 및 결과**

```text
donghwan@localhost:~/linux-test$ mkdir testdir
donghwan@localhost:~/linux-test$ ls -ld testdir
drwxr-xr-x 2 donghwan donghwan 4096 Nov  4 16:27 testdir

donghwan@localhost:~/linux-test$ chmod 700 testdir
donghwan@localhost:~/linux-test$ ls -ld testdir
drwx------ 2 donghwan donghwan 4096 Nov  4 16:27 testdir
```

---

## 5. Docker 설치 및 기본 운영 실습

### 5-1. Docker 설치 및 버전 확인

**실행 명령어 및 주요 결과**

```text
ahy@DESKTOP-OO963F5:~$ docker --version
Docker version 29.9.2, build a82e528

ahy@DESKTOP-OO963F5:~$ docker info
...
Server:
 Containers: 7
  Running: 3
  Paused: 0
  Stopped: 4
 Images: 4
 Server Version: 29.9.2
 Kernel Version: 6.18.54.1-microsoft-standard-WSL2
 Operating System: Docker Desktop
 OSType: linux
 Architecture: x86_64
```

Docker Engine 버전과 컨테이너·이미지 현황을 확인하였다.

### 5-2. Docker 이미지 다운로드 및 목록 확인

**실행 명령어 및 결과**

```text
ahy@DESKTOP-OO963F5:~$ docker pull nginx:alpine
Status: Downloaded newer image for nginx:alpine
docker.io/library/nginx:alpine

ahy@DESKTOP-OO963F5:~$ docker images
IMAGE                ID
hello-world:latest   c567b231f656
my-web:v1            985aa7ce8e0e
nginx:alpine         785835ea65db
nginx:latest         5ab5b0b01097
ubuntu:latest        6a06111c3b0a
```

### 5-3. 컨테이너 상태 확인

**실행 명령어 및 결과**

```text
ahy@DESKTOP-OO963F5:~$ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

ahy@DESKTOP-OO963F5:~$ docker ps -a
CONTAINER ID   IMAGE         COMMAND    CREATED         STATUS
8f66caa56b9d   ubuntu        "bash"     2 minutes ago   Exited (0) About a minute ago
68b248d3862a   hello-world   "/hello"   3 minutes ago   Exited (0) 3 minutes ago
```

`docker ps`로 실행 중인 컨테이너를, `docker ps -a`로 종료된 컨테이너를 포함한 전체 목록을 확인하였다.

### 5-4. Docker 로그 및 리소스 확인

**컨테이너 로그 확인**

```text
ahy@DESKTOP-OO963F5:~$ docker logs myubuntu
this is myubuntu
```

**리소스 사용량 확인 명령어**

```bash
docker stats --no-stream
```

### 5-5. hello-world 컨테이너 실행

**실행 명령어 및 결과**

```text
ahy@DESKTOP-OO963F5:~$ docker run hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.
```

Docker 클라이언트와 데몬 간 통신, 이미지 다운로드 및 컨테이너 실행이 정상적으로 이루어지는 것을 확인하였다.

### 5-6. Ubuntu 컨테이너 실행 및 내부 명령어 실습

**실행 명령어 및 결과**

```text
ahy@DESKTOP-OO963F5:~$ docker run -it ubuntu bash
root@8f66caa56b9d:/# pwd
/
root@8f66caa56b9d:/# ls
bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
root@8f66caa56b9d:/# echo "hello docker" > test.txt
root@8f66caa56b9d:/# cat test.txt
hello docker
```

`exit`로 대화형 컨테이너를 종료할 수 있으며, 종료된 컨테이너는 `docker ps -a`에서 `Exited` 상태로 확인할 수 있다.

---

## 6. Dockerfile 기반 커스텀 웹 서버 제작

### 6-1. 프로젝트 구성

NGINX 베이스 이미지(`nginx:alpine`)에 직접 작성한 HTML 파일을 복사하여 커스텀 웹 서버 이미지를 제작하였다.

| 커스텀 항목 | 적용 내용 |
|---|---|
| 웹 페이지 파일 | `site/index.html` |
| 페이지 제목 | My NGINX Web Server |
| 본문 | Hello Docker + NGINX! 및 한글 안내 문구 |

**파일 구조**

```text
site/
└── index.html
Dockerfile
```

### 6-2. 웹 서버 소스코드

**`site/index.html`**

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

### 6-3. Dockerfile 작성

**`Dockerfile`**

```dockerfile
FROM nginx:alpine
COPY site/index.html /usr/share/nginx/html/index.html
```

### 6-4. 커스텀 이미지 빌드

**실행 명령어**

```bash
docker build -t my-nginx-web:v1 .
```

**실행 결과**

```text
[+] Building 3.3s (7/7) FINISHED
 => [internal] load build definition from Dockerfile
 => [internal] load metadata for docker.io/library/nginx:alpine
 => [2/2] COPY site/index.html /usr/share/nginx/html/index.html
 => naming to docker.io/library/my-nginx-web:v1
```

### 6-5. 커스텀 컨테이너 실행 및 확인

**실행 명령어**

```bash
docker run -d --name my-nginx-container -p 8081:80 my-nginx-web:v1
```

**컨테이너 ID**

```text
6a41cb6773216cf6a6a764af9b393d0fc2b40102cf1a438d74854e806c60f662
```

**이미지 및 컨테이너 확인**

```text
ahy@DESKTOP-OO963F5:~/my-web-project$ docker images
IMAGE             ID
my-nginx-web:v1   cc185ab54764

ahy@DESKTOP-OO963F5:~/my-web-project$ docker ps -a
CONTAINER ID   IMAGE             COMMAND                  CREATED         STATUS         PORTS
6a41cb677321   my-nginx-web:v1   "/docker-entrypoint.…"   9 minutes ago   Up 9 minutes   0.0.0.0:8081->80/tcp, [::]:8081->80/tcp
```

---

## 7. 포트 매핑 및 웹 서버 접속 검증

호스트 포트와 컨테이너의 80번 포트를 연결하여 서로 다른 포트(8082, 8083)로 동일한 웹 서버에 접속하였다.

### 7-1. 첫 번째 컨테이너 실행

**실행 명령어**

```bash
docker run -d -p 8082:80 --name web-review1 my-nginx-web:v1
```

**실행 결과**

```text
6d98317c4b88989d38c930792fed56b71afcbaf38c08ea3f697a552017fa884c
```

`-p 8082:80`은 호스트의 8082번 포트를 컨테이너의 80번 포트에 연결한다. 컨테이너는 네트워크 네임스페이스로 격리되며, 포트 매핑을 통해 호스트에서 서비스에 접근할 수 있다.

### 7-2. 첫 번째 웹 서버 접속 확인

**접속 주소**: `http://localhost:8082`

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

### 7-3. 두 번째 포트로 추가 접속

**실행 명령어**

```bash
docker run -d -p 8083:80 --name web-review2 my-nginx-web:v1
```

**접속 확인 명령어**

```bash
curl http://localhost:8083
```

**실행 결과**

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

### 7-4. 브라우저 접속 증거

**8082 포트 접속 화면**

<img width="802" height="306" alt="8082" src="https://github.com/user-attachments/assets/5306fd7a-87b5-491a-b4a1-73287d78c856" />

**8083 포트 접속 화면**

<img width="814" height="340" alt="8083" src="https://github.com/user-attachments/assets/c5d1a067-7302-45e0-a1a1-1c5556044de6" />

---

## 8. 바인드 마운트 변경 반영 검증

### 8-1. 바인드 마운트 설정

호스트의 `site` 폴더를 컨테이너의 NGINX 웹 디렉터리에 연결하였다.

**실행 명령어 및 결과**

```text
ahy@DESKTOP-OO963F5:~/docker-web$ docker run -d --name web-bind -p 8084:80 -v $(pwd)/site:/usr/share/nginx/html nginx:alpine
Unable to find image 'nginx:alpine' locally
Status: Downloaded newer image for nginx:alpine
91c5c59178755ebf968c16412189ad69bf604c10af0a7e29e7ec7ec23509520e
```

### 8-2. 호스트 파일 수정

**수정 파일**: `~/docker-web/site/index.html`

```bash
nano ~/docker-web/site/index.html
```

**변경 후 파일 내용**

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
</html>
```

### 8-3. 컨테이너 내부 반영 확인

**검증 명령어 및 결과**

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
</html>
```

호스트의 HTML 파일을 수정한 뒤 컨테이너 내부 파일에도 동일한 내용이 반영되는 것을 확인하였다.

**브라우저 접속 증거**

<img width="822" height="306" alt="8084-1" src="https://github.com/user-attachments/assets/fb55b714-ed9d-4c6b-a3a9-d0bacdc81a5e" />
<img width="836" height="332" alt="8084" src="https://github.com/user-attachments/assets/ebee33cc-9610-4aec-846f-b96a8e393f9c" />

---

## 9. Docker 볼륨 영속성 검증

### 9-1. 볼륨 생성

**실행 명령어 및 결과**

```text
ahy@DESKTOP-OO963F5:~/docker-web$ docker volume create mydata-vol
mydata-vol

ahy@DESKTOP-OO963F5:~/docker-web$ docker volume ls
DRIVER    VOLUME NAME
local     mydata-vol
```

### 9-2. 컨테이너에 볼륨 연결 및 데이터 저장

**실행 명령어 및 결과**

```text
ahy@DESKTOP-OO963F5:~/docker-web$ docker run -d --name vol-test1 -v mydata-vol:/data ubuntu sleep infinity
Status: Downloaded newer image for ubuntu:latest
511339c9a673e468bfe90b21e51c2869b284431a5579869f465f7417c9d803df

ahy@DESKTOP-OO963F5:~/docker-web$ docker exec -it vol-test1 bash -lc "echo 'Docker volume persistence test' > /data/hello.txt && cat /data/hello.txt"
Docker volume persistence test
```

### 9-3. 첫 번째 컨테이너 삭제

**실행 명령어 및 결과**

```text
ahy@DESKTOP-OO963F5:~/docker-web$ docker rm -f vol-test1
vol-test1
```

### 9-4. 새 컨테이너에서 데이터 확인

동일한 볼륨을 연결하는 두 번째 컨테이너 실행 명령은 다음과 같다.

```bash
docker run -d --name vol-test2 -v mydata-vol:/data ubuntu sleep infinity
```

**기존 데이터 확인 결과**

```text
ahy@DESKTOP-OO963F5:~/docker-web$ docker exec -it vol-test2 bash -lc "cat /data/hello.txt"
Docker volume persistence test
```

### 9-5. 영속성 검증 결과

- 첫 번째 컨테이너 `vol-test1`의 `/data/hello.txt`에 데이터 저장
- `vol-test1` 삭제 후 동일한 `mydata-vol` 볼륨을 다른 컨테이너에 연결
- 두 번째 컨테이너 `vol-test2`에서 동일한 파일 내용이 유지됨을 확인

**증거 자료**

<img width="598" height="118" alt="volume create" src="https://github.com/user-attachments/assets/6b57f7f7-f440-4632-915f-714d8bb7f512" />
<img width="940" height="250" alt="volume data" src="https://github.com/user-attachments/assets/b6ebe2c7-8420-4b01-89b4-f348cb3c659e" />
<img width="928" height="130" alt="volume persistence" src="https://github.com/user-attachments/assets/5a0152fe-bb32-4111-b154-4961091dba4e" />

---

## 10. Git 설정 및 GitHub 연동

### 10-1. Git 버전 확인

```text
ahy@DESKTOP-OO963F5:~/docker-web$ git --version
git version 2.53.0
```

### 10-2. Git 사용자 정보 및 기본 브랜치 설정

**설정 명령어**

```bash
git config --global user.name "anahayoung-cpu"
git config --global user.email "a*****ng@gmail.com"
git config --global init.defaultBranch main
```

**설정 확인 결과**

```text
ahy@DESKTOP-OO963F5:~/docker-web$ git config --list
user.email=a*****ng@gmail.com
user.name=anahayoung-cpu
init.defaultbranch=main
remote.origin.url=https://github.com/anahayoung-cpu/test3-1.git
branch.main.remote=origin
branch.main.merge=refs/heads/main
```

### 10-3. 로컬 저장소 상태 확인

**실행 명령어 및 결과**

```text
ahy@DESKTOP-OO963F5:~/docker-web$ git init
Reinitialized existing Git repository in /home/ahy/docker-web/.git/

ahy@DESKTOP-OO963F5:~/docker-web$ git status
On branch main
Your branch is up to date with 'origin/main'.
nothing to commit, working tree clean
```

기존 Git 저장소가 이미 존재하여 새로 생성된 것이 아니라 재초기화되었으며, 현재 브랜치는 `main`이다.

### 10-4. 변경 사항 및 커밋 상태 확인

**실행 명령어 및 결과**

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

이미 모든 변경 사항이 커밋된 상태여서 새 커밋은 생성되지 않았다.

 -git add. : 현재 디렉터리와 하위 디렉터리에 있는 변경 사항을 Git의 스테이징 영역에 추가.
 -git commit : 변경 사항을 커밋으로 저장.
 -스테이징 영역 : 깃에서 변경한 파일을 커밋하기 전에 임시로 준비해 두는 공간.


### 10-5. GitHub 원격 저장소 및 브랜치 확인

**GitHub Repository**: [test3-1](https://github.com/anahayoung-cpu/test3-1)

**실행 명령어 및 결과**

```text
ahy@DESKTOP-OO963F5:~/docker-web$ git remote -v
origin  https://github.com/anahayoung-cpu/test3-1.git (fetch)
origin  https://github.com/anahayoung-cpu/test3-1.git (push)

ahy@DESKTOP-OO963F5:~/docker-web$ git branch -vv
* main effc9c8 [origin/main] Merge branch 'main' of https://github.com/anahayoung-cpu/test3-1
```

 -fetch : GitHub에서 데이터를 가져올 때 사용하는 주소
 -push : GitHub로 데이터를 업로드할 때 사용하는 주소

### 10-6. VS Code 및 GitHub 연동 확인

- VS Code에서 GitHub 로그인
- 프로젝트 폴더 열기
- Git 저장소 및 원격 저장소 연결 상태 확인

**증거 자료**

<img width="922" height="872" alt="GitHub login" src="https://github.com/user-attachments/assets/d3c96afd-d670-4ab6-ad38-4dbe4a4d512a" />
<img width="386" height="584" alt="Git integration" src="https://github.com/user-attachments/assets/971d0b81-ffe7-4139-ab61-9da024c14d5e" />
<img width="848" height="96" alt="Repository status" src="https://github.com/user-attachments/assets/3c6ed86d-9b54-4f36-a9d1-cfa6d6385687" />

---

## 11. 트러블슈팅

### 11-1. Docker 포트 충돌

**문제 상황**

8081 포트를 사용하여 컨테이너를 실행할 때 이미 해당 포트가 사용 중이라는 오류가 발생하였다.

**확인 결과**

```text
Error response from daemon: driver failed programming external connectivity on endpoint ...
Bind for 0.0.0.0:8081 failed: port is already allocated
```

**해결 명령어**

```bash
docker stop my-nginx-container
docker rm my-nginx-container
docker run -d --name my-nginx-container -p 8082:80 my-nginx-web:v1
```

사용 중인 컨테이너를 중지·삭제한 뒤 호스트 포트를 8082로 변경하여 다시 실행하였다. 이후 `http://localhost:8082`로 접속해 웹 페이지 출력을 확인하였다.

### 11-2. 바인드 마운트 디렉터리 권한 문제

**문제 상황 및 확인 결과**

호스트의 `site` 디렉터리 소유자가 `root:root`로 설정되어 있어 현재 사용자 계정으로 파일을 수정하기 어려운 상태였다.

```text
ahy@DESKTOP-OO963F5:~/docker-web$ ls -la ~/docker-web/site
total 8
drwxr-xr-x 2 root root 4096 Nov  4 23:21 .
```

**해결 명령어 및 결과**

```text
ahy@DESKTOP-OO963F5:~/docker-web$ sudo chown -R $USER:$USER ~/docker-web/site
[sudo: authenticate] Password:

ahy@DESKTOP-OO963F5:~/docker-web$ ls -ld ~/docker-web/site
drwxr-xr-x 2 ahy ahy 4096 Nov  4 23:21 /home/ahy/docker-web/site
```

`chown`으로 디렉터리 소유자를 현재 사용자로 변경한 후 파일 수정 및 바인드 마운트 반영을 확인하였다.

---

## 12. 최종 수행 결과

Linux CLI를 이용한 파일·디렉터리 관리와 권한 변경, Docker 이미지 및 컨테이너 운영, Dockerfile 기반 웹 서버 구축, 포트 매핑, 바인드 마운트 및 볼륨 영속성을 실습하였다. 또한 Git과 GitHub를 연동하고 실행 과정과 검증 결과를 README로 정리하였다.
