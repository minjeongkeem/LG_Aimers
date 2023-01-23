## `CNN`

- Convolution 연산을 통해 이미지로부터 필요한 특질(feature)을 스스로 학습할 수 있는 능력을 갖춘 심층 신경망 구조

- 컬러 이미지는 3차원의 Tensor로 표현됨 : Width X Height X 3 (RGB)

- 문제점 발생: 모든 픽셀을 서로 다른 가중치로 연결하게 되면 Input layer 와 First hidden layer 사이에 너무 많은 weights가 발생함

- 따라서 `Filter, Kernel`을 통하여 `Pooling`함 (사이즈를 줄인다)

    * `Filter, Kernel`: 특정 속성을 탐지하는데 사용하는 matrix
    * `Pooling`: 고차원의 Tensor를 보다 Compact하게 축약하는 역할 (`Max pooling`, `Average pooling`)

- 이미지 데이터의 특징:
  - 인접 픽셀 간 상관관계가 높음 (`spatially local correlation`)
  - 이미지의 부분적 특성은(ex) 사람의 눈, 코 고정된 위치에 등장하지 않는다 (`feature invariance`)

- 합성곱 연산 (convolution)

- Sparse connection: 인접한 픽셀만 가중치로 연결하여 연산 수행

- Shared Weight: 동일한 Filter는 대상 영역에 상관없이 같은 가중치를 사용하여 연산 수행

- CNN의 작동 과정: Convolution > Activation > Pooling > Flatten

- `Stride`: Filter가 한번에 여러칸을 이동할 수 있도록 허용

- `Padding`: 가장자리에 있는 픽셀들은 중앙에 있는 픽셀에 비해 Convolution 연산이 적게 수행되므로 가장 바깥 테두리에 0의 값을 갖는 pad 추가

- `Activation`: Convolution을 통해 학습된 값들의 비선형 변환을 수행 (ex) ReLU

-`Flatten`: 2~3차원의 Matrix, Tensor 구조를 1차원의 Vector로 변환 (그래야 output 산출 가능)

## 대표 CNN 구조

- `AlexNet`
  - 224 *224 크기 이미지를 input으로 사용
  - 초기 단계에는 큰 필터 사이즈와 Stride를 사용 (넓고 대충 보자)
  - 상위 Layer로 갈수록 작은 필터 사이즈와 Stride 사용(세밀히 보자)
  

- `VGGNet`
  - AlexNet에 비해 단순하지만 깊은 구조
  - 3 by 3 convolution with stride 1을 기본 연산으로 하며 중간 중간에 2 by 2 max polling 을 수행 (정해져 있음)


## CNN for Time-Series Data

- 기본 가정: 모든 변수는 동일한 주기 (초, 분, 시 등)로 수집된다.

- 대표 Task
  - Classification (ex) 제품의 양/불 판정 (`특정 범주`출력)
  - Regression
    - 1) 특정 기간 데이터를 input으로 하고 `특정 수치`(품질 지표)를 출력으로 하는 회귀 모델
    - 2) 일부 기간 데이터를 input으로 하고 `이후 기간` 데이터 예측
  - Anomaly Detection: 일부 기간 데이터를 input으로 하여 해당 상황의 `정상/비정상` 여부 탐지

- `1-D Convolution`
  - 시계열 데이터는 이미지 데이터와 달리 변수들 간 Spatial Correlation이 존재 X
  - 시간 축으로 움직이는 Convolution이 의미가 있음 > 모든 변수를 한번에 고려하여 시간 축에 대해서만 Convolution 연산을 수행 (필터 크기가 정사각형이 아니다)
  - 1 개의 Filter 를 사용하면 1 개의 vector 가 결과물로 산출됨

- `2-D Convolution`
 - 시간과 변수 두 축을 모두 Convolution 연산을 통해 탐색하는 방식

- `Dilated Convolution`
 - Standard Convolution 은 항상 인접한 연속된 시점의 데이터에 대한 합성곱 연산을 수행
 - 합성곱 연산을 띄엄띄엄 진행하는 것 > 원하는 과거 시점 몇개만 골라서 합성곱 연산 가능

- 보다 긴 길이의 시계열 데이터를 한번에 처리하기 위해서는 Standard Convolution 보다는 중간 지점을 생략하는 Dilated Convolution 을 사용하면 보다 효율적인 정보의 처리가 가능