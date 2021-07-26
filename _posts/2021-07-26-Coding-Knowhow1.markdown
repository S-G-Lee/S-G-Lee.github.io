---
layout: post
title:  "코딩 노하우 1편"
date:   2021-07-26 18:25:00 +0900
categories: coding
tags: [coding, skill]
---
# 코딩 노하우 1편

[TOC]

코딩하면서 필요했던 스킬들을 간략히 기술하고 각 항목의 자세한 내용은 추후 다룰 예정입니다.

## 1. Input으로 case개수를 받은 뒤 각 case별 코드 수행

알고리즘 문제 사이트에서는 일반적으로 input의 맨 윗줄에 case의 개수를 항목으로 주고 그 다음 줄부터 각 case별 필요한 input을 넣어줍니다. 그래서 이를 case별로 처리하기 위해 코드의 시작을 다음과 같이 하면 좋습니다.

```python
T = int(input()) # case 개수를 입력받음

for i in range(1, T+1): # case 1 ~ case T에 대해 코드실행
    # 코드작성
```



## 2. Python에서 대소문자 구분

Python에서는 문자열 객체에 대소문자를 판별하는 메소드 `isupper() `및 `islower()`를 제공합니다. `isupper()`메소드는 문자열이 모두 대문자인지 판별하고, `islower()`메소드는 문자열이 모두 소문자인지 판별합니다.

```python
word = 'something'
word.isupper() # 문자열이 모두 대문자이면 True를 반환
word.islower() # 문자열이 모두 소문자이면 True를 반환
```

## 3. 문자를 숫자로, 숫자를 문자로

```python
ord('A') # 문자 A를 해당하는 유니코드 숫자로 변환
chr(65) # 숫자 65를 해당하는 유니코드 문자로 변환
```

## 4. 문자열을 항목으로 갖는 리스트를 문자열로 변환

```python
'<something>'.join(<list>)
# ex
''.join(['1', '2', '3']) # '123'
'-'.join(['1', '2', '3']) # '1-2-3'
```

## 5. 줄바꿈 안하고 print

```python
print('something', end = '')
# end = '' 의 ''부분에 ' ', '-'등이 들어가면 문자열 맨 뒤에 줄바꿈 대신 해당 문자열이 붙어 출력된다
```

## 6. Python에서 문자열을 아주 쉽게 뒤집는 법

```python
some = 'string'
some[::-1] # 'gnirts'
```

## 7. 리스트에서 중복된 값을 제거하는 법

```python
# 리스트를 셋으로 바꾸고 다시 리스트로 바꾸면 된다. 셋은 중복값을 허용하지 않기 때문이다
list1 = [1, 2, 3, 4, 3, 2, 1]
set1 = set(list1)
list1 = list(set1) # [1, 2, 3, 4]
```

## 8. map 및 filter 사용시 조건에 들어갈 간단한 함수

```python
# lambda를 이용
map(lambda x : foo(x), <iterable>)
filter(lambda x : condition(x), <iterable>)
```

## 9. 소수점 자리수 원하는만큼 출력

```python
a = 123.456
print(f'{a:.1f}') # 소수점 1째자리까지 123.5
print(f'{a:.2f}') # 소수점 2째자리까지 123.46
print(f'{a:.4f}') # 소수점 4째자리까지 123.4560
```

## 10. 리스트 정렬

```python
list1 = [3, 1, 2]
a = list1.sort() # list1 = [1, 2, 3], a = None
list2 = sorted(list1) # list1 = [3, 1, 2], list2 = [1, 2, 3]
```

## 11. for문에서 인덱스와 값을 동시에 쉽게 받는 방법

```python
for idx, val in enumerate(iterable):
```

## 12. 2차원 이상의 배열을 얕은 복사가 안되게 하는법

```python
mat = [[0] * M] * N # 이러면 안됨
mat = [[0 for _ in range(M)] for _ in range(N)] # 이래야됨
```

## 13. 딕셔너리 정렬

```python
import operator

inputdict  = {
"TV": 2000000,
"냉장고": 1500000,
"책상": 350000,
"노트북": 1200000,
"가스레인지": 200000,
"세탁기": 1000000
}

resultdict = dict(sorted(inputdict.items(), key = operator.itemgetter(1), reverse = True))
```

## 14. getter, setter

