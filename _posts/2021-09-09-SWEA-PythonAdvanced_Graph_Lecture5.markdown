---
layout: post
title:  "SWEA - PythonAdvanced_Graph_Lecture5 solution"
date:   2021-09-09 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[5248. [파이썬 S/W 문제해결 구현] 6일차 - 그룹 나누기](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDYSqAAbw5UW6&subjectId=AWUYG3y62EcDFAVT)

풀이

```python
def find_root(tree, i):
    root = i
    while tree[root]['root'] != root:
        root = tree[root]['root']
    return root

        
def union(tree, dict1:dict, dict2:dict):
    dict1_root = find_root(tree, dict1['item'])
    dict2_root = find_root(tree, dict2['item'])

    if dict1_root != dict2_root:
        if tree[dict1_root]['rank'] > tree[dict2_root]['rank']:
            tree[dict2_root]['root'] = dict1_root
        elif tree[dict1_root]['rank'] < tree[dict2_root]['rank']:
            tree[dict1_root]['root'] = dict2_root
        else:
            tree[dict2_root]['root'] = dict1_root
            tree[dict1_root]['rank'] += 1


T = int(input())

answer = []
for tc in range(1, T + 1):
    
    N, M = map(int, input().split())
    
    tree = [{'item': i, 'root': i, 'rank': 0} for i in range(N)]

    input_seq = list(map(int, input().split()))
    for i in range(0, len(input_seq) - 1 , 2):
        union(tree, tree[input_seq[i]-1], tree[input_seq[i+1]-1])
    
    tree_root = set()
    for i in range(N):
        rootidx = find_root(tree, i)
        tree_root.add(rootidx)
    
    result = len(tree_root)
    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

