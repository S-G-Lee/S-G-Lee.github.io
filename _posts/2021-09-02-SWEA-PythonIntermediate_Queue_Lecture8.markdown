---
layout: post
title:  "SWEA - PythonIntermediate_Queue_Lecture8 solution"
date:   2021-09-02 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[5102. [파이썬 S/W 문제해결 기본] 6일차 - 노드의 거리](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDN86AAXw5UW6&subjectId=AWOVIoJqqfYDFAWg#)

풀이

```python
class Node:

    def __init__(self, node, dist):
        self.node = node
        self.dist = dist
        self.next = None


class Queue:

    def __init__(self):
        self.front = None
        self.rear = None
    
    def enQueue(self, node, dist):
        if self.front == None:
            self.front = Node(node, dist)
        else:
            new = Node(node, dist)
            if self.rear == None:
                self.front.next = new
            else:
                self.rear.next = new
            self.rear = new
        
    def deQueue(self):
        node, dist = self.front.node, self.front.dist
        self.front = self.front.next
        if self.front == None:
            self.rear = None
        return node, dist

    def isEmpty(self):
        if self.front == self.rear == None:
            return True
        return False

    def isFull(self):
        return False

    def Qpeek(self):
        return self.front.node, self.front.dist   


T = int(input())

answer = []
for tc in range(1, T + 1):

    V, E = map(int, input().split())

    graph = [[0 for _ in range(V)] for _ in range(V)]

    for _ in range(E):
        i, j = map(int, input().split())
        i -= 1
        j -= 1
        graph[i][j] = 1
        graph[j][i] = 1

    S, G = map(int, input().split())
    S -= 1
    G -= 1

    q = Queue()
    q.enQueue(S, 0)
    visited = [0] * V
    visited[S] = 1

    result = 0
    while not q.isEmpty():
        node, dist = q.Qpeek()
        if node == G:
            result = dist
            break

        for i in range(V):
            if graph[node][i] == 1:
                if not visited[i]:
                    visited[i] = 1
                    q.enQueue(i, dist+1)
        q.deQueue()

    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

