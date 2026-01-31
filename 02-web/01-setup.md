# 01-setup.md
## 플라스크 개발환경 세팅하기

## 0. 플라스크 설치
* 이제부터 진행하는 모든 쉘 코드는 가상환경을 활성화한 상태에서 실행합니다.
* 아래와 같은 상태로 나타나는 경우, 
```sh
(base)[사용자 이름]@[호스트 이름]:~$
```
* 다음 코드를 실행시켜 가상환경을 활성화해주세요.
```sh
conda activate [환경이름]
```
<details>
<summary> 가상환경 관련 미니콘다 명령어 모음집 </summary>
<div>

* 가상환경 리스트 확인
```sh
conda info --envs
```
* 가상환경 생성
```sh
conda create -n [환경이름] python=[버전(예: 3.11)]
```
* 가상환경 삭제
```sh
conda env remove -n [환경이름]
```
* 가상환경 비활성화
```sh
conda deactivate
```
* 명령어 목록 확인(미니콘다 아니어도 어지간한 경우는 -h 치면 설명 나옵니다)
```sh
conda -h
```
</div>
</details>
* (중요) 다음과 같이 나타나는 상태에서 
```sh
(환경이름)[사용자 이름]@[호스트 이름]:~$
```
* 플라스크 설치
```sh
pip install flask
```