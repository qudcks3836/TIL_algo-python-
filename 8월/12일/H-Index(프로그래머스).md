### H-Index(프로그래머스)

프로그래머스(https://programmers.co.kr/learn/courses/30/lessons/42747?language=python3)



문제설명

- H-Index는 과학자의 생산성과 영향력을 나타내는 지표입니다. 어느 과학자의 H-Index를 나타내는 값인 h를 구하려고 합니다. 위키백과[1](https://programmers.co.kr/learn/courses/30/lessons/42747?language=python3#fn1)에 따르면, H-Index는 다음과 같이 구합니다.

  어떤 과학자가 발표한 논문 `n`편 중, `h`번 이상 인용된 논문이 `h`편 이상이고 나머지 논문이 h번 이하 인용되었다면 `h`의 최댓값이 이 과학자의 H-Index입니다.

  어떤 과학자가 발표한 논문의 인용 횟수를 담은 배열 citations가 매개변수로 주어질 때, 이 과학자의 H-Index를 return 하도록 solution 함수를 작성해주세요.



제한사항

- 과학자가 발표한 논문의 수는 1편 이상 1,000편 이하입니다.
- 논문별 인용 횟수는 0회 이상 10,000회 이하입니다.




입출력 예제

- | citations       | return |
  | --------------- | ------ |
  | [3, 0, 6, 1, 5] | 3      |





```python
def solution(citations):
    # citations에서 큰 숫자가 앞에 위치하도록 내림차순으로 정렬한다
    citations.sort(reverse=True)
    
    # h를 citations의 각 요소들 중 가장 큰 수로 지정한 뒤 1씩 빼면서 비교해본다
    for h in range(citations[0],-1,-1):
        cnt = 0
        # h와 citations의 첫번째 요소가 h이상인지 확인한 뒤 이상일 경우 cnt 1을 더해준다
        for j in range(len(citations)):
            if h <= citations[j]:
                cnt += 1
        # 만약 cnt가 h이상일 경우가 처음 나올 경우가 가장 큰 h가 된다 
        if cnt >= i:
            return i
```



각 조건들을 보고 풀이 방법을 잘 생각해야한다

ex) citations를 내림차순으로 한 뒤 h를 1씩 줄여가며 해당 경우마다 citations 각 요소와 비교해보는 것