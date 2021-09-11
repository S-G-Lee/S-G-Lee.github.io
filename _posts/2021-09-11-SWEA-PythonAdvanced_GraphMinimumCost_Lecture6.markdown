---
layout: post
title:  "SWEA - PythonAdvanced_GraphMinimumCost_Lecture6 solution"
date:   2021-09-11 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[5249. [파이썬 S/W 문제해결 구현] 7일차 - 최소 신장 트리](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDYSqAAbw5UW6&subjectId=AWUYHO7a2JoDFAVT#)

풀이

```python
# INF_WEIGHT = 100

# def prim(V, graph, visited, min_path, pi):

#     for _ in range(V):
#         v = None
#         tempmin = INF_WEIGHT
#         for i in range(V):
#             if not visited[i] and tempmin > min_path[i]:
#                 tempmin = min_path[i]
#                 v = i
        
#         visited[v] = 1
#         for i in range(V):
#             if not visited[i] and graph[v][i] < min_path[i]:
#                 min_path[i] = graph[v][i]
#                 pi[i] = v


def find_root(disjoint_set, idx):
    while idx != disjoint_set[idx]['root']:
        idx = disjoint_set[idx]['root']
    return idx


def union(disjoint_set, idx1, idx2):
    root1 = find_root(disjoint_set, idx1)
    root2 = find_root(disjoint_set, idx2)
    if disjoint_set[root1]['rank'] < disjoint_set[root2]['rank']:
        disjoint_set[root1]['root'] = root2
    else:
        disjoint_set[root2]['root'] = root1
        if disjoint_set[root1]['rank'] == disjoint_set[root2]['rank']:
            disjoint_set[root1]['rank'] += 1


def kruskal(V, edges, disjoint_set):
    edges.sort(key = lambda x: x[2])
    count = 0
    idx = 0
    min_path = 0
    while count < V-1:
        i, j, weight = edges[idx]
        i_root = find_root(disjoint_set, i)
        j_root = find_root(disjoint_set, j)
        if  i_root != j_root:
            union(disjoint_set, i_root, j_root)
            min_path += weight
            count += 1
        idx += 1
    return min_path


T = int(input())

answer = []
for tc in range(1, T + 1):
    
    V, E = map(int, input().split())
    V += 1

    edges = [list(map(int, input().split())) for _ in range(E)]

    # prim algorithm

    # visited = [0] * V
    # graph = [[INF_WEIGHT for _ in range(V)] for _ in range(V)]
    # for a in range(E):
    #     i, j, weight = edges[a]
    #     graph[i][j] = weight
    #     graph[j][i] = weight
    # min_path = [INF_WEIGHT] * V
    # min_path[0] = 0
    # pi = [None] * V
    # prim(V, graph, visited, min_path, pi)
    
    # result = 0
    # for i in range(1, V):
    #     result += graph[i][pi[i]]
    # answer.append(result)

    # kruskal algorithm

    disjoint_set = [{'root': i, 'rank': 0} for i in range(V)]

    result = kruskal(V, edges, disjoint_set)

    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

