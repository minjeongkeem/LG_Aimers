# `Supervised Learning `(지도학습) 
- Data에 Label이 있다.

- 데이터 양식: 입력 변수- x와 label- y

- `입력 feature` == 입력 변수(`x`) => 따라서 domain 지식이 있다면 classification에 효과적인 feature 도입 용이

- x -> y로 가는 함수 h를 학습해서 새로운 데이터가 들어왔을 때 해당 데이터의 label을 맞추는 것 

- `Regression`와 `Classification`이 있음

## `Learning`

- 우리가 가지고 있는 ML 모델이 label과 비교하여 출력이 정확한지 알려줌
  
- 정확하게 정답을 맞추게끔 parameter training 

- `model output`과 정답과의 차이: `error`를 줄여가며 학습 진행

## `Testing`

- 모델이 실제 환경에 적용되는 것

- 새로운 test 데이터 사용

- 이 때의 모델 정확도가 실제 성능

## `Target function`

- x=> y로 mapping 하는 정답 함수

- 이상적인 함수

- why? 우리가 모든 입력 sample에 대해서 전세계 모든 data를 확인해야만 가능

- `machine learning model` == `hypothesis H` (일정 수의 data set을 가지고 target function에 가까운 결과값을 내는 함수의 역할)

## `Model Selection`

- 풀고자 하는 문제에 가장 적합한 모델을 선택하는 과정 

## `Optimizeation`

- model parameter를 최적화하여 model이 가장 우수한 성능을 제공하도록 하는 것

## `Generalization`

- model이 학습과정에서 관찰하지 못한 sample에 대해서도 우수한 성능을 가지는 것이 중요함

## `Generalization error E`
- model의 일반화된 성능을 측정하기 위한 measurement

- 우리의 목표: error function을 최소화하는 것

- 하지만 이것은 이상적인 함수임

- 따라서, `training error`, `validation error`, `test error`를 통해 이를 최소화 하려고 함

## `squared error`
- model 출력과 정답과의 차이를 제곱하여 계산

## `binary error`
- 내부 logic을 판별하여 맞으면 0 틀리면 1인 함수
=> model 출력과 정답이 같지 않으면 1을 출력하는 error 함수

## `overall error`
- 모든 `pointwise error`를 합한 값 == `loss function` or `cost function`

## `E train`
- `training error` => model을 주어진 data set에 맞추어 학습하는데 사용하는 error

- 주어진 sample에서 모델 parameter를 최적화 하기위해 사용

- 따라서 `E general`을 approximation하는 것에는 적합하지 않음 

## `E test`
- `test error` => model이 실제 적용될 때 나타나는 error == `E general`

- 따라서 `E test`를 0에 수렴하게 하여 `E general`을 0에 가깝게끔 하고자 함

- 1) `E test`와 `E train`이 가까워지도록 학습

- 학습한 model이 일반적인 성능을 갖도록 하는 작업

- 일반적인 성능? == `variance` (분산)이 작다.

- 실패? `overfitting`(과적합) (high variance)

- 해결: `regularization`, 더 많은 데이터

- 2) `E train`이 0에 가까워지도록 학습

- 모델의 정확도를 올리고 있다.

- `bias` (편차)가 낮아진다

- 실패시 `underfitting`

- 해결: `optimazation`, 더 복잡한 모델 사용

## `Curser of dimension`

- 입력 data 및 feature가 늘어나면 sample도 늘어나야하지만 현실적으로 어려움

## `data augmentation`
- data sample수를 늘리기 위한 방법

- `regularization`
  
- `ensemble`

## `cross-validation`
- Training set을 크게 k개 그룹으로 구분
- k-1개의 그룹을 training에 활용, 1개 그룹을 validation에 활용 
  
- training data: model parameter로 fiting하기 위해 사용

- validation data: model 최적화에 사용