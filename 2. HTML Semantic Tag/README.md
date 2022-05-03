# HTML Semantic Tag

## 🤔 Semantic tag가 무엇일까요?

<details>
<summary>자세히 보기</summary>
<br>

**`main`**, **`header`**, **`section`**, **`footer`**... 등등 전부 **`div`**와 같은 동작을 합니다.

하지만 그냥 **`div`**를 나열해서 HTML을 구성하는 것 보다는 각각의 태그에 역할을 부여해서 조금 더 나은 코드를 작성할 수 있습니다.

그래서 의미있는 태그, 안에 들어갈 내용을 예측할 수 있는 태그를 **`Semantic Tag`**라고 부르고 사용하고 있습니다.

</details>

## 🤔 HTML5 tag를 설명해 주세요.

<details>
<summary>자세히 보기</summary>
<br>

모든 HTML 문서는 <!DOCTYPE> 선언으로 시작합니다. HTML5의 경우 <!DOCTYPE html> 이런 식으로 선언됩니다. 이 선언은 태그는 아니지만 브라우저가 어떤 타입을 받아들여야 할지를 알려주는 정보입니다.

HTML5의 필수 태그는 html, head, body 등이 있습니다. html 태그는 HTML문서의 가장 최상단에 위치하는 태그이며, head 태그에는 style, script, title, link, meta 태그 등이 들어갑니다. body 태그는 HTML 문서의 내용이 들어갑니다.

meta 태그는 head 부분에서 다른 태그들로 나타낼 수 없는 메타데이터를 나타내는 태그를 의미합니다. <meta name="keywords" content="ABC"> 와 같이 검색 엔진을 위한 키워드나 <meta name="description" content="OWEN">과 같이 문서에 대한 설명 등에 사용됩니다. 화면에는 별다르게 표시되는 내용이 없지만, 검색 엔진이나 브라우저에서 읽히는 것이 특징입니다.

</details>

## 🤔 Semantic tag가 왜 중요할까요?

<details>
<summary>자세히 보기</summary>
<br>

#### SEO에 좋은 영향을 줄 수 있습니다.

검색 엔진은 **`Semantic Markup`**을 페이지의 검색 랭킹에 영향을 줄 수 있는 중요한 키워드로 간주합니다. 그래서 자신의 페이지에 의미에 맞고, 적당한 위치에 의미론적 태그를 잘 사용한다면 검색엔진최적화, 즉 **`SEO(Search Engine Optimization)`**에 좋은 영향을 줄 수 있습니다.

#### **웹 접근성이 좋아집니다.**

시각 장애가 있는 사용자가 화면 판독기로 페이지를 탐색할 때 의미론적 마크업을 푯말로 사용할 수 있습니다.

또한 적절한 시멘틱 태그로 잘 만들어진 웹 이라면 스크린리더, 키보드로만 문제 없이 동작할 수 있습니다.

#### **개발자 경험**

그냥 **`div`**로 **`HTML`**을 채우는 것 보다는 의미있는 태그로 작성하는 것이 개발자 경험을 좋게합니다. 의미론적 태그를 사용해서 해당 태그 안의 내용을 제안할 수 있습니다.

또한 코드를 수정해야할 때도 **`div`**들로 나열된 코드에서 찾는 것 보다 의미있는 태그들 사이에서 찾는 것이 훨씬 빠르고 쉽습니다.

</details>

## 🤔 `article` vs `section`

<details>
<summary>자세히 보기</summary>
<br>

### `article`

**HTML `<article>` 요소**
는 문서, 페이지, 애플리케이션, 또는 사이트 안에서 독립적으로 구분해 배포하거나 **재사용할 수 있는 구획**을 나타냅니다. 사용 예제로 게시판과 블로그 글, 매거진이나 뉴스 기사 등이 있습니다.

하나의 문서가 여러 개의 `<article>`
을 가질 수 있습니다. 예컨대 사용자가 스크롤하면 계속해서 다음 글을 보여주는 블로그의 경우, 각각의 글이 `<article>` 요소가 되며, 그 안에는 또 여러 개의 `[<section>](https://developer.mozilla.org/ko/docs/Web/HTML/Element/section)`이 존재할 수 있습니다.

• 각각의 `<article>`을 식별할 수단이 필요합니다. 주로 제목(`[<h1>](https://developer.mozilla.org/ko/docs/Web/HTML/Element/Heading_Elements)`-`[<h6>](https://developer.mozilla.org/ko/docs/Web/HTML/Element/Heading_Elements)`) 요소를 `<article>`의 자식으로 포함하는 방법을 사용합니다.

• `<article>` 요소가 중첩되어 있을 때, 안쪽에 있는 요소는 바깥쪽에 있는 요소와 관련된 글을 나타냅니다. 예를 들어 블로그 글의 댓글은, 글을 나타내는 `<article>` 요소 안에 중첩한 `<article>`로 나타낼 수 있습니다.

### `section`

**HTML `<section>` 요소**는 HTML 문서의 독립적인 구획을 나타내며, 더 적합한 의미를 가진 요소가 없을 때 사용합니다. 보통 `<section>`은 제목을 포함하지만, 항상 그런 것은 아닙니다.

