---
layout: post
title:  "SWEA - PythonIntermediate_Tree_Lecture8 solution"
date:   2021-09-04 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[5177. [파이썬 S/W 문제해결 기본] 8일차 - 이진 힙](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDN86AAXw5UW6&subjectId=AWOVJ-_6qfsDFAWg)

풀이

```python
class MinimumHeap:

    def __init__(self, N):
        self.heap = [0] * (N+1)
        self.idx = 0

    def isReversed(self, pidx, cidx):
        # pidx : parent index, cidx = child index
        if (0 < pidx <= self.idx) and (0 < cidx <= self.idx):
            if self.heap[pidx] > self.heap[cidx]:
                return True
        return False
    
    def swap(self, pidx, cidx):
        # pidx : parent index, cidx = child index
        self.heap[pidx], self.heap[cidx] = self.heap[cidx], self.heap[pidx]
    
    def insert(self, n):
        self.idx += 1
        self.heap[self.idx] = n
        idx = self.idx
        check = self.isReversed(idx//2, idx)
        while check:
            self.swap(idx//2, idx)
            idx = idx//2
            check = self.isReversed(idx//2, idx)
    
    def delete(self):
        if self.idx > 0:
            self.heap[self.idx], self.heap[1] = self.heap[1], self.heap[self.idx]
            self.idx -= 1
            idx = 1
            check = True
            while check:
                if self.isReversed(idx, idx*2) and self.isReversed(idx, (idx*2)+1):
                    if self.heap[idx*2] < self.heap[(idx*2)+1]:
                        self.swap(idx, idx*2)
                    else:
                        self.swap(idx, (idx*2)+1)
                elif self.isReversed(idx, idx*2):
                    self.swap(idx, idx*2)
                elif self.isReversed(idx, (idx*2)+1):
                    self.swap(idx, (idx*2)+1)
                else:
                    check = False

    def anscestor(self):
        result = []
        idx = self.idx // 2
        while idx > 0:
            result.append(self.heap[idx])
            idx = idx // 2
        return result


T = int(input())

answer = []
for tc in range(1, T + 1):

    N = int(input())

    mh = MinimumHeap(N)
    for i in list(map(int, input().split())):
        mh.insert(i)

    result = sum(mh.anscestor())
    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

