# Advanced Classification Model

-  ## `SVM`
   
-  `support vector`: postive sample (negative sample)과 hyper plane 사이에 가장 가까이에 있는 sample > 성능을 좌지우지 하는 민감한 data point

- `support vector` 간의 거리를 최소화 하는 `margin` 설정하는 전략

- `margin`: hyper plane과 가장 거리가 가까운 sv와의 거리 * 2

- `optimization`

- `hard margin svm`: linear하다는 것을 가정

- `soft margin svm`: 어느정도의 error를 용인

- `kernel 함수`: linearly sepable하지 않은 data sample들이 있다고 할 때, 그 차수를 높여 linearly sepable하게 만드는 과정

    **종류**
- `polynomial`
- `Gaussian radial basis function (RBF)`
- `Hyperbolic tangent` 

## `ANN` (Artificial Neural Network)

- nonlinear classification model

- `Activation function`
- `Sigmoid`: gradient 값이 점차 줄어드는 단점이 있음 
- `ReLU`: 미분해도 gradient값이 여전히 1임

- `multilayer perceptron`
- `xor`문제 풀 수 있음 

- `gradient vanishing problem` : 계층이 깊을 수록 gradient가 줄어들어 학습이 효과적이지 못함

- 이를 optimization하기 위한 행동을 `back propagation`이라고 함

## `CNN`
- cv 등에 많이 사용됨 




