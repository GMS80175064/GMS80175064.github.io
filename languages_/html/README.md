---
sort: 4
---

# HTML

- **용어**

  **태그**: `<시작태그이름>`,  `</종료태그이름>`

  **빈 태그**: `<img>`, `<br>`, `<hr>` 등

---

- **기본 구조**

  **`<!DOCTYPE html>`**: 현재 문서가 HTML5 문서임을 명시.

  **`<html>/`**: HTML 문서의 root 요소를 정의.

  - **`<head>/`**: HTML 문서의 metadata를 정의

    metadata: HTML 문서에 대한 정보로 웹 브라우저에는 직접 표현되지 않는 정보.

    > title, style, meta, link, script, base 태그 등을 이용해 표현.

    **`<title>/`**: HTML 문서의 title(제목)을 정의.

    > 웹브라우저의 툴바, 즐겨찾기 제목, 검색 엔진 결과 페이지 제목으로 표시.

  - **`<body>/`**: 웹 브라우저를 통해 보이는 내용.

    **`<h1>`~`<h6>/`**: 제목(heading)을 나타냄.

    **`<p>/`**: paragraph(단락), 문단을 나타냄.

    > 태그 내 작성된 띄어쓰기, 줄 나누기는 하나의 띄어쓰기로만 표현.

---

- **요소 구조**

  element(요소)는 여러 attribute(속성)을 가진다.

  > 속성: 해당 요소에 대한 추가적인 정보를 제공.
  >
  > 시작 태그 내에서 시작, 종료 태그에 끝. 언제나 소문자.

  **HTML 요소 구조**: `<p class="para">TCPschool.com</p>`

  > **`<태그이름 속성명="속성값">`**

  예시: `<img src="quotes.jpg" alt="이미지가 없어요">`

  > `alt`: 이미지를 불러올 수 없을 때 이미지 대신 모이는 문자열 설정.

---

- **텍스트 요소**

  - **\<p>/ 내부**

    - **Paragraph(단락)**

      **`<br>`**: 빈 태그로, 줄을 나누는 역할.

      **`<pre>/`**: 작성한 텍스트 서식(줄 나누기 등)을 그대로 표현.

      **`<hr>`**: 빈 태그로, horizontal rule, 수평 가로 구분선 긋기.

    - **Formatting(서식)**: 텍스트에 다양한 효과를 주는 태그.

      **`<p>/`** 태그 내부에서 텍스트를 꾸며줌.

      > 내용 강조: 검색엔진이 강조된 텍스트를 더 중요하게 인식.

      **`<b>/`**: 화면 텍스트를 굵게 표현.

      **`<strong>/`**: 텍스트를 굵게 표현 및 내용이 중요하다는 의미도 포함.

      **`<i>/`**: 화면 텍스트를 이탤릭체로 표현.

      **`<em>/`**: 텍스트를 이챌릭체로 표현 및 내용이 중요하다는 의미도 포함.

      **`<mark>/`**: 하이라이팅 효과 적용.

      **`<del>/`**: 삭제효과. 텍스트 중앙에 가로줄 긋기.

      **`<ins>/`**: 삽입효과. 텍스트 밑에 가로줄 긋기

      **`<sup>/`**: 위첨자 표현.

      **`<sub>/`**: 아래첨자 표현.

    - **Quotation(인용구)**

      **`<q>/`**: 짧은 인용구. 앞뒤에 큰따옴표가 붙음.

      **`<blockquote>/`**: 인용 부분을 별도의 단락으로 구분.

      그 외: 축약형 표현, 주소 표현 등등.

  - **Comment(주석)**

    **`<!-- 주석내용 -->`**: 파이썬의 # 같은 친구.

    > 하지만 종료 표시가 있으니 여러 줄에 걸쳐서도 인식 가능.

  - **Entity: 예약어를 기존 의미 그대로 사용**

    **`&lt;`**: <

    **`&gt;`**: >

    **`&amp;`**: &

    특수문자, 발음 부호, 기탕 등등 검색해보셈.

  - **Character set(문자셋)**

    HTML5에서 UTF-8의 경우 : `**<meta charset="UTF-8">`**

    > UTF-8: 모든 문자를 표현할 수 있는 유니코드 문자를 지원하는 HTML5의 기본 문자셋.
