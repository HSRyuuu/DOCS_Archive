# 파이썬 기초 학습 가이드 (Part 2) - Java 개발자용

> 제어문, 함수, 클래스, 입출력, 예외 처리

## 목차
1. if문
2. while문
3. for문
4. 함수
5. 클래스
6. 파일 입출력
7. 예외 처리
8. 주요 내장 함수

---

## 1. if문

**Java와의 차이점**: 중괄호 대신 들여쓰기, else if 대신 elif.

### 기본 구조
```python
money = 2000
if money >= 3000:
    print("택시")
else:
    print("걸어가라")
```

### 비교 연산자
```python
x < y
x > y
x == y
x != y
x >= y
x <= y
```

### 논리 연산자
```python
# Java: && || !
# Python: and or not

money = 2000
card = True
if money >= 3000 or card:
    print("택시")
else:
    print("걸어가라")
```

### in/not in 연산자
```python
1 in [1, 2, 3]  # True
1 not in [1, 2, 3]  # False
'a' in ('a', 'b', 'c')  # True
'j' not in 'python'  # True
```

### elif
```python
pocket = ['paper', 'handphone']
card = True

if 'money' in pocket:
    print("택시")
elif card:
    print("택시")
else:
    print("걸어가라")
```

### 조건부 표현식 (삼항 연산자)
```python
# Java: (score >= 60) ? "success" : "failure"
score = 70
message = "success" if score >= 60 else "failure"
```

---

## 2. while문

### 기본 구조
```python
treeHit = 0
while treeHit < 10:
    treeHit += 1
    print(f"나무를 {treeHit}번 찍었습니다.")
    if treeHit == 10:
        print("나무 넘어갑니다.")
```

### break와 continue
```python
# break
coffee = 10
while True:
    coffee -= 1
    if coffee == 0:
        break

# continue
a = 0
while a < 10:
    a += 1
    if a % 2 == 0:
        continue
    print(a)  # 홀수만 출력
```

---

## 3. for문

### 기본 구조
```python
test_list = ['one', 'two', 'three']
for i in test_list:
    print(i)

# 튜플
a = [(1, 2), (3, 4), (5, 6)]
for (first, last) in a:
    print(first + last)

# 딕셔너리
marks = {'kim': 90, 'lee': 80}
for subject, score in marks.items():
    print(subject, score)
```

### range 함수
```python
# 0~9
for i in range(10):
    print(i)

# 1~10
for i in range(1, 11):
    print(i)

# 0, 2, 4, 6, 8
for i in range(0, 10, 2):
    print(i)
```

### 리스트 컴프리헨션
```python
# 기본
a = [1, 2, 3, 4]
result = [num * 3 for num in a]  # [3, 6, 9, 12]

# 조건 포함
result = [num * 3 for num in a if num % 2 == 0]  # [6, 12]

# 다중 for문
result = [x * y for x in range(2, 10) for y in range(1, 10)]
```

---

## 4. 함수 (Function)

### 기본 구조
```python
def add(a, b):
    return a + b

result = add(3, 4)  # 7
```

### 다양한 함수 형태
```python
# 일반 함수
def add(a, b):
    return a + b

# 입력값 없음
def say():
    return 'Hi'

# 반환값 없음
def add(a, b):
    print(f"{a}, {b}의 합은 {a+b}입니다.")

# 입력값, 반환값 모두 없음
def say():
    print('Hi')
```

### 매개변수 기본값
```python
def say_myself(name, age, man=True):
    print(f"나의 이름은 {name}입니다.")
    print(f"나이는 {age}살입니다.")
    if man:
        print("남자입니다.")
    else:
        print("여자입니다.")

say_myself("박응용", 27)  # man은 True
say_myself("박응용", 27, False)
```

### 가변 매개변수
```python
def add_many(*args):
    result = 0
    for i in args:
        result += i
    return result

add_many(1, 2, 3)  # 6
add_many(1, 2, 3, 4, 5)  # 15
```

### 키워드 매개변수
```python
def print_kwargs(**kwargs):
    print(kwargs)

print_kwargs(a=1)  # {'a': 1}
print_kwargs(name='foo', age=3)  # {'name': 'foo', 'age': 3}
```

### 여러 값 반환
```python
def add_and_mul(a, b):
    return a+b, a*b

result1, result2 = add_and_mul(3, 4)
print(result1, result2)  # 7 12
```

### lambda 함수
```python
add = lambda a, b: a + b
result = add(3, 4)  # 7

# 리스트에서 활용
myList = [lambda a, b: a+b, lambda a, b: a*b]
print(myList[0](3, 4))  # 7
```

---

## 5. 클래스 (Class)

**Java와의 차이점**: 접근 제한자 없음, self 명시적 사용.

