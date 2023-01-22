## Causal Effect Identifiability 
(인과 관계를 특정할 수 있는가)

- 계산 방법
  
- `markovian 가정` (모든 변수가 obserable하고 x가 집합이 아닐때) 시, 해당 factor x만 전체 결합 분포에서 제거하고 인과관계 계산 가능

- `back-door criteria`: 
- x, y가 있을때 교란에 의한 상관성을 제거하고자 함 (정확히 x일때 y가 어떻게 변할지만 구하는 방법)

- complete하지 않은 단점이 있음 (모든 formular를 찾을순 없다)

- `do-calculus`: back-dooor cirteria의 단점 개선

- 여러가지 다른 중재 조건에서 나오는 확률들 끼리 서로 연결고리를 만들어주고 서로 다른 중재로 어떤 확률 분포를 바꿔주는 역할

- rule 1: 관찰에 대한 것이 추가되거나 삭제될 수 있다 (조건부 독립) 

- rule 2: action과 observation을 바꿀 수 있다

- rule 3: action이 추가되거나 제거될 수 있다 (action을 취하는 것이 아무런 영향이 없을 수 있다)

- 결론: 조건부 독립이라면 다른 확률로 변경할 수 있다