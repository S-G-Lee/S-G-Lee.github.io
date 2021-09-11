---
layout: post
title:  "SWEA - PythonAdvanced_GraphMinimumCost_Lecture8 solution"
date:   2021-09-11 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[[파이썬 S/W 문제해결 구현] 7일차 - 최소 이동 거리](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDYSqAAbw5UW6&subjectId=AWUYHO7a2JoDFAVT#)

풀이

```python
INF = 100000000


def dijkstra(V, graph):
    D = [INF for _ in range(V)]
    P = [None for _ in range(V)]
    visited = [0 for _ in range(V)]

    # start position: 0
    D[0] = 0

    for _ in range(V):
        v, min_path = -1, INF
        for i in range(V):
            if not visited[i] and min_path > D[i]:
                min_path = D[i]
                v = i
        
        visited[v] = 1
        for w in range(V):
            if D[v] + graph[v][w] < D[w]:
                D[w] = D[v] + graph[v][w]

    # end position: V-1
    return D[V-1]


T = int(input())

answer = []
for tc in range(1, T + 1):

    V, E = map(int, input().split())
    V += 1

    graph = [[INF for _ in range(V)] for _ in range(V)]
    for _ in range(E):
        v, w, weight = map(int, input().split())
        graph[v][w] = weight

    result = dijkstra(V, graph)

    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

