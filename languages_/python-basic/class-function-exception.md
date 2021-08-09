---
sort: 4
---

# Class, Function & Exception

- **Function**(**함수)**
  
    - **Defining a Function(함수 정의, 구조)**
    
        ```python
        def 함수명(매개변수):
            """독스트링"""
            수행할 문장
            return 결과값
        ```
    
        함수: 믹서기가 과일을 받으면 주스를 뱉듯이, 함수는 입력을 받으면 출력을 한다.
    
        독스트링: 함수가 무슨 일을 하는지 설명.
    
        Parameter(매개변수): 함수에 입력으로 전달되는 값, 즉 인수를 받는 변수.
    
        Argument(인수): 함수를 호출할 때 전달하는 입력값.
    
        `return`: 결괏값을 반환. 오직 return을 통해서만 결괏값 반환 가능.
    
        결괏값은 오직 하나만을 가진다.
    
    - **Calling a Function(함수 호출)**
    
        사용: `결괏값을 받을 변수 = 함수이름(입력인수1, 입력인수2)`
    
        함수를 호출할 때 매개변수 지정 가능: `a = add(b=2, a=1)`
    
        `global 객체`: 함수 밖의 변수를 함수 내로 가져옴.

    - **입력값, 결괏값 없는 함수**
        - **입력값이 없는 함수**
    
        괄호 안 매개변수를 비워놓으면 입력값 없이 결괏값만 있는 함수.
    
        e.g. `def say(): return 'Hi'`
    
        사용: `결괏값을 받을 변수 = 함수이름()`
    
        - **결괏값이 없는 함수**
    
        return 명령어가 없으면 결괏값 없이 입력값만 있는 함수. print()로 인한 출력은 함수의 구성 요소 중 하나인 '수행할 문장'일 뿐.
    
        `print(결괏값을 받을 변수)`: None 반환.
    
        사용: `함수이름(입력인수1, 입력인수2)`
    
        - **입력값, 결괏값 없는 함수**
    
        매개변수도, return문도 없으면 입력값과 결괏값이 없는 함수.
    
        e.g. `def say(): print('Hi')`
    
        사용: `함수이름()`
    
    - **입력값 수가 몇 개일지 모를 때**

        ```python
        def 함수이름(*args):
            수행할 문장
        ```
    
        *매개변수: 입력값들을 전부 모아 튜플로 만들어 줌.
    
        `for i in args`: 그래서 for 문장이 자주 쓰임.

    - **Keyword Parameter**
    
        ```python
        def 함수명(**kwargs):
            수행할 문장
        ```
    
        `key=value` 형태의 결괏값이 그 딕셔너리에 저장.

        사용: `함수명(a=1)`
    
    - **매개변수 초깃값 설정**
    
        ```python
        def 함수명(name, old, man=True):
            수행할 문장
        ```
    
        `man=True`: 매개변수에 미리 초깃값을 설정. 항상 변하는 것이 아닐 경우 설정해두면 유용함.
    
        `함수명(name, old)`: man은 입력값이 없어도 초깃값 True를 갖게 됨.

        `함수명(name, old, False`): '수행할 문장'에 따라 초깃값과 다른 명령을 수행.
    
        순서: `man=True`가 가운데에 있으면 꼭 입력 해주어야 함.
    
    - **변수 선언 효력 범위 and 전역변수**
    
        지역변수: 함수 안에서 새로 만든 매개변수는 함수 안에서만 사용하는, 함수만의 변수. 함수 밖의 변수 a가 아니다.
    
        전역변수: 프로그램 어디서든 부를 수 있는 이름.

        `return`: 함수 바깥으로 변수를, 결괏값을 반환.
    
        `global a`: 함수 밖의 변수 a를 불러와 이후 사용가능하게 함.
    
        > 그러나 추천하는 방법이 아님.
    
    - 참고: **Lambda**
    
        `lambda`: 함수를 생성할 때 사용하는 예약어, def와 동일한 역할. 함수를 한줄로 간결하게 만들 때, 복잡하지 않거나 def를 사용할 수 없는 곳에 주로 사용.
        
        정의: `변수 = lambda 매개변수1, 매개변수2: 표현식`
        
        사용: `변수(a,b)`
        
    - **Map**
    
        `map(함수, *args)`: 데이터마다 함수 적용
    
        > == `[함수 for i in 데이터]`
    
    - **재귀**
    
        재귀: 함수 자신을 호출하는 방법. 정의하는 함수 안에 그 함수를 넣는 것.
    
        예: `def x(a,b), 이후 if문, 이후 x(a,b+1)`
    

