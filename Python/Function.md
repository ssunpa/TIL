# 함수

## 함수 정의와 활용

-   함수 구현과 활용

    1. 함수 머리(function header)는 키워드 `def`, 함수 이름과 괄호, 괄호 사이의 인자 `arguments`들 그리고 함수 정의의 몸체인 블록을 예고하는 콜론`:` 이 필요하다.
    2. 함수 몸체(function body)는 들여쓰기로 시작하며, 기능을 수행하는 문장들과 마지막으로 키워드 `return`에 의한 반환 값을 돌려 주는 구문이 필요하다.
    3. `arguments`와 `return` 문장은 선택적이다.

    함수를 만드는 것을 함수 정의 또는 함수 구현이라고 한다.

    ```python
    # 함수 정의(구현)
    >>> def sayHi():
    	print('Hi how are you :)')

    >>> sayHi() # 함수 호출
    Hi how are you :)
    ```

    함수 호출은 코드 순서상 함수 정의 이후에 가능하다.

-   함수 인자와 기본값

    함수 인자에는 함수 호출 시 함수로 전달할 내용이 담겨 있다.

    ```python
    >>> def sayHi(name):
    	print('Hi {}! how are you?'.format(name))


    >>> sayHi('sun')
    Hi sun! how are you?
    >>> sname = 'pa'
    >>> sayHi(sname) # 변수로 지정한 값을 인자로 사용
    Hi pa! how are you?
    ```

    함수 호출 시 선택적으로 기본값을 설정할 수 있다.

    ```python
    >>> def sayHi(name = 'there'): # 기본값 설정하는 방법
    	print('Hi {}! how are you?'.format(name))


    >>> sayHi() # 인자 없이 호출
    Hi there! how are you?
    ```

-   함수 반환 값

    함수 실행 이후 함수 호출 쪽으로 값을 전달하는 것을 반환 값(return value)이라고 한다.

    ```python
    >>> def sum(x, y):
    	return x + y # 반환 값

    >>> sum(5, 6)
    11
    ```

    반환 값 없이 `return` 문장만 사용될 경우 반환 값 없이 함수 실행이 종료된다.

    ```python
    >>> def noReturn(str) :
    	print('인자 %s를 전달받아 noReturn함수가 실행됨!' % str)
    	return

    >>> noReturn('test')
    인자 test를 전달받아 noReturn함수가 실행됨!
    ```

    여러 개의 값을 반환하는 것도 가능하다.

    ```python
    >>> def op(x, y):
    	sum = x + y
    	average = sum / 2
    	return sum, average

    >>> op(10, 20)
    (30, 15.0)
    ```

-   지역 변수와 전역 변수

    파이썬에서는 메모리에 생성되고 유지되는 범위(scope)를 지역(local)과 전역(global)로 나눈다.

    ```python
    >>> def addone():
    	i = 50 # 지역 변수
    	i += 1
    	print('지역 변수 i:', i)


    >>> i = 20 # 전역 변수
    >>> print(i) # 전역 변수 출력
    20
    >>> addone() # 함수 호출
    지역 변수 i: 51
    >>> print(i) # 전역 변수 출력
    20
    ```

    지역 변수는 함수 내부에서 대입되어 생성된 변수이므로 함수 외부에서는 절대 사용될 수 없다.

    만약 함수 내부에서 대입이 없는 변수가 참조된다면 변수는 전역 변수로 인식된다.

    ```python
    >>> def addone():
    	print('i의 값:',i)


    >>> i = 10
    >>> addone()
    i의 값: 10
    >>> i = 20
    >>> addone()
    i의 값: 20
    ```

    변수는 참조되기 이전에 값이 대입되어야 한다.

    ```python
    >>> def addone():
    	print('i + 1의 값:', i + 1)
    	i += 1 # 수정이 있으므로 i는 지역 변수로 인지


    >>> i = 20
    >>> addone()
    Traceback (most recent call last):
      File "<pyshell#65>", line 1, in <module>
        addone()
      File "<pyshell#63>", line 2, in addone
        print('i + 1의 값:', i + 1)
    UnboundLocalError: local variable 'i' referenced before assignment
    ```

    함수 내부에서 대입 문장으로 생성이나 수정하는 변수는 기본적으로 지역 변수로 인식하며, 함수 내부에서는 기본적으로 지역 변수에만 값 대입이 가능하다.

    함수 내부에서도 `global` 문장으로 변수를 전역 변수로 지정할 수 있다.

    ```python
    >>> def addone():
    	global i # 명시적으로 변수를 전역 변수로 지정
    	print('i + 1의 값', i + 1)
    	i += 1


    >>> i = 20 # 전역 변수
    >>> addone()
    i + 1의 값 21
    >>> i
    21
    >>> addone()
    i + 1의 값 22
    >>> i
    22
    ```

