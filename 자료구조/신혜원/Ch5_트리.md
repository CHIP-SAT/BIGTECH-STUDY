# 트리(tree)

- 주로 계층적인 구조를 표현하기 위한 자료구조

## 노드(node) | 간선(edge) | 링크(link)

![image.png](attachment:813fb04c-4be5-462a-adcc-f164fa8ea5fb:image.png)

## 부모 노드(parent node) | 자식 노드(child node)

![image.png](attachment:55dc0388-bfbe-4022-a28e-26d9d62c4323:image.png)

## 루트 노드(root node) | 리프 노드(leaf node)

![image.png](attachment:63733f63-f389-4923-84db-24a335d12612:image.png)

- 형제 노드(sibling node)
- 조상 노드(ancestor node)
- 자손 노드(descendant node)

## 차수(degree)

- 각 노드가 가지는 자식 노드의 수

## 레벨(level)

- 루트 노드에서 시작해 특정 노드에 이르기까지 거치게 되는 간선의 수를 의미

## 깊이(depth)

- 특정 노드가 얼마나 깊은 곳에 있는지를 뜻함

## 높이(height)

- 노드 b는 레벨 1, 노드 f는 레벨2, 노드 i는 레벨 3인 셈
- 여기서 가장 높은 레벨이 트리의 높이

![image.png](attachment:cb3f72f3-58d9-418b-ab77-b73130669246:image.png)

## 서브트리(subtree)

![image.png](attachment:37409b12-a492-4c19-911a-d9c07be18013:image.png)

- 서브트리 1️⃣의 루트 노드는 노드 b이고,
- 서브트리 2️⃣의 루트 노드는 노드 d인 셈이다.

![용어표](attachment:0e88a484-6f71-4a54-b119-0fa6a07d532a:image.png)

용어표

### 메모리 상에 저장되는 트리 구조

- 마치 연결 리스트처럼 하나의 노드를 데이터를 저장할 공간과 자식 노드의 위치 정보(메모리 상의 주소)를 저장할 공간(들)의 모음으로 간주함으로써 구현할 수 있다.

![image.png](attachment:7e41f93d-a063-44bc-9cb4-a7bb7fe093ab:7b838766-6081-4dee-8c60-f4e61efa437e.png)

---

# 트리의 순회(tree traversal)

- 트리의 모든 노드를 한 번씩 방문하는 것

## 트리의 모든 노드를 한번씩 방문하는 순회

![image.png](attachment:f2707425-8dd7-417c-8b1e-67fde796053b:image.png)

- 전위 순회: a→b→d→h→i→e→j→k→c→f→l→g
- 중위 순회: h→d→i→b→j→e→k→a→l→f→c→g
- 후위 순회: h→i→d→j→k→e→b→l→f→g→c→a

전위 순회

## 전위 순회(preorder traversal)

- 루트 노드부터 시작해 왼쪽 서브트리를 전위 순회하고, 이후 오른쪽 서브트리를 전위 순회하는 순회 방법
- 1️⃣ 루트 노드→ 2️⃣ 왼쪽 서브트리 전위 순회 → 3️⃣ 오른쪽 서브트리 전위 순회
- 우선 루트 노드 a를 방문한 다음, 왼쪽 서브트리를 전위 순회하기 위해 왼쪽 서브트리의 루트 노드 b를 방문한다. 그리고는 노드 b를 기준으로 왼쪽 서브트리를 전위 순회한다.

![image.png](attachment:1b60d671-c318-4578-aebe-e31cf79052c4:image.png)

![image.png](attachment:5cc0a934-8f8b-4f9e-954d-f57d6f3636f4:image.png)

![image.png](attachment:8759dafc-ad88-48ee-a741-bcdeff7c4609:image.png)

![image.png](attachment:8f31d074-0b43-44d2-afe3-70866a13e351:image.png)

![image.png](attachment:8289b7e8-e0cb-48c8-b480-63c99cb4a923:image.png)

#### ⇒ a→b→d→h→i→e→j→k→c→f→l→g

### 의사 코드(pseudo code)

```python
전위 순회(노드):
	if 노드가 존재하지 않으면:
		return
	노드 값 출력
	전위 순회(노드의 왼쪽 자식)
	전위 순회(노드의 오른쪽 자식)
```

중위 순회

## 중위 순회(inorder traversal)

- 왼쪽 서브트리를 중위 순회한 다음, 로트 노드를 방문하고 오른쪽 서브트리를 중위 순회
- 1️⃣ 왼쪽 서브트리 중위 순회 → 2️⃣ 루트 노드 → 3️⃣ 오른쪽 서브트리 중위 순회

![image.png](attachment:2159c4ce-07d5-4c5e-8030-13a1a9da1895:image.png)

![image.png](attachment:9fbf5109-e8fe-438f-8a41-d12360c430eb:image.png)

