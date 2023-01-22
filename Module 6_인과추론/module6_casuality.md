# `Causality` (인과성)

- 하나의 어떤 무엇인가가 다른 무엇을 생성함에 있어 영향을 미치는 것

- 원인과 결과 사이의 관계는 필요조건이나 충분조건일 필요가 없다

## `인과 계층` by Pearl

- Level 1: 관측 계층

- Level 2: 실험 계층 

- Level 3: 반사실적 계층 (만약 ~하지 않았더라면 어떻게 변했을까?) 

## Simpson's Paradox

- 인과적 분석을 위해서는 주어진 데이터 뿐만 아니라 변수들 간의 인과적 관계를 이해해야 함

## 데이터 분석시 고려사항

- 주어진 데이터가 상관성을 지니는지 or 인과성을 지니는지

- 우리가 알고자 하는 질문이 단순히 조건부 확률같은 상관성에 관한 것인지 or 인과성에 관한 것인지

## `인과추론` (Causal Inference)

- 인과적 통찰을 이용해서 하는 모든 추론 (계층을 넘나드는 추론)

- 알 수 없는 실험 결과를 관측 데이터와 연결

## `Structural Causal Models` (SCM)

- V: observed
  (ex) Smoking, Cancer
- U: unobserved
- (ex) 사회적 요인, 유전 요인 등 
- F: mechanisms
  (ex) 흡연은 사회적 요인과, 유전적 요인과 같은 관측 불가능한 변수에 의해 영향을 받는다고 가정

  - Intervention: 변수 X를 고정

## `Causal Effect`

- p(y|do(x)): y가 중재했을 때 어떻게 변할 것인가

- Causal diagram에 어떤 정보가 담겨져 있고, 관측데이터로부터 인과관계를 계산할 때 사용하는 것이 중요

- 조건부 독립성(`Conditional Independence`)

: Causal diagram 그래프에서 조건부 독립성을 읽어낼 수 있음