### 기본 클래스
```python
class FourCal:
    def __init__(self, first, second):  # 생성자
        self.first = first
        self.second = second
    
    def add(self):
        return self.first + self.second
    
    def sub(self):
        return self.first - self.second
    
    def mul(self):
        return self.first * self.second
    
    def div(self):
        return self.first / self.second

# 객체 생성
a = FourCal(4, 2)
print(a.add())  # 6
print(a.div())  # 2.0
```

### 상속
```python
class MoreFourCal(FourCal):
    def pow(self):
        return self.first ** self.second

a = MoreFourCal(4, 2)
print(a.pow())  # 16
print(a.add())  # 6 (부모 메서드)
```

### 메서드 오버라이딩
```python
class SafeFourCal(FourCal):
    def div(self):
        if self.second == 0:
            return 0
        else:
            return self.first / self.second

a = SafeFourCal(4, 0)
print(a.div())  # 0 (오류 대신)
```

### 클래스 변수
```python
class Family:
    lastname = "김"  # 클래스 변수

print(Family.lastname)  # '김'

a = Family()
b = Family()
print(a.lastname)  # '김'

Family.lastname = "박"
print(a.lastname)  # '박' (모든 인스턴스에 영향)
print(b.lastname)  # '박'
```

---

## 6. 파일 입출력

### 파일 쓰기
```python
# 방법1: 수동 close
f = open("새파일.txt", 'w')
f.write("Hello")
f.close()

# 방법2: with문 (권장!)
with open("새파일.txt", 'w') as f:
    f.write("Hello")
```

### 파일 읽기
```python
# 전체 읽기
with open("새파일.txt", 'r') as f:
    data = f.read()

# 한 줄 읽기
with open("새파일.txt", 'r') as f:
    line = f.readline()

# 모든 줄 읽기
with open("새파일.txt", 'r') as f:
    lines = f.readlines()
    for line in lines:
        print(line.strip())
```

### 파일 모드
```python
# 'r': 읽기
# 'w': 쓰기 (덮어쓰기)
# 'a': 추가
# 'b': 바이너리

f = open("새파일.txt", 'a')  # 추가 모드
f.write("추가 내용\\n")
f.close()
```

---

## 7. 예외 처리

### 기본 구조
```python
try:
    4 / 0
except ZeroDivisionError as e:
    print(e)
```

### 여러 예외 처리
```python
try:
    a = [1, 2]
    print(a[3])
except ZeroDivisionError:
    print("0으로 나눌 수 없습니다")
except IndexError:
    print("인덱스 오류")
finally:
    print("항상 실행")
```

### 예외 발생시키기
```python
class Bird:
    def fly(self):
        raise NotImplementedError
```

### 사용자 정의 예외
```python
class MyError(Exception):
    pass

def say_nick(nick):
    if len(nick) < 3:
        raise MyError()
    print(nick)

try:
    say_nick("홍")
except MyError:
    print("닉네임은 3자 이상이어야 합니다.")
```

---

## 8. 주요 내장 함수
```python
# abs() - 절대값
abs(-3)  # 3

# all() - 모두 참?
all([1, 2, 3])  # True
all([0, 1, 2])  # False

# any() - 하나라도 참?
any([0, 1, 2])  # True
any([0, ""])  # False

# len() - 길이
len("python")  # 6
len([1, 2, 3])  # 3

# max(), min() - 최대/최소
max([1, 2, 3])  # 3
min("python")  # 'h'

# pow() - 거듭제곱
pow(2, 4)  # 16

# range() - 범위
list(range(5))  # [0, 1, 2, 3, 4]
list(range(1, 11))  # [1, 2, ..., 10]

# sorted() - 정렬
sorted([3, 1, 2])  # [1, 2, 3]

# sum() - 합계
sum([1, 2, 3])  # 6

# type() - 타입 확인
type(3)  # <class 'int'>
type([])  # <class 'list'>

# zip() - 묶기
list(zip([1, 2], [3, 4]))  # [(1, 3), (2, 4)]

# enumerate() - 인덱스와 값
for i, name in enumerate(['body', 'foo', 'bar']):
    print(i, name)
# 0 body
# 1 foo
# 2 bar

# map() - 함수 적용
list(map(str, [1, 2, 3]))  # ['1', '2', '3']

# filter() - 필터링
list(filter(lambda x: x > 0, [-1, 0, 1, 2]))  # [1, 2]
```

---

## Java vs Python 주요 차이점 요약

| 항목 | Java | Python |
|-----|------|--------|
| 타입 선언 | 필수 | 불필요 (동적 타이핑) |
| 들여쓰기 | 선택 (중괄호) | 필수 (문법) |
| 세미콜론 | 필수 | 불필요 |
| 배열/리스트 | 고정 타입 | 다양한 타입 혼합 가능 |
| 접근 제한자 | public, private 등 | 없음 (관례로 _) |
| 생성자 | 클래스명과 동일 | `__init__` |
| this/self | 암묵적 | 명시적 (self) |
| 오버로딩 | 지원 | 미지원 (기본값으로 대체) |
| 다중 상속 | 인터페이스로만 | 직접 지원 |
