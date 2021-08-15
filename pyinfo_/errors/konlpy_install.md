---
sort: 1
---

# Konlpy 설치 오류

[당시 상황 정리](https://githubmemory.com/repo/konlpy/konlpy/issues/316)

- **오류 내용**

터미널에서 `pip install konlpy`로 konlpy를 설치한 뒤 주피터 노트북에서 파이썬 코드를 작성했으나 `"ModuleNotFoundError: No module named 'konlpy'"`라는 오류 메세지가 나타났다. 설치가 안되어서 나타난 오류 같은데 왜 이런 오류가 나왔을까?

---

- **오류 발생 경위**

JAVA 설치 -> JAVA HOME 환경변수 설정 -> JPype 파이썬 버전에 맞게 설치 -> cmd: pip 업그레이드 -> cmd: pip install konlpy -> 파이썬에서 import 해봤으나 설치가 안되었다고 아래와 같은 오류가 나옴.

---

- **Python Konlpy 설치 오류 메세지**

```warning
	**konlpy 설치 후 파이썬에서 나타난 오류 메세지**

ModuleNotFoundError: No module named 'konlpy' # 난 설치 했는데??
```



```warning
**konlpy 설치 중 터미널에 나온 설치 오류 메세지**

>> pip install konlpy
Collecting konlpy Using cached konlpy-0.5.2-py2.py3-none-any.whl (19.4 MB) Requirement already satisfied: beautifulsoup4==4.6.0 in c:\anaconda3\lib\site-packages (from konlpy) (4.6.0) Requirement already satisfied: numpy>=1.6 in c:\anaconda3\lib\site-packages (from konlpy) (1.18.1) Requirement already satisfied: lxml>=4.1.0 in c:\anaconda3\lib\site-packages (from konlpy) (4.5.0) Requirement already satisfied: JPype1>=0.7.0 in c:\anaconda3\lib\site-packages (from konlpy) (1.0.1) WARNING: No metadata found in c:\anaconda3\lib\site-packages ERROR: Could not install packages due to an EnvironmentError: [Errno 2] No such file or directory: 'c:\anaconda3\lib\site-packages\JPype1-1.0.1.dist-info\METADATA'
```

---

- **오류 해결**

**보통은 `pip uninstall jpype1`, `pip install jpype1`으로 JPype를 재설치해주면 해결**이 되는 것 같다.

그런데 나는 이걸로는 해결이 안되었고, 터미널에 나온 오류 메세지의 마지막 줄에서 힌트를 얻어 위 파일 경로로 직접 가서 문제를 해결했다. Stackoverflow의 도움을 받아 살펴보니, **원래는 JPype를 설치하면 `c:\anaconda3\lib\site-packages\JPype1-1.0.1.dist-info`라는 경로에 `METADATA`라는 파일이 있어야 정상 작동이 되는데, 이 파일이 없어서 문제가 일어난 것이다.** 그래서 METADATA를 직접 다운 받는 법은 헷갈릴 것 같아서 그냥 폴더 자체를 삭제하고 터미널에서 재설치 해줬더니 konlpy가 정상 설치 및 작동하게 되었다!

```tip
- 	**오류 해결법**

JPype1-1.0.1.dist-info 폴더를 직접 삭제하고 `pip install jpype1`을 터미널에 작성해주면 되면 된다.
```
