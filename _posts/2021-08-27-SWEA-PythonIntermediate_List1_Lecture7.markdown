---
layout: post
title:  "SWEA - PythonIntermediate_List1_Lecture7 solution"
date:   2021-08-27 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[4831[파이썬 S/W 문제해결 기본] 1일차 - 전기버스](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDN86AAXw5UW6&subjectId=AWOVFCzaqeUDFAWg#)

풀이

```python
casenum = int(input())

for case in range(1, casenum+1):
    
    K, N, M = list(map(int, input().split()))
    batterylist = list(map(int, input().split()))
    batterypos = [0 for i in range(N+1)]
    for i in batterylist:
        batterypos[i] += 1
    
    pos = 0 # current station number
    comebycount = 0 # count for number of station that the bus come by
    
    chksuccess = 1 # check parameter whether bus can go to end or not
    while(True):
        if pos + K >= N:
            break
        tmpchk = 0
        for i in range(K,0,-1):
            if batterypos[pos + i] >= 1:
                pos = pos + i
                comebycount += 1
                tmpchk = 1
                break
        if tmpchk == 0:
            chksuccess = 0
            comebycount = 0
            break
    
    print(f'#{case} {comebycount}')
        
        
```