---

## 함수 인자

-   위치 인자와 키워드 인자

    위치 인자 방식은 고정적이며, 호출의 순서에 따라 인자를 구별하는 방식이다.

    ```python
    >>> def subtract(pre, post):
    	return pre - post

    >>> print(subtract(10, 5))
    5
    ```

    키워드 인자 방식은 함수를 호출할 때 값을 전달할 인자를 직접 대입으로 지정하는 방식이다.

    ```python
    >>> print(subtract(post = 5, pre = 10))
    5
    ```

    키워드 인자와 위치 인자를 함께 사용 할 때, 키워드 인자는 모든 위치 인자 이후에 사용한다.

    ```python
    >>> def info(first = 0, second = 10, third = 20):
    	return first, second, third

    >>> print(info(5, third = 15))
    (5, 10, 15)
    ```

-   가변 인자 `*args`

    가변 인자는 인자 이름 앞에 `*`를 넣어 사용한다. 함수 호출 시 사용된 여러 인자가 `(arg1, arg2, arg3, ...)`식의 튜플로 전달된다.

    ```python
    >>> def sayHi(*name):
    	for one in name:
    		print('Hi %s!' % one)


    >>> sayHi('papa')
    Hi papa!
    >>> sayHi('sun', 'pa', 'papa')
    Hi sun!
    Hi pa!
    Hi papa!
    >>> sayHi(*['sun','pa','papa']) # 반드시 * 필요!
    Hi sun!
    Hi pa!
    Hi papa!
    >>> sayHi(*('sun', 'pa', 'papa')) # 반드시 * 필요!
    Hi sun!
    Hi pa!
    Hi papa!
    ```

    리스트나 튜플 앞에 `*`는 리스트나 튜플을 풀어 가변 인자 형태로 변환한다는 의미있다.

-   임의의 키워드 인자 `**kwargs`

    함수 정의에서 인자 `**kwargs`는 인자 이름인 변수 `kwargs`가 딕셔너리 형태인 것을 의미한다.

    ```python
    >>> def keyprint(**kwargs):
    	for key in kwargs:
    		print('{}: {}'.format(key, kwargs[key])
    	print()


    >>> myinfo = {'name':'sun', 'birth':'981130', 'favorite':'tteokbokki'}
    >>> keyprint(**myinfo)
    name: sun
    birth: 981130
    favorite: tteokbokki
    ```

    `**`는 딕셔너리를 풀어 키워드 인자 형태로 변환한다는 의미이다.

    위치 인자와 `**kwargs`을 함께 사용 가능하다.

    ```python
    >>> def sumvalue(value, **kwargs):
    	hap = value
    	for key in kwargs:
    		hap += kwargs[key]
    	return hap

    >>> values = {'first':10, 'second':20, 'third':30}
    >>> print(sumvalue(100, **values))
    160
    ```

    키워드 인자와도 함께 사용 가능하다.

    ```python
    >>> print(sumvalue(value=100, **values))
    160
    >>> print(sumvalue(**values, value=100))
    160
    >>>
    ```

    가변 인자와도 함께 사용 가능하다.

    ```python
    >>> def sumvalue(*value, **kwargs):
    	hap = 0
    	for v in value:
    		hap += v
    	for key in kwargs:
    		hap += kwargs[key]
    	return hap

    >>> values = {'first':10, 'second':20, 'third':30}
    >>> valuelist = [100, 200, 300]
    >>> valuetuple = (100, 200, 300)
    >>> print(sumvalue(*valuelist, **values))
    660
    >>> print(sumvalue(*valuetuple, **values))
    660
    ```

---

## 람다 함수와 내장 함수

-   람다 함수
    람다 함수(lambda function)는 작고 익명성(anonymous)을 가진 함수를 말한다.
    1. 키워드 `lambda` 이후에 콤마로 구분된 인자 목록
    2. 여러 개의 인자를 취할 수 있지만 표현식은 하나만 가능
    3. 키워드 `return` 없이 하나의 표현식 결과값이 반환
    람다 함수는 일시적으로 사용하고 바로 버리는 함수에 주요 사용한다.
    ```python
    >>> lambda x: x + 1 # 람다 함수 선언 방법
    <function <lambda> at 0x0000027643778E50>
    >>> (lambda x, y : x * y)(10, 2) # 함수를 만들면서 동시에 인자를 넣어 함수 호출
    20
    >>> mult = lambda x, y : x * y # 함수를 변수에 저장해 재사용 하는 방법
    >>> mult(10, 2)
    20
    ```
    함수 내부에서 람다 함수를 사용할 수 있다.
    ```python
    >>> def inc(n):
    	return lambda x: x + n

    >>> incbase100 = inc(100)
    >>> incbase100(10)
    110
    >>> incbase100(20)
    120
    ```
