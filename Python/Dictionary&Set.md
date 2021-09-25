# 딕셔너리와 집합

## 딕셔너리

-   딕셔너리 개념과 생성

    딕셔너리란 키와 값의 쌍인 항목을 나열한 시퀀스이다.

    1. 딕셔너리는 중괄호 {...} 사이에 키와 값의 항목을 기술한다.
    2. 딕셔너리의 항목 순서는 의미가 없으며, 키는 중복될 수 없다.
    3. 키는 수정될 수 없지만, 값은 수정될 수 있다.
    4. 값은 키로 참조된다.

    ```python
    >>> dreamcar = { 'brand' : 'BMW', 'model' : 'mini', 'year' : 2020}
    >>> print(dreamcar)
    {'brand': 'BMW', 'model': 'mini', 'year': 2020}
    >>> print(type(dreamcar))
    <class 'dict'>
    ```

    빈 딕셔너리 생성을 하려면 빈 중괄호 `{}` 를 이용하거나 인자가 없는 내장 함수 `dict()` 호출한다.

    ```python
    >>> lect = {} # 빈 중괄호 이용
    >>> print(lect)
    {}
    >>> lecture = dict() # 내장 함수 dict() 이용
    >>> lecture['강좌명'] = 'Basic Python'  # 항목을 딕셔너리에 넣는 방법
    >>> lecture['개설년도'] = [2020, 1] # 항목 값으로 리스트 가능
    >>> lecture['학점시수'] = (3, 3) # 항목 값으로 튜플 가능
    >>> print(lecture)
    {'강좌명': 'Basic Python', '개설년도': [2020, 1], '학점시수': (3, 3)}
    ```

    항목을 딕셔너리에 넣으려면 `dict[key] = value` 꼴을 사용한다.

-   함수 `dict()`

    내장 함수 dict() 함수에서 인자로 리스트나 튜플 1개를 사용해 딕셔너리를 만들 수 있다.

    ```python
    >>> day = dict([]) # 빈 딕셔너리
    >>> day = dict(()) # 빈 딕셔너리
    ```

    함수 dict()의 리스트나 튜플 내부에서 일련의 key-value 쌍으로 `[key, value]` 리스트 형식과 `(key, value)` 튜플 형식을 모두 사용할 수 있다.

    ```python
    >>> day = dict([['월', 'mom'], ['화', 'tue'], ['수', 'wed']])
    >>> day = dict([('월', 'mom'), ('화', 'tue'), ('수', 'wed')])
    >>> day = dict((['월', 'mom'], ['화', 'tue'], ['수', 'wed']))
    >>> day = dict((('월', 'mom'), ('화', 'tue'), ('수', 'wed')))
    ```

    key가 문자열이면 `key = value` 항목의 나열로도 딕셔너리 생성

    ```python
    >>> day = dict(mon='monday', tue='tuesday', wed='wednesday') # 키에 따옴표 생략 가능
    >>> print(day)
    {'mon': 'monday', 'tue': 'tuesday', 'wed': 'wednesday'}
    ```

-   딕셔너리 키

    딕셔너리 키로 수정 불가능한 객체는 모두 가능하다.

    ```python
    >>> real = {3.14: '원주율'}
    >>> real[2.71] = '자연수' # 키 2.71로 값 '자연수' 항목 삽입
    >>> print(real)
    {3.14: '원주율', 2.71: '자연수'}
    >>> real[2.72] = '오일러수'
    >>> real[1.61] = '황금비'
    >>> print(real)
    {3.14: '원주율', 2.71: '자연수', 2.72: '오일러수', 1.61: '황금비'}
    >>> print(real[3.14])
    원주율
    >>> print(real[2.71])
    자연수
    ```

    수정 불가능한 정수도 가능하다.

    ```python
    >>> month = {1: 'January', 2: 'February', 3: 'March'}
    >>> print(month[2]) # 첨자가 아닌 키임을 잊지 말자
    February
    ```

    수정 불가능한 튜플도 가능하지만 리스트는 불가능하다.

    ```python
    >>> city = {(37.33, 126.58): '서울', (35.06, 129.03): '부산'} # 튜플로 키 설정
    >>> print(city)
    {(37.33, 126.58): '서울', (35.06, 129.03): '부산'}
    >>> city = {[37.33, 126.58]: '서울', [35.06, 129.03]: '부산'} # 리스트로 키 설정
    Traceback (most recent call last):
      File "<pyshell#4>", line 1, in <module>
        city = {[37.33, 126.58]: '서울', [35.06, 129.03]: '부산'}
    TypeError: unhashable type: 'list'
    ```

