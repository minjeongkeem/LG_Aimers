# `Batch gradient descent`

- 단점: theta 0, theta 1을 업데이트 하면서 전체 sample (m) 을 고려해야 함 > 따라서 m이 늘어날수록 복잡도가 커지게됨

## `SGD`

- Batch gradient descent 알고리즘 방식의 단점을 개선하기 위해 m을 극도로 줄인 (m=1) 알고리즘

- 단점: noise의 영향을 받기 쉬움 (m=1이니까)

- `local minimum`에` 빠지기 쉬움

## `momentum`

- 과거의 gradient가 업데이트 되어오던 방향 및 속도를 어느정도 반영해서 현재 포인트에서 graident가 0이 되더라도 게속해서 학습을 진행할 수 있는 동력 제공

- `local minimum`에 빠지는 것을 방지하고 `global minimum`에 도달할 수 있도록 함

## `nestrov momentum`

- gradient를 먼저 평가하고 업데이트를 함

## `AdaGrad`

- 각 방향으로의 learning rate를 적응적으로 조절하여 학습 효율을 상승

- 그 방향으로 gradient가 크다: 이미 그 방향으로 학습이 많이 되었다. 따라서 너무 크다면 그 방향으로 theta 값을 줄인다. 반대로도 가능

- 단점: gradient값이 누적됨에 따라 learning rate 값이 작아짐 > 그 지점에서 학습이 멈춰버림

## `RMS Prop`

- `AdaGrad`의 단점을 개선한 알고리즘

- 완충된 방식으로 learning rate가 감소됨

## `Adam`

- `RMS Prop` + `momentum` 방식의 알고리즘

- 가장 자주 사용


## `learning rate scheduling`

- hyper parameter (learning rate)를 학습 과정에 따라 설정하기

- 초기에는 빠르게 학습을 진행하고, 이후에는 학습을 조절

## model 과적합 문제

- model이 지나치게 복잡하여, 학습 parameter 숫자가 많아 제한된 학습 sample에 너무 과하게 학습이 되는 현상

- 일부 입력변수가 상호간에 dependent할 수 있음

- 따라서 입력 feature가 많다고 성능이 높아지지 않음

- 해결 방법

## `Regularization`

- 복잡한 모델을 사용하더라도 (parameter 숫자가 많더라도), 모델 복잡도에 penalty를 주어 model의 overfitting 방지

- 가능한 theta를 쓰지않고 에러를 최소화하도록 노력 > paramter가 덜 중요하다면 그 값을 0으로 보내버려서 없애버림
