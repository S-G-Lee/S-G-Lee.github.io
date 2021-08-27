---
layout: post
title:  "SWEA - PythonIntermediate_List1_Lecture6 solution"
date:   2021-08-27 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[4828. [파이썬 S/W 문제해결 기본] 1일차 - min max](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDN86AAXw5UW6&subjectId=AWOVFCzaqeUDFAWg#)

풀이

```python
casenum = int(input())

for case in range(1, casenum+1):
    
    amount = int(input())
    inputstr = input().split()
    numlist = list(map(int, inputstr))
    
    minnum = min(numlist)
    maxnum = max(numlist)
    
    print(f'#{case} {maxnum - minnum}')
```

