# Linear Classification

- classification의 경우 모델 출력값이 `discrete`함

- possitive sample: h(x) > 0

- negative sample: h(x) < 0

- `hyper plane` (=> `decision boundary`) 을 구해서 linear combination에 의해 postive sample과 negative sample을 구분하는 것이 목적

- 장점: 단순, 해석가능성, 다양한 환경에서 일반적으로 안정적인 성능

## Loss function의 종류

- `Zero-one loss`
- 내부의 로직을 판별하여 맞으면 0, 틀리면 1을 출력하는 함수

- `score`: 모델이 얼마나 confident한지 측정할 수 있음

- `margin`: score * y 값

- 따라서, score(+) * y(+)인경우와 / score(-) * y(-)인경우 margin 값이 큼 => 정답을 맞췄을 때 >> `margin`이 크다 == `model prediction이 높다`

- `gradient`가 모두 0이 되어버림 > 학습 불가
  
- `Hinge loss`
- 1-`margin` 값과 0을 비교하여 더 큰 값을 출력

- EX) `margin`이 큰 경우 (model prediction이 높은 경우) >> 1-margin값은 (-)이므로 0을 출력

- 반대로면, 1-margin (+)를 출력 > 점차 증가> gradient(미분값) 역시 점차 증가함

- `Cross-entropy loss`

- 가장 많이 사용하는 loss function

- 두 pmfs의 다른 정도를 평가하는 지표

- 두 개의 서로 다른 q와 p가 다름에 따라 달라짐

- q와 p가 비슷하다면 loss가 작고, 다르다면 커짐

- `sigmoid`함수: `score값(실수)`과 확률함수 값(0아니면1)을 mapping할때 사용 >> `logistic model`

## Parameter 최적화 방법

- `Gradient descent algorithm`

## `Multiclass classification`

- One-VS-All

- C or not, B or not, A or not으로 `Binary classification`으로 바꾸어 (확장하여) 생각

## `One Hot Encoding`

- 두개의 서로 다른 표 사이에 거리를 가깝게 하면서 학습

- multification classification에서 `1로 label 정보를 저장`