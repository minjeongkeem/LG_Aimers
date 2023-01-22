## Limitaion of supervised learning 

- 예측 결과가 '왜' 이 모델이 이 결과를 나타내었는지 설명하지 못할 경우 제약이 있는 분야가 있음 (ex) 자율주행 등 

## `XAI 기법`

- 모델, dataset의 오류 검출 가능

- 모델의 편향도 확인 가능

- 사람이 모델을 쓸 때 그 동작을 `이해`하고 `신뢰`할 수 있게 해주는 ML 기술

## `Local` vs `Global`

- `Local`: 주어진 특정 데이터에 대한 예측 결과를 개별적으로 설명하려는 방법

- `Global`: 전체 dataset에서 모델의 전반적인 행동을 설명 > 개별 데이터 결과 따로 설명 X

## `White-box` vs `Black-box`

- `White-box`: 모델의 내부 구조를 정확히 알고 있는 상황에서 설명을 시도하는 방법

- `Black-box`: 단순히 모델의 입출력만 가지고 설명 시도 > 모델 내부구조 모름


## `Intrinsic` vs `Post-hoc`

- `Intrinsic`: 모델의 복잡도를 훈련하기 이전부터 설명하기 용이하도록 제안한 뒤 학습 시켜서 그 후 학습된 모델을 가지고 설명하는 방법

- `Post-hoc`: 임의 모델의 훈련이 끝난 후 이 방법을 적용하여 그 모델의 행동을 설명하는 방법 

## `Model-specific` vs `Model-agnostic`

- `Model-specific`: 특정 모델 구조에만 적용 가능

- `Model-agnostic`: 모델의 구조와 관계없이 어느 모델에도 항상 적용

## (ex) Linear model, Simple Decision Tree


- `Global`, `White-box`, `Intrinsic` `Model-specific` 한 방법

## (ex) Grad-CAM

- `Local`, `White-box`, `Post-hoc`, `Model-agnostic` 한 방법

- `Gradient` 로 예측 결과에 대해 설명

- `Gradient`의 단점: noisy할 수 있음

- 해결방안: noise를 섞어서 gradient를 계산 (`smooth grad`)