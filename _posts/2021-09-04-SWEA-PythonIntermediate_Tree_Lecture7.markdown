---
layout: post
title:  "SWEA - PythonIntermediate_Tree_Lecture7 solution"
date:   2021-09-04 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[\5176. [파이썬 S/W 문제해결 기본] 8일차 - 이진탐색](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDN86AAXw5UW6&subjectId=AWOVJ-_6qfsDFAWg)

풀이

```python
number = 1


def inorder(node, N, idx):
    global number
    if idx*2 <= N:
        inorder(node, N, idx*2)
    node[idx] = number
    number += 1
    if (idx*2)+1 <= N:
        inorder(node, N, (idx*2)+1)


T = int(input())

answer = []
for tc in range(1, T + 1):

    N = int(input())
    
    number = 1

    node = [0] * (N+1)

    inorder(node, N, 1)

    result = f'{node[1]} {node[N//2]}'
    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')

```

