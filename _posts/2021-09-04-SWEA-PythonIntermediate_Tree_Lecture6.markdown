---
layout: post
title:  "SWEA - PythonIntermediate_Tree_Lecture6 solution"
date:   2021-09-04 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[5174. [파이썬 S/W 문제해결 기본] 8일차 - subtree](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDN86AAXw5UW6&subjectId=AWOVJ-_6qfsDFAWg)

풀이

```python
T = int(input())

answer = []
for tc in range(1, T + 1):

    E, N = map(int, input().split())

    tree = [[] for _ in range(E+2)]

    input_seq = list(map(int, input().split()))

    for i in range(len(input_seq)//2):
        parent, child = input_seq[i * 2], input_seq[(i * 2) + 1]
        tree[parent].append(child)
    
    queue = []
    queue.append(N)
    count = 1
    while queue:
        n = queue.pop()
        for i in tree[n]:
            queue.append(i)
            count += 1        

    result = count
    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

