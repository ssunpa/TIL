# 목록과 표 형식 표현을 위한 태그

## 목록(List)

-   순서 없는 목록(Unordered List)
    ```html
    <!DOCTYPE html>
    <html>
        <body>
            <h1>Unordered List</h1>
            <ul>
                <li>iphone</li>
                <li>ipad</li>
                <li>macbook</li>
            </ul>
        </body>
    </html>
    ```
    `ul`tag를 사용한다.
-   순서 있는 목록(Ordered List)
    ```html
    <!DOCTYPE html>
    <html>
        <body>
            <h1>Unordered List</h1>
            <ol>
                <li>iphone</li>
                <li>ipad</li>
                <li>macbook</li>
            </ol>
        </body>
    </html>
    ```
    `ol` tag를 사용한다.
    `type` 어트리뷰트를 사용하여 순서를 나타내는 문자를 지정할 수 있다.
    -   "1"
        숫자(기본값)
    -   "A"
        대문자 알파벳
    -   "a"
        소문자 알파벳
    -   "I"
        대문자 로마숫자
    -   "i"
        소문자 로마숫자

`start` 어트리뷰트로 리스트의 시작값을 지정할 수 있다.

```html
<ol start="4">
    <li>iphone</li>
    <li>ipad</li>
    <li>macbook</li>
</ol>

<!-- 
4.iphone
5.ipad
6.macbook
-->
```

`reversed` 어트리뷰트를 지정하면 리스트의 순서값을 역으로 표현한다.

```html
<ol reversed>
    <li>iphone</li>
    <li>ipad</li>
    <li>macbook</li>
</ol>

<!-- 
3.iphone
2.ipad
1.macbook
-->
```

-   중첩 목록

```html
<!DOCTYPE html>
<html>
    <body>
        <h1>중첩 목록</h1>
        <ul>
            <li>Samsung</li>
            <li>
                Apple
                <ol>
                    <li>iphone</li>
                    <li>ipad</li>
                </ol>
            </li>
        </ul>
    </body>
</html>
```

목록 태그는 내비게이션 메뉴를 만들 때 자주 사용된다.

---

## 테이블(Table)

표(table)를 만들 때 사용하는 태그이다.

-   `table`
    표를 감싸는 태그
-   `tr`
    표 내부의 행 (table row)
-   `th`
    행 내부의 제목 셀 (table heading)
-   `td`
    행 내부의 일반 셀 (table data)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7f0376d3-bc4a-4da6-bc3c-405a2927d48a/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7f0376d3-bc4a-4da6-bc3c-405a2927d48a/Untitled.png)

테이블 태그의 어트리뷰트이다.

-   `border`
    표 테두리 두께를 지정
-   `rowspan`
    해당 셀이 점유하는 행의 수 지정
-   `colspan`
    해당 셀이 점유하는 열의 수 지정
