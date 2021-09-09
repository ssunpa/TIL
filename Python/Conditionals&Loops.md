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
