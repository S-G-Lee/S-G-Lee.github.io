---
layout: post
title:  "SWEA - PythonIntermediate_Tree_Lecture8 solution"
date:   2021-09-04 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[5178. [파이썬 S/W 문제해결 기본] 8일차 - 노드의 합](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDN86AAXw5UW6&subjectId=AWOVJ-_6qfsDFAWg)

풀이

```python
class BinaryTree:

    def __init__(self, N):
        self.heap = [0] * (N+1)
        self.idx = 0
    
    def insert(self, n):
        self.idx += 1
        self.heap[self.idx] = n
    
    def complete(self):
        for i in range(self.idx, 1, -1):
            self.heap[i//2] += self.heap[i]
    
    def get(self, idx):
        return self.heap[idx]


T = int(input())

answer = []
for tc in range(1, T + 1):

    N, M, L = map(int, input().split())
    nodes = []
    for _ in range(M):
        nodes.append(list(map(int, input().split())))

    bt = BinaryTree(N)

    for i in range(1, N+1):
        for j in nodes:
            if i == j[0]:
                bt.insert(j[1])
                break
        else:
            bt.insert(0)

    bt.complete() 
    
    result = bt.get(L)

    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

