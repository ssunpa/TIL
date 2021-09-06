# 문자열

## 문자열 다루기

-   클래스와 객체

    > 클래스는 객체지향 프로그래밍 언어의 관점에서 객체를 정의하기 위한 틀 또는 모형인 템플릿(templet)이라고 한다. 객체는 클래스로부터 만들어진 하나의 구체적인 사례인 인스턴스(instance)다.

    > 클래스는 객체를 만들기 위한 정의, 객체는 해당 클래스의 구체적인 자료이다

-   문자열의 문자 참조

    함수 `len()`으로 문자열의 길이를 참조한다.

    ```python
    >>> sayHi = 'Hi there:)'
    >>> len(sayHi)
    10
    >>> len('Hello')
    5
    ```

    문자열을 구성하는 문자는 0부터 시작되는 첨자(index)를 대괄호 안에 기술해 참조(indexing)가 가능하다.

    ```python
    >>> 'Hello'[0]
    'H'
    >>> 'Hello'[3]
    'l'
    >>> 'Hello'[-1] # 역순으로도 참조 가능하다.
    'o'
    >>> 'Hello'[len('Hello')-1]
    'o'
    >>> 'Hello'[5] # 유효범위를 벗어나면 IndexError발생
    Traceback (most recent call last):
      File "<pyshell#9>", line 1, in <module>
        'Hello'[5]
    IndexError: string index out of range
    ```

-   문자열의 부분 문자열 참조 방식

    문자열 일부분을 참조하는 방법을 슬라이싱(slicing)이라고 한다.

    ```python
    >>> 'python'[1:5]
    'ytho'
    >>> 'python'[2:4]
    'th'
    >>> 'python'[0:6]
    'python'
    >>> 'python'[0:len('python')]
    'python'
    ```

    `[start:end]`로 부분 문자열을 반환하는데 `start` 첨자에서 `end-1` 첨자까지의 문자열을 반환한다.

    ```python
    >>> 'python'[-5:-1]
    'ytho'
    >>> 'python'[-3:-2]
    'h'
    >>> 'python'[-4:-2]
    'th'
    ```

    순반향의 `0`, `양수`, 역방향의 `음수`를 혼합해 슬라이싱에 사용할 수 있다.

    ```python
    >>> 'python'[1:-1]
    'ytho'
    >>> 'python'[0:2]
    'py'
    >>> 'python'[-5:5]
    'ytho'
    >>> 'python'[5:-1] # start와 end로 구성하는 문자열이 없다면 빈 문자열을 반환한다.
    ''
    ```

    슬라이싱에서 `start`와 `end`를 비우면 각각 '처음부터'와 '끝까지'를 의미한다.

    ```python
    >>> 'python'[:4]
    'pyth'
    >>> 'python'[2:]
    'thon'
    >>> 'python'[:]
    'python'
    ```

    `str[start:end:step]`으로 문자 사이의 간격을 step으로 조정 가능하다.

    ```python
    >>> 'python'[::1] # 기본 값
    'python'
    >>> 'python'[::2]
    'pto'
    >>> 'python'[::3]
    'ph'
    ```

    `step`은 음수도 가능하며, 이는 역순으로 구성된 문자열을 반환한다.

    ```python
    >>> 'python'[::-1]
    'nohtyp'
    >>> 'python'[::-2]
    'nhy'
    >>> 'python'[::-3]
    'nt'
    ```

-   문자 함수 `ord()`와 `chr()`

    -   `ord()`

        문자의 유니코드 번호를 반환하는 내장 함수.

        ```python
        >>> ord('S')
        83
        >>> ord('P')
        80
        ```

    -   `chr()`

        유니코드 번호로 문자를 반환하는 내장 함수.

        ```python
        >>> chr(83)
        'S'
        >>> chr(80)
        'P'
        ```

    -   이스케이프 시퀀스 문자

        하나의 문자를 역슬래시(`\`)로 시작하는 조합으로 표현하는 문자를 이스케이프 시퀀스 문자(escape sequence characters)라고 한다.

        ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b82048e7-d17f-4191-bbee-db041510c599/Untitled.png)

-   문자열의 최대와 최소

    내장 함수 `min()`은 최솟값을, 내장 함수 `max()`는 최댓값을 반환하는 함수이다.

    ```python
    >>> min('BirthDay')
    'B'
    >>> max('BirthDay')
    'y'
    >>> min('981130')
    '0'
    >>> max('981130')
    '9'
    ```

    인자가 문자열 1개이면 문자열을 구성하는 문자에서 코드 값으로 최대와 최소를 찾아 반환한다.

    ```python
    >>> min('happy', 'birth', 'day')
    'birth'
    >>> max('happy', 'birth', 'day')
    'happy'
    >>> min('98', '11', '30')
    '11'
    >>> max('98', '11', '30')
    '98'
    ```

    인자가 2개 이상이면 문자열 중 최대와 최소인 문자열을 반환한다.

---