-   딕셔너리 항목의 순회

    메소드 `keys()`는 키로만 구성된 리스트를 반환한다.

    ```python
    >>> day = dict(월='monday', 화='tuesday', 수='wednesday', 목='thursday')
    >>> print(day)
    {'월': 'monday', '화': 'tuesday', '수': 'wednesday', '목': 'thursday'}
    >>> print(day.keys())
    dict_keys(['월', '화', '수', '목'])
    ```

    `for문`에서 시퀀스 위치에 `keys()`를 사용하면 딕셔너리의 모든 항목을 참조하는 구문을 사용할 수 있다.

    ```python
    >>> for key in day.keys():
    	print('%s요일 %s' % (key, day[key]))


    월요일 monday
    화요일 tuesday
    수요일 wednesday
    목요일 thursday
    ```

    메소드 `items()`는 `(key, value)` 쌍의 튜플이 들어 있는 리스트를 반환한다.

    ```python
    >>> day = dict(월='monday', 화='tuesday', 수='wednesday', 목='thursday')
    >>> print(day.items())
    dict_items([('월', 'monday'), ('화', 'tuesday'), ('수', 'wednesday'), ('목', 'thursday')])
    ```

    각 튜플의 첫 번째 항목은 키, 두 번째 항목은 키 값이다. 이를 이용해서 딕셔너리의 모든 항목을 참조하는 `for문` 은 아래와 같다.

    ```python
    >>> for key, value in day.items():
    	print('%s요일 %s' % (key, value))


    월요일 monday
    화요일 tuesday
    수요일 wednesday
    목요일 thursday
    ```

    메소드 `values()`는 값으로 구성된 리스트를 반환한다.

    ```python
    >>> day = dict(월='monday', 화='tuesday', 수='wednesday', 목='thursday')
    >>> print(day.values())
    dict_values(['monday', 'tuesday', 'wednesday', 'thursday'])
    ```

    for문에서 딕셔너리 변수로만 모든 키 순회하는 방법

    ```python
    >>> birthstone = dict(일월='석류석', 이월='자수정', 삼월='남옥', 사월='금강석')
    >>> for key in birthstone:
    	print('%s: %s' % (key, birthstone[key]))


    일월: 석류석
    이월: 자수정
    삼월: 남옥
    사월: 금강석
    ```

