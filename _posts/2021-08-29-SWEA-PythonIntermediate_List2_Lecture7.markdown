---
layout: post
title:  "SWEA - PythonIntermediate_List2_Lecture7 solution"
date:   2021-08-29 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[4839. [파이썬 S/W 문제해결 기본] 2일차 - 이진탐색](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDN86AAXw5UW6&subjectId=AWOVF-WqqecDFAWg#)

풀이

```python
def searchcount(totalpage, page):
    
    count = 1
    
    l = 1
    r = totalpage
    c = int((l + r)/2)
    while c != page:
        if c < page:
            if r - l == 1:
                c = page
            else:
                l = c
                c = int((l + r)/2)
            count += 1
        else:
            if r - l == 1:
                c = page
            else:
                r = c
                c = int((l + r)/2)
            count += 1
    
    return count


casenum = int(input())

for case in range(1, casenum+1):
    
    P, Pa, Pb = list(map(int, input().split()))
    Acount = searchcount(P, Pa)
    Bcount = searchcount(P, Pb)
    
    result = 0
    if Acount < Bcount:
        result = 'A'
    elif Bcount < Acount:
        result = 'B'
    print(f'#{case} {result}')
```

