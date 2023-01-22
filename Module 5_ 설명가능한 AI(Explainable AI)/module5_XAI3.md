# XAI 설명 평가 

## `AMT (Amazon Mechanical Turk) test`

- 사람이 직접 비교하며 평가 

- 단점: 시간이 오래걸리며, 높은 비용

## `Hunman annotation`

- 사람들이 이미 만들어 놓은 annotation data를 사용

- `Pointing Games`: bounding box를 통해 평가

## `Weakly supervised semantic segmentation`

- 어떤 이미지에 대해서 classification label만 주어져 있을 때 그것을 활용하여 픽셀별로 객체의 label을 예측하는 방법 

- 픽셀별로 정답 label은 다 주어져있지 않음

- `IoU`: 정답 map과 만들어낸 segmentation map이 얼마나 겹치는지 평가하는 metric

- 단점: annotation data 얻기 쉽지 않음

## `Motivation`

- 픽셀을 교란함으로써 모델의 출력값이 어떻게 변화하는지 직접 test

- `AOPC`: 중요도 순서의 정렬한 pixel들을 중요도 순서대로 교란하였을 때 원래 예측한 모델 출력 값이 얼마나 빨리 변화하는지 평가

- `Deletion`: 낮을수록 설명력이 좋다

- `Insertion`: 높을수록 설명력이 좋다

단점: pixel을 지우면 출력 score를 잘 설명하지 못할 수도 있음

## `ROAR`

- XAI가 중요하다고 생각한 pixel을 지우고 다시 지운 data를 활용해 모델을 재학습하고 정확도가 얼마나 떨어지는지 확인 

단점: 계산 복잡도 높음

### XAI에 대한 신뢰성 연구 진행 중