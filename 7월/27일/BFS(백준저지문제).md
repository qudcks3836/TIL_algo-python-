### BFS(Breadth First Search)

출처(이것이 취업을 위한 코딩 테스트다 with 파이썬)

BFS 알고리즘은 `너비 우선 탐색` 이라는 의미를 가진다. 즉 가까운 노드부터 탐색하는 알고리즘이다.

BFS 구현에는 FIFO(선입선출) 방식인 큐 자료구조를 이용하는 것이 대부분이다.

인접한 노드부터 반복적으로 큐에 넣고 알고리즘을 작성해 자연스레 먼저 들어온 것이 나가도록 하면 된다.

요약

1. 탐색 시작 노드를 큐에 삽입하고 방문 처리
2. 큐에서 노드를 꺼내 해당 노트의 인접 노드 중에서 방문하지 않은 노드를 모두 큐에 삽입하고 방문 처리
3. 2번 과정을 끝날때까지 반복





백준저지(https://www.acmicpc.net/problem/7562)

문제

- 체스판 위에 한 나이트가 놓여져 있다. 나이트가 한 번에 이동할 수 있는 칸은 아래 그림에 나와있다. 나이트가 이동하려고 하는 칸이 주어진다. 나이트는 몇 번 움직이면 이 칸으로 이동할 수 있을까?

![image-20210727222550022](C:\Users\qudck\AppData\Roaming\Typora\typora-user-images\image-20210727222550022.png)



입력

- 입력의 첫째 줄에는 테스트 케이스의 개수가 주어진다.

  각 테스트 케이스는 세 줄로 이루어져 있다. 첫째 줄에는 체스판의 한 변의 길이 l(4 ≤ l ≤ 300)이 주어진다. 체스판의 크기는 l × l이다. 체스판의 각 칸은 두 수의 쌍 {0, ..., l-1} × {0, ..., l-1}로 나타낼 수 있다. 둘째 줄과 셋째 줄에는 나이트가 현재 있는 칸, 나이트가 이동하려고 하는 칸이 주어진다.

출력

- 각 테스트 케이스마다 나이트가 최소 몇 번만에 이동할 수 있는지 출력한다.



예제 입력1

```
3
8
0 0
7 0
100
0 0
30 50
10
1 1
1 1
```

예제 출력1

```
5
28
0
```



```python
from collections import deque

def bfs(x, y, x_end, y_end):
    queue = deque()
    queue.append([x, y])
    visited[x][y] = 0

    while queue:
        # queue에 가장 먼저 들어온 x,y 값을 꺼내기
        x, y = queue.popleft()
        # 현재 위치와 도착점이 같을 경우 return 해주기
        if x == x_end and y == y_end:
            return visited[x_end][y_end]
        # 이동할 수 있는 곳을 전부 확인해보기
        for step in steps:
            nx = x + step[0]
            ny = y + step[1]
            # 방문하지 않았고, 갈 수 있는 곳이면 이동하기
            if -1 < nx < l and -1 < ny < l and visited[nx][ny] == -1:
                visited[nx][ny] = visited[x][y] + 1
                # queue에 넣어주기
                queue.append([nx, ny])


T = int(input())
for tc in range(1, T+1):
    l = int(input())
    # 시작점
    x, y = list(map(int, input().split()))
    # 도착점
    x_end, y_end = list(map(int, input().split()))
    # 방문 표시하면서 cnt 해주기
    visited = [[-1]*l for _ in range(l)]
    # 이동할 수 있는 방법
    steps = [(-2, -1), (-1, -2), (1, -2), (2, -1), (2, 1), (1, 2), (-1, 2), (-2, 1)]

    result = bfs(x, y, x_end, y_end)
    print(result)
```

