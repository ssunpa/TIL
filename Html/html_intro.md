## HTML5

-   HTML(HyperText Markup Language)은 웹 페이지를 기술하기 위한 마크업 언어이다.
    -   Markup Language
        태그 등을 이용하여 문서나 데이터의 구조를 명기하는 언어의 한 가지로, 일반적으로 데이터를 기술하는 정도로만 사용되기에 프로그래밍 언어와는 구별된다.
-   웹페이지의 내용(content)와 구조(structure)를 담당하는 언어로써 HTML 태그를 통해 정보를 구조화 하는 것이다.
-   아래의 기능을 포함하고 있다.
    -   멀티미디어(Multimedia)
        플래시와 같은 플로그인의 도움없이 비디오 및 오디오 기능을 자체적으로 지원한다.
    -   그래픽(Graphics & Effects)
        SVG, canvas를 사용한 2차원 그래픽과 CSS3, WebGL을 사용한 3차원 그래픽을 지원한다.
    -   통신(Connectivity)
        이전까지의 HTML은 단방향 통신만이 가능하였으나 HTML5는 서버와의 소켓 통신을 지원하므로 서버와의 양방향 통신이 가능하다.
    -   디바이스 접근(Device acess)
        카메라, 동작센서 등의 하드웨어 기능을 직접적으로 제어할 수 있다.
    -   오프라인 및 저장소(Offline & Storage)
        오프라인 상태에서도 애플리케이션을 동작시킬 수 있다. 이는 HTML5가 플랫폼으로써 사용될 수 있음을 의미한다.
    -   시맨틱 태그(Semantics)
        HTML 요소의 의미를 명확히 설명하는 시맨틱 태그를 도입하여 브라우저, 검색엔진, 개발자 모두에게 콘텐츠의 의미를 설명할 수 있다. 이를 통해 HTML 요소의 의미를 명확히 해석하고 그 데이터를 활용할 수 있는 시맨틱 웹을 실현할 수 있다.
    -   CSS3
        HTML5는 CSS3를 완벽하게 지원한다.

---

## Hello HTML5

-   HTML5 문서는 대소문자 구분 없이 `<!DOCTYPE html>` 으로 시작하여 선언할 수 있다.
-   실제적인 HTML document는 `<html>`과 `</html>` 사이에 기술한다.
-   `<head>`와 `</head>` 사이에는 document title, 외부 파일의 참조, 메타데이터의 설정 등이 위치하며 이 정보들은 브라우저에 표시되지 않는다.
    -   metadata
        HTML 문서에 대한 정보로 웹 브라우저에는 직접적으로 표현되지 않는 정보를 의미한다.
-   웹브라우저에 출력되는 모든 요소는 `<body>`와 `</body>` 사이에 위치한다.

```html
<!DOCTYPE html>
<html>
    <head>
        <meta chrset="utf-8" />
        <title>Hello HTML5!</title>
    </head>
    <body>
        <h1>Hello HTML5!</h1>
        <p>안녕 HTML5!</p>
    </body>
</html>
```

-   HTML 문서는 .html 확장자를 갖는 순수한 텍스트 파일이다.
