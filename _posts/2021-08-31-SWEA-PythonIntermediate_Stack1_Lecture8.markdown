---
layout: post
title:  "SWEA - PythonIntermediate_Stack1_Lecture8 solution"
date:   2021-08-31 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[4871. [파이썬 S/W 문제해결 기본] 4일차 - 그래프 경로](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDN86AAXw5UW6&subjectId=AWOVHzyqqe8DFAWg#)

풀이

```python
def search_a_vertex(vertexnum, visited, node_list):

    w = -1
    for i in range(vertexnum):
        if node_list[i]:
            if not visited[i]:
                w = i
                break
    return w

def stack_push(stack, top): # push at top+1 position and return top+1
    top += 1
    stack[top] = v
    return top
 
def stack_pop(stack, top): # pop the last element and return top-1
    stack[top] = -1
    top -= 1
    return top

T = int(input())

for tc in range(1, T + 1): 

    V, E = map(int, input().split())
    graph = [[0 for _ in range(V)] for _ in range(V)]

    for _ in range(E):
        src, dist = map(int, input().split())
        graph[src-1][dist-1] = 1 # index는 0에서 시작, 주어진 노드는 1에서 시작. 그래서 -1해야됨

    visited = [False for _ in range(V)]
    stack = [-1] * 10000 # -1 means empty

    S, G = map(int, input().split())
    
    v = S - 1
    w = -1
    top = -1

    result = 0

    while True:
        
        if not visited[v]:
            top = stack_push(stack, top)
            visited[v] = True
        
        w = search_a_vertex(V, visited, graph[v])
                
        while w >= 0:
            v = w
            top = stack_push(stack, top)
            visited[v] = True
            
            if v is G - 1:
                break

            w = search_a_vertex(V, visited, graph[v])
        

        if v is G - 1:
            result = 1
            break            

        top = stack_pop(stack, top)
        v = stack[top]

        if top >= 0:
            continue
        break
    
    print(f'#{tc} {result}')
```

