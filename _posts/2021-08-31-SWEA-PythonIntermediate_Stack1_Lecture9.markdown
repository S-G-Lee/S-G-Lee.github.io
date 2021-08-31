---
layout: post
title:  "SWEA - PythonIntermediate_Stack1_Lecture9 solution"
date:   2021-08-31 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[4873. [파이썬 S/W 문제해결 기본] 4일차 - 반복문자 지우기](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDN86AAXw5UW6&subjectId=AWOVHzyqqe8DFAWg#)

풀이

```python
T = int(input())

for tc in range(1, T + 1): 

    s = input()
    
    stack = [-1] * 10000
    top = -1

    for char in s:
        if char is stack[top]:
            stack[top] = -1
            top -= 1
        else:
            top += 1
            stack[top] = char
    
    print(f'#{tc} {top + 1}')
```

