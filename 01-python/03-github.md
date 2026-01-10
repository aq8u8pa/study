# 03-github.md
## 깃허브 계정을 생성하고 내가 작성한 코드를 업로드해보자
## 1. [깃허브](https://github.com/)에  들어가서 회원가입을 한다. 
* 지메일 연동을 추천드려요. 사유: 편함
* 안 쓰는 지메일로 가입하는 것을 권장합니다
  * 사유: 개인정보 털릴 수도 있음. 컴퓨터 하는 사람들은 메일 털 줄 아는 사람 많으니까 주의합시다
  * 상관없으면 아무거나 써도 됨
## 2. 레포지토리를 만든다
* 이름은 아무거나 쓰셔도 됩니다
    ![alt text](/00-images/01-python/03-github/image-0.png)
    ![alt text](/00-images/01-python/03-github/image-1.png)
## 3. 명령어 복사
![alt text](/00-images/01-python/03-github/image-2.png)
```sh
git remote add origin git@github.com:[아이디]/[레포지토리 이름].git
git branch -M main
git push -u origin main
```
## 4. 쉘에서 깃허브 초기설정하기
[01-환경세팅](https://github.com/aq8u8pa/study/blob/main/01-python/00-setup.md)에서 사용했던 우분투 쉘을 열면 커맨드라인이 아래와 같이 나옴 
```sh
[사용자 이름]@[호스트 이름]:~$
```
아래 명령어 입력 
```sh
cd study
```
그러면 현재위치가 ~/study로 변경됨
3에서 복사한 명령어를 붙여넣기하고 `yes`하신뒤
깃허브 새로고침 해보시면 기존에 작성한 코드가 올라가는 것을 확인하실 수 있습니다