# 그래프의 종류와 구현

## 그래프(graph)

- 정점(vertex) = 데이터를 간선(edge) 혹은 힝크(link)로 연결한 형태의 자료구조
- = 데이터 간의 연결 관계를 표현하는 자료구조
    - ex) 지하철 노선도
- 트리도 그래프의 일종
    - 사이클을 형성X , 연결된 노드 간에 상하 관계O
- 사이클 형성 O, 이웃한 정점끼리 상하 관계 X

![image.png](attachment:cd549346-328e-45a8-95a8-f09a7c564b45:image.png)

## 그래프 유형

- 연결/비연결 그래프
- 방향/무방향 그래프
- 가중치 그래프
- 서브그래프

연결/비연결 그래프

### 연결 그래프(connected graph)

- 그래프 상에 있는 임의의 두 정점 사이의 경로가 존재하는 그래프를
- = 2개의 아무 정점이나 골라 간선(들)으로 서로를 이을 수 있는 그래프

### 비연결 그래프(disconnected graph)

- 어떤 정점 사이에는 경로가 존재하지 않을 수도 있는 그래프

![image.png](attachment:f94b0fea-55e0-4dde-8c70-a7c7cd068a33:image.png)

방향/무방향 그래프

### 방향 그래프(directed graph)

- 간선에 방향이 있는 그래프

### 무방향 그래프(undirected graph)

- 방향이 없는 그래프

![image.png](attachment:1415550f-69c7-4065-bacb-f1bf22159d5f:image.png)

가중치 그래프/서브그래프

### 가중치 그래프(weighted graph)

- 간선에 부여된 (값인 가중치 = 비용) 그래프

### 서브그래프(subgraph)

- 부분 그래프
		

---

## 인접 행렬 기반 그래프 표현

- 메모리에 저장하는 방법
    - 인접행렬
    - 인접 리스트

### 인접 행렬(adjacency matrix) 기반 그래프 표현

- N x N 크기의 행렬로 그래프를 표현하는 방법
    - N x N 행렬의 <행, 열> 값은 <출발 정점, 도착 정점>
- 1 : 두 정점이 연결되었을 때 표기
- 0 : 연결되지 않았을 때 표기

방향 그래프

![방향 그래프](attachment:420566c3-f455-427a-9844-0331dabd2529:image.png)

방향 그래프

| From \ To | 1번 | 2번 | 3번 | 4번 |
| --- | --- | --- | --- | --- |
| **1번** | 0 | 1 | 0 | 0 |
| **2번** | 0 | 0 | 0 | 0 |
| **3번** | 0 | 0 | 0 | 1 |
| **4번** | 1 | 0 | 0 | 0 |

무방향 그래프

![무방향 그래프](attachment:94d607ec-f12f-476e-ae45-dd1a277ad4ac:image.png)

무방향 그래프

| From \ To | 1번 | 2번 | 3번 | 4번 |
| --- | --- | --- | --- | --- |
| **1번** | 0 | 1 | 0 | 1 |
| **2번** | 1 | 0 | 0 | 0 |
| **3번** | 0 | 0 | 0 | 1 |
| **4번** | 1 | 0 | 1 | 0 |
- 행렬의 대각선 요소를 기준으로 대칭을 이룸

가중치 그래프

![가중치 그래프](attachment:36d60856-0cc1-4e7e-b14f-74fffaa50e58:image.png)

가중치 그래프

| From \ To | 1번 | 2번 | 3번 | 4번 |
| --- | --- | --- | --- | --- |
| **1번** | 0 | 2 | 0 | 0 |
| **2번** | 0 | 0 | 0 | 0 |
| **3번** | 0 | 0 | 0 | 3 |
| **4번** | 4 | 0 | 0 | 0 |
		

## 인접 리스트 기반 그래프 표현

### 인접 리스트(adjacency list) 기반 그래프 표현

- 그래프의 특정 정점과 연결된 정점들을 연결 리스트로 표현하는 방법
- 각각의 정점마다 연결 리스트를 가지는데, 특정 정점에서 나가는 간선에 연결된 정점들을 연결 리스트로 삼는다는 의미

![image.png](attachment:403ae76b-553c-4607-8df1-33c2bd6cf0ab:image.png)

![image.png](attachment:778194c4-7f3d-4e9c-83f3-bbc3e7f15b7b:image.png)

