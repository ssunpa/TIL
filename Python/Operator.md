# 논리 자료와 다양한 연산

## 논리 값과 논리 연산

-   논리 유형 `bool`과 함수 `bool()`

    파이썬은 논리 값으로 `True`와 `False`를 키워드로 제공하고 이러하 논리 값의 자료형을 클래스 bool로 제공한다.

    ```python
    >>> type(True)
    <class 'bool'>
    >>> type(False)
    <class 'bool'>
    ```

    정수의 `0`, 실수의 `0.0`, 빈 문자열 `''`등은 `False`이며, 음수와 양수 빈 문자열이 아닌 문자열은 `True`다. 내장 함수 `bool()`로 인자인 변수나 상수의 논리 값을 알 수 있다.

    ```python
    >>> bool(0), bool(0.0), bool('')
    (False, False, False)
    >>> bool(10), bool(10.1), bool('ten')
    (True, True, True)
    ```

    논리값 `True`와 `False`는 `int()` 함수에 의해 각각 `1`과 `0`으로 변환된다.

    ```python
    >>> int(True), int(False)
    (1, 0)
    ```

-   논리곱과 논리합 연산자 `and`와 `or`

    논리곱인 `and`와 `&`연산자는 두 항이 모두 참이어야 `True`이다.

    ```python
    >>> True & True, True and True
    (True, True)
    >>> True & False, True and False
    (False, False)
    >>> False & True, False and True
    (False, False)
    >>> False & False, False and False
    (False, False)
    ```

    하나라도 거짓이면 `False`를 반환한다.

    논리합인 `or`과 `|`연산자는 두 항이 모두 거짓이어야 `False`이다.

    ```python
    >>> True | True, True or True
    (True, True)
    >>> True | False, True or False
    (True, True)
    >>> False | True, False or True
    (True, True)
    >>> False | False, False or False
    (False, False)
    ```

    하라나도 참이면 `True`를 반환한다.

-   배타적 논리합 연산자 `^`와 연산자 `not`

    배타적 논리합(exclusive or)연산자인 `^`은 두 항이 다르면 `True`, 같으면 `False`다.

    ```python
    >>> True ^ True
    False
    >>> True ^ False
    True
    >>> False ^ True
    True
    >>> False ^ False
    False
    ```

    연산자 `not`은 뒤에 위치한 논리 값을 반대로 바꾼다.

    ```python
    >>> not False
    True
    >>> not True
    False
    ```

-   논리 연산 우선순위

    `not` 연산 → 논리곱 `and` → 논리합 `or` 순으로 논리 연산을 진행한다.

    ```python
    >>> not False and True
    True
    >>> (not False) and True
    True
    >>> not True or True and False
    False
    >>> (not True) or (True and False)
    False
    ```

---

## 관계 연산

-   관계 연산자

    관계 연산자(relational operator)는 수나 문자열 등의 크기 비교에 사용되는 연산자이다. 논리 값을 반환한다.

    ```python
    >>> ord('a'), ord('A'), ord('\0'), ord('B') # 코드 값을 알려주는 내장 함수
    (97, 65, 0, 66)
    >>> 8 > 2, 'a' > 'A'
    (True, True)
    >>> 8 >= 2, 'a' >= 'A'
    (True, True)
    >>> 8 < 2, 'a' < 'aB'
    (False, True)
    >>> 8 <= 2, 'a' <= 'aB'
    (False, True)
    >>> 8 == 2, 'a' == 'aB'
    (False, False)
    >>> 8 != 2, 'a' != 'aB'
    (True, True)
    ```

    문자열의 비교는 문자열을 구성하는 하나하나의 문자와 문자를 왼쪽부터 순서대로 유니코드 값을 비교한다.

    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4d047557-1c0a-4a0c-b38d-75d99d7b5328/Untitled.png)

-   논리 값 `True`와 `False`의 산술 연산

    논리 값 `True`와 `False`는 각각 1과 0으로 산술 연산에 활용할 수 있다.

    ```python
    >>> 40 * True # 40 * 1
    40
    >>> 40 * False # 40 * 0
    0
    ```

---

## 멤버십 연산 in

-   문자열에서의 부분 문자열인지 검사

    키워드 `in`은 멤버의 소속을 알 수 있는 멤버십 연산이며 `True`, `False`의 논리 값을 반환한다.

    ```python
    >>> 'e' in 'hello' # x in s, 문자열 s에 부분 문자열 x가 있으면
    True
    >>> 'a' in 'hello' # x in s, 문자열 s에 부분 문자열 x가 없으면
    False
    >>> 'e' not in 'hello' # x in s, 문자열 s에 부분 문자열 x가 있으면
    False
    >>> 'a' not in 'hello' # x in s, 문자열 s에 부분 문자열 x가 없으면
    True
    ```

