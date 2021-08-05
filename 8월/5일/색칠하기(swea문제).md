### SWEA 사이트 알고리즘 문제 풀기

SWEA(https://swexpertacademy.com/main/learn/course/lectureProblemViewer.do)

전기버스 문제(4831)



문제

- 그림과 같이 인덱스가 있는 10x10 격자에 빨간색과 파란색을 칠하려고 한다.

  N개의 영역에 대해 왼쪽 위와 오른쪽 아래 모서리 인덱스, 칠할 색상이 주어질 때, 칠이 끝난 후 색이 겹쳐 보라색이 된 칸 수를 구하는 프로그램을 만드시오.

  주어진 정보에서 같은 색인 영역은 겹치지 않는다.

  ![image-20210805234837255](색칠하기(swea문제).assets/image-20210805234837255.png)

- 예를 들어 2개의 색칠 영역을 갖는 위 그림에 대한 색칠 정보이다.

  2

  2 2 4 4 1 ( [2,2] 부터 [4,4] 까지 color 1 (빨강) 으로 칠한다 )

  3 3 6 6 2 ( [3,3] 부터 [6,6] 까지 color 2 (파랑) 으로 칠한다 )


입력

- 첫 줄에 테스트 케이스 개수 T가 주어진다.  ( 1 ≤ T ≤ 50 )
  
  다음 줄부터 테스트케이스의 첫 줄에 칠할 영역의 개수 N이 주어진다. ( 2 ≤ N ≤ 30 )
    
    다음 줄에 왼쪽 위 모서리 인덱스 r1, c1, 오른쪽 아래 모서리 r2, c2와 색상 정보 color가 주어진다. ( 0 ≤ r1, c1, r2, c2 ≤ 9 )
    
    color = 1 (빨강), color = 2 (파랑)

출력

- 각 줄마다 "#T" (T는 테스트 케이스 번호)를 출력한 뒤, 답을 출력한다.



예제 입력1

```
3
2
2 2 4 4 1
3 3 6 6 2
3
1 2 3 3 1
3 6 6 8 1
2 3 5 6 2
3
1 4 8 5 1
1 8 3 9 1
3 2 5 8 2
```

예제 출력1

```
#1 4
#2 5
#3 7
```



```python
T = int(input())
for tc in range(1, T+1):
    N = int(input())
    arr = [[0]*10 for _ in range(10)]

    for _ in range(N):
        r1, c1, r2, c2, color = map(int, input().split())
        # 각각의 위치에 해당하는 색깔을 for문을 통해 행렬에 더해준다
        for i in range(r1, r2+1):
            for j in range(c1, c2+1):
                arr[i][j] += color
    
    cnt = 0
    for i in range(10):
        for j in range(10):
            # 1, 2 두가지의 색깔이 합쳐지면 3이 되기 때문에
            if arr[i][j] == 3:
                cnt += 1

    print(f'#{tc} {cnt}')
```