- 가중치 그래프를 인접 리스트로 표현

![image.png](attachment:5b060454-2845-4594-8c41-1e9c71a4ee56:image.png)

---

# 깊이 우선 탐색과 너비 우선 탐색

## 깊이 우선 탐색(DFS = Depth-First Search)

- 더 이상 방문 가능한 정점이 없을 때까지 최대한 깊이 탐색하기를 반복하는 탐색 방법

![image.png](attachment:69cc8b54-6b13-4082-8a8d-1a9514549d3c:image.png)

![image.png](attachment:f3dfce9e-c1e9-44c9-a384-8e5cab6306e6:image.png)

![image.png](attachment:066a0147-7a0b-4669-afb9-0c4a525c8889:image.png)

![image.png](attachment:a3e691d9-76e9-4ed0-b03d-800ded84e840:image.png)

![image.png](attachment:931cfef7-e878-4dbb-a43c-16a476ffb78c:image.png)

---

## 너비 우선 탐색(BFS = Breadth-First Search)

- 인접한 모든 정점들을 방문하고, 방문한 정점들과 연결된 모든 정점들을 방문하고, 또 방문한 정점들과 연결된 모든 정점들을 방문하기를 반복하는 탐색 방법

![image.png](attachment:eebd3366-fa78-4908-892c-e3c779fae8c6:image.png)

![image.png](attachment:05014430-37d2-4274-91a4-0f81de89b6a2:image.png)

![image.png](attachment:55292267-9174-49c4-8dc2-5979139118dc:36ad2217-eb1c-4e43-93a0-d2aa3bb60676.png)

![image.png](attachment:8ee9e882-e8f5-4cf2-9eb5-20bd8041efea:fab04bc1-e209-48a5-97cf-427f3bb62ce6.png)

![image.png](attachment:bbe1f657-b07b-4565-a4f3-16f707b74057:image.png)

---

# 최단 경로 알고리즘

## 최단 경로 알고리즘

- 한 정점에서 목적지 정점까지 이르는 가중치의 합이 최소가 되는 경로를 결정하는 알고리즘

## 다익스트라 알고리즘(Dijkstra’s algorithm)

- 간선의 가중치가 음이 아닌 수라는 가정 하에 사용 가능한 알고리즘
- = 특정 정점에서 다른 모든 정점까지의 최단 거리를 구해 주는 알고리즘

### 시간 복잡도

- 배열 기반 → O(V²)
- 우선순위 큐(힙) 사용 → O(E log V)

![image.png](attachment:a65b9b9f-b92e-42fe-a791-113c1a812c18:image.png)

① 최단 거리 테이블 상에서 시작 정점을 제외한 정점들은 모두 충분히 큰 수로 초기화합니다.

![image.png](attachment:1bca768f-a509-4622-91eb-dcc7ed9d42f4:image.png)

② (시작)정점을 방문합니다.

![image.png](attachment:b938a0d4-486f-4000-ac85-44c5218708f9:image.png)

③ 방문한 정점과 인접한 정점들을 탐색합니다.

- 정점 1과 인접한 정점은 정점 2이다.

④ 경로 상의 가중치 합과 최단 거리 테이블 상의 값을 비교합니다.

![image.png](attachment:7fca961e-ef72-41b9-8ee7-a978a01f41e8:image.png)

⑤ 최단 거리 테이블을 갱신할 수 있다면 갱신합니다.

![image.png](attachment:c7b19676-99f0-41ad-9ad5-ac2b2ed320f8:image.png)

⑥ 방문하지 않은 정점 중 최단 거리가 가장 작은 정점을 방문합니다.

![image.png](attachment:14f12265-3a22-454b-b4e8-0995ab62083d:image.png)

⑦ 더 이상 방문할 정점이 없을 때까지 ③~⑥의 과정을 반복하고 종료합니다.

- 아직 있음
- ③으로 돌아가기
    - 정점 2와 인접한 정점은 정점 3, 4, 5

---

④ 경로 상의 가중치 합과 최단 거리 테이블 상의 값을 비교합니다.

![image.png](attachment:8925f45a-ea55-4b75-9f5e-53f758c98f5e:image.png)

⑤ 최단 거리 테이블을 갱신할 수 있다면 갱신합니다.

![image.png](attachment:6b945310-a5a4-4990-8e42-f04c7aff69bf:image.png)

