---
sort: 3
---

# Scrapy

```tip
수정 중~~~~
```



- **Scrapy란?**

  Crawling/Scraping의 아주 대표적인 프레임워크 (외국에서 많이 쓰인다고 함)

  터미널을 이용하여 크롤링을 진행한다.

- **프레임워크란?**

  기존 크롤링: 빈 코드 칸에 우리가 직접 코드를 써내려가며 크롤링함.

  프레임워크: 함수와 코드가 미리 작성되어 있는 곳에, 사용법에 따라 일부분만 채워 놓으면 되는 프로그램.

  즉 코드는 이미 짜놨으니 크롤링할 주소, selector, 크롤링 조건 등만 채워넣으면 됨.

  > 제어 역전: 우리가 작성한 프로그램을 Scrapy 쪽에서 호출하고 실행.

---
- **순서**

  spider에서 사이트 크롤링 -> 선택한 데이터를 item으로 가져옴, yield -> pipeline에서 후처리 -> 아이템으로 저장.

  1. **프로젝트 생성**: `scrapy startproject 프젝이름`

  2. **크롤러(spider) 생성**: `scrapy genspider 이름 주소`

  3. **css로 shell에서 데이터 살펴보기**: `scrapy shell 주소`

  4. **크롤러(spider.py) 및 크롤링할 아이템(items.py) 설정**

  5. 필요하다면 **설정(settings.py)과 크롤링조건(pipelines.py) 설정**

  6. **크롤러 실행**: `scrapy crawl 스파이더이름`

  7. **item 저장**: `scrapy crawl 스파이더이름 -o 저장파일이름.파일형식 -t 파일형식`

---

- **파일들**

  **spider.py**: items.py에서 선언된 아이템에 맞게 parse 메서드를 적용하여 **크롤링**. **해당 아이템을 items로** 전달.

  **items.py**: **어떤 아이템을 가져올 것인지**를 선언. 즉 item을 정의.

  **settings.py**: 인코딩, pipeline 활성화 등의 **설정** 변경.

  **pipelines.py**: 크롤링 조건 설정, 아이템 **데이터의 후처리**를 위해 사용되는 기능.

  middlewarse.py: 심화 학습 하면 알아보자...

---

0. **설치**

   ```powershell
   !pip install scrapy
   
   # 혹시 위 명령 실행 안될시 아래 명령까지 사용 (윈도우)
   # pip install --upgrade setuptools
   # pip install pypiwind32
   # pip install twisted[tls]
   ```

1. **프로젝트 생성**

   ```powershell
   #scrapy startproject <프로젝트 이름> -> scrapy.cfg가 있는 바로 아래 경로로 이동
   scrapy startproject st11
   cd st11
   ```

2. **크롤러(spider) 작성**

   ```powershell
   # 하부 디렉토리에서 아래 명령 수행
   # scrapy genspider <크롤러이름> <크롤링 페이지주소>
   scrapy genspider st11_best "www.11st.co.kr/browsing/BestSeller.tmall?method=getBestSellerMain"
   
   # 주소에서 http://는 제외. 만약 https://만 지원하는 사이트의 경우에는 적어줘야 함.
   # 참고: https의 s는 secure로 보안이 강화된 것에 대한 인터넷의 약속? 같은거라 생각하면 됨.
   # 그리고 여러가지 사이트를 크롤링 할 때에는 "https://"를 붙여주게 됨. 이후 참고.
   ```

   ```python
   #st11_all.py: 기본 형태
   import scrapy
   
   class St11Spider(scrapy.Spider):
       name = 'st11_best' # spider의 이름을 설정. 자동으로 설정되며 이후 spider 실행에 사용됨.
       # 크롤링 대상 도메인 리스트를 지정. 다수의 웹사이트를 크롤링할 경우는 지우는 것도 방법.
       allowed_domains = ['www.11st.co.kr/browsing/BestSeller.tmall?method=getBestSellerMain'] 
       # 크롤링을 시작할 URL 목록. 여러개 지정 가능.
       #start_urls = ['http://www.11st.co.kr', 'http://www.naver.com']
       start_urls = ['http://www.11st.co.kr/browsing/BestSeller.tmall?method=getBestSellerMain/']
       
       def parse(self, response): # 추출한 웹 페이지 요청에 대한 response의 처리를 위한 콜백 함수.
           print(response.text)
           #pass
   ```

3. **크롤러 실행**

   ```
   scrapy crawl st11_best
   ```

4. **Shell: css 경로 선택**

   ```powershell
   # scrapy shell: 주피터 노트북 같은, 터미널에서 제공해주는 인터페이스.
   # 가져온 데이터에서 여러가지 문법을 이용하여 특정 데이터를 추출해보고 테스트할 수 있음. 특히 CSS나 XPath
   
   scrapy shell "http://www.11st.co.kr/browsing/BestSeller.tmall?method=getBestSellerMain"
   # 윈도우는 작은 따옴표가 안됨. 아예 따옴표를 없애거나, 큰따옴표("")를 이용
   # 여기도 http://는 지워도 됨.
   ```

   ```powershell
   # shell 명령어: 위 명령 실행하면 바로 위에 [s]로 설명이 약간 적혀있음.
   
   view(response) # 기본 브라우저에서 위 경로를 열어줌.
   shelp() # shell에서 사용가능한 명령들을 알려줌.
   response.url # 크롤링할, 경로의 주소를 출력.
   response.text # 해당 주소를 html 파일로 출력.
   
   response.body
   response.encoding
   response.status
   
   exit # shell에서 나감.
   ```

   ```powershell
   # response.css(): css selector로 데이터 가져오기
   response.css('head > title').get() # 하나만
   response.css('head > title').getall() # 전부다, 리스트 형태로 (title은 하나이긴 함)
   response.css('head > title::text').get() # text만 가져오기
   response.css('div.best-list li a::text').getall() # 베스트 상품의 이름을 리스트 형태로, text로 다 가져오기
   response.css('div.best-list li a::attr("href")')[3].get() # 3번째 베스트 상품의 주소만 가져오기
   response.css('div.best-list li a::text')[1].re('(/w+)') # re: 정규표현식으로 데이터 가져오기
   ```

5. **데이터 처리**

   ```python
   # items.py: 기본 형태
   import scrapy
   
   class St11Item(scrapy.Item):
       # define the fields for your item here like:
       # name = scrapy.Field()
       pass
   
   # items.py: 아이템 정의
   import scrapy
   
   class St11Item(scrapy.Item):
       title = scrapy.Field() # 자신이 쓸 아이템의 필드를 정의: 그냥 변수 이름만 적당히
       prices = scrapy.Field()
   ```

   ```python
   # st11_all.py
   import scrapy
   from st11.items import St11Item
   
   class St11BestSpider(scrapy.Spider):
       name = 'st11_best'
       allowed_domains = ['www.11st.co.kr/browsing/BestSeller.tmall?method=getBestSellerMain']
       start_urls = ['http://www.11st.co.kr/browsing/BestSeller.tmall?method=getBestSellerMain']
   
       def parse(self, response):
           titles = response.css('div.best-list li > a::text').getall()
           prices = response.css('div.best-list ul li div.item_price div.s-price strong span::text').getall()
           
           for num, title in enumerate(titles):
               doc = St11Item()
               doc['title'] = title
               doc['price'] = prices[num]
               yield doc
   ```

   











