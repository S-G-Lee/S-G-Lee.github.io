---
layout: post
title:  "SWEA - PythonIntermediate_Stack1_Lecture7 solution"
date:   2021-08-31 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[4866. [파이썬 S/W 문제해결 기본] 4일차 - 괄호검사](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDN86AAXw5UW6&subjectId=AWOVHzyqqe8DFAWg#)

풀이

```python
T = int(input())

for tc in range(1, T + 1): 

    string = input()

    stack = [0] * 10000
    top = 0

    for letter in string:
        if letter in ['(', '{']:
            top += 1
            stack[top] = letter
        elif letter is ')':
            if stack[top] == '(':
                stack[top] = 0
                top -= 1
            else:
                top = -1
                break
        elif letter is '}':
            if stack[top] == '{':
                stack[top] = 0
                top -= 1
            else:
                top = -1
                break
    
    result = 0
    if top == 0:
        result = 1
    print(f'#{tc} {result}')
```

