---
layout: post
title:  "SWEA - PythonIntermediate_Queue_Lecture6 solution"
date:   2021-09-02 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[5099. [파이썬 S/W 문제해결 기본] 6일차 - 피자 굽기](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDN86AAXw5UW6&subjectId=AWOVIoJqqfYDFAWg#)

풀이

```python
T = int(input())

class Node:

    def __init__(self, arg):
        self.item = arg
        self.next = None

class RoundQueue:

    def __init__(self):
        self.front = None
        self.rear = None
    
    def enQueue(self, arg):
        if self.front == None:
            self.front = Node(arg)
            self.front.next = self.front
        else:
            new = Node(arg)
            if self.rear != None:
                self.rear.next = new
            else:                
                self.front.next = new
            self.rear = new
            self.rear.next = self.front
    
    def deQueue(self):
        item = self.front.item
        if self.front == self.front.next:
            self.front = None
            self.rear = None
        else:
            self.front = self.front.next
            self.rear.next = self.front
        return item
    
    def isEmpty(self):
        if self.front == self.rear == None:
            return True
        else:
            return False
    
    def isFull(self):
        return False

    def rotate(self):
        if self.front != None:
            self.front, self.rear = self.front.next, self.rear.next

    def swap(self, arg):
        item = self.front.item
        self.front.item = arg
        return item

    def get_list(self):
        if self.front == None:
            queue_list = []
        else:
            queue_list = []
            cur = self.front
            while cur.next != self.front:
                queue_list.append([cur.item])
                cur = cur.next
            queue_list.append([cur.item])
        return queue_list




answer = []
for tc in range(1, T + 1):

    N, M = map(int, input().split())
    cheese = list(map(int, input().split()))
    q = RoundQueue()

    for i in range(N):
        q.enQueue([i, cheese[i]]) # item[0] : 인덱스, item[1] : 치즈양
    
    idx = N
    result = []
    while not q.isEmpty():
        if q.front.item[1] > 1:
            q.front.item[1] = q.front.item[1] // 2
            q.rotate()
        else:
            if idx < M:
                result = q.swap([idx, cheese[idx]])
                idx += 1
                q.rotate()
            else:
                result = q.deQueue()
        a = q.get_list()
        b = q.get_list()

    answer.append(result[0]+1)


for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

