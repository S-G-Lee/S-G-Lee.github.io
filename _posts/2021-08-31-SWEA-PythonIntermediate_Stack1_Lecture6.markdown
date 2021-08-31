---
layout: post
title:  "SWEA - PythonIntermediate_Stack1_Lecture6 solution"
date:   2021-08-31 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[4869. [파이썬 S/W 문제해결 기본] 4일차 - 종이붙이기](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDN86AAXw5UW6&subjectId=AWOVHzyqqe8DFAWg#)

풀이

```python
# use DFS

# T = int(input())

# for tc in range(1, T + 1):   

#     N = int(input())

#     v = 0 # current index
#     stack = [[] for _ in range(10000)] # set arbitrary size of stack
#     top = 0
#     count = 0 # count the case

#     #initialize
#     if v + 10 < N: 
#         stack[top].append(v + 1) # put one 20 * 10 block
#     if v + 20 < N:
#         stack[top].append(v + 2) # put one 20 * 20 block
#         stack[top].append(v + 2) # put two 10 * 20 block

#     while True:       
        
#         w = stack[top]
        
#         while w:

#             stack[top] = w
#             v = stack[top][0]
#             stack[top].pop(0)
#             top += 1

#             w = [] # index list to go next
#             if v + 1 <= N//10:
#                 w.append(v + 1) # put one 20 * 10 block
#             if v + 2 <= N//10:
#                 w.append(v + 2) # put one 20 * 20 block
#                 w.append(v + 2) # put two 10 * 20 block
#             if v == N//10:
#                 count += 1
        
#         top -= 1
            
#         # code that makes do-while structure at Python
#         if top >= 0:
#             continue
#         break

#     print(f'#{tc} {count}')

# use DP

T = int(input())

for tc in range(1, T + 1): 

    N = int(input())

    memory = [ 0 for _ in range(N//10 + 1)]

    for i in range(len(memory)):
        if i == 0 :
            memory[i] = 1
        elif i == 1:
            memory[i] = 1
        else:
            memory[i] = (memory[i-2] * 2) + memory[i-1]
    
    print(f'#{tc} {memory[-1]}')
```

