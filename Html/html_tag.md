# 기본 태그

## 문서 형식 정의 tag

```html
<!DOCTYPE html>
```

문서 형식 정의(Document Type Definition, DTD) 태그는 출력할 웹 페이지의 형식을 브라우저에게 전달한다.

문서의 최상위에 위치해야 하며 대소문자를 구별하지 않는다.

---

## html tag

html 태그는 모든 HTML 요소의 부모 요소이며, 웹페이지에 단 하나만 존재한다. `<!DOCTYPE html>` 은 예외!

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8" />
        <title>문서 제목</title>
    </head>
    <body>
        브라우저에 표시할 콘텐츠 기술
    </body>
</html>
```

html은 `<html lang="ko">`와 같은 글로벌 어트리뷰트를 지원한다.

---

## head tag

head 요소는 메타데이터를 포함하기 위한 요소이며 웹페이지에 단 하나만 존재한다. 메타데이터는 HTML 문서의 title, style, link, script에 대한 데이터로 화면에 표시되지 않는다.

head 요소에는 메타데이터 이외의 화면에 표시되는 일체의 요소를 포함시킬 수 없다.

---

## title tag

title 요소는 문서의 제목을 정의한다. 정의된 제목은 브라우저의 탭에 표시된다.

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8" />
        <title>탭에 표시될 문서 제목</title>
    </head>
    <body>
        브라우저에 표시할 콘텐츠 기술
    </body>
</html>
```

---

## style tag

style 요소에는 HTML 문서를 위한 style 정보를 정의한다.

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8" />
        <title>문서 제목</title>
        <style>
            body {
                background-color: blue;
                color: white;
            }
        </style>
    </head>
    <body>
        브라우저에 표시할 콘텐츠 기술
    </body>
</html>
```

---

## link tag

link 요소에는 외부 리소스와의 연계 정보를 정의한다. 예로 HTML과 외부 CSS 파일을 연계할 때 사용한다.

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8" />
        <title>문서 제목</title>
        <link rel="stylesheet" href="style.css" />
    </head>
    <body>
        브라우저에 표시할 콘텐츠 기술
    </body>
</html>
```

---

## script tag

script 요소에는 client-side JavaScript를 정의한다.

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8" />
        <script>
            document.addEventListener('click', function () {
                console.log('hey');
            });
        </script>
    </head>
    <body>
        브라우저에 표시할 콘텐츠 기술
    </body>
</html>
```

src 어트리뷰트를 이용해 외부 JavaScript 파일을 불러올 수 있다.

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8" />
        <title>문서 제목</title>
        <script src="app.js"></script>
    </head>
    <body>
        브라우저에 표시할 콘텐츠 기술
    </body>
</html>
```

---

## meta tag

meta 요소는 description, keywords, author, 기타 메타데이터 정의에 사용된다. 메타데이터는 부라우저, 검색엔진 등에 의해 사용된다.

-   웹페이지의 설명을 정의
    ```html
    <meta name="description" content="about HTML" />
    ```
-   검색엔진이 사용할 keywords를 정의
    ```html
    <meta name="keywords" content="HTML, CSS, JavaScript" />
    ```
-   웹페이지의 저자를 명시
    ```html
    <meta name="author" content="Choi" />
    ```
-   웹페이지를 30초 마다 Refresh
    ```html
    <meta http-equiv="refresh" content="30" />
    ```

---

## body tag

HTML 문서의 내용을 나타내며 웹페이지에 단 하나만 존재한다. 메타데이터를 제외한 웹페이지를 구성하는 대부분의 요소가 body 요소 내에 기술된다.

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8" />
        <title>문서 제목</title>
    </head>
    <body>
        브라우저에 표시할 콘텐츠 기술
    </body>
</html>
```