-   딕셔너리 항목의 참조와 삭제

    키로 조회하는 딕셔너리 메소드 `get(key[, default])`

    ```python
    >>> city = {'대한민국':'서울', '일본':'도쿄', '중국':'베이징'}
    >>> city.get('대한민국')
    '서울'
    >>> city.get('베트남') # 오류가 발생하지 않고 None을 반환한다.
    >>> city.get('베트남','새로운 정보')
    '새로운 정보'
    ```

    키로 삭제하는 딕셔너리 메소드 `pop(key[, default])`

    ```python
    >>> city = {'대한민국':'서울', '일본':'도쿄', '중국':'베이징'}
    >>> print(city.pop('일본')) # 삭제되는 키의 해당 값을 반환한다.
    도쿄
    >>> print(city)
    {'대한민국': '서울', '중국': '베이징'}
    >>> print(city.pop('베트남', '새로운 정보'))
    새로운 정보
    >>> print(city)
    {'대한민국': '서울', '중국': '베이징'}
    >>> print(city.pop('미국')) # 삭제할 키가 없는데 인자로 키만 넘겼을 경우 오류 발생
    Traceback (most recent call last):
      File "<pyshell#34>", line 1, in <module>
        print(city.pop('미국'))
    KeyError: '미국'
    ```

    임의의 항목을 삭제하는 딕셔너리 메소드 `popitem()`

    ```python
    >>> city = {'대한민국':'서울', '일본':'도쿄', '중국':'베이징'}
    >>> print(city.popitem()) # 임의의 튜플을 반환하고 삭제한다.
    ('중국', '베이징')
    >>> print(city)
    {'대한민국': '서울', '일본': '도쿄'}
    >>> print(city.popitem())
    ('일본', '도쿄')
    >>> print(city.popitem())
    ('대한민국', '서울')
    >>> print(city)
    {}
    >>> print(city.popitem()) # 데이터가 하나도 없다면 오류가 발생한다.
    Traceback (most recent call last):
      File "<pyshell#43>", line 1, in <module>
        print(city.popitem())
    KeyError: 'popitem(): dictionary is empty'
    ```

    문장 `del`로 딕셔너리 항목 삭제

    ```python
    >>> city = {'대한민국':'서울', '일본':'도쿄', '중국':'베이징'}
    >>> del city['일본'] # 키로 지정한 항복이 삭제된다.
    >>> print(city)
    {'대한민국': '서울', '중국': '베이징'}
    ```

-   딕셔너리 항목 전체 삭제와 변수 제거

    모든 항목을 제거하는 딕셔너리 메소드 `clear()`

    ```python
    >>> city = {'대한민국':'서울', '일본':'도쿄', '중국':'베이징'}
    >>> city.clear() # 기존의 모든 키:값 항목을 삭제한다.
    >>> print(city)
    {}
    ```

    문장 `del`로 딕셔너리 변수 제거

    ```python
    >>> city = {'대한민국':'서울', '일본':'도쿄', '중국':'베이징'}
    >>> del city # 변수 자체가 메모리에서 제거된다.
    >>> print(city) # 제거 이후에는 변수를 참조할 수 없다.
    Traceback (most recent call last):
      File "<pyshell#54>", line 1, in <module>
        print(city)
    NameError: name 'city' is not defined
    ```

-   딕셔너리 결합과 키의 멤버십 검사 연산자 `in`

    딕셔너리를 결합하는 메소드 `update()`

    ```python
    >>> kostock = {'Samsung Elec.':40000, 'Daum KAKAO' : 80000}
    >>> usstock = {'MS' : 150, 'Apple':180}
    >>> kostock.update(usstock)
    >>> kostock
    {'Samsung Elec.': 40000, 'Daum KAKAO': 80000, 'MS': 150, 'Apple': 180}
    >>> usstock.update({'MS':200}) # 동일한 키가 있다면 인자 딕셔너리의 값으로 대체된다.
    >>> usstock
    {'MS': 200, 'Apple': 180}
    ```

    문장 `in`으로 딕셔너리에 키가 존재하는지 검사

    ```python
    >>> cp = {'한국' : '서울', '중국' : '북경', '독일' : '베를린'}
    >>> '한국' in cp
    True
    >>> '일본' in cp
    False
    >>> if '미국' not in cp: # not in 가능
    	cp['미국'] = '워싱턴'


    >>> cp
    {'한국': '서울', '중국': '북경', '독일': '베를린', '미국': '워싱턴'}
    ```

---

## 집합

-   집합을 처리하는 자료형

    1. 원소는 불변 값으로 중복될 수 없으며 서로 다른 값이어야 한다.
    2. 원소는 중복을 허용하지 않으며 원소의 순서는 의미가 없다.

    ```python
    >>> set1 = {1, 2, 3, 4, 5}
    >>> set2 = {'py', 'c', 'js'}
    >>> set3 = {(1, 1), (2, 4), (3, 9)}
    ```

