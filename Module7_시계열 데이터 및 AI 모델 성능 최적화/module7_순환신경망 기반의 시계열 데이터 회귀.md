## Non-sequential vs Sequential Data 

- `Non-sequential Data`: 시간 정보를 포함하지 않고 생성된 데이터

- N (관측하는 data 개수) * D (변수의 개수) 행렬로 나타남

- `Sequential Data`: 시간정보를 포함하여 순차적으로 생성되는 데이터
-  N by D Tensor로 생성

## `RNN`(순환 신경망)

- 순차 데이터를 처리하는데 특화된 인공신경망 구조

- 현 시점에서의 Hidden State => 이전 시점에서의 Hidden State와 현 시점에서의 입력을 이용한 연산으로 계산

- `Vanilla RNN` (초기 모델)은 Long-term relationship 파악엥 어려움이 있어서 이를 해결하기 위해 `LSTM` 및 `GRU` 구조가 제안됨

## `LSTM`

- Long Short-Term Memory

- 구성 요소
   -  Cell state: LSTM 핵심 구성 요소, 일종의 정보를 저장하는 곳

- Setp 1: 지금까지 cell state에 저장된 정보 중에서 얼마나 망각할 것인지 결정
  
   -  Forget gate: 이전 단계의 hidden state와 현 단계의 입력으로부터 0과 1 사이 값 출력 
      -  1: 지금까지 cell state에 저장된 모든 정보 보존
      -  0: 지금까지 cell state에 저장된 모든 정보 무시

- Setp 2: 새로운 정보를 얼마만큼 cell state에 저장할 것인지 결정
    - Input gate: 어떤 값을 업데이트 할 것인지 결정
  
- Setp 3: 예전 cell state를 새로운 cell state로 업데이트
  - forget gate 결과 값과 곱한 값 + input gate 결과 값 곱한 값 = 새로운 cell state 값

- Setp 4: 출력 값 결정
  - 이전 hidden state 값과 현재 입력 값을 이용하여 output gate 값 산출
  - output gate 값과 현재 cell state 값을 결합하여 현재 hidden state 값 계산

## `GRU`

- 구성 요소: Reset / Update 
- LSTM 보다 단순화된 구조
- 그러나, 실험적인 측면에서 보았을 때 LSTM이나 GRU의 성능 차이가 크지 않음

## `Attention`

- 시계열 데이터의 어느 시점이 최종예측에 영향을 주는지 판별할 수 있는 매커니즘

- 구성 요소

  - a(알파): i번째 hidden state vector가 context vector
생성에 기여하는 비중

  - c(context vetor): 각 입력 단계의 hidden state의 선형 결합 (가중치 = alpha)

  - h: Attention이 고려된 hidden state는 context vector와 기존 hidden state를 concatenation한 뒤 선형 및 비선형 변환을
수행


- Attention을 추가한 구조가 대체로 예측 성능이 더 우수함

