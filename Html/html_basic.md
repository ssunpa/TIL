# HTML5의 기본 문법

## 요소(Element)

HTML 요소는 시작 태그(start tag)와 종료 태그(end tag) 그리고 태그 사이에 위치한 content로 구성된다.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/856bf8da-cc51-4a65-accc-4afc4060a278/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/856bf8da-cc51-4a65-accc-4afc4060a278/Untitled.png)

HTML document는 요소(Element)들의 집합으로 이루어진다.

태그는 대소문자를 구별하지 않으나 소문자를 사용하는 것이 일반적이다.

---

## 요소의 중첩(Nested Element)

요소는 중첩될 수 있다. 즉, 요소는 다른 요소를 포함할 수 있다. 이때 부자 관계가 성립된다.

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8" />
    </head>
    <body>
        <h1>I wanna get a Macbook</h1>
        <p>hehe</p>
    </body>
</html>
```

위 예제를 보면 `html` 요소는 `body` 요소를 포함하며, `body` 요소는 `h1`과 `p` 요소를 포함하고 있다. 이 중첩 관계(부자 관계)로 웹페이지의 구조(structure)를 표현한다.

---

## 빈 요소(Empty Element)

content를 가질 수 없는 요소를 빈 요소(Empty element or Self-Closing element)라 한다. 빈 요소는 어트리뷰트(Attribute)만을 가질 수 있다.

대표적인 빈 요소는 아래와 같다.

-   br
    `<br>`요소는 텍스트 안에 줄 바꿈을 생성한다.
-   hr
    `<hr>`요소는 수평 가로선을 정의한다.
-   img
    `<img>` 요소는 이미지를 삽입할 때 사용하고 `src` 특성을 필수로 사용하여 포함하고자 하는 이미지로의 경로를 지정한다. `alt`특성은 필수는 아니지만 스크린 리더가 `alt`의 값을 읽어 사용자에게 이미지를 설명하므로, 접근성 차원에서 유용하다.
-   input
    `<input>` 요소는 웹 기반 양식에서 사용자의 데이터를 받을 수 있는 대화형 컨트롤을 생성. `type` 특성에 따라 동작 방식이 달라진다. 기본값은 `text`이다.
-   link
    `<link>` 요소는 현재 문서와 외부 리소스의 관계를 명시한다. 스타일 시트를 연결하는 등 사용한다.
-   meta
    `<base>`, `<link>`, `<script>`, `<style>`, `<title>` 과 같은 다른 메타관련 요소를 나타낼 수 없는 메타데이터를 나타낼 때 사용한다.

---

## 어트리뷰트(Attribute)

어트리뷰트(Attribute)이란 요소의 성질, 특징을 정의하는 명세이다. 요소는 어트리뷰트를 가질 수 있으며, 어트리뷰트는 시작 태그에 위치해야 하며 이름과 값의 쌍을 이룬다. 글로벌 어트리뷰트(HTML Global Attribute)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f5486167-0017-45c0-b849-3aa6f91dc668/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f5486167-0017-45c0-b849-3aa6f91dc668/Untitled.png)

```html
<img src="hello.jpg" width="100" height="120" />
```

`src`는 이미지의 경로와 파일명, `width`는 이미지의 너비, `height`는 이미지 높이 정보를 브라우저에 알려준다.

---

## 글로벌 어트리뷰트(HTML Global Attribute)

글로벌 어트리뷰트는 모든 HTML 요소가 공통으로 사용할 수 있는 어트리뷰트다. 대체로 모든 요소에 사용될 수 있다.

자주 사용되는 글로벌 어트리뷰트.

-   id
    유일한 식별자(id)를 요소에 지정한다. 중복 지정은 불가능하다.
-   class
    스타일시트에 정의된 class를 요소에 지정한다. 중복 지정이 가능하다.
-   hidden
    css의 hidden과는 다르게 의미상으로도 브라우저에 노출되지 않게 된다.
-   lang
    지정된 요소의 언어를 지정한다. 검색엔진의 크롤링 시 웹페이지의 언어를 인식할 수 있게 한다.
-   style
    요소에 인라인 스타일을 지정한다.
-   tabindex
    사용자가 키보드로 페이지를 내비게이션 시 이동 순서를 지정한다.
-   title
    요소에 관한 제목을 지정한다.

---

## 주석(Comments)

주로 개발자에게 코드를 설명하기 위해 사용되며 브라우저는 화면에 표시하지 않는 부분이다.

```html
<!-- 주석처리가 된 부분, 화면에 표시되지 않아요! -->
<p>I wanna get a Macbook</p>
```
