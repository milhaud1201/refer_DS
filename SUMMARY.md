### Vectorization의 잠재점 이점은?
코드 실행 속도가 빨라지고, 코드를 더 짧게 만들어주거나, 병렬 컴퓨팅 하드웨어에서 코드를 보다 쉽게 샐행할 수 있습니다.

### Feature scaling의 유용한 단계 (데이터 정규화, 표준화)
 * Feature scaling $x_1=\frac{x_1}{max}$
   * 각 값을 해당 값의 최대값으로 나눈다.
 * Mean normalization $x_1=\frac{x_1-\mu_1}{max-min}$
 * Z-score normalization $x_1=\frac{x_1-\mu_1}{σ_1}$

### Overfitting이란?

과적합은 너무 적은 예제에 노출된 모델이 새로운 데이터에 일반화되지 않는 패턴을 학습할 때, **즉 모델이 예측을 위해 관련 없는 기능을 사용하기 시작할 때 발생합니다.**  
Overfitting happens when a model exposed to too few examples learns patterns that do not generalize to new data, i.e. when the model starts using irrelevant features for making predictions.

### Dropout이란?

**Over-specialization 및 Overfitting을 방지하여 네트워크를 보다 효율적으로 만들기 위해 드롭아웃을 하용하여 정규화(이상현상을 없애는 과정)를 합니다.**  
드롭아웃은 신경망에서 무작위로 많은 뉴런을 제거하는 아이디어에서 나왔습니다. 두 가지 이유로 잘 작동합니다. 첫번째는 인접한 뉴런이 종종 비슷한 가중치를 가지게 되고, 이것은 과적합으로 이어질 수 있기 때문에, 무작위로 일부를 떨어뜨리면 과적합을 제거할 수 있습니다. 두번째는 종종 뉴런이 이전 레이어에 있는 뉴런의 입력을 과대평가 over-weigh 할 수 있고 결과적으로 과도하게 전문화될 수 있다는 것입니다. 그러므로 드롭아웃은 이 잠재적은 나쁜 습관으로부터 신경망을 벗어날 수 있게 합니다.  
The idea behind it is to remove a random number of neurons in your neural network. This works very well for two reasons: The first is that neighboring neurons often end up with similar weights, which can lead to overfitting, so dropping some out at random can remove this. The second is that often a neuron can over-weigh the input from a neuron in the previous layer, and can over specialize as a result. Thus, dropping out can break the neural network out of this potential bad habit!  
Check out Andrew's terrific video explaining dropouts here: https://www.youtube.com/watch?v=ARq74QuavAo

### Transfer Learning이란?

사전 훈련된 모델을 사용하여 소규모 train dataset으로도 좋은 결과를 얻을 수 있는 방법입니다. 기존 모델의 훈련된 레이어를 활용하고 **자신의 애플리케이션에 맞게 자신의 레이어를 추가하여 수행**할 수 있습니다.  
예를 들어, 다음과 같이 수행할 수 있습니다:  
1. 한 모델의 컨볼루션 레이어만 가져옵니다.
2. 그 위에 몇 개의 dense 레이어를 붙입니다.
3. dense 네트워크만 훈련시킵니다.
4. 결과를 평가합니다.

이렇게 하면 학습 시간을 매우 단축시키고 자신의 데이터셋에 맞게 조정할 수 있습니다.  

you can use a pre-trained model to achieve good results even with a small training dataset. This is called transfer learning and you do this by leveraging the trained layers of an existing model and adding your own layers to fit your application. For example, you can:  
1. just get the convolution layers of one model
2. attach some dense layers onto it
3. train just the dense network
4. evaluate the results  

Doing this will allow you to save time building your application because you will essentially skip weeks of training time of very deep networks. You will just use the features it has learned and tweak it for your dataset. 

For more on how to freeze/lock layers, you can explore the [documentation here.](https://www.tensorflow.org/tutorials/images/transfer_learning?hl=ko)
