# 05-python.md
## 파이썬 파일을 실행하는 세 가지 방법

사전 용어 설명: 터미널, 커맨드라인, shell은 명령어 치는 창으로만 생각해두셔도 됩니다. 나중에 리눅스 제대로 공부할때 차이 파악하셈

### 1. IDE에서 실행하기

vscode에서 `Ctrl+Shift+P`를 누르면 아래 창이 뜸, Python 클릭

![image.png](/00-images/01-python/05-python/image-0.png)

초기환경 세팅 때 만들었던 가상환경 설정 그대로 따라했다면 Python 3.11.xx (p11)으로 표기되어 있을 거임

![image.png](/00-images/01-python/05-python/image-1.png)

이후 터미널 > 새 터미널 누르면 vscode 하단에 터미널이 뜸

![image.png](/00-images/01-python/05-python/image-2.png)

우측상단 실행버튼을 누르면 터미널에서 실행된다.

![image.png](/00-images/01-python/05-python/image-3.png)

### 2. shell에서 실행하기

기본적으로는 아래 코드로 실행한다.

VSCode에서 실행 버튼을 누르는 것은 내부적으로는 아래와 같이 `python3 파일명`을 실행하는 것과 같다.

```bash
python3 [실행할 파일 주소]
# 예시
python3 001-hello_world.py
```

실행할 파일 주소를 보기 위해서는 커맨드라인에 표기되는 현재 경로를 확인해야 한다.

커맨드라인은 아래와 같이 구성된다.

```bash
[사용자 이름]@[호스트 이름]:[현재 경로][프롬프트 기호]
# 예시
aqupa@[호스트 이름]:~/study$
```

현재 경로와 실행하고 싶은 파일의 위치를 파악한 다음, 코드를 실행한다.

예: ~/study/01-python/001-hello_world.py를 실행하고 싶고, 나는 지금 ~/study에 있다. → `python3 01-python/001-hello_world.py`

매번 `01-python` 치기 귀찮아요 → `cd 01-python`명령어로 `01-python` 파일 안으로 들어간 다음, `python3 001-hello_world.py`

### 3. 예제/영상에서는 >>> 옆에다가 명령어를 치던데, 이건 뭐냐?

shell에서 실행할 때, 실행할 파일을 명시하지 않으면 해당 방식으로 실행할 수 있다.

```bash
# 예시
python3
>>> print("Hello World")
Hello World
>>>quit()
```

python3으로 진입하고, quit()를 쳐서 빠져나올 수 있다.

`>>>` 환경은 간단한 테스트나 확인용이며 나중엔 거의 안 씀