**참고**
: 요소의 콘텐츠를 외부와 구분하여 단독으로 묶는 것이 나아보인다면 `[<article>](https://developer.mozilla.org/ko/docs/Web/HTML/Element/article)` 요소가 더 좋은 선택일 수 있습니다.

- 요소의 콘텐츠를 따로 구분해야 할 필요가 있으면 `[<article>](https://developer.mozilla.org/ko/docs/Web/HTML/Element/article)` 요소를 고려하세요.
- `<section>` 요소를 일반 컨테이너로 사용하지 마세요. 특히 단순한 스타일링이 목적이라면 `[<div>](https://developer.mozilla.org/ko/docs/Web/HTML/Element/div)` 요소를 사용해야 합니다. 대개, 문서 요약에 해당 구획이 논리적으로 나타나야 하면 `<section>`이 좋은 선택입니다.

</details>

## 🤔 `button` vs `a`

<details>
<summary>자세히 보기</summary>
<br>

> 두 개다 버튼처럼 스타일링하면 버튼처럼 보입니다!

### `button`

어떤 특정 액션을 취하는 버튼이면 button태그를 사용합니다.

- 로그인 하기
- 로그아웃 하기
- 하트 버튼

### `a`

어디론가 순수하게 이동하는 버튼이면 a 태그를 사용하는게 낫습니다.

- 홈 버튼
- nav 태그안의 버튼들

</details>

## 🤔 `i` vs `em`

<details>
<summary>자세히 보기</summary>
<br>

> 둘 다 이텔릭체로 폰트 타입을 변환시킵니다.

`i` 태그는 그냥 시각적으로만 이탤릭체로 변경하고,

`em` 태그는 정말 강조하기를 원할 때 사용합니다. (강조라는 의미가 들어갑니다.)

</details>

## 🤔 `b` vs `strong`

<details>
<summary>자세히 보기</summary>
<br>

> 둘 다 bold체로 바꿉니다.

`b` 태그는 시각적으로만 bold채로 변경합니다.

`strong` 태그는 정말 강조하고 싶을 때 사용합니다.

</details>

## 🤔 `<ol>` vs` <ul>` vs `<dl>`

<details>
<summary>자세히 보기</summary>
<br>

<ul> 는 `순서가 없는` 리스트 (unordered- list)

<ol> 는 `순서가 있는` 리스트 <ordrdered-list)

<dl> 는 어떤 `단어에 대한 설명`을 나타내는  리스트

- 예시
    <ul>
    
    ```jsx
    <ul>
    		<li>사과</li>
    		<li>바나나</li>
    		<li><포도/li>
    </ul>
    ```
    
    <ol>
    
    ```jsx
    <ol>
    	<li>첫번쨰</li>
    	<li>두번째</li>
    	<li>세번째</li>
    </ol>
    ```
    
    <dl>
    
    ```jsx
    <dl>
    	<dt>HTML</dt>
    	<dd>웹페이지의 골격, 문서를 만들 때 사용</dd>
    
    	<dt>HTML</dt>
    	<dd>웹페이지의 골격, 문서를 만들 때 사용</dd>
    
    	<dt>HTML</dt>
    	<dd>웹페이지의 골격, 문서를 만들 때 사용</dd>
    </dl>
    ```

</details>

## 🤔 `img` vs `background-image`

<details>
<summary>자세히 보기</summary>
<br>

`img`: 웹 페이지 안에서 하나의 중요한 요소를 담고 있을 떄,

css `bacground-image` : 이미지가 문서의 일부분이 아니고, 스타일링 목적으로만 사용될 때

</details>

## 🤔 `alt`와 `title에` 대해 설명해 주세요.

<details>
<summary>자세히 보기</summary>
<br>

alt 특성은 이미지의 대체 텍스트 설명이며 필수는 아니지만 스크린 리더가 alt의 값을 읽어 사용자에게 이미지를 설명하므로 접근성 차원에서 유용합니다. 네트워크 오류, 콘텐츠 차단, 유효하지 않은 이미지, 지원하지 않는 형식 등의 이유로 이미지를 표시할 수 없는 경우에 브라우저가 alt 특성의 텍스트를 대신 보여줍니다. 또한 이미지를 텍스트로 복사-붙여넣기 할 때와 이미지 링크를 북마크 할 때도 alt값을 사용합니다.

title은 alt 특성을 대체하지 못합니다. alt의 값과  title값이 같을 경우 일부 스크린 리더가 같은 설명을 두 번씩 읽게 되므로 혼란스러울 수 있으므로 반복되는 것을 지양해야 합니다. title 특성은 보통 툴팁 형태로 표현되어 사용자가 볼 수 없는 경우도 있기 때문에 중요한 정보를 포함해야 하면 다른 방법을 사용해야합니다.

</details>

## 팀원들 정리 내용들

| 이름 | 링크                                                                          |
| ---- | ----------------------------------------------------------------------------- |
| 현수 | [시멘틱 태그에 대해서](https://junghyeonsu-dev.vercel.app/posts/Semantic-tag) |
| 지승 | -                                                                             |
| 서연 | -                                                                             |
| 동현 | -                                                                             |
| 재연 | -                                                                             |

[⬆️ 맨 위로 이동 ⬆️](#HTML-Semantic-Tag)
