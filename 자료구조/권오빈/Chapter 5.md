# 5장 트리

<aside>

**트리(tree)**는 계층적인 구조를표현하는 자료구조이다.
노드와 간선으로 이루어져 있다.

![image.png](attachment:9531a792-187f-471d-bea8-14466356ac85:image.png)

## 트리의 순회

트리 순회에는 크게 전위 순회(preorder), 중위 순회(inorder), 후위 순회(postorder)가 존재한다.

![image.png](attachment:754706e5-0f06-4aae-b92c-9f15151a5c6b:image.png)

## 트리의 종류

![image.png](attachment:784a6392-65ed-4f2c-af89-ba75dc806c4c:image.png)

## 탐색에 활용되는 트리 : 이진 탐색 트리와 힙

![image.png](attachment:885b7d09-76c1-4f44-af97-d7fc416c72a0:image.png)

## 레드-블랙트리

1. 노드는 레드 혹은 블랙 중의 하나이다.
2. 루트 노드는 블랙이다.
3. 모든 리프 노드들(NIL)은 블랙이다.
4. 레드 노드의 자식노드 양쪽은 언제나 모두 블랙이다. (즉, 레드 노드는 연달아 나타날 수 없으며, 블랙 노드만이 레드 노드의 부모 노드가 될 수 있다)
5. 어떤 노드로부터 시작되어 그에 속한 하위 리프 노드에 도달하는 모든 경로에는 리프 노드를 제외하면 모두 같은 개수의 블랙 노드가 있다.

![image.png](attachment:43fd7c41-0577-4b95-b787-ccc2cee7a248:image.png)

## 레드-블랙트리의 삽입

![image.png](attachment:21eeaed9-2133-4af9-bbb5-a4a2906c80ee:image.png)

![image.png](attachment:f87b4df2-5a02-45ec-94f9-351c0576182c:image.png)

앞으로 새로 삽입할 노드를 N(New), 부모 노드를 P(Parent), 조상 노드를 G(Grand Parent), 삼촌 노드를 U(Uncle)라고 하자.

Double Red가 발생했을 때

- 삼촌 노드가 `검은색`이라면 -> Restructuring
- 삼촌 노드가 `빨간색`이라면 -> Recoloring

### Restructuring

![image.png](attachment:f9549086-cfdf-4ecd-a204-030159e74fa5:image.png)

1. 새로운 노드(N), 부모 노드(P), 조상 노드(G)를 오름차순으로 정렬한다.

2. 셋 중 중간값을 부모로 만들고 나머지 둘을 자식으로 만든다.

3. 새로 부모가 된 노드를 검은색으로 만들고 나머지 자식들을 빨간색으로 만든다.

### Recoloring

![image.png](attachment:47a19bfc-1e92-429e-9195-74231572e5f5:image.png)

1. 새로운 노드(N)의 부모(P)와 삼촌(U)을 검은색으로 바꾸고 조상(G)을 빨간색으로 바꾼다.

1-1. 조상(G)이 루트 노드라면 검은색으로 바꾼다.

1-2. 조상(G)을 빨간색으로 바꿨을 때 또다시 Double Red가 발생한다면 또다시 Restructuring 혹은 Recoloring을 진행해서 Double Red 문제가 발생하지 않을 때까지 반복한다.

Recoloring은 간단해 보이지만 문제는 조상 노드(G)가 루트 노드가 아니면서, 조상 노드(G)가 또다시 Double Red 문제가 발생하는 경우이다. 이런 경우 1-2에 따라 Restructuring 혹은 Recoloring을 반복해서 실행한다.

## B 트리

한 노드가 여러 자식 노드를 가질 수 있는 다진 탐색 트리의 한 종류이다.
한 노드가 가질 수 있는 자식 노드의 최소, 최대 개수가 정해져있다.
최대 자식 노드의 개수가 M개인 B트리는 **M차 B트리**라고 한다.
M차 B트리가 가질 수 있는 **최소 자식 노드의 개수는 ceil(M/2)**이다.

ㅇㅇ

![image.png](attachment:a25b1fa1-f6ec-42cc-b25c-c398b1fd3354:image.png)

## B+ 트리

실질적인 데이터는 최하위 리프 노드에 위치한다.
최하위 리프 노드는 연결 리스트의 형태를 띄고 있다.

![image.png](attachment:dc7828a6-2dc3-4961-b7db-6799045d1682:image.png)

</aside>
