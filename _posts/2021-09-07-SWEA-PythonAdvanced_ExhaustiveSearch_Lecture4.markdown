---
layout: post
title:  "SWEA - PythonAdvanced_ExhaustiveSearch_Lecture4 solution"
date:   2021-09-07 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[ 5189. [파이썬 S/W 문제해결 구현] 2일차 - 전자카트](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDYSqAAbw5UW6&subjectId=AWUYDrI61lYDFAVT)

풀이

```python
T = int(input())

answer = []
for tc in range(1, T + 1):

    N = int(input())
    graph = [list(map(int, input().split())) for _ in range(N)]

    seq_list = []
    q = [list(range(N))]
    for i in range(1, N):
        new_q = []
        for item in q:
            for j in range(i, N):
                temp_item = item[:]
                temp_item[i], temp_item[j] = temp_item[j], temp_item[i]
                new_q.append(temp_item)
        q = new_q
    
    min_path = 100000
    for item in q:
        item.append(0)
        temp = 0
        for i in range(len(item)-1):
            temp += graph[item[i]][item[i+1]]
        if min_path > temp:
            min_path = temp

    result = min_path
    
    # answer.append(result)
    print(f'#{tc} {result}')

# for tc in range(1, T+1):
#     print(f'#{tc} {answer[tc-1]}')
```

