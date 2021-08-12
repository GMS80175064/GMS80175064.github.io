---
sort: 1
---

# NumPy

- NumPy는 같은 type만을 다룸. 즉 하나라도 float 형이면 정수도 float로 변환됨.

- 리스트, 튜플, array를 `array()`로 받을 수 있다.

- 리스트와 달리 벡터, 행렬끼리의 연산이 가능하다.

  > 브로드캐스트: 상수나 다른 차원끼리도 가능.

---

- **Creating arrays**
  
    - **Dimensional array**
    
        `np.array([1,2])`: ndarray 배열 생성.
    
        `np.array([range(i,i+1) for i in [2,4,6]])`: 조건문 줄바꿈으로 2차원 array 생성.
    
        `np.array([[1,2], [3,4]])`: 리스트 안의 리스트로 2차원 array 생성.
    
    - **간격 array**
    
        `np.arange(a,z,t)`: `a`부터 `z-1`까지 `t`(디폴트=1) 간격으로 array 생성.
    
        `np.linspace(a,z,t)`: `a`와 `z` 사이를 등간격으로 나눈 `t`개의 array 생성.
    
    - **Random/Normal**
    
        `np.random.random((x,y))`: x행 y열 array를 0과 1사이 랜덤 수로 채움.
    
        `np.random.randint(x,y,n)`: x와 y-1 사이 랜덤 정수가 n개인 array 생성.
    
        `np.random.normal(m,v,n)`: 평균이 m, 분산이 v인 정규분포에서 n개인 array 생성.
    
    - **Fill**/**반복**
    
        `np.zeros(n)`: 0이 n개인 array를 float로 생성.
    
        `np.ones(n)`: 1이 n개인 array를 float로 생성.
    
        `np.full(n, a)`: a가 n개인 array를 float로 생성.
    
        - n을 아래처럼 바꾸면 차원, size 조절 가능.
    
          `n=(x,)`: size가 x행인 1차원 array.
    
          `n=(x,y)`: size가 x행 y열인 2차원 array.
    
          `n=(x,y,z)`: size가 x행 y열인 z개의 3차원 array. 

          `,dtype=float)`: array 요소의 type을 변경.

          > `int`: 소수점 있으면 버림.

    - 기타(참고)
    
        `np.eye(x)`: x*x 크기의 identity matrix(단위행렬) 생성.
    
        `np.empty()`: 초기화 되지 않은 array 생성.
        
        > 컴퓨터 메모리에 있는, size에 맞는 array 값을 무작위로 불러옴.

---

- **NumPy array attributes**

    모든 배열에는 ndim, shape, size가 있다.

    `x.ndim`: 배열 x의 차원 수.

    `x.shape`: 배열 x의 행, 열, 차원.

    `x.size`: 배열 x의 크기.

    `x.dtype`: 배열 x의 데이터 타입.

---

- **Array indexing**
  
    - **Indexing**
    
        `x[n]`: 1차원 array 인덱싱.
    
        `x[x,y]`: 2차원 array의 x행 y열 인덱싱.

        > (0,0)부터 시작임.

        `x[n]=i`: 특정 value 수정.

    - **Fancy indexing**

        `x[n]`와 같은 경우, 결과는 index arrays의 형태를 따른다.

---

- **Array slicing**

    `x[a:z:t]`: `a`부터 `z-1`까지 `t`간격으로 1차원 array 슬라이싱.

    > default 값은 각각 0, size, 1.

    `x[a:z:t, a:z:t]`: 앞에서 행, 뒤에서 열의 범위를 지정하여 2차원 array 슬라이싱.

    > `x[::-1, ::-1]`: 상하좌우 반전.

    `x[:, n]`: 하나의 행, 열 전체 슬라이싱.

    리스트와 같이 슬라이싱한 값을 넣어준 변수를 변경하면, 원래 배열도 변경된다. 즉`b=a[:2,:2]`일 때, `b[0,0]=99`면, `a[0,0]`도 `99`로 바뀐다.

    `a[x,y].copy()`: array를 복사한 값.
    ㄴ 변수에 넣어주면 원본에 영향 없음.

---

- **Reshaping of arrays**

    `x.reshape(n)`: 배열 x의 형태를 n개인 1차원 array로 변경.

    > `n=(x,y,z)`: 3차원 형태.

    `x[:, np.newaxis]`: `(n,1)` 형태로 열의 수가 1이고 수직으로만 이루어진 배열 반환.

    `x.flatten()`: 배열 x의 형태를 1차원 배열로 반환.

---

- **Array joining and splitting**

    결합 기준 행/열의 size가 같아야 한다.

    `np.concatenate([x,y,z])`: 배열 x, y, z를 수직으로 결합.

    `,axis)=1`: 행과 열끼리 맞춰서 결합.

    `np.vstack([x,y])`: 차원이 다른 배열 x, y를 세로로 결합.

    `np.hstack([x,y])`: 차원이 다른 배열 x, y를 가로로 결합.

    `np.split(x, [n])`: 배열 x의 n행부터 array를 나눔.

    > `a,b,c = np.split(x, [2, 4])`: a는 0~1행, b는 2~3행, c는 4~행.

    `np.vsplit(x, [n])`: 배열 x를 세로로 나눔.

    `np.hsplit(x, [n])`: 배열 x를 가로로 나눔.

---

- **Ufunc**
    - **기본 연산**

        `np.add()`: array와 숫자/배열 덧셈. +

        `np.subtract()`: array와 숫자/배열 뺄셈. -

        `np.negative()`: array -부호. -

        `np.multiply()`: array와 숫자/배열 곱셈. *
    
        > `out=y`: size가 같은 배열 y나 y 슬라이싱에 결과를 반환.
    
        `np.divide()`: array와 숫자/배열 나눗셈. /
    
        `np.floor_divide()`: array를 숫자/배열로 나눈 몫. //
    
        `np.power()`: array의 숫자/배열 제곱. **
    
        `np.mod()`: array를 숫자/배열로 나눈 나머지. %
    
        `np.absolute(x)`: 배열 x의 절댓값.

        > == `abs(x)` or `np.abs(x)`

        `np.exp(x)`: 배열 x의 각 요소를 `e^x`로.

        `np.log10(x)`: 배열 x의 각 요소를 로그함수로.

        np.: `mean`, `std`, `var`

        np.: `pi`, `sin`, `cos`, `tan`, `arcsin`, `arccos`, `arctan`

    - **Aggregates**

        `np.add.reduce(x)`: 배열 x 요소들의 연산.

        `np.add.accumulate(x)`: 배열 x 요소들을 누적하여 연산.

        `np.add.outer(x, x)`: x의 요소만큼 행과 열을 만들고, 행과 열 연산 만큼 요소 값을 넣어줌.
    
        > `multiply`등 연산 가능.
        >
        > `.outer`: 두 배열의 모든 요소에 대해 연산 수행 및 확장.

        `np.sum(x)`: 배열 x의 모든 요소 더하기.
    
        > == `sum(x)` or `x.sum()`
    
        `sum`, `prod`, `mean`, `std`, `var`, min, max 등은 nan을 붙여서 쓸 수 있다.
    
        > 없는 값은 무시하고 연산.

    - **Min/Max**
    
        `np.min(x)`: 배열 x 요소의 최솟값.
    
        > == `min(x)` or `x.min()`
    
        `np.max(x)`: 배열 x 요소의 최댓값.
    
        > == `max(x)` or `x.max()`
    
        `,axis=0)`: 각 열에서 최소/최대.
    
        `,axis=1)`: 각 행에서 최소/최대.
    
        > x.max()의 형태는 안에 숫자만 적어도 됨.
    
    - **Broadcasting**
    
        array의 확장: ndim, shape, size가 다른 array들의 연산의 경우.

        `np.arange(3) + 5`: [0 1 2] + [5 5 5] => [5 6 7]

        `np.ones((3,3)) + np.arange(3)`: [[1 1 1], [1 1 1], [1 1 1]] + [0 1 2] => [[1 2 3], [1 2 3], [1 2 3]]

        `np.ones((3,1)) + np.arange(3)`: [[0], [1], [2]] + [0 1 2] => [[0 1 2], [1 2 3], [2 3 4]]

    - **Comparison**

        조건: `>=`, `!=`, `axis`, `&`, `|` 등.
        
        > 아래 이외에도 `sum` 등의 method에 사용 가능.
        
        `np.count_nonzero(x)`: 배열 x에 0이 아닌 요소 수를 반환.
        
        `np.isnan(x)`: 배열 x에 nan이 있는지 boolean 형태로 반환.
        
        `np.any(조건)`: 조건에 해당하는 값이 하나라도 있는지 boolean 형태로 반환.
        
        `np.all(조건)`: 모든 값이 조건에 해당하는지 boolean 형태로 반환.
        
        `np.sort(x)`: 배열 x를 오름차순으로 반환. 원본은 그대로.
    
        > `[::-1]`: 역순으로.
    
        `x.sort()`: 배열 x를 오름차순으로 변환.
    
        `np.argsort(x)`: 배열 x의 요소를 작은 순서로 위치값 반환.
    
        2차원 array에서는 각 행에 대해 정렬.
        
        `x[조건]`: 조건에 해당하는 배열 x의 요소들로 array를 만듦.