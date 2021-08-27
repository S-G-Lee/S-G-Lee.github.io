---
layout: post
title:  "SWEA - PythonIntermediate_List1_Lecture9 solution"
date:   2021-08-27 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[4835. [파이썬 S/W 문제해결 기본] 1일차 - 구간합](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDN86AAXw5UW6&subjectId=AWOVFCzaqeUDFAWg#)

풀이

```python
casenum = int(input())

for case in range(1, casenum+1):
    
    N, M = list(map(int, input().split()))
    numberlist = list(map(int, input().split()))
    
    sumlist = [0] * (N-M+1) #list that save sum of each subarray
    for i in range(N-M+1):
        sum = 0
        for j in numberlist[i:i+M]:
            sum += j
        sumlist[i] = sum
    
    print(f'#{case} {max(sumlist)-min(sumlist)}')
```