![image.png](attachment:ba7c5081-27ae-4292-8726-297300fb5963:image.png)

![image.png](attachment:55339547-8ee6-4549-b888-a9f3ceb11a6d:image.png)

![image.png](attachment:d2ed92bb-0509-4759-9c34-3d25df632678:image.png)

#### ⇒ h→d→i→b→j→e→k→a→l→f→c→g

### 의사 코드(pseudo code)

```python
중위 순회(노드):
	if 노드가 존재하지 않으면:
		return
	전위 순회(노드의 왼쪽 자식)
	노드 값 출력
	전위 순회(노드의 오른쪽 자식)
```

후위 순회

## 후위 순회(postorder traversal)

- 왼쪽 서브트리를 후위 순회하고, 오른쪽 서브트리까지 후위 순회한 다음, 루트 노드를 방문하는 순서로 노드에 접근하는 순회 방법
- 1️⃣ 왼쪽 서브트리 후위 순회 → 2️⃣ 오른쪽 서브트리 후위 순위 → 3️⃣ 루트 노드

![image.png](attachment:92810f99-0df7-4eb4-96a8-be125b8cf170:image.png)

![image.png](attachment:cf6bc5c7-7f96-4304-ac73-0b6e50497e4a:image.png)

![image.png](attachment:22a7fb24-a677-4ae8-b5fd-9fee234cfdb9:image.png)

![image.png](attachment:5a95d58e-987e-4db6-9cf2-4534050ae023:image.png)

![image.png](attachment:fcb8b6da-d734-4fa2-b2f8-cc79c9f33724:image.png)

#### ⇒ h → i → d → j → k → e → b → l → f → g → c → a

### 의사 코드(pseudo code)

```python
후위 순회(노드):
	if 노드가 존재하지 않으면:
		return
	전위 순회(노드의 왼쪽 자식)
	전위 순회(노드의 오른쪽 자식)
	노드 값 출력
```
		

<aside>
📌

#### 전위 순회: 루트 노드 → 왼쪽 서브트리 전위 순회 → 오른쪽 서브트리 전위 순회

#### 중위 순회: 왼쪽 서브트리 중위 순회 → 루트 노드 → 오른쪽 서브트리 중위 순회

#### 후위 순회: 왼쪽 서브트리 후위 순회 → 오른쪽 서브트리 후위 순회 → 루트 노드

</aside>

---

# 트리의 종류

## 이진 트리(binary tree)

- 자식 노드의 개수가 2개 이하인 트리

![image.png](attachment:4bac7154-86e7-4d1e-a543-5e3b98eec83a:image.png)

## 편향된 이진 트리(skewed binary tree)

![image.png](attachment:fe7e45ea-3651-4305-b7b0-24679048dd71:image.png)

## 정 이진 트리(full binary tree)

- 자식 노드의 개수가 1개가 아닌 이진 트리
- = 자식 노드의 개수가 0개 또는 2개인 이진 트리

![image.png](attachment:094a9f50-3c68-4d50-a779-ce24b1b17315:image.png)

## 포화 이진 트리(perfect binary tree)

- 리프 노드를 제외한 모든 노드들이 자식 노드를 2개씩 가지고 있고, 모든 리프 노드의 레벨이 동일한 이진 트리

## 완전 이진 트리(complete binary tree)

![image.png](attachment:89404029-08b4-4d06-a26a-b3dbd430af8c:image.png)

- 마지막 레벨을 제외한 모든 레벨이 2개의 자식 노드를 가지고 있으며, 마지막 레벨의 모든 노드들이 왼쪽부터 존재하는 이진 트리

![image.png](attachment:e060e127-eb81-4244-98af-7a768e9c1609:image.png)

---

## 탐색에 활용되는 트리: 이진 탐색 트리와 힙

### 이진 탐색 트리(BST, Birnary Search Tree)

- 특정 노드의 왼쪽 서브트리에는 해당 노드보다 작은 값을 지닌 노드들이 있고, 오른쪽 서브트리에는 해당 노드보다 큰 값을 지닌 노드들이 있는 구조의 이진 트리
- = 왼쪽에는 작은 값, 오른쪽에는 큰 값

![image.png](attachment:c63d5992-5a41-44ce-8111-3ae0099f5cb8:image.png)

- 최악의 상황 ⇒ 편향된 이진 트리의 경우, 탐색 속도 O(n)#

![image.png](attachment:f087b14e-b0ca-4c28-aed1-20fbe8113704:image.png)

---

## 힙(heap)

- 탐색에 특화된 또 다른 이진 트리의 일종
- 최댓값과 최솟값을 빠르게 찾기 위해 사용

### 시간 복잡도 : O(log n)

![image.png](attachment:62d3c2ca-081f-4725-9d6d-7ff2fff6d54d:image.png)

