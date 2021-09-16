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

## 리스트 부분 참조와 항목의 삽입 삭제

-   슬라이싱

    슬라이스는 `list[start:stop:step]`와 같이 사용하며, 첨자 `start`에서 첨자 `stop-1`까지 `step`간격의 요소로 구성된 부분 리스트를 반환한다.

    ```python
    >>> alp = list('abcdefghij')
    >>> print(alp)
    ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j']
    >>> print(alp[:])
    ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j']
    >>> print(alp[::])
    ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j']
    >>> print(alp[::-1])
    ['j', 'i', 'h', 'g', 'f', 'e', 'd', 'c', 'b', 'a']
    >>> print(alp[:]) # 원래 리스트에는 전혀 영향을 미치지 않는다.
    ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j']
    ```

    ```python
    >>> alp = list('abcdefghij')
    >>> print(alp[1:5]) # 첨자 1에서 4까지의 항목으로 구성
    ['b', 'c', 'd', 'e']
    >>> print(alp[1:10:2]) # 첨자 1에서 9까지 2씩 증가하는 항목으로 구성
    ['b', 'd', 'f', 'h', 'j']
    >>> print(alp[-3::-2]) # 역순으로 첨자 -3부터 끝까지 2씩 감소하는 역순의 항목으로 구성
    ['h', 'f', 'd', 'b']
    >>> print(alp[1:-1]) # 정순 첨자와 역순 첨자 함께 사용 가능
    ['b', 'c', 'd', 'e', 'f', 'g', 'h', 'i']
    >>> print(alp[-1:1:-1])
    ['j', 'i', 'h', 'g', 'f', 'e', 'd', 'c']
    >>> print(alp[-2:2:-2])
    ['i', 'g', 'e']
    ```

-   리스트 부분 수정

    슬라이스 방식에 대입하여 리스트의 일부분을 수정한다.

    ```python
    >>> apple = ['iphone', 'ipad', 'airpods', 'mac', 'macbook']
    >>> apple[3:] = ['ipod']
    >>> print(apple)
    ['iphone', 'ipad', 'airpods', 'ipod']
    ```

    의도와 조금 달라지는 경우

    ```python
    >>> sports = ['풋살', '족구', '야구', '농구', '배구']
    >>> sports[0:2] = '축구'
    >>> print(sports)
    ['축', '구', '야구', '농구', '배구'] # 문자열은 문자로 구성되는 리스트이다.

    >>> number = [1, 2, 3, 4, 5, 6]
    >>> number[1:3] = [10,20]
    >>> print(number)
    [1, 10, 20, 4, 5, 6] # 정수는 문제 없이 적용 된다.
    >>> number[1:3] = 30 # 하지만 항목만 넣을 경우 오류
    Traceback (most recent call last):
      File "<pyshell#21>", line 1, in <module>
        number[1:3] = 30
    TypeError: can only assign an iterable

    >>> sports = ['풋살', '족구', '야구', '농구', '배구']
    >>> sports[4] = ['핸드볼']
    >>> print(sports)
    ['풋살', '족구', '야구', '농구', ['핸드볼']]
    >>> sports[4] = '핸드볼'
    >>> print(sports)
    ['풋살', '족구', '야구', '농구', '핸드볼'] # 알맞는 첨자에 직접 넣을 경우는 문자열로
    ```

    리스트 슬라이스에 동일한 리스트 슬라이스를 대입할 수 있다.

    ```python
    >>> apple = ['iphone12', 'iphone12pro', 'iphone12mini', 'iphone11', 'iphone11pro']
    >>> apple[0:2] = apple [3:] # 동일한 리스트 슬라이스에 대입하는 경우
    >>> print(apple)
    ['iphone11', 'iphone11pro', 'iphone12mini', 'iphone11', 'iphone11pro']

    >>> series11 = ['iphone11', 'iphone11pro']
    >>> series12 = ['iphone12', 'iphone12mini','iphone12pro']
    >>> series12[:2] = series11[:] # 다른 리스트 슬라이스에 대입하는 경우
    >>> print(series12)
    ['iphone11', 'iphone11pro', 'iphone12pro']
    ```

-   리스트의 항목 삽입과 삭제

    메소드 `insert(첨자, 항목)`으로 삽입

    ```python
    >>> disney = []
    >>> disney.insert(0, 'aladdin')
    >>> disney.insert(0, 'coco')
    >>> disney
    ['coco', 'aladdin']
    >>> disney.insert(1, 'mulan')
    >>> disney
    ['coco', 'mulan', 'aladdin']
    ```

    메소드 `remove(항목)`과 `pop(첨자)`, `pop()` 으로 삭제

    ```python
    >>> disney = ['aladdin','mulan','up','coco']
    >>> disney.remove('up')
    >>> print(disney)
    ['aladdin', 'mulan', 'coco']

    >>> print(disney.pop(1)) # 첨자 1인 mulan 삭제
    mulan
    >>> print(disney.pop()) # 마지막 항목인 coco 삭제
    coco
    >>> print(disney)
    ['aladdin']
    ```

    `del`에 의한 항목이나 변수 삭제

    ```python
    >>> disney = ['aladdin','nulan','coco','moana','up']
    >>> del disney[4] # del(disney[4])도 가능
    >>> print(disney)
    ['aladdin', 'nulan', 'coco', 'moana']
    >>> del disney[0:2] # 리스트의 일부분 삭제도 가능
    >>> print(disney)
    ['coco', 'moana']
    >>> del disney # 변수 자체를 메모리에서 제거
    >>> print(disney)
    Traceback (most recent call last):
      File "<pyshell#48>", line 1, in <module>
        print(disney)
    NameError: name 'disney' is not defined
    ```

    메소드 `clear()`로 리스트의 모든 항목 제거

    ```python
    >>> disney = ['aladdin','nulan','coco','moana','up']
    >>> print(disney)
    ['aladdin', 'nulan', 'coco', 'moana', 'up']
    >>> disney.clear()
    >>> print(disney)
    []
    ```

