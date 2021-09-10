---
layout: post
title:  "SWEA - PythonAdvanced_Backtracking_Lecture6 solution"
date:   2021-09-10 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[5209. [파이썬 S/W 문제해결 구현] 5일차 - 최소 생산 비용](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDYSqAAbw5UW6&subjectId=AWUYGf7K180DFAVT)

풀이

```python
def find_min_cost(N, costs, visited, i, cur_cost):
    global min_cost
    # promising
    if min_cost > cur_cost:
        # is a solution
        if i == N:
            min_cost = cur_cost
        # is not a solution
        # find next node
        else:
            for j in range(N):
                if not visited[j]:
                    visited[j] = 1
                    find_min_cost(N, costs, visited, i+1, cur_cost + costs[i][j])
                    visited[j] = 0

T = int(input())

answer = []
for tc in range(1, T + 1):
    
    N = int(input())
    costs = [list(map(int, input().split())) for _ in range(N)]

    min_cost = 2000
    visited = [False] * N

    find_min_cost(N, costs, visited, 0, 0)

    result = min_cost
    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