-   산술 연산 관련 내장 함수

    표준 라이브러리란, 다른 부가적인 작업 없이 사용할 수 있는 라이브러리를 말하고, 표준 라이브러리 중 `import`없이 바로 함수 호출로 사용할 수 있는 함수를 내장 함수라고 한다.

    -   `abs()`
        함수 `abs(num)`은 정수 또는 실수인 `num`의 절댓값을 반환한다.
        ```python
        >>> abs(-10)
        10
        >>> abs(-3.1415)
        3.1415
        >>> abs(3.1415)
        3.1415
        ```
    -   `bin()`, `oct()`, `hex()`
        함수 `bin(num)`은 정수 `num`을 "`0b`"가 앞에 붙은 이진 문자열로 `oct(num)`은 "`0o`"가 붙은 8진수, `hex(num)` "`0x`"가 붙은 16진수의 문자열로 반환한다.
        ```python
        >>> bin(20)
        '0b10100'
        >>> oct(20)
        '0o24'
        >>> hex(20)
        '0x14'
        ```
    -   `pow()`, `round()`, `divmod()`
        함수 `pow(x, y)`는 `x`의 `y` 거듭제곱을 반환한다.
        ```python
        >>> pow(2, 3)
        8
        >>> pow(2.4, 3.1) # 인자는 정수와 실수 모두 가능하다.
        15.088805115741808
        ```
        함수 `round(x)`는 실수 `x`에 가장 가까운 정수를 반환하고, `round(x, y)`는 실수 `x`에서 소수점 다음에 `y` 자릿수로 반올림한 값을 반환한다.
        ```python
        >>> round(3.141592)
        3
        >>> round(3.141592, 3)
        3.142
        ```
        함수 `divmod(a, b)`는 인자 2개의 나누기 몫과 나머지로 구성된 한 쌍의 튜플을 반환한다.
        ```python
        >>> divmod(10, 3)
        (3, 1)
        >>> divmod(5.5, 1.5)
        (3.0, 1.0)
        ```

-   시퀀스 관련 내장 함수

    -   `min()`, `max()`, `sum()`
        ```python
        >>> min(5, 1, 10) # 여러 인자 중 최솟값을 반환
        1
        >>> max(5, 1, 10) # 여러 인자 중 최댓값을 반환
        10
        >>> min([5, 1, 10]) # 시퀀스 항목 중에서 최솟값을 반환
        1
        >>> max([5, 1, 10]) # 시퀀스 항목 중에서 최댓값을 반환
        10
        >>> sum([5, 1, 10]) # 시퀀스의 모든 항목을 합한 결화를 반환
        16
        >>> sum([5, 1, 10], 5) # 두 번째 인자는 인자를 더해 반환
        21
        ```
    -   `sorted()`와 `reversed()`
        ```python
        >>> values = [50, 30, 10, 90, 70]
        >>> sorted(values) # 항목을 오름차순으로 정렬한 리스트로 반환
        [10, 30, 50, 70, 90]
        >>> sorted(values, reverse=True) # 항목을 내림차순으로 정렬한 리스트로 반환
        [90, 70, 50, 30, 10]
        >>> reversed(values) # 시퀀스의 역순을 반환한다.
        <list_reverseiterator object at 0x00000205555A1880>
        >>> list(reversed(values)) # 리스트나 튜플에 담아 사용할 수 있다.
        [70, 90, 10, 30, 50]
        ```
        함수 `sorted()`는 키워드 인자로 `key`를 사용할 수 있는데 이의 값으로 정렬에 사용될 키를 반환하는 함수가 되어야 한다.
        ```python
        >>> famous = "We accept the love we think we deserve.".split()
        # 각 항목 단어의 첨자 1, 두 번째 문자를 키로 정렬
        >>> sorted(famous, key = lambda famous: famous[1])
        ['accept', 'We', 'we', 'we', 'deserve.', 'the', 'think', 'love']

        >>> num = '919 427 731'.split()
        # 두 번째 문자를 키로 정렬
        >>> sorted(num, key = lambda num: num[1])
        ['919', '427', '731']
        # 세 번째 문자를 키로 정렬
        >>> sorted(num, key = lambda num: num[2])
        ['731', '427', '919']
        ```
    -   `all()`과 `any()`
        함수 `all(sequence)`은 `sequence`의 모든 항목이 참이거나 항목이 비어 있으면 `True`를 반환한다.
        ```python
        >>> all([10 < 5, 'h' in 'hello'])
        False
        >>> all('hello')
        True
        >>> all('')
        True
        >>> all({}) # 항목이 비어 있는 시퀀스는 True를 반환한다.
        True
        >>> all(())
        True
        ```
        함수 `any(sequence)`는 `sequence`에서 하나의 항목이라도 참이거나 항목이 비어 있지 않으면 `True`를 반환한다.
        ```python
        >>> any([10 < 5, 'h' in 'hello'])
        True
        >>> any('hello')
        True
        >>> any('')
        False
        >>> any({})
        False
        >>> any(())
        False
        ```
    -   `map()`
        함수 `map(function, iterable, ...)` 은 `iterable`의 모든 항목에 `function`을 적용한 후 그 결과를 돌려주는 `iterator`를 반환한다.
        이터러블(iterable)은 항목을 하나씩 차례로 반환할 수 있는 객체(object)를 말한다. 즉, 시퀀스인 문자열, 리스트와 튜플 모두 대표적인 이터러블이다.
        `iterator`는 시퀀스인 튜플이나 리스트로 변환해 항목을 활용할 수 있다.
        ```python
        >>> def addone(n):
        	return n + 1

        >>> lst = list(map(addone, [10, 40, 30, 50]))
        >>> print(lst)
        [11, 41, 31, 51]
        ```
        인자가 2개인 `function`을 사용할 경우
        ```python
        >>> def add(x, y):
        	return x + y

        >>> lst = list(map(add, [10, 30, 20, 40], [5, 35, 15, 25]))
        >>> print(lst)
        [15, 65, 35, 65]
        ```
        람다 함수를 활용할 경우
        ```python
        >>> lst = list(map(lambda x, y: x + y, [10, 30, 20, 40], [5, 35, 15, 25]))
        >>> print(lst)
        [15, 65, 35, 65]
        ```