-   내장 함수 `set()`을 이용한 집합 생성

    내장 함수 `set()`은 집합을 만드며, 인자가 없으면 빈 집합인 공집합이 생성된다.

    ```python
    >>> s = set()
    >>> type(s)
    <class 'set'>
    >>> s # 공집합을 출력
    set()
    >>> d = {} # 빈 딕셔너리를 만드는 방법
    >>> type(d)
    <class 'dict'>
    ```

    리스트나 튜플을 인자로 사용하는 `set()` 함수

    ```python
    >>> set([1, 2, 3]) # 인자인 리스트의 항목으로 구성되는 집합을 생성
    {1, 2, 3}
    >>> set((1, 2, 2,)) # 인자인 튜플의 항목으로 구성되는 집합을 생성
    {1, 2} # 중복을 제거하고 생성
    >>> set(['a', 'b'])
    {'a', 'b'}
    ```

    문자열을 인자로 사용하는 `set()` 함수

    ```python
    >>> set('abc') # 각각의 문자가 원소인 집합이 생성
    {'c', 'a', 'b'} # 집합의 순서는 의미가 없다.
    ```

    수정 가능한 리스트와 딕셔너리는 집합의 원소로 사용할 수 없다.

    ```python
    >>> set([1, [2, 3]]) # 오류 발생
    Traceback (most recent call last):
      File "<pyshell#23>", line 1, in <module>
        set([1, [2, 3]])
    TypeError: unhashable type: 'list'
    ```

-   중괄호 `{}`를 이용한 집합 생성

    숫자, 문자열, 문자, 튜플 등과 같이 변할 수 없는 것이 원소로 가능하다.

    ```python
    >>> {1, 'sp', 'a', (1.2, 3.4)}
    {1, 'a', 'sp', (1.2, 3.4)}
    ```

    리스트나 딕셔너리는 원소로 사용불가

    ```python
    >>> {[1, 2, 3]} # 오류
    Traceback (most recent call last):
      File "<pyshell#25>", line 1, in <module>
        {[1, 2, 3]}
    TypeError: unhashable type: 'list'
    >>> {{1:'a', 2:'b'}} # 오류
    Traceback (most recent call last):
      File "<pyshell#26>", line 1, in <module>
        {{1:'a', 2:'b'}}
    TypeError: unhashable type: 'dict'
    ```

-   집합의 원소 추가와 삭제

    집합 메소드 `add(원소)`로 항목 추가

    ```python
    >>> odd = {1, 3, 5}
    >>> odd.add(7)
    >>> odd.add(9)
    >>> print(odd)
    {1, 3, 5, 7, 9}
    ```

    집합 메소드 `remove(원소)`으로 항목 삭제

    ```python
    >>> odd = {1, 3, 5}
    >>> odd.remove(3)
    >>> print(odd)
    {1, 5}
    >>> odd.remove(9) # 삭제하려는 원소가 없으면 오류가 발생한다.
    Traceback (most recent call last):
      File "<pyshell#38>", line 1, in <module>
        odd.remove(9)
    KeyError: 9
    ```

    집합 메소드 `discard(원소)`로 항목 삭제

    ```python
    >>> odd = {1, 3, 5}
    >>> odd.discard(3)
    >>> print(odd)
    {1, 5}
    >>> odd.discard(9) # 삭제하려는 원소가 없어도 오류가 발생하지 않는다.
    ```

    집합 메소드 `pop()`으로 임의의 항목 삭제

    ```python
    >>> odd = {1, 3, 5}
    >>> print(odd.pop())
    1
    >>> print(odd)
    {3, 5}
    ```

    집합 메소드 `clear()`로 집합의 모든 항목 삭제

    ```python
    >>> odd = {1, 3, 5}
    >>> odd.clear()
    >>> print(odd) # 빈 집합을 출력
    set()
    ```

