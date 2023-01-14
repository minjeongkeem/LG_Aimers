# `Ensemble Learning`
- 이미 사용하고 있거나 개발한 알고리즘의 간단한 확장

- `Supervised learning task에서 성능을 올릴 수 있는 방법`

- 원리: 머신러닝에서 알고리즘 종류에 상관 없이 서로 다르거나, 같은 매커니즘으로 동작하는 다양한 머신러닝 모델을 묶어 함께 사용하는 방식

- 학습 방식: 학습 data set을 random하게 나누어서 학습을 진행하며, 최종 결정은 마지막에 학습한 다수의 모델이 각각 결정을 내린 후 다수결로 최종 예측 결과를 알려줌

- 장점
  1. 예측 성능을 안정적으로 향상할 수 있음
  2. 쉽게 구현이 가능
  3. 각 model은 독립적으로 구현되어 모델 파라미터 튜닝이 많이 필요 없음
- 단점
  1. 다양한 모델을 사용하기 때문에 compact한 표현 어려움



## `bagging`
- 학습과정에서 training sample을 random하게 나누어 선택해 학습 

- lower variance의 안정적 성능 제공에 유용 
- sample 구분 후 서로 다른 classifier를 `병렬적`으로 사용함
-따라서, train data가 적고 overfitting이 발생할 때 > sample을 random하게 설정하는 과정에서 `data augmentation`효과를 가질 수 있음

## `bootstrapping`
- 다수의 sample dataset을 생성해서 학습하는 방식

## `boosting`
  
- `weak classifier`: bias가 높은 classifier, 모델이 단순하여 혼자서는 높은 성능을 제공하기 어려움
  
- `weak classifier cascading`: weak classifier들을 `sequential`하게 동작

- ex> `Adaboost`: base classifier에 의해서 오분류된 sample에 대해 높은 가중치를 두어 다음 학습에 사용할 수 있게함
- 장점: 간단하게 구현이 가능하며, 특정 학습 알고리즘에 구애받지 않음

- `Random Forest` : `bagging` + `boosting` 활용하는 알고리즘, `GBM` 방식

- DT의 집합: 서로 다르게 학습된 DT의 결정으로 예측을 수행 (`bagging` 한 학습)

- DT는 매 노드에서 결정함 > 자체적으로 weak classifier의 `boosting` 방식 

## Model 성능 평가

- `Accuracy`와 `Precision`, `Recall` 값을 모두 같이 봐야 성능 평가 의미가 있음

- `Accuracy` 평가 
  - TP + TN / ALL
  
- `Confusion matrix` : 각 경우에 대해 오차가 얼마 있었는지 표현하는 방법
- TP/TN <-> FP/FN

- `FP` (False Positve Error)
-  predict 값 = positive but actual = negative

- `FN` (False Negative Error)
- predict 값 = negative but actual = positive

- `Precision`
  - 실제환자 / 실제환자 + 환자가 아닌데 환자로 예측된사람
  - TP / TP + FP

- `Recall`
  - 실제환자 / 실제환자 + 실제환자지만 환자 아닌것으로 예측된사람
  - TP / TP + FN

- `ROC Curve`: 서로 다른 classifier의 성능을 측정하는데 사용하는 curve

- 가로축: `FPR` = 1- `TPR(True Positive Rate`

- 세로축:  `Sensitivity` = `recall`

- 동일 sensitivity에서 더 낮은 FPR 값을 나타내는 것이 더 좋은 성능의 모델

## 성능 평가 example

- 암환자 예측 모델(`암 판정이 기준`) 의 경우 `'FN'` (실제 환자인데 예측이 환자가 아닌 것으로 된 사람) 의 숫자가 줄어드는 것이 중요함 

- 재난지원금 대상자 예측 모델 (`미지급자가 기준`) 의 경우 `'FP'` (실제 대상자지만 미지급 대상으로 판정된 경우)가 많다면 complain이 많을 것임