---

## 비트 논리 연산

-   비트 논리곱 `&`, 비트 논리합 `|`, 비트 배타적 논리합 `^`

    비트 연산은 정수로 저장된 메모리에서 비트와 비트의 연산을 말한다.

    ```python
    >>> m, n = 0, 0
    >>> '{} {} {}'.format(m & n, m | n, m ^ n)
    '0 0 0'
    >>> m, n = 0, 1
    >>> '{} {} {}'.format(m & n, m | n, m ^ n)
    '0 1 1'
    >>> m, n = 1, 0
    >>> '{} {} {}'.format(m & n, m | n, m ^ n)
    '0 1 1'
    >>> m, n = 1, 1
    >>> '{} {} {}'.format(m & n, m | n, m ^ n)
    '1 1 0'
    ```

    `True`를 `1`, `False`를 `0`으로 본다.

    -   비트 논리곱, 논리합, 배타적 논리합 연산

        ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6fe7a373-923c-4ec4-b2b6-4b2ea3790278/Untitled.png)

-   비트 논리곱 `&`로 특정 비트의 값 알아 내기

    ```python
    >>> a = 180
    >>> mask = 0b1111 # 0xf도 가능
    >>> print('정수 {0} 2진수로는 {0:b}'.format(a))
    정수 180 2진수로는 10110100
    >>> print('가장 오른쪽 4비트: {0:04b} 정수로는 {0}'.format(a&mask))
    가장 오른쪽 4비트: 0100 정수로는 4
    ```

    원하는 특정 비트를 모두 1로 지정한 마스크(mask) 값을 정수 a와 논리곱으로 연산한 결과는 a의 특정 비트값만을 뽑아낸다.

-   비트 배타적 논리합 `^`을 사용해 암호화

    -   비트 배타적 논리합의 특성
        1. `a ^ a == 0`, `a ^ 0 == a`, `a ^ 1 == ~a`
        2. `a ^ b == b ^ a`, `(a ^ b) ^ c == a ^ (b ^ c)`
        3. `(a ^ b) ^ b == a ^ (b ^ b) == a ^ 0 == a`

    정수 a와 key를 연산식 `a ^ key`한 결과를 암호화 결과로 저장 → 필요 시 결과 값 `a ^ key`를 이용해 `a ^ key ^ key`를 수행 → 원래 a로 복호화

---

## 비트 이동 연산

-   비트 이동 연산자 `>>`와 `<<`

    비트 단위로 뒤 피연산자인 지정된 횟수만큼 `<<`은 왼쪽으로, `>>`은 오른쪽으로 이동시킨다.

    이로 인해 생긴 빈자리는 모두 `0`으로 채워지며, `>>`에 의한 빈자리는 원래의 정수 부호에 따라 0이나 양수이면 `0`을 음수이면 `1`이 채워진다.

    오른쪽 이동 연산 `>>` 수행 1회마다 2로 나눈 것과 같다.

    ```python
    >>> a = 0b00010111
    >>> print('10진수 {0:3d}, 2진수 {0:08b}'.format(a))
    10진수  23, 2진수 00010111
    >>> print('10진수 {0:3d}, 2진수 {0:08b}'.format(a >> 1))
    10진수  11, 2진수 00001011
    >>> print('10진수 {0:3d}, 2진수 {0:08b}'.format(a // 2))
    10진수  11, 2진수 00001011
    >>> print('10진수 {0:3d}, 2진수 {0:08b}'.format(a >> 2))
    10진수   5, 2진수 00000101
    >>> print('10진수 {0:3d}, 2진수 {0:08b}'.format(a // 2 ** 2))
    10진수   5, 2진수 00000101
    ```

    왼쪽 이동 연산 << 수행 1회마다 2를 곱한 것과 같다.

    ```python
    >>> a = 0b00010111
    >>> print('10진수 {0:3d}, 2진수 {0:08b}'.format(a))
    10진수  23, 2진수 00010111
    >>> print('10진수 {0:3d}, 2진수 {0:08b}'.format(a << 1))
    10진수  46, 2진수 00101110
    >>> print('10진수 {0:3d}, 2진수 {0:08b}'.format(a * 2))
    10진수  46, 2진수 00101110
    >>> print('10진수 {0:3d}, 2진수 {0:08b}'.format(a << 2))
    10진수  92, 2진수 01011100
    >>> print('10진수 {0:3d}, 2진수 {0:08b}'.format(a * 2 ** 2))
    10진수  92, 2진수 01011100
    ```

    -   연산자 우선순위

        ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cec9d31a-0a04-4722-97de-6d18893df746/Untitled.png)
