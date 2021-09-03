---
layout: post
title:  "SWEA - PythonIntermediate_LinkedList_Lecture7 solution"
date:   2021-09-03 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[5120. [파이썬 S/W 문제해결 기본] 7일차 - 암호](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDN86AAXw5UW6&subjectId=AWOVJ1r6qfkDFAWg#)

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
            new.prev = cur
            cur.next = new

    def insert_ll(self, idx, first, last):
        if idx >= 0:
            count = 0
            cur = self.head
            while count < idx:
                cur = cur.next
                count += 1
            next = cur.next
            if next:
                next.prev = last
            else:
                self.tail.prev = last
            last.next = next
            first.prev = cur
            cur.next = first
        else:
            count = 0
            cur = self.tail
            while count >= idx:
                cur = cur.prev
                count -= 1
            next = cur.next
            if next:
                next.prev = last
            else:
                self.tail.prev = last
            last.next = next
            first.prev = cur
            cur.next = first

    def getitem(self, idx):
        if idx >= 0:
            count = -1
            cur = self.head
            while count < idx:
                cur = cur.next
                count += 1
            if cur == None:
                return None
            return cur.item
        else:            
            count = -1
            cur = self.tail
            while count >= idx:
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

    # def get_full(self):
    #     result = []
    #     cur = self.head.next
    #     while cur != None:
    #         result.append(cur.item)
    #         cur = cur.next
    #     return result

    def insert_special(self, N, M, K):
        cur = self.head
        for _ in range(K):
            for _ in range(M):
                if cur.next == None:
                    cur = self.head.next
                else:
                    cur = cur.next

            next = cur.next            
            n1 = cur.item
            if next:
                n2 = next.item
            else:
                n2 = self.head.next.item
            new = Node(n1+n2)
            if next:
                next.prev = new
            else:
                self.tail.prev = new
            new.next = next
            new.prev = cur
            cur.next = new

            # a = self.get_full()


T = int(input())

answer = []
for tc in range(1, T + 1):

    N, M, K = map(int, input().split())
    ll = LinkedList()

    for item in list(map(int, input().split())):
        ll.append(item)
    
    ll.insert_special(N, M, K)

    result = []
    for i in range(-1, -11, -1):
        if ll.getitem(i):
            result.append(ll.getitem(i))
    result = ' '.join(map(str, result))

    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

