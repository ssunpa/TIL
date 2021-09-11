# 조건과 반복

## 조건문

-   조건의 논리 값에 따른 선택 `if`

    조건 `if`의 논리 표현식 결과는 `True` 또는 `False`이며, `True`이면 이후에 구성된 블록 구문을 실행하고, `False`이면 실행하지 않는다.

    ```python
    >>> weather = 'good'
    >>> if weather == 'good': # 반드시 콜론이 있어야 한다.
    				print('Have a good day!') # 반드시 들여쓰기를 해야 한다.


    Have a good day!
    ```

-   조건에 따라 하나를 선택하는 `if ~ else`

    `if ~ else` 문에서 결과가 `True`이면 `if` 블록이 `False` 이면 `else` 블록이 실행된다.

    ```python
    >>> weather == 'bad'
    >>> if weather == 'good' :
    	print ("It's a good day")
    else :
    	print("It's a bad day")

    It's a bad day**
    ```

-   여러 조건 중에서 하나를 선택하는 구문 `if ~ elif`

    조건의 여로 경로 중 하나를 선택하는 `if ~ elif`문은 `True`인 조건을 만나면 해당 블록을 실행하고 종료한다.

    ```python
    >>> point = 82
    >>> if 90 <= point:
    	print('점수 {}, 성적 {}'.format(point, 'A'))
    elif 80 <= point:
    	print('점수 {}, 성적 {}'.format(point, 'B'))
    elif 70 <= point:
    	print('점수 {}, 성적 {}'.format(point, 'C'))
    elif 60 <= point:
    	print('점수 {}, 성적 {}'.format(point, 'D'))
    else:
    	print('점수 {}, 성적 {}'.format(point, 'F'))


    점수 82, 성적 B
    ```

    `else`는 선택적으로 생략할 수 있다.

조건문 내부에 조건문이 있는 중첩 조건문 사용 가능하다!

---

## 반복문

반복문을 사용하면 중복을 줄여 프로그램이 간결해지며, 프로그램 절차를 효과적으로 수행할 수 있다.

-   시퀀스 내부 값으로 반복을 실행하는 `for`문

    -   실행 흐름
        1. 여러 개의 값을 가지는 시퀀스에서 변수에 하나의 값을 순서대로 할당한다.
        2. 할당된 변수의 값을 가지고 블록의 문장들을 순차적으로 실행한다.
        3. 반복 몸체에서도 변수를 사용할 수 있다.
        4. 시퀀스의 그 다음 값을 변수에 할당해 다시 반복 블록을 실행한다.
        5. 이러한 과정을 시퀀스의 마지막 항목까지 수행한다.
        6. 시퀀스의 마지막 항목까지 실행한 후 `else:` 블록(선택 사항)을 실행하고 반복을 종료한다.

    ```python
    >>> for s in 'python':
    	print(s, ord(s))
    else:
    	print('반복문 종료')

    p 112
    y 121
    t 116
    h 104
    o 111
    n 110
    반복문 종료
    ```

    내장함수 `range()`를 사용하여 `for`문을 작성할 수 있다.

    ```python
    >>> for i in range(10): # 0부터 10-1까지
    	print(i, end = ' ')

    0 1 2 3 4 5 6 7 8 9
    >>> for i in range(1, 10): # 1부터 10-1까지
    	print(i, end = ' ')

    1 2 3 4 5 6 7 8 9
    >>> for i in range(1, 10, 2): # 1부터 10-1까지 2씩 증가하면서
    	print(i, end = ' ')

    1 3 5 7 9
    ```

    -   함수 `range()`

        일정 간격의 정수 값을 가진 리스트(list)라는 시퀀스를 생성해 주는 함수.

        인자는 총 3개로, 적어도 1개(stop)의 인자를 지정해 줘야 한다.

        -   `range(stop)` : start는 자동으로 0, step은 자동으로 1로 설정된다.
        -   `range(start, stop)` : step은 자동으로 1로 설정된다.
        -   `range(start, stop, step)`

-   횟수를 정하지 않은 반복에 적합한 `while` 문

    -   실행 흐름
        1. 논리 표현식이 `True`이면 반복 몸체를 실행한 후 다시 논리 표현식을 검사해 실행한다.
        2. 논리 표현식이 `False`이면 반복 몸체를 실행하지 않고, 선택사항인 `else:` 이후의 블록을 실행한 후 반복을 종료한다.

    ```python
    >>> n = 1
    >>> while n <= 5:
    	print(n, end = ' ')
    	n += 1
    else:
    	print('\n 반복 while 종료: n => %d' % n)


    1 2 3 4 5
     반복 while 종료: n => 6
    ```

반복문 속의 반복문이 있는 중첩 반복문 사용 가능하다!

---

## 제어문

-   난수 발생과 반복 활용

    `random`의 함수 `randint(start, end)`를 사용해 정수 시작과 끝을 포함한 사이에서 임의의 정수를 얻을 수 있다.

    ```python
    >>> import random # import 모듈
    >>> random.randint(1, 10) # 모듈. 함수()
    9
    >>> random.randint(1, 10)
    4
    >>> random.randint(1, 10)
    8
    ```

    -   함수를 바로 사용하는 방법!

        ```python
        >>> from random import randint # from 모듈 import 변수
        >>> randint(1, 10) # 함수()
        5
        >>> randint(1, 10)
        10
        >>> randint(1, 10)
        10
        ```

-   반복을 제어하는 `break`문과 `continue`문

    `for`나 `while` 반복 내부에서 특정 조건에서 즉시 반복을 종료시키고 싶다면 `break`를, 이후 반복 몸체를 실행하지 않고 다음 반복을 위해 논리 조건을 수행하고 싶다면 `continue`를 사용한다.

    ```python
    days = ['monday', 'tuesday', 'wednesday' ,'thursday', 'friday', 'saturday', 'sunday']

    while True:
        user = input('영어로 요일을 입력 >> ')
        if user not in days:
            print('다시 입력해보기!')
            continue # 다음 반복으로 이동
        print('입력한 요일 %s, 정답입니다.' % user)
        break # 반복을 종료

    print('종료'.center(15, '*'))
    ```
