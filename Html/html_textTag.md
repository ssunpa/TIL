# 텍스트 관련 태그

## 제목(Headings) 태그

Heading 태그는 제목을 나타낼 때 사용하며 h1부터 h6까지의 태그가 있다. 숫자가 작을수록 중요한 제목을 의미하며, 글자의 크기가 크다.

시맨틱 웹의 의미를 살려서 제목 이외에는 사용하지 않는 것이 좋다. 검색엔진은 제목 태그를 중요한 의미로 받아들일 가능성이 크다.

---

## 글자 형태(Text Formatting) 태그

-   b
    bold체를 지정한다. 의미론적(Semantic) 중요성의 의미는 없다.
-   strong
    b tag와 동일하게 bold체를 지정하지만 의미론적(Semantic) 중요성의 의미를 갖는다.
-   i
    Italic체를 지정한다. 의미론적(Semantic) 중요성의 의미는 없다.
-   em
    emphasized text를 지정한다. 외양은 i tag와 동일하지만 의미론적(Semantic) 중요성의 의미를 갖는다.
-   small
    small text를 지정한다.
-   mark
    highlighted text를 지정한다. 해당 글자 배경색 생성
-   del
    deleted (removed) text를 지정한다. 가로선 생성
-   ins
    inserted (added) text를 지정한다. 밑줄 생성
-   sub/sup
    sub tag는 subscripted(아래에 쓰인) text를 sup tag는 superscripted(위에 쓰인) text를 지정한다.

---

## 본문 태그

-   p
    단락(Paragraphs)을 지정한다
-   br
    줄바꿈(line break 를 지정한다. empty element로 종료 태그가 없다.
    HTML에서는 1개 이상의 연속된 공백(space)을 삽입하여도 1개의 공백으로 표시된다. 1개 이상의 연속된 줄바꿈(enter)도 1개의 공백으로 표시된다.
    연속적 공백은 `&nbsp;`를 사용하여 삽입한다.
-   pre
    형식화된(preformatted) text를 지정한다. pre tag 내의 content는 작성된 그대로 브라우저에 표시된다.
-   hr
    수평줄을 삽입한다.
-   q
    짧은 인용문(quotation)을 지정한다. 브라우저는 인용부호("",quotation marks)로 content를 감싼다.
-   blockquote
    긴 인용문 블록을 지정한다. 브라우저는 blockquote 요소를 들여쓰기한다. css를 이용하여 다양한 style을 적용할 수 있다.
