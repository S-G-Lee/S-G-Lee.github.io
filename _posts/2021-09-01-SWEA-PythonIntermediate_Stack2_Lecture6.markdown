---
layout: post
title:  "SWEA - PythonIntermediate_Stack2_Lecture6 solution"
date:   2021-09-01 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[4880. [파이썬 S/W 문제해결 기본] 5일차 - 토너먼트 카드게임](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDN86AAXw5UW6&subjectId=AWOVIc7KqfQDFAWg#)

풀이

```python
def srp(card_list, person1, person2):
    '''
    1: scissor 2: rock 3: paper\n
    return winner
    '''
    a = card_list[person1]
    b = card_list[person2]
    if a == 1:
        if b == 2:
            return person2
    elif a == 2:
        if b == 3:
            return person2
    else:
        if b == 1:
            return person2
    return person1

T = int(input())

answer = []
for tc in range(1, T + 1): 
    
    # 1 : 가위, 2 : 바위, 3 : 보
    N = int(input())

    card_list = list(map(int, input().split()))
    
    i, j = 0, N-1

    stack = [[i, j]]
    a = 0
    b = 0

    while True:

        if type(stack[-1]) is list:
            i, j = stack[-1][0], stack[-1][1]
            if i == j:
                stack.pop()
                stack.append(i)
            else:
                stack.pop()
                stack.append([((i+j)//2) + 1, j])
                stack.append([i, (i+j)//2])
        else:
            if type(stack[-2]) is list:
                i, j = stack[-2][0], stack[-2][1]
                if i == j:
                    stack.pop(-2)
                    stack.append(i)
                else:
                    stack.pop(-2)
                    stack.append([((i+j)//2) + 1, j])
                    stack.append([i, (i+j)//2])
            else:
                a = stack[-2]
                b = stack[-1]
                c = srp(card_list, a, b)
                stack.pop()
                stack.pop()
                stack.append(c)


        if len(stack) <= 1:
            break
    
    result = stack[0] + 1
    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

