## `CAM` (Class Activation Map)

- Saliency map 기반의 설명 가능 방법

- `Global Average Pooling` (Gap Layer): 각 Activation map의 모든 Activation들을 평균 내는 연산

- acivation이 크다: map이 주어진 입력과 관련이 많다. 

- 장점: 모델이 중요하고 있는 이미지 내 object를 정확히 인식 

- 단점: 모델 specific한 설명 > GAP Layer가 없는 모델도 많음

## `Grad-CAM`

- CAM을 Gradient 방법을 활용한 설명 가능 방법

- GAP Layer가 없어도 사용 가능

- 장점: `Model-specific` 하다 (backpropagation을 통해 gradient를 얻을 수 있다면 어떠한 모델이어도 사용할 수 있음)

- 단점: activation gradient가 정확하지 않은 경우가 있음 

## `Pertubation-based`

- 입력 데이터를 조금씩 바꾸면서 그에 대한 출력을 보고 그 변화를 설명하는 방법

- `LIME` (Local Interpretable Model-agnostic Explanations): 주어진 데이터 포인터에 대해서는 선형화가 가능하다.

- 주어진 데이터를 변화하면서 변화된 데이터를 모델에 여러번 통과시키면서 발생되는 (입력, 출력) pair를 간단한 선형모델로 근사하면서 설명하는 방법

- 장점: `Black-box` 방법이다. (입출력만 있다면 사용 가능)

- 단점: 데이터 교란이 필요하므로 계산 복잡도가 올라간다.

- `RISE`: LIME과 비슷

## `Influence function` 

- 해당 결과를 나타내는데 가장 많은 영향력을 준 training set을 알려줘 설명하는 방법