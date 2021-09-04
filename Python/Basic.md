# 기초

## 문자열과 수

-   자료의 종류와 문자열 표현

    문자가 모인 단어나 문장 또는 단락 등을 문자열(string)이라고 한다. 따옴표로 둘러싸면 모두 문자열 취급한다.

    ```python
    >>>print("Hello World!")
    Hello World!
    >>>print('Hello Python!')
    Hello Python!
    ```

    작은 따옴표와 큰 따옴표 모두 사용가능하지만 앞뒤를 동일하게 사용하여야 한다.

-   문자열 연산자 `+`,`*`와 주석처리

    문자열을 연결하고 싶다면 연결연산자 `+`를 사용, 문자열을 반복하고 싶다면 반복연산자 `*`를 사용한다.

    ```python
    >>>print("Hello" 'World')
    HelloWorld
    >>>print("Hello" + "World")
    HelloWorld
    ```

    ```python
    >>>print("hey " * 3)
    hey hey hey
    >>>print(3 * "hey ")
    hey hey hey
    ```

    `*`는 앞뒤의 자료는 순서와 상관없이 각각 문자열과 정수이면 반복을 수행하며, 수의 연산과 같이 연산자 `+`보다 먼저 수행한다.

    여러 줄에 걸쳐 문자열을 처리하기 위해 삼중 따옴표 `"""`, `'''` 를 사용한다.

    ```python
    >>>print('''String operatort + and * are
    very easy!''')
    String operatort + and * are
    very easy!
    ```

    ```python
    '''comments.py
        studing python'''
    print('# 이후는 주석') # 한 줄에서 문장 이후에도 주석 사용 가능
    print('string: "python"') # 작은따옴표 내부에서 큰따옴표는 문자열
    print("numner: 3.14") # 문자열 내부에서 숫자도 문자열
    print("string: 'python'") # 큰따옴표 내부에서 작은따옴표는 문자열
    ```

    파이썬 주석은 `#`으로 시작하고 그 줄의 끝까지 유효하다.

    여러줄 주석 처리를 위해 삼중따옴표나 줄마다 `#`을 넣어 사용한다.

-   정수와 실수

    숫자는 정수(integer)와 실수(real 또는 float)로 나눈다.

    ```python
    >>>15
    15
    >>>0
    0
    >>>000
    0
    >>>003.14 # 정수 앞 0은 불가능
    3.14
    ```

    정수와 실수는 문자 `e`나 `E`를 통해 거듭제곱으로 표현할 수 있다.

    ```python
    >>> 2.7834e4
    27834.0
    >>> 2.7834E4
    27834.0
    >>> 2.7834e-4
    0.00027834
    >>> 2.7834E-4
    0.00027834
    >>> 3543e-4
    0.3543
    >>> 3543E4
    35430000.0
    ```

-   정수와 실수의 연산

    더하기(addition) `+`, 빼기(subtraction) `-`, 곱하기(multiplication) `*`, 나누기(division) `/` 연산자

    ```python
    >>> 5 + 3
    8
    >>> 5 - 3
    2
    >>> 5 * 3
    15
    >>> 5 / 3 # 결과는 항상 실수이기 때문에 0으로 나누면 오류 발생
    1.6666666666666667
    ```

    정수 나눗셈(floor division) `//`, 나머지(modulus, modulo) `%`, 거듭제곱(exponentiation) `**` 연산자

    ```python
    >>> 5 // 3 # 결과는 나누기 결과를 넘지 않는 가장 작은 정수 부분
    1
    >>> 5 % 3
    2
    >>> 5 ** 3
    125
    ```

    -   연산자의 우선순위

        괄호 → 지수 `**` → 부호 `+`,`-` → `*`,`/`,`//`,`%` → 가감 `+`,`-`

        거듭제곱`**`은 오른쪽에서 왼쪽, 나머지 연산자는 왼쪽에서 오른쪽으로 계산한다.

    대화형 모드에서 마지막에 실행된 결과값은 `_`에 대입된다.

    ```python
    >>> 60
    60
    >>> _
    60
    >>> 3 * _
    180
    >>> _
    180
    ```

-   함수 `print()`

    출력에 이용되는 함수이다. 콤마 `,` 로 구분해 여러 자료를 출력할 수 있다.

    ```python
    >>> print('Hi','there',':)')
    Hi there :)
    ```

-   함수 eval()

    실행 가능한 연산식 문자열인 expression을 실행한 결과를 반환한다.

    ```python
    >>> eval('3 + 15 / 2')
    10.5
    >>> eval('4 * 3 % 5')
    2
    >>> eval('3 * -2 ** 3')
    -24
    >>> eval('"python " * 3')
    'python python python'
    >>> eval("'python ' * 3")
    'python python python '
    ```

---