-   객체 관련 내장 함수
    -   `dir()`
        인자 없이 함수 `dir()`를 호출하면 현재 정의된 변수와 함수 이름의 리스트를 돌려준다.
        ```python
        >>> def addone(n):
        	return n + 1

        >>> one = 1
        >>> two = 2
        >>> num = [one, two]
        >>> dir()
        ['__annotations__', '__builtins__', '__doc__', '__loader__', '__name__', '__package__', '__spec__', 'addone', 'num', 'one', 'two']
        ```
    -   `help()`
        대화형 모드에서 도움말을 휘한 함수다.
        ```python
        >>> help()

        Welcome to Python 3.9's help utility!

        If this is your first time using Python, you should definitely check out
        the tutorial on the Internet at https://docs.python.org/3.9/tutorial/.

        Enter the name of any module, keyword, or topic to get help on writing
        Python programs and using Python modules.  To quit this help utility and
        return to the interpreter, just type "quit".

        To get a list of available modules, keywords, symbols, or topics, type
        "modules", "keywords", "symbols", or "topics".  Each module also comes
        with a one-line summary of what it does; to list the modules whose name
        or summary contain a given string such as "spam", type "modules spam".

        help> lambda # 궁금한 함수나 키워드 입력
        Lambdas
        *******

           lambda_expr ::= "lambda" [parameter_list] ":" expression

        Lambda expressions (sometimes called lambda forms) are used to create
        anonymous functions. The expression "lambda parameters: expression"
        yields a function object.  The unnamed object behaves like a function
        object defined with:

           def <lambda>(parameters):
               return expression

        See section Function definitions for the syntax of parameter lists.
        Note that functions created with lambda expressions cannot contain
        statements or annotations.

        Related help topics: FUNCTIONS

        help> quit # 빠져나오는 방법

        You are now leaving help and returning to the Python interpreter.
        If you want to ask for help on a particular object directly from the
        interpreter, you can type "help(object)".  Executing "help('string')"
        has the same effect as typing a particular string at the help> prompt.

        >>> help(print) # 인자를 넣어서 활용 가능!
        Help on built-in function print in module builtins:

        print(...)
            print(value, ..., sep=' ', end='\n', file=sys.stdout, flush=False)

            Prints the values to a stream, or to sys.stdout by default.
            Optional keyword arguments:
            file:  a file-like object (stream); defaults to the current sys.stdout.
            sep:   string inserted between values, default a space.
            end:   string appended after the last value, default a newline.
            flush: whether to forcibly flush the stream.
        ```
