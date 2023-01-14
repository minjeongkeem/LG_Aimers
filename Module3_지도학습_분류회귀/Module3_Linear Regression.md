# Linear Regression

- 주어진 입력에 대해 출력과의 선형적인 관계를 추론하는 문제

- Supervised learning 중 하나 

- model이 출력이 연속되는 값을 가짐

- data set에서 입력과 정답이 있는 label이 있는 data를 사용

## Linear model
- **선형 model이라고 해서 반드시 입력 변수에 선형일 필요는 없음**

- 장점
- 1. 단순하다 - 입력 parameter와 결과가 해석 가능함

- 2. 일반화: 다양한 환경에서 안정적 성능을 제공할 수 있음

- 입력 변수의 수에 따라 `univariate model`과 `multivariate model`로 나뉨

- loss function: `MSE` 주로 사용 (model 출력 값 - 정답) 오차의 제곱

- model parameter에 따른 함수

- 우리의 목적: `MSE`를 최소화하는 theta0, theta1을 구하는 것

- parameter optimization하는 방법: 

- cost function을 최적화하는 것

- `Normal equation` - `Least square`: data set이 늘어나는 현재 상황에선 다소 비효율적임

- 1 STEP으로 해를 구함

- `Gradient descent algorithm`: `grdient`가 0인 지점

- `gradient method`:함수의 변화도가 `가장 큰 방향으로 이동하며 이를 반복`함

- `Learning rate`: parameter를 업데이트 하는 속도 조절하는 hyper parameter (사전에 설정하는 파라미터, 항상 양수 값을 가짐)

- `hypothesis`와 `learnable parameter `(theta)는 linear` 해야함  

- 따라서 `Learning rate`가 너무 크면 수렴하는데 많은 시간이 소요되고, 반대로 너무 작으면 gradient가 0인 곳을 놓치기 쉬워서 수렴이 어려움

- `global optimum`과 `local optimum`의 차이

- `global optimum`: 전체 error surface에서 가장 최소 값을 갖는 지점

- `local optimum`: 지역적으로는 최소지만 전체 영역에서는 최소가 아닐 수도 있음