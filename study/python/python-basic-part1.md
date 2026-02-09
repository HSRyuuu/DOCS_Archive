# 파이썬 기초 학습 가이드 (Part 1) - Java 개발자용

> Java에서 파이썬으로: 핵심 개념 비교 학습

## 목차
1. 숫자형
2. 문자열
3. 리스트
4. 튜플
5. 딕셔너리
6. 집합
7. 불 자료형
8. 변수

---

## 1. 숫자형 (Number)

**Java와의 차이점**: 파이썬은 정수 크기 제한이 없고, 타입 선언이 불필요합니다.

### 정수형 (Integer)
```python
# Java: int a = 123;
a = 123
a = -178
a = 0
```

### 실수형 (Floating-point)
```python
# Java: double a = 1.2;
a = 1.2
a = -3.45
a = 4.24E10  # 지수 표현
a = 4.24e-10
```

### 8진수와 16진수
```python
a = 0o177  # 8진수 (Java: 0177)
a = 0x8ff  # 16진수 (Java: 0x8ff)
```

### 산술 연산자
```python
a, b = 3, 4

# 사칙연산 (Java와 동일)
a + b  # 7
a - b  # -1
a * b  # 12
a / b  # 0.75

# 거듭제곱 (Java: Math.pow(a, b))
a ** b  # 81

# 나머지 (Java: a % b)
7 % 3  # 1

# 몫 (Java: a / b로 정수 나눗셈)
7 // 4  # 1
```

### 복합 연산자
```python
a += 1  # a = a + 1
a -= 1  # a = a - 1
a *= 2
a /= 2
a //= 2
a %= 3
a **= 2
```

---

## 2. 문자열 (String)

**Java와의 차이점**: 문자열 생성 방법이 다양하고, 인덱싱/슬라이싱이 매우 강력합니다.

### 문자열 생성
```python
# 4가지 방법 모두 가능 (Java는 "만 사용)
s1 = "Hello World"
s2 = 'Python is fun'
s3 = """Life is too short"""  # 여러 줄 문자열
s4 = '''You need python'''
```

### 이스케이프 코드
```python
# Java와 동일
multiline = "Life is too short\\nYou need python"
tab_string = "Hello\\tWorld"
quote = "Python's \\"best\\""
```

### 문자열 연산
```python
# 연결 (Java: + 연산자와 동일)
"Python" + " is fun!"  # 'Python is fun!'

# 반복 (Java에는 없는 기능!)
"python" * 2  # 'pythonpython'

# 길이 (Java: s.length())
len("Life is too short")  # 17
```

### 인덱싱 (Java의 charAt()과 유사)
```python
a = "Life is too short"
a[0]   # 'L' (Java: a.charAt(0))
a[3]   # 'e'
a[-1]  # 'n' (뒤에서 첫번째, Java에는 없음!)
a[-2]  # 'o' (뒤에서 두번째)
```

### 슬라이싱 (Java의 substring()보다 강력!)
```python
a = "Life is too short, You need Python"

# Java: a.substring(0, 4)
a[0:4]   # 'Life'
a[0:3]   # 'Lif'

# 시작/끝 생략 가능 (Java에는 없음!)
a[:4]    # 'Life'
a[5:]    # 'is too short, You need Python'
a[:]     # 전체 복사

# 음수 인덱스 사용
a[19:-7] # 'You need'
```

### 문자열 포매팅

**1. % 포매팅**
```python
"I eat %d apples." % 3
"I eat %s apples." % "five"
"I ate %d apples. so I was sick for %s days." % (10, "three")
```

**2. format() 메서드**
```python
"I eat {0} apples".format(3)
"I ate {number} apples. so I was sick for {day} days.".format(number=10, day=3)

# 정렬
"{0:<10}".format("hi")  # 왼쪽
"{0:>10}".format("hi")  # 오른쪽
"{0:^10}".format("hi")  # 가운데

# 소수점
"{0:0.4f}".format(3.42134234)  # '3.4213'
```

**3. f-문자열 (Python 3.6+, 가장 권장!)**
```python
name = '홍길동'
age = 30

f'나의 이름은 {name}입니다. 나이는 {age}입니다.'
f'나는 내년이면 {age + 1}살이 된다.'
f'{3.42134234:0.4f}'  # '3.4213'
f"난 {1500000:,}원이 필요해"  # '난 1,500,000원이 필요해'
```

### 주요 문자열 메서드
```python
# count - 개수 세기
"hobby".count('b')  # 2

# find - 위치 찾기 (없으면 -1)
"Python is the best".find('b')  # 14

# index - 위치 찾기 (없으면 에러)
"Life is too short".index('t')  # 8

# join - 결합
",".join('abcd')  # 'a,b,c,d'

# upper/lower - 대소문자 변환
"hi".upper()  # 'HI'
"HI".lower()  # 'hi'

# strip - 공백 제거
" hi ".strip()   # 'hi'
" hi ".lstrip()  # 'hi '
" hi ".rstrip()  # ' hi'

# replace - 치환
"Life is too short".replace("Life", "Your leg")

# split - 분리
"Life is too short".split()  # ['Life', 'is', 'too', 'short']
"a:b:c:d".split(':')  # ['a', 'b', 'c', 'd']

# 검증
"Python".isalpha()   # True
"12345".isdigit()    # True
"Life".startswith("Li")  # True
"short".endswith("rt")   # True
```

---

## 3. 리스트 (List)

**Java와의 차이점**: Java의 ArrayList와 유사하지만 다양한 타입 혼합 가능!

