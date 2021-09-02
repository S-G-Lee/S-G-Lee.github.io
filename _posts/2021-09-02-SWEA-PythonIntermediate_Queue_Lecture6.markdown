---
layout: post
title:  "SWEA - PythonIntermediate_Queue_Lecture6 solution"
date:   2021-09-02 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[\5105. [파이썬 S/W 문제해결 기본] 6일차 - 미로의 거리](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDN86AAXw5UW6&subjectId=AWOVIoJqqfYDFAWg#)

풀이

```python
T = int(input())

class Node:

    def __init__(self, arg, dist):
        self.item = arg
        self.distance = dist
        self.next = None


class Queue:

    def __init__(self):
        self.length = 0
        self.front = None
        self.rear = None

    def enQueue(self, arg, dist):
        if self.front == None:
            self.front = Node(arg, dist)
        else:
            new = Node(arg, dist)            
            if self.front.next == None:
                self.front.next = new
            if self.rear != None:
                self.rear.next = new
            self.rear = new
        self.length += 1

    def deQueue(self):
        item = self.front.item
        self.front = self.front.next
        if self.front == None:
            self.rear = None
        self.length -= 1
        return item

    def isEmpty(self):
        if self.front == self.rear == None:
            return True
        return False

    def isFull(self):
        return False

    def Qpeek(self):
        return self.front.item


answer = []
for tc in range(1, T + 1):

    N = int(input())
    board = [list(map(int, input())) for _ in range(N)]
    q = Queue()

    boardcheck = [[0 for _ in range(N)] for _ in range(N)]

    starti, startj = 0, 0
    for i in range(N):
        for j in range(N):
            if board[i][j] == 2:
                starti = i
                startj = j
                break
    
    result = 0
    direction = [[1, 0], [-1, 0], [0, 1], [0, -1]]
    q.enQueue([starti, startj], 0)
    while not q.isEmpty(): 
        i, j, dist = q.front.item[0], q.front.item[1], q.front.distance
        if boardcheck[i][j] == 0:
            boardcheck[i][j] = 1
            for diri, dirj in direction:
                if 0 <= i+diri < N and 0 <= j+dirj < N and board[i+diri][j+dirj] != 1 and boardcheck[i+diri][j+dirj] == 0:
                    q.enQueue([i+diri, j+dirj], dist+1)

        if board[i][j] == 3:
            result = dist-1
            break

        q.deQueue()

    answer.append(result)


for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

