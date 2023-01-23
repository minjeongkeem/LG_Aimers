## `Transformer`

- Attention의 병렬적 사용을 통해 효율적 학습이 가능한 구조의 언어 모델

- 언어 모델: 특정 문장 (단어의 나열)이 등장할 확률을 계산해주는 모델

- Transformer의 개괄적 구조: 내부 `encoder` 파트와 `decoder` 파트가 있고, 이 둘 사이를 이어주는 연결고리가 존재

- 6개 (n개) 의 `encoder` 파트 존재

- `embedding vector`:       
  
    - 컴퓨터는 특정 단어를 특정 차원의 숫자로 인식해야함 (ex) 512차원의 임베딩 : '개'라는 단어를 512의 vector로 변환하여 생각
    - 의미상으로 유사하다면 공간상에서도 유사하도록 학습시키는 매커니즘 (word embedding)

- `positional encoding`: transformer는 단어를 순차적으로 받지 않고 한번에 받는 구조이므로 입력 시퀀스에서 단어들 간의 위치 관계를 표현하는 역할

-`multihead attention`: 문서 (문장) 안에서 단어들이 어떤 연관관계를 가지고 있는지 해석 하는 것 
 - position encoding이 더해진 word embedding은 첫번째 인코딩 블록에서 `self-attention`(의존성 o)과 `FFNN`(의존성 x, 병렬화 가능)을 거치게됨 
 - `특정 위치의 단어는 해당 위치를 유지하면서 연산이 수행됨`

- `encoder`과정
  - 일련의 벡터들을 입력으로 받음
  - 입력된 벡터들은 `self-attention`과 `FFNN`을 거쳐 상위 인코더의 입력으로 투입

- `self-attention`
  - 입력 시퀀스의 다른 위치에 있는 단어들을 둘러보면서 특정 위치의 단어를 잘 설명할 수 있게 함 (한번에 들어온 문장에서 `단어들 간의 서로 어떠한 관계가 있는지 스스로 학습`할 수 있게 하는 구조)
  - 절차
    - step 1: 입력 벡터에 대해 세가지 벡터를 생성
    - 아래 세가지는 `data를 통해서 학습을 하는 대상` 
      - `Query`: 어떤 단어가 다른 단어들하고 무슨 관계가 있는지 알고 싶은 `질의 대상`이 되는 단어
      - `Key`: query를 매칭시켜주는 label 값에 해당하는 embedding vector
      - `Value`: key값에 해당하는 실제 연결된 value 값 (단어)
    - step 2: 지금 표현하고자 하는 단어(query)에 대해 `어떤 단어들을 함께 고려해야 하는지(key)`를 알려주는 스코어 산출
      - Q와 K를 곱한 후 softmax 함수를 취해서 스코어 계산
    - step 3: step 2에서 계산한 score를 차원의 루트 수로 나눠 줌 > 이를 통해 gradient 전파가 안정적으로 수행됨 
    - step 4: 결과물을 이용해 softmax 함수를 적용하여 해당 단어에 대한 집중도를 산출 > 결론적으로 q를 해석하기 위해 어떤 걸 집중해서 봐야하냐(k,v)를 알려줌
    - step 5: step 4에서 산출된 확률값과 해당 단어의 key, value와 곱함
    - step 6: step 5에서 산출된 모든 값을 더해서 출력으로 반환 
- `multihead attention`: 복잡한 문장이라면 (ex)it이 의미하는게 상당히 다양할 수 있음 > 여러가지 attention을 동시에 적용

- `decoder` 과정에서도 동일하게 진행됨

`Feed-forward Networks`: attention을 통해 산출된 출력 값에 대해 다시 비선형 변환과 관계식을 통해 학습을 하는 과정

 - `같은 encoder 부분끼리는 동일한 가중치를 사용`함

-`masked multihead attention`: `decoder` 시 사용한다. decoding은 encoding과 달리 순차적으로 일어남. 
 - (ex) I love you >> '나는 너를 사랑해'로 번역 시 '나는'이라는 단어를 번역할 때 '사랑해'가 가지고 있는 정보를 사용하면 안됨
 - 따라서 Query보다 `뒤에 위치한 토큰들에 대한 정보는 가용하지 않다고 가정`하고 해당 부분을 전부 `마스킹 `처리 (`가중치를 0으로` 만들어버림)
 - 해당 과정은 순차적으로 수행할 필요 없이 `한번에 수행 가능`함 (이미 `학습 과정에서 순서를 알고 있기 때문`)

## `TST`: Transformer의 시계열 데이터 적용

- Transformer의 Encoder 구조만 사용
- `Pre-training` (사전 학습) 과업을 위해 연속적 길이의 Input masking 사용
  - '나'에 대해 빈칸을 만들어 놓고 학습시켜서 '나'를 잘 알도록 설계하는 것 <자체 학습, 시계열 data가 주어지고 어떤 목적으로 쓰이는지 모를 때 input data밖에 없는 것이므로>
- Layer Normalization 대신 Batch Normalization 사용
- `Fine-tuning` (내가 원하는 문제를 잘 풀 수 있도록 고도화) 단계에서 구조를 어떻게 설계하느냐에 따라 Classification, Regression, Forecasting, Missing Value Imputation 등 다양한 task 적용 가능
 - `Fine-tuning`에서는 masking을 하지 않음

- Pre-training을 통해 기존의 Supervised Learning만 수행했을 경우보다도 우수한 예측 성능을 내는 것을 확인