### 리스트 생성
```python
a = []  # 빈 리스트
b = [1, 2, 3]
c = ['Life', 'is', 'too', 'short']
d = [1, 2, 'Life', 'is']  # 다양한 타입!
e = [1, 2, ['Life', 'is']]  # 중첩 리스트
```

### 인덱싱과 슬라이싱
```python
a = [1, 2, 3, 4, 5]

# 인덱싱
a[0]   # 1
a[-1]  # 5 (마지막)

# 슬라이싱
a[0:2]  # [1, 2]
a[:2]   # [1, 2]
a[2:]   # [3, 4, 5]

# 중첩 리스트
a = [1, 2, ['a', 'b', 'c']]
a[2][0]  # 'a'
```

### 리스트 연산
```python
# 연결
[1, 2, 3] + [4, 5]  # [1, 2, 3, 4, 5]

# 반복
[1, 2] * 3  # [1, 2, 1, 2, 1, 2]

# 길이
len([1, 2, 3])  # 3
```

### 리스트 수정과 삭제
```python
a = [1, 2, 3]
a[2] = 4  # [1, 2, 4]
del a[1]  # [1, 4]
```

### 주요 리스트 메서드
```python
a = [1, 2, 3]

# append - 추가
a.append(4)  # [1, 2, 3, 4]

# sort - 정렬
a = [3, 1, 2]
a.sort()  # [1, 2, 3]

# reverse - 역순
a.reverse()  # [3, 2, 1]

# index - 위치
a = [1, 2, 3]
a.index(3)  # 2

# insert - 삽입
a.insert(0, 4)  # [4, 1, 2, 3]

# remove - 제거
a = [1, 2, 3, 1]
a.remove(1)  # 첫 번째 1만 제거

# pop - 꺼내기
a = [1, 2, 3]
a.pop()   # 3 반환, a는 [1, 2]
a.pop(0)  # 1 반환, a는 [2]

# count - 개수 세기
[1, 2, 1, 3].count(1)  # 2

# extend - 확장
a = [1, 2]
a.extend([3, 4])  # [1, 2, 3, 4]
```

---

## 4. 튜플 (Tuple)

**Java와의 차이점**: 변경 불가능한 리스트. Java에는 직접 대응 개념 없음.

### 튜플 생성과 특징
```python
t1 = ()
t2 = (1,)  # 요소 1개일 때는 쉼표 필수!
t3 = (1, 2, 3)
t4 = 1, 2, 3  # 괄호 생략 가능

# 인덱싱, 슬라이싱 가능
t = (1, 2, 3)
t[0]    # 1
t[1:]   # (2, 3)

# 연산 가능
(1, 2) + (3, 4)  # (1, 2, 3, 4)
(1, 2) * 3  # (1, 2, 1, 2, 1, 2)

# 수정 불가!
# t[0] = 4  # TypeError!
```

---

## 5. 딕셔너리 (Dictionary)

**Java와의 차이점**: Java의 HashMap과 유사하지만 문법이 더 간결.

### 딕셔너리 생성과 사용
```python
# 생성
dic = {'name': 'pey', 'phone': '010-1234-5678', 'birth': '1118'}

# 접근
dic['name']  # 'pey'

# 추가
dic['age'] = 30

# 삭제
del dic['phone']
```

### 주요 딕셔너리 메서드
```python
a = {'name': 'pey', 'phone': '010-1234', 'birth': '1118'}

# keys - 키 목록
a.keys()  # dict_keys(['name', 'phone', 'birth'])

# values - 값 목록
a.values()  # dict_values(['pey', '010-1234', '1118'])

# items - 키-값 쌍
a.items()  # dict_items([('name', 'pey'), ...])

# get - 값 가져오기
a.get('name')  # 'pey'
a.get('nokey', 'default')  # 'default'

# in - 존재 확인
'name' in a  # True

# clear - 초기화
a.clear()  # {}
```

---

## 6. 집합 (Set)

**Java와의 차이점**: Java의 HashSet과 거의 동일.

### 집합 생성과 연산
```python
s1 = set([1, 2, 3, 4, 5, 6])
s2 = set([4, 5, 6, 7, 8, 9])

# 교집합
s1 & s2  # {4, 5, 6}
s1.intersection(s2)

# 합집합
s1 | s2  # {1, 2, 3, 4, 5, 6, 7, 8, 9}
s1.union(s2)

# 차집합
s1 - s2  # {1, 2, 3}
s1.difference(s2)
```

### 집합 메서드
```python
s = set([1, 2, 3])

s.add(4)  # 추가
s.update([5, 6])  # 여러 값 추가
s.remove(2)  # 제거
```

---

## 7. 불(Bool) 자료형
```python
a = True   # 대문자 주의!
b = False

# 비교 연산
1 == 1    # True
1 != 1    # False
2 > 1     # True

# 자료형의 참/거짓
bool([1, 2])  # True (비어있지 않음)
bool([])      # False (비어있음)
bool("")      # False
bool("python")  # True
bool(0)       # False
bool(3)       # True
```

---

## 8. 변수 (Variable)

**Java와의 차이점**: 타입 선언 불필요 (동적 타이핑).
```python
# 변수 생성
a = 3
b = "Life"

# 여러 변수 동시 할당
a, b = ('python', 'life')
a, b = 'python', 'life'
[a, b] = ['python', 'life']

# 값 교환 (임시변수 불필요!)
a, b = b, a

# 리스트 복사 주의
a = [1, 2, 3]
b = a  # 같은 객체 참조
b = a[:]  # 진짜 복사
```
