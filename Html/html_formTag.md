# 폼 태그

## form

form 태그는 사용자가 입력한 데이터를 수집하기 위해 사용되며 `input`, `textarea`, `button`, `select`, `checkbox`, `radio`, `submit button` 등의 입력 양식 태그를 포함할 수 있다.

attribute

-   action
    value 값으로 URL이 쓰인다. 입력 데이터(form data)가 전송될 URL을 지정한다.
-   method
    value 값으로 get과 post가 쓰이고, 이는 입력 데이터(form data) 전달 방식을 지정한다.
    GET과 POST는 HTTP 프로토콜을 이용해서 사용자 입력 데이터를 서버에 전달하는 나타내며 HTTP request method라고 한다.
    -   GET
        -   GET 방식은 전송 URL에 입력 데이터를 쿼리 스트링(Query String)으로 보내는 방식이다.
        -   전송 URL 바로 뒤에 '?'를 통해 데이터의 시작을 알려주고, key-value형태의 데이터를 추가한다. 1개 이상의 전송 데이터는 '&'로 구분한다.
        -   URL에 전송 데이터가 모두 노출되기 때문에 보안에 문제가 있으며 전송할 수 있는 데이터의 한계가 있다.(최대 255자)
        -   REST API에서 GET 메소드는 모든 또는 특정 리소스의 조회를 요청한다.
    -   POST
        -   POST 방식은 Request Body에 담아 보내는 방식이다.
        -   URL에 전송 데이터가 모두 노출되지 않지만 GET에 비해 속도가 느리다.
        -   REST API에서 POST 메소드는 ㅌㄱ정 리소스의 생성을 요청한다.

---

## input

사용자로부터 데이터를 입력받기 위해 사용된다.

type 어트리뷰트에 의해 구분된다. form 태그 내에 존재하여야 입력 데이터를 전송할 수 있으나 ajax를 사용할 시에는 form 태그 내에 존재하지 않아도 된다.

서버에 전송되는 데이터는 name 어트리뷰트를 키로, value 어트리뷰트를 값으로 하여 key=value의 형태로 전송된다.

type 어트리뷰트

-   button
    button 생성
    ```html
    <DOCTYPE html>
        <html>
            <body>
                <h3>button</h3>
                <input
                    type="button"
                    value="Click here"
                    onclick="alert('hello<3')"
                />
            </body></html
    ></DOCTYPE>
    ```
-   checkbox
    checkbox 생성
    ```html
    <DOCTYPE html>
        <html>
            <body>
                <h3>checkbox</h3>
                <input type="checkbox" name="AAPL1" vlaue="iphone" checked />
                iphone <br />
                <input type="checkbox" name="AAPL2" vlaue="ipad" /> ipad <br />
                <input type="checkbox" name="AAPL3" vlaue="macbook" /> macbook
                <br />
            </body></html
    ></DOCTYPE>
    ```
-   color
    컬러 선택 생성
    ```html
    <DOCTYPE html>
        <html>
            <body>
                <h3>color</h3>
                <input type="color" name="selectcolor" />
            </body></html
    ></DOCTYPE>
    ```
-   date
    date control(년원일) 생성
    ```html
    <DOCTYPE html>
        <html>
            <body>
                <h3>date</h3>
                <input type="date" name="hbd" />
            </body></html
    ></DOCTYPE>
    ```
-   datetime
    data & time control(년월일시분초) 생성
    ```html
    <DOCTYPE html>
        <html>
            <body>
                <h3>datetime</h3>
                <input type="datetime" name="htdtime" />
            </body></html
    ></DOCTYPE>
    ```
-   datetime-local
    지역 date & time control(년월일시분초) 생성
    ```html
    <DOCTYPE html>
        <html>
            <body>
                <h3>datetime-local</h3>
                <input type="datetime-local" name="hbdtime" />
            </body></html
    ></DOCTYPE>
    ```
-   email
    이메일 입력 form 생성
    ```html
    <DOCTYPE html>
        <html>
            <body>
                <h3>email</h3>
                <input type="email" name="myemail" />
            </body></html
    ></DOCTYPE>
    ```
-   file
    파일 선택 form 생성
    ```html
    <DOCTYPE html>
        <html>
            <body>
                <h3>file</h3>
                <input type="file" name="myfile" />
            </body></html
    ></DOCTYPE>
    ```
-   hidden
    감추어진 입력 form 생성
-   image
    이미지로 된 submit button 생성
-   month
    월 선택 form 생성
-   number
    숫자 입력 form 생성
-   password
    password 입력 form 생성
-   radio
    radio 버튼 생성
-   range
    범위 선택 form 생성
-   reset
    초기화 button 생성
-   search
    검색어 입력 form 생성
-   submit
    제출 button 생성
-   tel
    전화번호 입력 form 생성
-   text
    텍스트 입력 form 생성
-   time
    시간 선택 form 생성
-   url
    url 입력 from 생성
-   week
    주 선택 입력 form 생성

---

## select

복수개의 리스트에서 복수개의 아이템을 선택할 때 사용한다.

서버에 전송되는 데이터의 select 요소의 name 어트리뷰트를 키로, option 요소의 value 어트리뷰트를 값으로 하여 key=value의 형태로 전송된다.

-   select tag
    select form 형성
-   option tag
    option 생성
-   optgroup
    option을 그룹화

---

## textarea

textarea 태그는 여러 줄의 글자를 입력할 때 사용한다.

```html
<!DOCTYPE html>
<html>
    <body>
        <textarea name="message" rows="10" cols="30">
Write something here</textarea
        >
    </body>
</html>
```

---

## button

button 태그는 클릭할 수 있는 버튼을 생성한다. `<input type="button">`과 유사하지만 input 태그는 빈 태그인 반면 button 태그는 그렇지 않다.

type 어트리뷰트는 반드시 지정하는 것이 바람직하며 어트리뷰트값으로 button, reset, submit를 지정할 수 있다.

```html
<!DOCTYPE html>
<html>
    <body>
        <button type="button" onclick="alert('Hey <3')">Click here</button>

        <input type="button" value="Click here" onclick="alert('Hey <3')" />
    </body>
</html>
```

input 태그와는 달리 콘텐츠로 문자열은 물로 HTML 요소를 받을 수도 있다는 장점이 있다.

---

## fieldset/legend

fieldset 태그는 관련된 입력 양식들을 그룹화할 때 사용한다. legend 태그는 fieldset 태그 내에서 사용되야 하며 그룹화된 fieldset의 제목을 정의한다.

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8" />
    </head>
    <body>
        <fieldset>
            <legend>Login</legend>
            Username <input type="text" name="username" /> Password
            <input type="text" name="password" />
        </fieldset>
    </body>
</html>
```
