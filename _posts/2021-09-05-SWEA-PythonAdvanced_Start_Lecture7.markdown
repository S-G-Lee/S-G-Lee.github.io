---
layout: post
title:  "SWEA - PythonAdvanced_Start_Lecture7 solution"
date:   2021-09-05 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[5186. [파이썬 S/W 문제해결 구현] 1일차 - 이진수2](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDYSqAAbw5UW6&subjectId=AWUYDLaK1kMDFAVT)

풀이

```python
T = int(input())

answer = []
for tc in range(1, T + 1):

    num = float(input())

    digit = 1/2
    result = ''
    for _ in range(12):
        if num > digit:
            num = num-digit
            result += '1'
        elif num < digit:
            result += '0'
        else:
            result += '1'
            break
        digit = digit / 2
    else:
        result = 'overflow'
    
    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

