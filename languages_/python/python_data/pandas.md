---
sort: 2
---

# Pandas

- **Creating data**
    - **DataFrame**

        DataFrame은 테이블과 같다.
        여러 개의 Series가 합쳐진 것.

        `pd.DataFrame()`: DataFrame 생성.

        `,index=[])`: 인덱스 이름 설정.

    - **Series**

        Series는 리스트와 같다.
        Series는 열이 하나다.

        `Series([])`: Series 생성.
        
        > `,index=[])`: 각 인덱스 행 이름 설정.
        >
        > `,name='')`: Series 이름 지정. 열 이름과 마찬가지.
    

---

- **Reading data**
    
    - **pandas.read()**
    
        `pd.read_csv()`: csv 파일 열기
    
        `pd.read_xlsx()`: xlsx 파일 열기.
    
        `,thousands=',')`: 천 단위 구분 없애기.
    
        `,encoding='')`: 유니코드 지정.

        > `utf-8`, `euc-kr` 등.

        `,header=2)`: 2번 행을 column으로 지정.

        `,index_col=0)`: 0번 열 삭제 후 인덱스로 지정.

        `,usecols=[])`: 실제 필요한 칼럼만 로딩.

    - **데이터 불러오기/저장하기**
    
        `x.head()`: 위 5행만 반환.
        
        > 괄호 안 숫자로 조정.

        `x.shape()`: `(행, 열)` 형태 반환.
    
        `x.to_csv()`: 데이터 x를 csv 파일로 저장. 주소 지정 가능.
    

---

- **Indexing**
    - **Indexing 기초**

        `x.man`: 데이터 프레임 `x`의 `'man'` 열을 Series로 인덱싱.
    
        > == `x['man']`: 열 이름 선택도 가능하다는 장점.
    
        `x['a'][0]`: 데이터프레임 `x`의 `a`열 `0`번 행 인덱싱.
    
        `&`, `|`와 같은 연산자를 사용하려면 괄호로 수식들을 묶어줘야 한다.

        > `x[(수식)&(수식)]`

        `x[x.i=='a']`: 조건문에 맞는 행들만 반환.

    - **iloc:** index-based selection

        integer position을 통해 열 값 찾기

        `.iloc[n]`: `n`번 행 반환.

        `.iloc[n,i]`: `n`행, `i`열 값들 반환.

    - **loc:** label-based selection

        label을 통해 열 값 찾기

        `.loc[n]`: 인덱스가 `n`인 행 반환.

        `.loc[n,'i']`: 인덱스가 `n`인 행의 컬럼 `'i'`에 해당하는 값 반환.

        참고로 `loc[0:1000]`은 1001개의 요소를 갖는다.

    - **Assigning**

        `x['a']='b'`: 모든 컬럼 `a`에 값 `b` 할당.

        `x.iloc`를 통해 행을 추가/변경도 가능.
    

---

- **Methods and Functions**
    - **Summary Functions**

        `.describe()`: 자료 요약통계량 출력.

        `.info()`: 데이터프레임 정보 출력.

        `.shape()`: (행, 열) 반환

        `.unique()`: unique 값 ndarray로 반환.
    
        > unique: 중복되지 않은 column내 값.
    
        `.value_counts()`: unique 값 별로 개수 세기.
    
        `.index`: 인덱스 명과 dtype 반환.
    
        `.columns`: 컬럼 명과 dtype 반환.
    
        > `[]`로 지정 가능.
    
    - **Sort**

        `.groupby()`: 컬럼(들)에 따라 그룹화.
    
        > 연산 안하면 그룹화만 함.
    
        `.sort_values('컬럼')`: 컬럼을 오름차순으로 정렬.

        > `ascending=`, `axis=`, `inplace=`, `na_position=` 등
    
        `.value_counts()`: 유일한 값별로 개수 세기.
    
        > `sort=`, `ascending=` 
    
        `.isin(['a','b'])]`: 컬럼 `i`의 값이 리스트 안에 있는 행들만 반환.

        > `notnull()`, `isnull()`
    
    - **Manipulating index**
    
        `.set_index()`: 특정 컬럼을 인덱스로 설정.
    
        > `drop=`, `inplace=`
    
        `.reset_index()`: 인덱스를 리셋하고 기존 인덱스를 데이터프레임의 0번 열로 전송.
    
        > `drop=`, `inplace=`
    
        `.rename({'기존':'새이름'})`: 기존 컬럼/인덱스 이름을 새이름으로 바꿈.
    
        > `index=` or `columns=`, `inplace=`
        >
        > == `.index=[]` or `.columns=[]`

    - **Nan**

        `.fillna(n)`: 공백(Nan) 값을 n으로 변경.
    
        `.isnull()`: Nan 값이 있는지 판단.
    
        `.notnull()`: Nan 값이 없는지 판단.

        `.dropna()`: 결측값이 존재하는 행 삭제

        > `axis=`, `how=`, `thresh=`

    - **Drop / Duplicated**
    
        `.drop('col', axis=1)`: 특정 열 삭제.
    
        > `axis=`, `inplace=`
    
        `.drop_duplicates()`: 중복을 삭제.

        > `subset=`, `keep=`

        `.duplicated()`: 중복된 행에 대한 boolean 값 반환.
    
    - **Append / Merge**
    
        `.append()`: 마지막 행에 더해줌.
    
        > `ignore_index=True`
    
        loc나 iloc로 지정해서 넣어주기도 가능.

        `.concat(df1, df2)`: 열 이름 기반으로 행에 그대로 합치기. 없는 컬럼의 값은 Nan으로 채움.

        > `axis=`

        - Merge: `.merge(df1, df2)`:
    
        `how='inner'`: 교집합끼리만 합침.
    
        `how='outer'`: 합집합으로 전체 붙이기.
    
        `how='left'`: 왼쪽을 기준으로 같은 것만 가져오고 없는 것은 Nan으로 채움.

        `on='a'`: how 방향의 컬럼 a를 기준으로 합치기.
    
        `left_on='a'`: 왼쪽의 a컬럼과
    
        `right_on='b'`: 오른쪽의 b컬럼은 사실 같으니 붙여줘라.

        - join

        현재 데이터에 덧붙이는 것으로, 기본적으로 left join을 가지고 있음.

        `df.join(df2)`: df를 기준으로 df2 붙이기.
    
        > `how=`
    
    - **Dtype**
    
        `.dtypes`: 각 열의 데이터 타입 반환.
    
        `.convert_dtypes()`: object형 변수까지 분명하게 정리해줌.
    
        `.astype({'col':'float'})`: 컬럼을 특정 타입으로 반환.
    
        > `x[] = x[].astype()` 형식을 통해 변환 가능.
    
        `pd.to_numeric()`: 컬럼의 숫자를 숫자 타입으로, 그 외는 Nan으로 변환.
    
        > `,errors='coerce')`: 에러 처리를 강제적으로 시행, Nan으로 변경.
    
        `.apply(pd.to_numeric, errors='coerce).fillna(0)`: 데이터 전체 숫자 타입 변환.
    
    - 기타
    
        `.transpose()`: 행과 열을 바꿔 반환.
        
        > == `.T`: numpy에서도 가능.