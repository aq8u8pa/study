# 01-setup.md
## 파이썬 개발환경 세팅하기

* 실습환경  
Windows 11 Pro 


## 0. VSCode, WSL, Ubuntu 22.04 설치


### VSCode
1. [링크](https://code.visualstudio.com/download)에 들어가 `Windows` 클릭, 다운로드

2. 아래 내용 모두 체크, 나머지 설정은 건드리지 말고 다운로드  
  ![alt text](/00-images/01-python/00-setup/image-0.png)


### WSL
1. `Windows 기능 켜기/끄기` 열고 **Linux용 Windows 하위 시스템**과 **가상 머신 플랫폼** 체크 후 
  * **리부팅**
  ![alt text](/00-images/01-python/00-setup/image-3.png)
  ![alt text](/00-images/01-python/00-setup/image-4.png)
  
2. **windows 11 이상**인 경우 `Windows Terminal` 열고 아래 코드 입력  
    ```ps
    wsl --install -d Ubuntu-22.04
    ```
    입력 후 Ubuntu 22.04 2. 사용자명, 패스워드 설정 항목부터 진행   
    **windows11 미만**인 경우  
    [링크](https://learn.microsoft.com/ko-kr/windows/wsl/install-manual#step-4---download-the-linux-kernel-update-package)에 들어가 `WSL` 설치  
  ![alt text](/00-images/01-python/00-setup/image-1.png)

3. **windows11 미만**인 경우  
    [링크](https://apps.microsoft.com/detail/9p9tqf7mrm4r?hl=ko-KR&gl=KR)에 들어가 `Windows Subsystem for Linux` 설치

4. [링크](https://apps.microsoft.com/detail/9n8g5rfz9xk3?hl=ko-KR&gl=KR)에 들어가`Windows Terminal Preview` 설치 (선택)
    * 안 써도 되는데, 쓰면 편함


### Ubuntu 22.04
1. **windows11 미만**인 경우 `Windows Terminal Preview` 열고 아래 코드 입력  
	```ps
    wsl --install Ubuntu-22.04
    ```

2. 사용자명, 패스워드 설정  
    * 이때 작성한 사용자명은 앞으로 쉘 커맨드라인에 노출된다.  
    * 비밀번호 입력 시 커서도 안 움직이는 것이 정상이다. 입력 후 엔터, 재입력, 엔터 
    * 만약 이 과정이 진행되지 않는다면 6. 계정 생성을 건너뛰면 안 된다. 
    * 패스워드는 잊어버리지 마세요  

3. WSL을 기본으로 설정  
	```ps
    wsl --set-default-version 2
    ```

4. `Ubuntu` 환경 실행, 이 다음부터는 우분투 환경에서만 진행함
    ```ps
    ubuntu
    ```
    * 안 되는 경우  
    `Windows Terminal Preview`쓰는 경우 탭 위치에 + v가 보일 거임  
    v를 누르고 우분투를 클릭하세요  

5. 설정 (선택)
    ![alt text](/00-images/01-python/00-setup/image-5.png)
    * Default terminal application을 Ubuntu로 변경해두면, Windows Terminal Preview를 열 때마다 자동으로 접속할 수 있다.
    * Launch on machine startup을 체크하면, 컴퓨터를 켤 때마다 Windows Terminal Preview가 실행된다. 

<details>
<summary> 6. 계정 생성 (2. 사용자명, 패스워드 설정 진행이 안 된 경우에만) </summary>
<div>

* `Windows Terminal Preview` 열고 `Ubuntu` 환경에 접속했을 때 `커맨드 라인`은 아래와 같이 표시된다.
```sh
[사용자 이름]@[호스트 이름]:[현재 경로][프롬프트 기호]
```
* 아래와 같이 표시되는 경우, [2. C](#2-c)부터 진행하면 된다.
```sh
[사용자 이름]@[호스트 이름]:~$
```
* 만약 아래와 같이 표시되는 경우, 건너뛰지 말고 계정 생성을 진행해야 한다.
```sh
[사용자 이름]@[호스트 이름]:~#
```
* 계정 생성
```sh
useradd [사용자 이름]
```
* 비밀번호 설정
```sh
passwd [사용자 이름]
```
* 이후 비밀번호 입력, 엔터  
* 홈 디렉토리 생성
```sh
mkdir -p /home/[사용자 이름]
chown -R [사용자 이름]:[사용자 이름] /home/사용자 이름
```
* 해당 계정을 기본으로 설정
```sh
usermod -s /bin/bash [사용자 이름]
cat /etc/passwd | grep [사용자 이름]
```
* 계정 로그인
```sh
su - [사용자 이름]
```
</div>
</details>

<details>
<summary> 7. DSN/네트워크 설정 (이후 진행하는 코드에서 sudo apt-get update 안 되는 경우에만) </summary>
<div>

* `Windows Terminal Preview` 열고 `Ubuntu` 환경에서 아래 코드 입력 
```sh
sudo rm /etc/resolv.conf
sudo nano /etc/resolv.conf
```
```nginx
nameserver 8.8.8.8
nameserver 1.1.1.1
```
* 저장: Ctrl + O → Enter → Ctrl + X
```sh
sudo chattr -i /etc/resolv.conf
```
```sh
sudo apt clean
sudo apt update
```

</div>
</details>


## 2. C 컴파일러
1. `Windows Terminal Preview` 열고 `Ubuntu` 환경에서 아래 코드 입력  
    ```sh
    sudo apt-get update
    sudo apt-get install build-essential gdb -y
    ```

## 3. Python
1. `Windows Terminal Preview` 열고 `Ubuntu` 환경에서 아래 코드 입력  
    ```sh
    sudo apt install python3 -y
    sudo apt install python3-pip -y
    ```

## 4. Miniconda
1. `Windows Terminal Preview` 열고 `Ubuntu` 환경에서 아래 코드 입력  
    ```sh
    wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
    bash ./Miniconda3-latest-Linux-x86_64.sh
    ```
    * 이후 G(내용 스킵하고 문서 제일 밑으로 가기) → yes → Enter → yes 입력 후 아래 코드 입력
    ```
    source ~/miniconda3/bin/activate
    ```

2. 가상환경 생성
	```
    conda create -n [가상환경 이름] python=3.11
    ```
    * 가상환경 이름은 마음대로 작성해도 되나 직관적이고 짧을수록 좋음(예: p11)  
    * a → a → y 입력 

3. 가상환경 활성화  
	```sh
    conda activate [가상환경 이름]
    ```

4. 가상환경 비활성화(참고)
	```sh
    conda deactivate
    ```

5. 가상환경 삭제(참고)
	```sh
    conda remove --name [가상환경 이름] --all
    ```


## 5. VSCode
1. `Windows Terminal Preview` 열고 `Ubuntu` 환경에서 아래 코드 입력
    ```sh
    code .
    ```
    * 이후 모든 내용에 동의하면 VSCode창이 뜬다. Trust 누르고 우측 하단 확인

2. 아래 항목 모두 설치
    ![alt text](/00-images/01-python/00-setup/image-6.png)
    ![alt text](/00-images/01-python/00-setup/image-7.png)


## 6. 학습용 폴더 만들기
1. `Windows Terminal Preview` 열고 `Ubuntu` 환경에서 아래 코드 입력
    ```sh
    mkdir study
    mkdir study/01-python
    cd study
    code .
    ```

2. VSCode창이 뜬다. 여기에서 앞으로의 학습을 진행하면 된다. 


## 7. Git
* `Windows Terminal Preview` 열고 `Ubuntu` 환경에서 아래 코드 입력
    ```sh
    sudo apt-get install git
    ```
* 사용자 정보 설정
    ```sh
    git config --global user.name "[아이디]" 
    git config --global user.email "[이메일]@gmail.com" 
    ```
* ssh 키 생성
    ```sh
    mkdir -p ~/.ssh
    ssh-keygen -t ed25519 -C "[이메일]@gmail.com"
    ```
    엔터엔터엔터
    ```sh
    eval "$(ssh-agent -s)"
    ssh-add ~/.ssh/id_ed25519
    ```
    아래 명령어 친 뒤에 나오는 것을 손수 복붙하시면 됩니다 
    ```sh
    cat  < ~/.ssh/id_ed25519.pub
    ```
* `깃허브`에 키 등록 
    ![alt text](/00-images/01-python/00-setup/image-8.png)
    ![alt text](/00-images/01-python/00-setup/image-9.png)
    ![alt text](/00-images/01-python/00-setup/image-10.png)
    * 빨간 박스 안에 붙여넣기 후 add SSH key

<details>
<summary> Github 계정 여러개 쓰는 경우만 </summary>
<div>

* 방금 썼던 `Windows Terminal Preview` 열고 `Ubuntu` 환경에서 아래 코드 입력
    ```sh
    cd ~/.ssh
    vim config
    ```
* 아래 내용 붙여넣기 후 :wq 엔터 입력
    ```sh
    Host github.com
        HostName github.com
        User git
        IdentityFile ~/.ssh/id_ed25519
    ```
</div>
</details> 
