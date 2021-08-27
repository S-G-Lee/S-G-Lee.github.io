---
layout: post
title:  "SWEA - PythonIntermediate_List1_Lecture8 solution"
date:   2021-08-27 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[4834. [파이썬 S/W 문제해결 기본] 1일차 - 숫자 카드](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDN86AAXw5UW6&subjectId=AWOVFCzaqeUDFAWg#)

풀이

```python
casenum = int(input())

for case in range(1, casenum+1):
    
    N = int(input())
    cardlist = list(map(int, list(input())))
    cardcount = [0 for i in range(10)] # count each amount of number in cardlist, index = counting number
    
    for i in cardlist:
        cardcount[i] += 1
    
    maxcount = max(cardcount)
    maxnum = (9 - cardcount[::-1].index(maxcount))
    
    print(f'#{case} {maxnum} {maxcount}')
   
```

