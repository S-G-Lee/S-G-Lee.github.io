---
layout: post
title:  "SWEA - PythonAdvanced_String_Lecture8 solution"
date:   2021-09-16 18:30:00 +0900
categories: algorithm
tags: [algorithm, SWEA, solution]
---
[5253. [파이썬 S/W 문제해결 최적화] 1일차 - 접두어 검색](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDYSqAAbw5UW6&subjectId=AWUYM1Ca240DFAVT)

풀이

```python
T = int(input())

answer = []
for tc in range(1, T + 1):

    N, M = map(int, input().split())
    str_list1 = [input() for _ in range(N)]
    str_list2 = [input() for _ in range(M)]

    # suf_list1 = []
    # for string in str_list1:
    #     suf_list1.append(create_suffix_list(string))
    
    # lcp1 = create_LCP_list(suf_list1)
    result = 0
    for prefix in str_list2:
        for string in str_list1:
            if len(prefix) <= len(string):
                for i in range(len(prefix)):
                    if prefix[i] != string[i]:
                        break
                else:
                    result += 1
                    break

    answer.append(result)

for tc in range(1, T+1):
    print(f'#{tc} {answer[tc-1]}')
```

