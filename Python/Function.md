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
