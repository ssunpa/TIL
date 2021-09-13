# 리스트와 튜플

## 리스트

-   리스트 개념과 생성

    여러 항목(item)을 하나의 단위로 묶어 손쉽게 사용하는 복합(compound)자료형을 여러 개 제공 하는 방법 중 하나가 리스트(`list`)이다.

    ```python
    >>> menu = ['coffee', 'tea', 'ade'] # 대괄호 사이에 항목을 기술한다.
    >>> ade = ['orange', 'lemon', 'peach']
    >>> adeprice = [['orange', 5500], ['lemon', 5000], ['peach', 5000]]
    ```

    리스트는 항목의 나열인 시퀀스다.

    콤마로 구분된 항목(또는 원소)들의 리스트로 표현되며, 각 항목은 모두 다른 자료형일 수 있다.

    항목 순서는 의미가 있으며, 항목 자료 값은 중복돼도 상관없다.

    ```python
    >>> print(menu)
    ['coffee', 'tea', 'ade']
    >>> print(ade)
    ['orange', 'lemon', 'peach']
    >>> print(adeprice)
    [['orange', 5500], ['lemon', 5000], ['peach', 5000]]

    >>> type(menu)
    <class 'list'>
    >>> type(ade)
    <class 'list'>
    >>> type(adeprice)
    <class 'list'>

    ```

    빈 리스트의 생성방법

    ```python
    >>> empty_ = [] # 빈 리스트 생성
    >>> print(empty_)
    []
    >>> empty__ = list() # 인자가 없는 내장 함수 list()이용
    >>> print(empty__)
    []
    ```

    메소드 `append()`을 이용해 리스트 가장 뒤에 항목을 추가할 수 있다.

    ```python
    >>> pl = list()
    >>> pl.append('C++')
    >>> pl.append('java')
    >>> pl.append('python')
    >>> print(pl)
    ['C++', 'java', 'python']
    ```

    함수 `list(str)`은 문자열의 항목인 문자로 구성되는 리스트를 변환한다.

    ```python
    >>> pl = list('python')
    >>> print(pl)
    ['p', 'y', 't', 'h', 'o', 'n']
    >>> len(pl) # 리스트 항목 수를 알 수 있는 내장 함수
    6
    ```

-   리스트의 항목 참조

    리스트에서 첨자(`index`)를 사용해 항목을 참조할 수 있다.

    1. 첨자는 첫 요소가 0부터 시작하며, 순차적으로 1씩 증가한다.
    2. 마지막 요소의 첨자는 역순으로 -1부터 시작하며, 반대로 1씩 감소한다.
    3. 첨자의 범위는 0에서 `[len(시퀀스)-1]`까지, -1에서 `[-len(시퀀스)]`까지 가능하다.

    ```python
    >>> py = list('python')
    >>> print(py[0], py[5])
    p n
    >>> print(py[-3], py[-1])
    h n
    >>> print(py[-len(py)], py[len(py)-1])
    p n
    ```

-   리스트의 항목 수정

    리스트 메소드 `count(값)` 는 값을 갖는 항목의 수, `index(값)` 는 인자인 값의 항목이 위치한 첨자를 반환한다.

    ```python
    >>> apple = ['iphone', 'ipad', 'ipod', 'airpods', 'mac', 'ipad', 'macbook']
    >>> apple.count('ipad')
    2
    >>> apple.index('mac')
    4
    >>> apple.index('ipad') # 첫 번째의 첨자를 반환한다.
    1
    ```

    리스트의 첨자로 항목을 수정할 수 있다.

    ```python
    >>> apple = ['iphone', 'ipad', 'ipod', 'airpods', 'mac', 'ipad', 'macbook']
    >>> apple[1] = 'watch'
    >>> print(apple)
    ['iphone', 'watch', 'ipod', 'airpods', 'mac', 'ipad', 'macbook']
    ```

-   중첩 리스트

    리스트 내부에 다시 리스트가 항목으로 올 수 있다.

    ```python
    >>> menu = [['orange ade', 'lemon ade', 'peach ade'], ['hot tea', 'ice tea'], 'coffee']
    >>> print(menu)
    [['orange ade', 'lemon ade', 'peach ade'], ['hot tea', 'ice tea'], 'coffee']
    >>> print(menu[0])
    ['orange ade', 'lemon ade', 'peach ade']
    >>> print(menu[0][0])
    orange ade
    ```

    ```python
    >>> animal = [['강아지','고양이','토끼'],'새','물고기']
    >>> for s in animal: # 각 항목을 한 줄씩 출력
    	print(s)
    ['강아지', '고양이', '토끼']
    새
    물고기
    >>> bird = ['참새','병아리','물떼새']
    >>> fish = ['광어','방어','가오리']
    >>> animal[1:] = [bird, fish] # 새로운 리스트로 대체
    >>> print(animal)
    [['강아지', '고양이', '토끼'], ['참새', '병아리', '물떼새'], ['광어', '방어', '가오리']]
    ```

---
