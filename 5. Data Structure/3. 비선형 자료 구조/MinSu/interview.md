## 📝 Interview

#### 그래프와 트리의 차이점에 대해 설명하세요.
```
그래프는 정점과 간선으로 구성되어 있는 비선형 자료구조입니다. 부모-자식 관계라는 개념이 없고 그래프는 순환 혹은 비순환 구조를 이루며 방향성이 존재할 수도 있다는 특징이 있습니다.
트리는 그래프의 한 종류로 사이클이 없으며 두 개의 노드 사이에 오직 하나의 경로를 갖는 계층적인 형태로 데이터를 저장하는 자료구조입니다.
```
<br>

#### 이진트리의 순회방법에 대해 설명하세요.
```
이진 트리의 탐색 방법으로는 전위순회, 중위순회, 후위순회가 있습니다.
전위 순회는 루트 -> 왼쪽 서브트리 -> 오른쪽 서브트리 순으로 순회하는 방법을 말합니다.
중위 순회는 왼쪽 서브트리 -> 루트노드 -> 오른쪽 서브트리 순으로 순회하는 방법을 말합니다.
후위 순회는 왼쪽 서브트리 -> 오른쪽 서브트리 -> 루트노드 순으로 순회하는 방법을 말합니다.
```
<br>

#### 해시충돌과 해결방법에 대해 설명하세요.
```
해시 충돌이란 해시 테이블에서 작은 크기의 메모리로 데이터를 관리하는 과정에서 해시 함수가 서로 다른 두 개의 입력값에 대해 동일한 장소에 저장을 하려는 것을 의미합니다.
해시 충돌이 발생하는 상황으로는 첫째로, Key는 다른데 Hash가 같은 상황일 때 둘째로, Key도 Hash도 다른데 Index(hash % map_capacity)가 같은 경우가 있습니다.
이런 해시 충돌의 대표적인 방법으로 개방 주소법과 체이닝이 있습니다.
```
<br>


