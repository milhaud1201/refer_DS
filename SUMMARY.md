## Vectorization의 잠재점 이점은?
코드 실행 속도가 빨라지고, 코드를 더 짧게 만들어주거나, 병렬 컴퓨팅 하드웨어에서 코드를 보다 쉽게 샐행할 수 있습니다.

## Feature scaling의 유용한 단계 (데이터 정규화, 표준화)
 * Feature scaling $x_1=\frac{x_1}{max}$
   * 각 값을 해당 값의 최대값으로 나눈다.
 * Mean normalization $x_1=\frac{x_1-\mu_1}{max-min}$
 * Z-score normalization $x_1=\frac{x_1-\mu_1}{σ_1}$

## Gradient Descent With Multiple Variables란?
여러 변수를 위한 경사 하강법에 대한 방정식입니다.:

$$\begin{align*} \text{repeat}&\text{ until convergence:} \; \lbrace \newline\;
& w_j := w_j -  \alpha \frac{\partial J(\mathbf{w},b)}{\partial w_j}   \; & \text{for j = 0..n-1}\newline
&b\ \ := b -  \alpha \frac{\partial J(\mathbf{w},b)}{\partial b}  \newline \rbrace
\end{align*}$$
objective: $min_{\vec w, b}J(\vec w, b)$$  

경사하강법은 매개변수 $w$를 찾는 것이고 $b$는 비용함수 $J$를 최소화합니다.  
여기서 $n$은 동시에 업데이트되는 $w_j$,  $b$ 파라미터와 피처의 수 입니다.  

$$\begin{align}
\frac{\partial J(\mathbf{w},b)}{\partial w_j}  &= \frac{1}{m} \sum\limits_{i = 0}^{m-1} (f_{\mathbf{w},b}(\mathbf{x}^{(i)}) - y^{(i)})x_{j}^{(i)}   \\
\frac{\partial J(\mathbf{w},b)}{\partial b}  &= \frac{1}{m} \sum\limits_{i = 0}^{m-1} (f_{\mathbf{w},b}(\mathbf{x}^{(i)}) - y^{(i)}) 
\end{align}$$

* $m$ is the number of training examples in the data set
*  $f_{\mathbf{w},b}(\mathbf{x}^{(i)})$ is the model's prediction, while $y^{(i)}$ is the target value


## 수렴을 위한 Gradient descent 확인
100, 200의 interations 후에 업데이트 된 비용 함수 $J(\vec w, b)$ 의 learning curve를 확인합니다. 경사하강법이 제대로 작동한다면, 비용 함수 J는 감소하거나 수렴합니다.

## Learning rate $\alpha$란? 
Learning rate는 파라미터에 대한 **업데이트 크기를 제어**합니다.  
The learning rate controls the size of the update to the parameters.

### $\alpha$ = 9.9e-7 너무 높을 때
학습률이 너무 높으면 해가 수렴하지 않아 Cost가 계속 증가합니다.
![image](https://user-images.githubusercontent.com/108461149/230441141-5376f586-b16e-4a30-a4e0-8f83417192f7.png)  
반복할 때마다 최적의 값을 초과하고 결과적으로 비용이 최소값에 도달하지 않고 증가 overshooting 합니다.
### $\alpha$ = 9e-7 적당할 때
![image](https://user-images.githubusercontent.com/108461149/230444412-4bc2dd84-6c00-4095-b5fd-5e77927529ce.png)  
최소값에서 머물고 있지만 각 반복이 증가하는 것이 아니라 감소합니다. 반복하며 알파값을 수렴합니다.
### $\alpha$ = 1e-7 너무 작을 때
![image](https://user-images.githubusercontent.com/108461149/230444659-90ebe8a1-9e36-4f88-8509-825b0d8aedec.png)  
이 솔루션도 이전 그래프만큼 빠르지는 않지만 결국 수렴됩니다.

## Overfitting이란?

과적합은 너무 적은 예제에 노출된 모델이 새로운 데이터에 일반화되지 않는 패턴을 학습할 때, **즉 모델이 예측을 위해 관련 없는 기능을 사용하기 시작할 때 발생합니다.**  

Overfitting happens when a model exposed to too few examples learns patterns that do not generalize to new data, i.e. when the model starts using irrelevant features for making predictions.

## Dropout이란?

**Over-specialization 및 Overfitting을 방지하여 네트워크를 보다 효율적으로 만들기 위해 드롭아웃을 하용하여 정규화(이상현상을 없애는 과정)를 합니다.** 드롭아웃은 신경망에서 무작위로 많은 뉴런을 제거하는 아이디어에서 나왔습니다. 두 가지 이유로 잘 작동합니다. 첫번째는 인접한 뉴런이 종종 비슷한 가중치를 가지게 되고, 이것은 과적합으로 이어질 수 있기 때문에, 무작위로 일부를 떨어뜨리면 과적합을 제거할 수 있습니다. 두번째는 종종 뉴런이 이전 레이어에 있는 뉴런의 입력을 과대평가 over-weigh 할 수 있고 결과적으로 과도하게 전문화될 수 있다는 것입니다. 그러므로 드롭아웃은 이 잠재적은 나쁜 습관으로부터 신경망을 벗어날 수 있게 합니다.  

The idea behind it is to remove a random number of neurons in your neural network. This works very well for two reasons: The first is that neighboring neurons often end up with similar weights, which can lead to overfitting, so dropping some out at random can remove this. The second is that often a neuron can over-weigh the input from a neuron in the previous layer, and can over specialize as a result. Thus, dropping out can break the neural network out of this potential bad habit!  
Check out Andrew's terrific video explaining dropouts here: https://www.youtube.com/watch?v=ARq74QuavAo

## Transfer Learning이란?

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
