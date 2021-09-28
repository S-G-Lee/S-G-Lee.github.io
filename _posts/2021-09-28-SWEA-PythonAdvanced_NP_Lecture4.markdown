---
layout: post
title:  "SWEA - PythonAdvanced_NP_Lecture4 solution"
date:   2021-09-28 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[5286. [파이썬 S/W 문제해결 최적화] 5일차 - 그래프 색칠하기](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDYSqAAbw5UW6&subjectId=AWUYOWt63IMDFAVT)

풀이

```python
def coloring(N, edges, M):
    
    visited = [0] * (N+1)

    for v in range(1, N+1):
        colors = set(range(1, M+1))        
        for w in edges[v]:
            colors -= set({visited[w]})
        if not colors:
            return 0
        else:
            visited[v] = min(colors)

    return 1

T = int(input())

answer = []
for tc in range(1, T + 1):

    N, E, M= map(int, input().split())
    edges = [[] for _ in range(N+1)]
    for _ in range(E):
        i, j = map(int, input().split())
        edges[i].append(j)
        edges[j].append(i)
    
    result = coloring(N, edges, M)
    answer.append(result)

for tc in range(1, T + 1):
    print(f'#{tc} {answer[tc-1]}')
```

