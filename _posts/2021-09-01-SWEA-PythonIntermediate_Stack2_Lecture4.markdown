---
layout: post
title:  "SWEA - PythonIntermediate_Stack2_Lecture4 solution"
date:   2021-09-01 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[4874. [파이썬 S/W 문제해결 기본] 5일차 - Forth](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDN86AAXw5UW6&subjectId=AWOVIc7KqfQDFAWg#)

풀이

```python
T = int(input())

answer = []
for tc in range(1, T + 1): 
    
    input_list = input().split()

    stack = []
    result = 'error'
    try:
        for symbol in input_list:

            if symbol in '+-*/':
                b = int(stack.pop())
                a = int(stack.pop())
                if symbol == '+':
                    c = a + b
                elif symbol == '-':
                    c = a - b
                elif symbol == '*':
                    c = a * b
                else:
                    c = a // b
                stack.append(c)
            elif symbol == '.':
                result = int(stack.pop())
                if len(stack) != 0:
                    result = 'error'
                break
            else:
                stack.append(symbol)
    except:
        pass

    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

