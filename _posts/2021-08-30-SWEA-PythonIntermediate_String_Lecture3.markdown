---
layout: post
title:  "SWEA - PythonIntermediate_String_Lecture3 solution"
date:   2021-08-30 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[4864. [파이썬 S/W 문제해결 기본] 3일차 - 문자열 비교](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDN86AAXw5UW6&subjectId=AWOVGOEKqeoDFAWg#)

풀이

```python
T = int(input())

for tc in range(1, T + 1):

    str_N = input()
    str_M = input()

    length_N = len(str_N)
    length_M = len(str_M)

    pivot_M = length_N
    result = 0
    while pivot_M < length_M:

        pivot_N = length_N - 1
        tmppivot = pivot_M
        chkmatch = 0
        while pivot_N >= 0:
            if str_M[tmppivot] == str_N[pivot_N]:
                tmppivot -= 1
                chkmatch += 1
            else:
                tmppivot = pivot_M
                chkmatch = 0
            pivot_N -= 1
        
        if chkmatch == length_N:
            result = 1
            break
        else:
            pivot_M += length_N - chkmatch        

    print(f'#{tc} {result}')
```