-   집합의 주요 연산

    -   합집합

        연산자 `|`와 메소든 `union()`, `update()`

        ```python
        >>> a = {4, 6, 8, 10, 12} # 4에서 12까지의 2의 배수
        >>> b = {3, 6,9, 12} # 3에서 12까지의 3의 배수
        >>> a | b
        {3, 4, 6, 8, 9, 10, 12}
        >>> a.union(b) # a에는 영향을 주지 않는다.
        {3, 4, 6, 8, 9, 10, 12}
        >>> a
        {4, 6, 8, 10, 12}
        >>> a.update(b) # a에 반영되어 수정된다.
        >>> a
        {3, 4, 6, 8, 9, 10, 12}
        ```

    -   교집합

        연산자 `&`와 메소드 `intersection()`

        ```python
        >>> a = {4, 6, 8, 10 ,12}
        >>> b = {3, 6, 9, 12}
        >>> a & b
        {12, 6}
        >>> a.intersection(b) # a, b 모두에 영향을 미치지 않는다.
        {12, 6}
        >>> a
        {4, 6, 8, 10, 12}
        >>> a.intersection_update(b) # a를 수정
        >>> a
        {12, 6}
        ```

    -   차집합

        연산자 `-`와 메소드 `difference()`

        ```python
        >>> a = {4, 6, 8, 10, 12}
        >>> b = {3, 6, 9, 12}
        >>> a - b
        {8, 10, 4}
        >>> a.difference(b)
        {8, 10, 4}
        >>> a # a에 영향을 주지 않는다
        {4, 6, 8, 10, 12}
        >>> b - a # 교환 법칙은 성립하지 않는다.
        {9, 3}
        >>> b.difference(a)
        {9, 3}
        >>> a.difference_update(b) # a를 수정
        >>> a
        {2, 4, 8, 10}
        ```

    -   여집합

        연산자 `^`와 메소드 `symmetric_difference()`

        ```python
        >>> a = {4, 6, 8 ,10 ,12}
        >>> b = {3, 6, 9, 12}
        >>> a ^ b
        {3, 4, 8, 9, 10}
        >>> a.symmetric_difference(b)
        {3, 4, 8, 9, 10}
        >>> a # a에 영향을 주지 않는다
        {4, 6, 8, 10, 12}
        >>> a.symmetric_difference_update(b) # a를 수정
        >>> a
        {3, 4, 8, 9, 10}
        ```

    집합 연산 네 가지에도 축약 대입 연산자 `|=`, `&=`, `-=`, `^=`을 제공한다.

    ```python
    >>> A = set('abcd'); B = set('cde')
    >>> A |= B # A = A | B, A.update(B) 와 같은 결과
    >>> A
    {'d', 'b', 'a', 'c', 'e'}

    >>> A = set('abcd'); B = set('cde')
    >>> A &= B # A = A & B, A.intersection_update(B) 와 같은 결과
    >>> A
    {'d', 'c'}

    >>> A = set('abcd'); B = set('cde')
    >>> A -= B # A = A - B, A.difference_update(B) 와 같은 결과
    >>> A
    {'b', 'a'}

    >>> A = set('abcd'); B = set('cde')
    >>> A ^= B # A = A ^ B, A.symmetric_difference_update(B) 와 같은 결과
    >>> A
    {'b', 'a', 'e'}
    ```

-   함수 `len()`

    함수 `len()`으로 집합에 들어 있는 원소의 개수를 확인할 수 있다.

    ```python
    >>> good = {'weekend', 'chill', 'netfilx'}
    >>> len(good) # 원소의 개수
    3
    ```

-   소속 연산자 `in`

    특정 원소가 집합에 있는지 확인하기 위해 사용한다.

    ```python
    >>> good = {'weekend', 'chill', 'netfilx'}
    >>> bad = {'week', 'blue', 'exercise'}
    >>> 'exercise' in good
    False
    >>> 'exercise' in bad
    True
    ```
