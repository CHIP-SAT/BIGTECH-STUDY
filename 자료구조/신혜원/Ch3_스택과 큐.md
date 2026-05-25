# 스택(stack)

- 한 쪽에서만 데이터의 삽입 및 삭제가 가능한 자료구조

## 푸시(push)

- 데이터를 저장하는 연산

## 팝(pop)

- 데이터를 빼내는 연산
- 후입선출(LIFO = Last In First Out)

![image.png](attachment:3c5a9ecc-f52c-48cf-b620-631a7775ce4d:image.png)

- 최근에 임시 저장한 데이터를 가장 먼저 활용해야 할 때
    - 매개변수를 저장하기 위해 스택을 사용하는 경우
- 뒤로가기 기능을 만들고 싶을 때

```python
int bar(int y) {
	return y + 2;
}

int foo(int x) {
	bar(2);
	return x + 1;
}

foo(1);
```

![image.png](attachment:d80b2cfc-d139-4e01-b8a6-549c2c89da76:image.png)

1️⃣ 우선 매개변수 x가 1로 초기화됨

2️⃣ bar 함수가 호출되어 매개변수 y가 2로 초기화됨

3️⃣ bar 함수가 2+2를 반환한 뒤 매개변수 y가 메모리에서 삭제됨

4️⃣ foo 함수 1+1을 반환한 뒤 매개변수 x가 메모리에서 삭제됨

⇒ 최근에 호출된 함수의 매개변수가 가장 먼저 활용되고, 가장 먼저 메모리에서 삭제됨

ex1) 웹 브라우저의 뒤로가기 버튼

![image.png](attachment:32cc08c6-086f-46c4-b6ef-420cb295d63d:image.png)

ex2) 아래와 같이 생긴 미로에서 이동하는 경우

![image.png](attachment:96bd66f1-c0d0-4e5c-8fe9-61af67d5da47:image.png)

![image.png](attachment:b711b931-6892-4651-92e1-3f99ddf0d033:image.png)

+ex)

- 괄호 검사
- 재귀 호출
- 실행 취소(Undo)
- DFS(깊이 우선 탐색)

---

# 큐(queue)

- 한 쪽으로 데이터를 삽입하고, 다른 한 쪽으로 데이터를 삭제할 수 있는 자료구조
- 데이터가 저장, 관리되면 먼저 삽입된(선입)First In 데이터가 먼저 나오게(선출)First Out
    - ⇒ 선입선출(FIFO = First In First Out)

ex)

- 프린터 작업 대기열
- CPU 스케줄링
- BFS(너비 우선 탐색)
- 네트워크 패킷 처리

## 인큐(enqueue)

- 큐의 한 쪽 끝에 데이터를 삽입하는 연산
- 시간 복잡도 : O(1)

## 디큐(dequeue)

- 다른 한 쪽 끝으로 데이터를 빼내는 (삭제하는) 연산
- 시간 복잡도 : O(1)

## 원형 큐(circular queue)

- 데이터를 삽입하는 쪽과 삭제하는 쪽, 양쪽을 하나로 연결해 원형으로 사용하는 자료구조

![image.png](attachment:ca4e9506-5a41-4309-912b-2f998ece1335:image.png)

### 원형 큐 사용하는 이유

- 일반 큐는 앞쪽 공간이 비어도 재사용이 어려울 수 있지만, 원형 큐는 배열 공간을 효율적으로 재사용 O

---

## 덱(deque)

- 양방향 큐(double-ended queue)의 약자
- 양쪽으로 데이터를 삽입/삭제할 수 있는 큐
- 스택과 큐의 특징을 모두 가진 자료구조

## 우선순위 큐(priority queue)

- 저장된 요소들이 선입선출로 처리되는 것이 아니라 정해진 우선순위가 높은 순으로 처리되는 큐
- 요소가 저장되어 있는 순서와 무관하게 우선순위가 높은 순서대로 빠져나가는 큐라고 볼 수 있음

![image.png](attachment:05a9f2c3-1ca3-4ec0-bef6-1fd5a39f14bb:image.png)

- 우선순위 큐는 일반적으로 힙(Heap) 자료구조를 이용해 구현

| 연산 | 시간 복잡도 |
| --- | --- |
| 삽입 | O(log n) |
| 삭제 | O(log n) |

---

<aside>
🗣

### 스택 vs 큐

| 항목 | 스택(Stack) | 큐(Queue) |
| --- | --- | --- |
| 구조 | 후입선출(LIFO) | 선입선출(FIFO) |
| 삽입 | Push | Enqueue |
| 삭제 | Pop | Dequeue |
| 데이터 처리 방식 | 최근 데이터 우선 | 먼저 들어온 데이터 우선 |
| 사용 예시 | 함수 호출, 뒤로가기 | 작업 대기열, BFS |
</aside>