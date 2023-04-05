### Overfitting이란?

과적합은 너무 적은 예제에 노출된 모델이 새로운 데이터에 일반화되지 않는 패턴을 학습할 때, 즉 모델이 예측을 위해 관련 없는 기능을 사용하기 시작할 때 발생합니다.  
Overfitting happens when a model exposed to too few examples learns patterns that do not generalize to new data, i.e. when the model starts using irrelevant features for making predictions.

### Dropout이란?

드롭아웃은 신경망에서 무작위로 많은 뉴런을 제거하는 아이디어에서 나왔습니다. 두 가지 이유로 잘 작동합니다. 첫번째는 인접한 뉴런이 종종 비슷한 가중치를 가지게 되고, 이것은 과적합으로 이어질 수 있기 때문에, 무작위로 일부를 떨어뜨리면 과적합을 제거할 수 있습니다. 두번째는 종종 뉴런이 이전 레이어에 있는 뉴런의 입력을 과대평가 over-weigh 할 수 있고 결과적으로 과도하게 전문화될 수 있다는 것입니다. 그러므로 드롭아웃은 이 잠재적은 나쁜 습관으로부터 신경망을 벗어날 수 있게 합니다.  
The idea behind it is to remove a random number of neurons in your neural network. This works very well for two reasons: The first is that neighboring neurons often end up with similar weights, which can lead to overfitting, so dropping some out at random can remove this. The second is that often a neuron can over-weigh the input from a neuron in the previous layer, and can over specialize as a result. Thus, dropping out can break the neural network out of this potential bad habit!  
Check out Andrew's terrific video explaining dropouts here: https://www.youtube.com/watch?v=ARq74QuavAo
