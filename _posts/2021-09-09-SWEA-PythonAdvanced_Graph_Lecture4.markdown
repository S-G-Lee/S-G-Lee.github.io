---
layout: post
title:  "SWEA - PythonAdvanced_Graph_Lecture4 solution"
date:   2021-09-09 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[5247. [파이썬 S/W 문제해결 구현] 6일차 - 연산](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDYSqAAbw5UW6&subjectId=AWUYG3y62EcDFAVT)

풀이

```python
class Node:

    def __init__(self, item, rank):
        self.item = item
        self.rank = rank
        self.next = None


class Queue:

    def __init__(self):
        self.front = None
        self.rear = None

    def enQueue(self, item, rank):
        new = Node(item, rank)
        if self.front == None:
            self.front = new
            self.rear = new
        else:
            self.rear.next = new
            self.rear = new

    def deQueue(self):
        cur = self.front
        self.front = self.front.next
        if self.front == None:
            self.rear = None
        return cur.item, cur.rank
    
    def isEmpty(self):
        if self.front == None:
            return True
        return False
    
    def isFull(self):
        return False
    
    def Qpeek(self):
        return self.front.item, self.front.rank
        

T = int(input())

answer = []
for tc in range(1, T + 1):
    
    N, M = map(int, input().split())

    q = Queue()
    visited = set()

    q.enQueue(N, 0)

    rank = 0
    while True:

        v, rank = q.deQueue()
        if v == M:
            break
        if v not in visited:
            visited.add(v)
            
            if 0 < v + 1 <= 1000000:
                q.enQueue(v + 1, rank+1)
            if 0 < v - 1 <= 1000000:
                q.enQueue(v - 1, rank+1)
            if 0 < v * 2 <= 1000000:
                q.enQueue(v * 2, rank+1)
            if 0 < v - 10 <= 1000000:
                q.enQueue(v - 10, rank+1)

    
    result = rank
    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

