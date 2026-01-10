# 02-linux.md
## 기본적인 쉘 명령어와 내용에 대해 알아보자

### 들어가기에 앞서 
- 에러 메시지는 읽으면 대부분 해결 가능함. 
컴퓨터가 하는 말을 무시하지 마시고 최대한 들어보세요. 컴퓨터에 뜨는 모든 로그는 사람들이 프로그램 짤 때 이런 문제가 생기면 이런 안내를 출력하라고 정해놨기 때문에 나오는 것입니다. 쓸모없는 내용이었으면 굳이 출력도 안 했을거임. 꼭 화면에 뜨는 글자를 읽는 습관을 들입시다
- 복붙보다 직접 쳐보는 게 중요합니다 외우는게 아니라 익숙해지게 하는 거임
- 모르는 거: 구글링 습관을 들이자 

### 1. 디렉토리 구조

### 핵심 개념

- 리눅스 파일 구조는 **루트(/)** 부터 시작함
- 윈도우 탐색기에서 폴더를 열어야 해당 파일 안에 있는 파일과 폴더 등등을 확인할 수 있는 것처럼, 리눅스에서는 기본적으로 현재 위치(working directory)를 기준으로 파일과 명령어가 동작함
따라서 원하는 파일이 있는 위치로 이동한 뒤 작업하는 것이 기본
- 경로==주소는 두 가지로 나뉜다.
    - 절대경로: 루트(/)부터 시작해서 절대적으로 어느 위치에 있는지에 대한 경로
        - 예: /home/username/study/01-python/001-hello_world.py)
    - 상대경로: 현재 내가 있는 위치기준 경로
        - 예: ./study/01-python/001-hello_world.py, study/01-python/001-hello_world.py
        - ./은 생략 가능

### 경로

- `/` : 루트 디렉토리
- `~` : 내 홈 디렉토리 (`/home/username`)
- `.` : 현재 디렉토리
- `..` : 상위 디렉토리
- `/var/www` : 웹 서버 루트(개념만)
- `/etc` : 설정 파일 위치(읽기만)

### 명령어

```bash
pwd        # 현재 위치 Print Working Directory의 약자
ls         # 목록 보기 list
ls -al     # 숨김 파일 포함 자세히
cd 폴더명    # 이동 Change Directory
cd ..      # 상위로 이동
cd ~       # 홈으로 이동
```

---

### 2. 파일 관리

### 파일과 디렉토리 생성/삭제

```bash
touch a.txt        # 파일 생성
mkdir project      # 폴더 생성 make directory
mkdir -p a/b/c     # 중첩 폴더 생성
rm a.txt           # 파일 삭제 remove
rm -r folder       # 폴더 삭제
rm -rf folder      # 강제 삭제 (확인 없이 바로 삭제)
cp a.txt b.txt     # a내용을 b에 복사 copy 
cp -r a b          # a폴더를 b폴더에 복사
mv a.txt folder/   # a 파일을 폴더로 이동 move
mv old.txt new.txt # 이름 변경
cat file.txt       # 전체 출력 concatenate
less file.txt      # 스크롤로 보기 (q로 종료)
head file.txt      # 앞부분
tail file.txt      # 뒷부분
tail -f log.txt    # 실시간 로그 확인
```

---

### 3. 코드 실행

### 실행 권한

```bash
chmod +x run.sh    # 실행 권한 부여
```

### 스크립트 실행

```bash
./run.sh           # 현재 디렉토리 실행
bash run.sh        # bash로 실행
```

- 그냥 실행이랑 bash 실행이랑 뭔 차이임?
    
    `./run.sh`
    
    - 파일 안에 적힌 첫 줄(shebang, 예: #!/bin/bash)을 기준으로 실행됨
    - 실행 권한이 있어야 함
    
    `bash run.sh`
    
    - bash로 강제로 실행
    - 실행 권한 없어도 됨
    - 스크립트 테스트용

### 프로세스 관리

```bash
ps
ps aux | grep node
kill PID
```

---

### 4. Git

레포지토리를 로컬(내 컴퓨터)에 복사하기

```bash
git clone repo주소 # 레포지토리 클론
git status        # 현재 상태 확인
```

깃허브 레포지토리에 내가 작업한 파일 올리기(기본)

```bash
# 로컬(내 컴퓨터)에서 만든 변경사항을 추가한다
git add .
# message 부분에 어느 변경사항을 적용했는지 입력하고, 변경사항을 저장한다 
git commit -m "message"
# 저장한 변경사항을 레포지토리에 업로드하기 이전에, 레포지토리에 있는 내용을 받아와 로컬 상태를 최근 상태로 반영한다
git pull
# 저장한 변경사항을 업로드한다 
git push
```

위 내용은 쉘에서 직접 써도 되고(단, 위치가 레포지토리와 같아야 됨. 예로들어, study 레포지토리에 변경사항을 올리고 싶으면 로컬 위치도 study여야 함) vscode에서 해도 된다. 메세지 란에 커밋 메세지를 쓰고 밑에 있는 한 번 누르면 커밋, 두 번 누르면 푸쉬임

![alt text](/00-images/01-python/02-linux/image.png)

충돌 발생했을 때 해결하는 방법, 브랜치 파는 방법, 커밋 메세지 깔끔하게 쓰는 방법, 디스코드 연동해서 push 때마다 메세지 오게 하는 법 등은 2월에 안내할 예정(요청이 있을 시 추가하겠음)