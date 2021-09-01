---
layout: post
title:  "SWEA - PythonIntermediate_Stack2_Lecture5 solution"
date:   2021-09-01 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[4875. [파이썬 S/W 문제해결 기본] 5일차 - 미로](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDN86AAXw5UW6&subjectId=AWOVIc7KqfQDFAWg#)

풀이

```python
def search_way(N, i, j, board, visited):

    if i + 1 < N and board[i + 1][j] != 1 and not visited[i + 1][j]:
        return [i + 1, j]
    elif i - 1 >= 0 and board[i - 1][j] != 1 and not visited[i - 1][j]:
        return [i - 1, j]
    if j + 1 < N and board[i][j + 1] != 1 and not visited[i][j + 1]:
        return [i, j + 1]
    if j - 1 >= 0 and board[i][j - 1] != 1 and not visited[i][j - 1]:
        return [i, j - 1]


T = int(input())

answer = []
for tc in range(1, T + 1): 
    
    N = int(input())

    board = []
    for _ in range(N):
        board.append(list(map(int, input())))

    visited = [[0 for _ in range(N)] for _ in range(N)]
    
    start = [-1, -1]
    goal = [-1, -1]
    for i in range(N):
        for j in range(N):
            if board[i][j] == 2:
                start = [i, j]
            elif board[i][j] == 3:
                goal = [i, j]

    stack = []
    stack.append(start)
    result = 0
    while stack:
        
        w = search_way(N, stack[-1][0], stack[-1][1], board, visited)
        while w:
            if w == goal:
                result = 1
                break
            visited[w[0]][w[1]] = 1
            stack.append(w)
            w = search_way(N, stack[-1][0], stack[-1][1], board, visited)
        if w == goal:
            result = 1
            break
        stack.pop()
        
    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

