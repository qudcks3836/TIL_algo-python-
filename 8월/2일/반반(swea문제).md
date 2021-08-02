### SWEA 사이트 알고리즘 문제 풀기

SWEA(https://swexpertacademy.com/main/code/problem/problemDetail.do?problemLevel=3&contestProbId=AXjS1GXqZ8gDFATi&categoryId=AXjS1GXqZ8gDFATi&categoryType=CODE&problemTitle=&orderBy=FIRST_REG_DATETIME&selectCodeLang=PYTHON&select-1=3&pageSize=10&pageIndex=1)

반반 문제



문제

-  길이 4의 알파벳 대문자로 이루어진 문자열 S가 주어졌을 때, S에 정확히 두 개의 서로 다른 문자가 등장하고, 각 문자가 정확히 두 번 등장하는 지 판별하라.


입력

- 첫 번째 줄에 테스트 케이스의 수 TC가 주어진다. 이후 TC개의 테스트 케이스가 새 줄로 구분되어 주어진다. 각 테스트 케이스는 다음과 같이 구성되었다.
    ∙ 첫 번째 줄에 문자열 S가 주어진다.

출력

- 각 테스트 케이스마다
      ∙ 조건이 만족되면 “Yes”, 아니면 “No” 를 출력하라.



예제 입력1

```

5
ABAB
CCDD
EFFE
EEEE
NONE
```

예제 출력1

```

#1 Yes
#2 Yes
#3 Yes
#4 No
#5 No
```



```python
def test(work):
    # 딕셔너리를 만든 후 word를 하나하나씩 순서대로 확인하며 해당 알파벳의 갯수를 확인한다
    dic = {}
    for alpha in word:
        if alpha not in dic:
            dic[alpha] = 1
        else:
            dic[alpha] += 1

    # 딕셔너리 key의 숫자가 2가 아닐 경우 제외
    if len(dic) != 2:
        return 'No'
    #  딕셔너리 value가 1이나 3이 있을 경우 제외
    elif (1 or 3) in dic.values():
        return 'No'
    else:
        return 'Yes'

T = int(input())
for tc in range(1, T+1):
    word = input()

    print(f'#{tc} {test(word)}')
```

