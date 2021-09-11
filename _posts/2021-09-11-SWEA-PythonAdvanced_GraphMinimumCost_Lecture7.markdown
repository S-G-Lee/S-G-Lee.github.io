---
layout: post
title:  "SWEA - PythonAdvanced_GraphMinimumCost_Lecture7 solution"
date:   2021-09-11 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[5250. [파이썬 S/W 문제해결 구현] 7일차 - 최소 비용](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDYSqAAbw5UW6&subjectId=AWUYHO7a2JoDFAVT#)

풀이

```python
INF = 1000000


def dijkstra(N, graph):

    D = [[INF for _ in range(N)] for _ in range(N)]
    P = [[[None, None] for _ in range(N)] for _ in range(N)]
    visited = [[0 for _ in range(N)] for _ in range(N)]

    # start position: 0, 0
    D[0][0] = 0

    candidate = [[0, 0]]

    for _ in range(N):
        for _ in range(N):
            pass

            min_i, min_j, min_weight = None, None, INF
            for i, j in candidate:
                if not visited[i][j] and min_weight > D[i][j]:
                        min_weight = D[i][j]
                        min_i = i
                        min_j = j                    
            
            visited[min_i][min_j] = 1
            candidate.remove([min_i, min_j])

            for edge in graph[min_i][min_j]:
                i, j = edge['idx']
                if D[min_i][min_j] + edge['w'] < D[i][j]:
                    D[i][j] = D[min_i][min_j] + edge['w']
                    P[i][j][0] = min_i
                    P[i][j][1] = min_j
                    if not visited[i][j] and [i, j] not in candidate:
                        candidate.append([i, j])

    # end position: N-1, N-1
    return D[N-1][N-1]


T = int(input())

answer = []
for tc in range(1, T + 1):

    N = int(input())
    land = [list(map(int, input().split())) for _ in range(N)]
    graph = [[[] for _ in range(N)] for _ in range(N)]
    for i in range(N):
        for j in range(N):
            if i-1 >= 0:
                graph[i][j].append({'idx': (i-1, j), 'w': max(0, land[i-1][j] - land[i][j]) + 1})
            if j-1 >= 0:
                graph[i][j].append({'idx': (i, j-1), 'w': max(0, land[i][j-1] - land[i][j]) + 1})
            if i+1 < N:
                graph[i][j].append({'idx': (i+1, j), 'w': max(0, land[i+1][j] - land[i][j]) + 1})
            if j+1 < N:
                graph[i][j].append({'idx': (i, j+1), 'w': max(0, land[i][j+1] - land[i][j]) + 1})

    result = dijkstra(N, graph)

    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