⑥ 방문하지 않은 정점 중 최단 거리가 가장 작은 정점을 방문합니다.

![image.png](attachment:1b234612-f65e-48c3-854b-23b55139d632:image.png)

---

③ 방문한 정점과 인접한 정점들을 탐색합니다.

- 정점 4과 인접한 정점은 정점 5이다.

④ 경로 상의 가중치 합과 최단 거리 테이블 상의 값을 비교합니다.

![image.png](attachment:5e3e6ed0-b03d-4705-813c-87e353f9cfd9:image.png)

⑤ 최단 거리 테이블을 갱신할 수 있다면 갱신합니다.

![image.png](attachment:316896ea-6048-472e-8753-6f5f7b206387:image.png)

⑥ 방문하지 않은 정점 중 최단 거리가 가장 작은 정점을 방문합니다.

![image.png](attachment:fefa84c6-8d6a-448b-b742-4027ab8664ea:image.png)

---

③ 방문한 정점과 인접한 정점들을 탐색합니다.

- 정점 5과 인접한 정점은 정점 3과 6이다.

④ 경로 상의 가중치 합과 최단 거리 테이블 상의 값을 비교합니다.

![image.png](attachment:fde44d81-fda1-420f-bd2c-537c5c6f84f2:image.png)

⑤ 최단 거리 테이블을 갱신할 수 있다면 갱신합니다.

![image.png](attachment:25f69c80-1c37-4904-b715-94f93fd7b354:image.png)

⑥ 방문하지 않은 정점 중 최단 거리가 가장 작은 정점을 방문합니다.

![image.png](attachment:4dbbd60a-b8f6-444b-912d-d98d88c5b83d:image.png)

---

③ 방문한 정점과 인접한 정점들을 탐색합니다.

- 정점 3 → X
- 정점 5와 인접한 정점은 정점 6이다.

⑥ 방문하지 않은 정점 중 최단 거리가 가장 작은 정점을 방문합니다.

![image.png](attachment:9e726fea-1f3f-4319-92cb-6bca8f64aa3f:image.png)

---

③ 방문한 정점과 인접한 정점들을 탐색합니다.

- 정점 6과 인접한 정점은 정점 3이다.

④ 경로 상의 가중치 합과 최단 거리 테이블 상의 값을 비교합니다.

![image.png](attachment:ce0cd50a-00e0-4484-a4fc-872328b040bc:image.png)

⑤ 최단 거리 테이블을 갱신할 수 있다면 갱신합니다.

- 더 이상 방문할 정점이 없으므로 탐색 종료

![image.png](attachment:9ef11777-034a-43c2-9c52-aa91366eba08:image.png)

## 또 다른 그래프 알고리즘

- 최소 신장 트리(MST)
    - 크루스칼(Kruskal)
    - 프림(Prim)
- 벨만-포드(Bellman-Ford)
    - 음수 가중치 허용
- 플로이드-워셜(Floyd-Warshall)
    - 모든 정점 간 최단 경로

<aside>
🗣

### DFS vs BFS

| 항목 | DFS | BFS |
| --- | --- | --- |
| 탐색 방식 | 깊게 우선 탐색 | 가까운 곳부터 탐색 |
| 사용 자료구조 | 스택(Stack), 재귀 | 큐(Queue) |
| 특징 | 구현 간단 | 최단 경로 탐색에 유리 |
| 사용 예시 | 백트래킹, 미로 탐색 | 최단 거리, 레벨 탐색 |
</aside>

<aside>
🗣

### 인접 행렬 vs 인접 리스트

| 항목 | 인접 행렬 | 인접 리스트 |
| --- | --- | --- |
| 저장 방식 | 2차원 배열 | 연결 리스트 |
| 공간 복잡도 | O(V²) | O(V + E) |
| 간선 확인 | 빠름 | 느릴 수 있음 |
| 희소 그래프 | 비효율적 | 효율적 |
</aside>

<aside>
🗣

### 트리 vs 그래프

| 트리 | 그래프 |
| --- | --- |
| 사이클 없음 | 사이클 가능 |
| 부모-자식 관계 존재 | 관계 제한 없음 |
| 루트 노드 존재 | 루트 개념 없음 가능 |
| 연결 구조 고정 | 자유로운 연결 가능 |
</aside>