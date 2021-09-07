---
layout: post
title:  "SWEA - PythonAdvanced_ExhaustiveSearch_Lecture3 solution"
date:   2021-09-07 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[5188. [파이썬 S/W 문제해결 구현] 2일차 - 최소합](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDYSqAAbw5UW6&subjectId=AWUYDrI61lYDFAVT)

풀이

```python
def get_min_path(N, board, i, j):
    if i==j==(N-1):
        return board[i][j]
    else:
        min_path = 10000000
        if i < N-1:
            temp = get_min_path(N, board, i+1, j)
            if min_path > temp:
                min_path = temp
        if j < N-1:
            temp = get_min_path(N, board, i, j+1)
            if min_path > temp:
                min_path = temp
        return board[i][j]+min_path

T = int(input())

answer = []
for tc in range(1, T + 1):

    N = int(input())
    board = [list(map(int, input().split())) for _ in range(N)]

    result = get_min_path(N, board, 0, 0)
    
    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