---

- **Class**
    - **Class 구조 만들기**

        ```python
        class Cookie:
            ''' 독스트링 '''
            pass/def
        a = Cookie()
        ```
    
        `Class`: 똑같은 무엇인가를 계속해서 만들 수 있는 도면, 틀. - `Cookie`
    
        > 파스칼 표기법: 단어의 첫글자를 대문자로 표기
    
        `독스트링`: 클래스의 의미와 역할을 설명.
    
        `Object`: Class로 만든 피조물. - `a`
    
        `Instance`: Object가 어떤 Class의 객체인지의 관계. - `a`는 `Cookie`의 `Instance`.
    
        보통 `def` 수행문에 setdata가 많이 나오는 듯.
    
        > `isinstance(1, int)`: 객체가 유형에 속하는지 확인.
        >
        > 참조하는 것이기 때문에 클래스가 바뀌면 인스턴스도 바뀜. 하지만 인스턴스 변화가 클래스의 변화는 아님.
    
    - **Methods**
    
        `Method`: Class 안에 구현된 함수.
    
        `def method(self, first, second)`: Method는 일반 함수와 달리 첫 번째 매개변수로 `self`를 갖는다.
    
        - method parameter
    
        `self.method(first,second)` = `class.method(self, first, second)`
    
        - method statement(예시)
    
        `self.first = first`
    
        `self.second = second`
    
    - **Constructor(생성자)**
    
        `__init__()`: setdata method와 동일. 값을 설정하는 역할이지만 `Class(인수)`로 실행.
    
        ```python
        class a:
            def __init__ (self, first, second):
            	self.first = first
            	self.second = second
        ```
    
        `__str__()`: 문자열 반환기능을 오버라이딩하는 것. print로 확인 가능.
    
    - **Inheritance(상속)**
    
        상속: 기존 클래스는 놔두고 추가, 변경이 필요할 때.
    
        Overriding: 상속한 클래스에 있는 Method나 객체를 동일한 이름으로 덮어쓰면 overriding한 Method나 객체가 호출됨.
    
        `class b(a)`: `a`라는 클래스를 `b`클래스로 상속.

        `super().__init__(b,c)`: `def __init__` 내부에서 사용되며, 기존 클래스에서 정의된 초기화 변수는 그대로 쓴다는 뜻.
    
        > a라는 변수만 바꾸고 싶을 때, 바꾸고 아래에 적어줘서 나머지는 그대로 상속되게 함.
    
        `issubclass(a, b)`: a가 b의 하위 클래스인가를 판단.
    
    - **클래스 변수**
    
        ```python
        class Family:
            lastname = "김"
        ```
    
        클래스 변수: 클래스 안에 변수를 선언하여 생성.
        
        `Family.lastname` ⇒ 김
    

---

- **Exception(예외 처리)**
    - **기본 구조**

        ```python
        try:
        	실행할 코드
        except:
        	오류발생시 수행
        finally:
        ```

        `try`: 실행.

        `except`: **오류 발생시** 수행.

        `finally`: **항상 수행**. 보통 리소스 close 시에 많이 사용.

    - **오류 처리**

        `except 발생 오류 as 변수:`: **특정 오류** 발생시, 변수로 넣어 **오류 메시지 내용 출력** 가능.

        `except: pass`: 오류 발생시 그냥 **회피**하도록.

    - **오류 발생 유도**

        `raise 오류명`: **오류가 나타나게** 함. def나 Class에 넣어줌.
    
    - **예외 만들기**

    - ```python
        class MyError(Exception):
            def __str__(self):
            	return "오류임"
        ```
    
        : except와 print를 묶은 거라고 보면 됨.
    
        1. `Exception`: Python 내장 클래스.
        2. `pass`로 정의 시: 오류 메시지 출력되지 않음.
        3. `__str__`: 원하는 오류 메시지를 **print문으로 출력할 경우** 호출되는 method.
        4. **def 내부 if문 등**에 `raise MyError()`와 함께 쓰임.
        5. `return`: 나타나는 **오류 메시지**. `as 변수`와 `print(변수)`를 쓰면 이 내용이 출력됨.