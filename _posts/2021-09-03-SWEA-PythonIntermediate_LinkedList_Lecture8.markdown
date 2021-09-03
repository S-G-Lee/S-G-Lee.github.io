---
layout: post
title:  "SWEA - PythonIntermediate_LinkedList_Lecture8 solution"
date:   2021-09-03 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[5122. [파이썬 S/W 문제해결 기본] 7일차 - 수열 편집](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDN86AAXw5UW6&subjectId=AWOVJ1r6qfkDFAWg#)

풀이

```python
class Node:

    def __init__(self, item):
        self.item = item
        self.prev = None
        self.next = None


class LinkedList:

    def __init__(self):
        self.head = Node(None)
        self.tail = Node(None)

    def append(self, item):
        prev = self.tail.prev
        new = Node(item)
        if self.head.next == None:
            self.head.next = new
        new.prev = prev
        if prev:
            prev.next = new
        self.tail.prev = new

    def prepend(self, item):
        next = self.head.next
        new = Node(item)
        if self.tail.prev == None:
            self.tail.prev = new
        new.next = next
        if next:
            next.prev = new
        self.head.next = new

    def insert(self, idx, item):
        if idx >= 0:
            count = 0
            cur = self.head
            while count < idx:
                cur = cur.next
                count += 1
            next = cur.next
            new = Node(item)
            if next:
                next.prev = new
            else:
                self.tail.prev = new
            new.next = next
            if cur != self.head:
                new.prev = cur
            cur.next = new
        else:
            count = 0
            cur = self.tail
            while count >= idx:
                cur = cur.prev
                count -= 1
            next = cur.next
            new = Node(item)
            if next:
                next.prev = new
            else:
                self.tail.prev = new
            new.next = next
            if cur != self.head:
                new.prev = cur
            cur.next = new

    def popitem(self, idx):
        if idx >= 0:
            count = -1
            cur = self.head
            while count < idx:
                cur = cur.next
                count += 1
            next = cur.next
            prev = cur.prev
            if next:
                next.prev = prev
            else:
                self.tail.prev = prev
            
            if prev:
                prev.next = next
            else:
                self.head.next = next
            return cur.item
        else:
            count = -1
            cur = self.tail
            while count >= idx:
                cur = cur.prev
                count -= 1
            next = cur.next
            prev = cur.prev
            if next:
                next.prev = prev
            else:
                self.tail.prev = prev
            
            if prev:
                prev.next = next
            else:
                self.head.next = next
            return cur.item

    def getitem(self, idx):
        if idx >= 0:
            count = -1
            cur = self.head
            while count < idx:
                if cur == None:
                    break
                cur = cur.next
                count += 1
            if cur == None:
                return None
            return cur.item
        else:            
            count = -1
            cur = self.tail
            while count >= idx:
                if cur == None:
                    break
                cur = cur.prev
                count -= 1
            if cur == None:
                return None
            return cur.item
    
    def getfirst(self):
        return self.head.next
    
    def getlast(self):
        return self.tail.prev

    def get(self, idx):
        if idx >= 0:
            count = -1
            cur = self.head
            while count < idx:
                cur = cur.next
                count += 1
            if cur == None:
                return None
            return cur
        else:            
            count = -1
            cur = self.tail
            while count >= idx:
                cur = cur.prev
                count -= 1
            if cur == None:
                return None
            return cur

    def change(self, idx, item):
        cur = self.get(idx)
        cur.item = item



T = int(input())

answer = []
for tc in range(1, T + 1):

    N, M, L = map(int, input().split())
    ll = LinkedList()

    for item in list(map(int, input().split())):
        ll.append(item)
    
    for _ in range(M):
        input_seq = input().split()
        if input_seq[0] == 'D':
            idx = int(input_seq[1])
            ll.popitem(idx)
        elif input_seq[0] == 'I':
            idx = int(input_seq[1])
            num = int(input_seq[2])
            ll.insert(idx, num)
        else:
            idx = int(input_seq[1])
            num = int(input_seq[2])
            ll.change(idx, num)
    
    result = ll.getitem(L)
    if not result:
        result = -1
    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