### **최대 힙 기반 우선순위 큐**

![image.png](attachment:55b5c8c7-f0f1-49b5-b93e-0fad10c0de60:image.png)

---

## 균형을 맞추는 트리: RB 트리

![image.png](attachment:b5a07803-9314-4619-87bb-7e7acb508cda:image.png)

- 케이스 1: 이진 탐색 트리에 삽입되는 순서
    - 3→2→4→1(편향 발생X)
- 케이스 2: 이진 탐색 트리에 삽입되는 순서
    - 1→2→3→4(편향 발생O)

⇒ 균형을 맞추는 트리가 필요 ⇒ 자가 균형 이진 탐색 트리(self-balancing binary search tree)

⇒ AVL 트리(Adelson-Velsky and Landis Tree)와 RB 트리(Red Black Tree)

#### 1️⃣ 루트 노드는 블랙 노드이다.

#### 2️⃣ 리프 노드는 블랙 노드이다.

#### 3️⃣ 레드 노드의 자식 노드는 블랙 노드이다.

#### 4️⃣ 루트 노드에서 임의의 리프 노드에 이르는 경로의 블랙 노드 수는 같다.

### NIL(Null Leaf) 노드

- 실질적인 데이터가 저장되어 있는 않은 노드라고 가정

![image.png](attachment:3e7c14aa-07cd-4238-9801-3b34e7b90ad3:image.png)

#### 삽입

- RB 트리에서 새 노드를 삽입할 때는 일반 이진 탐색 트리처럼 넣되, 새 노드는 빨간색으로 설정한다.
- 삽입 후 RB 트리의 조건이 깨지면, 조건을 만족할 때까지 회전(rotation)이나 색상 변경을 수행해 균형을 유지한다.

![image.png](attachment:fe43c322-a941-4c8b-99ab-cdd2318fda4c:image.png)

<aside>
📎

## **트리의 회전**

![image.png](attachment:635e743c-8228-4dc3-978c-a072cc9681a6:image.png)

---

![image.png](attachment:6b72f402-a0f3-4a70-b488-5d8b9e898385:image.png)

</aside>

#### 3️⃣ 레드 노드의 자식 노드는 블랙 노드이다.

조건에 부합하지 않는다.

⇒ 조건에 맞게 12를 15의 자식 노드로 만들고, 12를 레드 노드로, 15를 블랙 노드로 변환

![image.png](attachment:3a365f07-4c25-49f6-8a86-de89c63d58b0:image.png)

#### 삭제

- RB 트리에서 5를 삭제한다고 가정

![image.png](attachment:f671a9a3-070c-4755-8c8e-b3e1e06e8733:image.png)

![RB 트리 유지 조건에 부합하도록 트리 회전하거나 색상을 재지정한 트리](attachment:715403b3-da72-4c6b-a613-08e2a7e7193a:image.png)

RB 트리 유지 조건에 부합하도록 트리 회전하거나 색상을 재지정한 트리

---

## 대용량 입출력을 위한 트리: B 트리

- B 트리는 RB 트리와 마찬가지로 균형을 유지하는 트리 중 하나
- 이진 탐색 트리가 아닌 다진 탐색 트리의 한 종류
- 한 노드가 가질 수 있는 자식 노드의 수는 최소, 최대 개수가 정혀져 있다.

#### M차 B트리

- 최대 자식 노드의 개수가 M개
- 최소 자식 노드의 개수는 $\lceil M/2 \rceil$개
- 하나 이상의 키(key) 값이 존재하고 각 키들이 오름차순

![image.png](attachment:bc4e7777-6bb4-4da6-8a95-be614545c4be:image.png)

- **자식 노드의 수 (N + 1 규칙)**
    - 노드 내부의 키가 N개라면, 자식 노드의 수는 반드시 N + 1 개
- **모든 리프 노드의 깊이가 동일**
    - 데이터가 한쪽으로 치우치는 편향 상태가 발생하지 않아 항상 일정한 탐색 성능을 보장

<aside>
📎

## B 트리의 변형, B+ 트리

#### 1️⃣ B+ 트리에서는 실질적인 데이터가 모두 최하위 리프 노드에 위치

#### 2️⃣ 실질적 데이터를 저장하는 최하위 리프 노드는 연결 리스트의 형태를 띔

---

![image.png](attachment:9095a376-9cd7-46c1-9bbe-15ed1d29b449:image.png)

</aside>

### 트라이(trie)

- 문자열을 효율적으로 탐색하고 저장하기 위한 트리

### 세그먼트 트리

- 빠른 구간 연산을 위한 트리

### 펜윅 트리(fenwick tree)

- 이진수 비트 연산으로 구간 합과 수정을 O(\log N)에 처리하는 경량화된 세그먼트 트리