-   리스트의 추가, 연결과 반복

    메소드 `extend()`로 리스트에 리스트를 추가

    ```python
    >>> week = ['MON', 'TUE', 'WED', 'THU', 'FRI']
    >>> weekend = ['SAT', 'SUN']
    >>> week.extend(weekend) # 인자인 리스트를 가장 뒤에 추가한다
    >>> print(week)
    ['MON', 'TUE', 'WED', 'THU', 'FRI', 'SAT', 'SUN']
    ```

    연산자 `+`로 리스트 연결하기

    ```python
    >>> week = ['MON', 'TUE', 'WED', 'THU', 'FRI']
    >>> weekend = ['SAT', 'SUN']
    >>> oneweek = week + weekend
    >>> print(oneweek)
    ['MON', 'TUE', 'WED', 'THU', 'FRI', 'SAT', 'SUN']

    >>> holyday = ['SAT' ,'SUN']
    >>> holydays = holyday * 3 # 곱하기 연산자(*)로 지정된 정수만큼 반복된 리스트를 생성
    >>> print(holydays)
    ['SAT', 'SUN', 'SAT', 'SUN', 'SAT', 'SUN']
    ```

-   리스트 항목의 순서와 정렬

    메소드 `reverse()`로 리스트 항목 순서를 뒤집기

    ```python
    >>> text = '내가그린기림그림'
    >>> textList = list(text)
    >>> print(textList)
    ['내', '가', '그', '린', '기', '림', '그', '림']
    >>> textList.reverse()
    >>> print(textList)
    ['림', '그', '림', '기', '린', '그', '가', '내']
    ```

    메소드 `sort()`로 리스트 항목 순서를 정렬

    ```python
    >>> birthday = '19981130'
    >>> luckynum = list(birthday)
    >>> luckynum.sort()
    >>> print(luckynum)
    ['0', '1', '1', '1', '3', '8', '9', '9']
    >>> luckynum.sort(reverse=True)
    >>> print(luckynum)
    ['9', '9', '8', '3', '1', '1', '1', '0']
    ```

    작은 것부터 오름차순(ascending order)로 배열하기 위해 `sort()`를 사용하고, 큰 것부터 내림차순(descending order)으로 배열하기 위해 `sort(reverse=True)`를 호출한다.

    내장함수 `sorted()`로 새로운 리스트 만들기

    ```python
    >>> birthday = list('19981130') # birthday이라는 리스트 생성
    >>> luckynum = sorted(birthday) # luckynum이라는 새로운 리스트 생성
    >>> print(birthday) # 원래 리스트는 변화 없음!
    ['1', '9', '9', '8', '1', '1', '3', '0']
    >>> print(luckynum)
    ['0', '1', '1', '1', '3', '8', '9', '9']
    >>> luckynum = sorted(birthday, reverse=True) # 내림차순으로 정렬된 리스트 생성
    >>> print(luckynum)
    ['9', '9', '8', '3', '1', '1', '1', '0']
    ```

-   리스트 컴프리헨션

    리스트 컴프리헨션(comprehension)이란 리스트를 만드는 간결한 방법이다.

    ```python
    >>> even = []
    >>> for i in range(2, 11, 2):
    	even.append(i)


    >>> print(even)
    [2, 4, 6, 8, 10]
    ```

    이를 이용해 위 코드를 다음과 같이 간결화 할 수 있다.

    ```python
    >>> even = [i for i in range(2, 11, 2)]
    >>>
    >>>
    >>> print(even)
    [2, 4, 6, 8, 10]
    ```

    리스트로 만들기 위해 대괄호로 감싸고 구성항목인 `i`를 가장 앞에 배치한다. for문 뒤 콜론 `:`은 생략한다.

    -   조건이 있는 경우!

        ```python
        >>> odd = []
        >>> for i in range(10):
        	if(i % 2 == 1):
        		odd.append(i)


        >>> print(odd)
        [1, 3, 5, 7, 9]
        ```

        위와 같은 코드를 컴프리헨션으로 함축한다면

        ```python
        >>> odd = [i for i in range(10) if i%2 == 1]
        >>> print(odd)
        [1, 3, 5, 7, 9]
        ```

        `리스트 = [항목연산식 for 항목 in 시퀀스 if 조건식]` 꼴
