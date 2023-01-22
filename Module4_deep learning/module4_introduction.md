# Deep Neural Networks의 기본 동작 과정

- 두뇌의 동작과정을 모방하여 수학적인 인공지능 알고리즘으로 만든 것

## `Deep Learning`

- AI > ML > DL

- Computer Vision, Natural Language Processing, Time-Series Analysis

- Reinforcement Learning (ex) 바둑

## `Perceptron`

- 입력신호는 뉴런 내부적으로 특정한 가중치와 곱해지고, 그 값이 다 합산된 형태로 계산됨

## `Decision Boundary`
- 선형 결합의 가중치에 따라 output이 1 과 0으로 달라지는 경계
- 좌표 공간: `input feature space`


## `XOR Gate`
- x1 | x2 | y
  
  0  | 0  |  0

  0  | 1  |  1

  1  | 0  |  1

  1  | 1  |  0

## `Hidden Layer`
- 정보를 처리하는 중간 단계에 있는 layer

- (ex) tensorflow playground: layer 구성 test

## `Forward Propagation`
- a (ativation): multi-layer-perceptron의 순차적인 계산과정

## classficiation 시 `MSE Error` 문제

- 학습에 사용되는 gradient 값이 그렇게 크지 않을 수 있다 (학습이 느리다)

# Training Neural Networks

- deep learning의 학습 과정
: gradient descenting 

- loss function을 최소화 하도록 하는 parameter 찾기

## `Back Propagation`
- nerual net에 존재하는 각 parameter들에 대한 최종 loss function의 편미분 값 

## `Gradient Vanishing`

- gradient가 점차적으로 사라져 학습효과가 거의 없는 이슈

## `Batch Normalization`

- 특정 활성 함수를 썼을 때 학습을 용이하게 하는 특별한 형태의 뉴런 or layer

- (ex) tanh activation > gradient vanishing 되지 않기 위한 값의 범위가 대략 정해져있음 (대략 0 근처)

- mini batch 내에 있는 값들을 평균이 0이고 분산이 1이도록 normalize함

- 이후 가장 최적의 평균과 분산을 가지도록 스스로 결정할 수 있게끔 함

- deep learning에게 더 많은 권한을 주고, gradient vanishing을 효과적으로 해결할 수 있는 방법 중 하나

# `CNN`의 원리 

- computer vision task에 주로 사용

- 물체에서 일관되게 발견되는 요소를 조합해서 cnn으로 구분함

- 각 pixel별로 매칭이 됐는지를 작은 요소(패치)를 오버랩 시켜 확인 > 같다면 모두 1이 되고 이를 패치 수로 나눔 >> 매칭 확률

- 입력 이미지 수 >> 채널 == depth

- convolution layer 수 == output activation map 수

## `pooling layer`
- 이미지 패치를 옮겨가면서 해당 이미지 패치 범위에서 가장 큰 값을 기입

- max pooling => 2 by 2 적용 시 이미지 사이즈를 반으로 줄여줌

## `Relu Layer`
- output activation 값에다가 Relu activation Function 적용
- 양수 값은 그대로, 음수 값은 0으로 변환해줌

- convolution > Relu > convolution > Relu > Pooling > convolution > Relu > Pooling 형태로 stacking 됨

- layer를 stacking 하면서 분류할 수 있는 요소를 더 세밀화한다고 볼 수 있음

## `Hyperparameters`

- `Convolution`: Filter 수, Filter 사이즈
- `Pooling`: Window size, Window stride (window 이동시 몇 pixel 이동할건지를 결정)
- `Fully Connected Layer`: Layer 수, Neuron 수

## `Architecture`
- 높은 성능이 나올 수 있도록 앞의 Hyperparameter 값 혹은 순서가 정해져 있는 모델들 (프레임워크와 비슷한 개념?)
  
- AlexNet
- VGGNet: 3x3 conv 필터만 사용 가능, deep한 layer 쌓음
- GoogLeNet
- ResNet: layer를 필요할 때는 skip 할 수 있도록 skip connection 기능이 있음 > layer 수가 많아져도 학습 성능이 좋아지지 않는 단점 개선

# `RNN`의 원리

## `RNN` 이란?
- sequence data에 특화된 형태
  
- 동일한 function을 반복적으로 호출한다는 특징이 있음

- 입력신호가 시간에 따라 변화하는 입력이 순차적으로 들어온다고 할 때, 현재 time step에서의 입력신호와 그 이전 time step에서의 입력신호로 계산한 output인 hidden state vector을 입력으로 받아서 현재 time step의 output인 current hidden state vector를 만들어줌

- 동일한 parameter를 가진 함수가 각 time step마다 수행됨

- 특정 time step에서의 output 예측? current hiddent state vector를 다시 입력으로 output layer에 전달하여 예측



## `seq2seq with Attention`

- `many to many`: 

- (ex) 기계 번역 > 입력과 출력이 모두 sequence인 경우: 영어 문장을 모두 입력 받고 마지막 단어가 비로소 입력 되었을 때, 한국어로 차례대로 번역

- `encoder`: 입력 모델

- `decoder`: 예측 모델에 사용

- 제약조건: sequence가 길어질 때 정보가 유실되는 단점이 있음 (vector가 항상 동일해야 output에 다시 넣을 수 있음)

- `Attention`: enoder에서 나온 여러 hidden state vector를 가져다가 쓴다가 핵심 (원래는 마지막 time step의 hidden state vector만 사용)

## `Transformer`

- `seq2seq with Attention`의 개선판

- `self-attention`: RNN, CNN 없이 attention module이 encorder와 decoder를 처리한다.

- 기존 RNN, CNN의 경우 long-term dependency issue: 정보소실의 이슈가 있었음

