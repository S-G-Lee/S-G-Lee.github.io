---
layout: post
title:  "SWEA - PythonIntermediate_String_Lecture5 solution"
date:   2021-08-30 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[4865. [파이썬 S/W 문제해결 기본] 3일차 - 글자수](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDN86AAXw5UW6&subjectId=AWOVGOEKqeoDFAWg#)

풀이

```python
T = int(input())

for tc in range(1, T + 1):   

    str1 = input()
    str2 = input()

    str1_dict = { char : 0 for char in str1}

    for char in str2:
        if char in str1_dict:
            str1_dict[char] = str1_dict[char] + 1
    
    maxcount = 0
    for count in str1_dict.values():
        if maxcount < count:
            maxcount = count
    
    print(f'#{tc} {maxcount}')
```

