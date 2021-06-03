# [CNN]Convolution neural network(1)

> (이 게시물은 Hands-On Machine Learning with Scikit-Learn, Keras & TensorFlow (오렐리앙 제롱 지음, 박해선 옮김) 의 책을 참고하여 작성한 글입니다.)  
> 위 책의 p542~p559의 내용을 담고 있습니다. 
​
주제 : 합성곱 신경망에서 합성곱 층, 풀링층 구성 요소에 대해서 설명합니다.
​
---
​
### 합성곱 층 
​
네트워크가 첫 번째 은닉층에서는 작은 저수준 특성에 집중하고, 그 다음 은닉층에서는 더 큰 고수준 특성으로 조합해나가도록 도와준다. 
​
![image](https://user-images.githubusercontent.com/55094745/120574903-15199c00-c45b-11eb-936f-fcd2038d801a.png)
​
**스트라이드 **
​
-   한 수용장과 다음 수용장 사이의 간격
-   모델의 계산 복잡도를 크게 낮춰줌
-   큰 입력층을 훨씬 작은 층에 연결하는 것이 가능
​
![image](https://user-images.githubusercontent.com/55094745/120574944-29f62f80-c45b-11eb-81fb-1830ce4a153d.png)
​
**필터(합성곱 커널)**
​
-   층의 전체 뉴런에 적용된 하나의 필터는 하나의 특성맵을 만든다.
​
![image](https://user-images.githubusercontent.com/55094745/120574991-3ed2c300-c45b-11eb-8411-c3a9e23873ed.png)
​
**특성맵**
​
-   필터를 가장 크게 활성화시키는 이미지의 영역을 강조한다.
-   훈련하는 동안 합성곱 층이 자동으로 해당 문제에 가장 유용한 필터를 찾고 상위층은 이들을 연결하여 더 복잡한 패턴을 학습한다.
-   각 특성 맵의 픽셀은 하나의 뉴런에 해당한다.
-   하나의 특성 맵에 있는 모든 뉴련이 같은 파라미터를 공유한다. --> 모델 전체 파라미터의 수를 줄여준다.
​
입력 이미지는 컬러 채널 마다 하나씩 여러 서브 층으로 구성되기도 한다. 
​
CNN은 '위치 불변성' 특징이 있어 어느 위치에 있던 패턴을 인식할 수 있다. 반면에 DNN은 학습된 그 위치에서만 감지할 수 있다. 
​
![image](https://user-images.githubusercontent.com/55094745/120575023-498d5800-c45b-11eb-8431-0907465014e7.png)

​
### keras.layers.Conv2D
​
```
conv = keras.layers.Conv2D(filters = 32, kernel_size = 3, strides = 1, padding="same", activation= "relu")
```
​
-   3x3 크기의 필터 32개를 가짐
-   스트라이드 1
-   same패딩을 사용 (패딩이 valid면 패딩이 없음, same이면 제로 패딩)
-   출력을 위해 relu함수를 적용
​
### 메모리 요구 사항
​
\* 예시)
​
필터 : 5X5
​
스트라이드 : 1
​
패딩 : "same"
​
출력할 특성 맵 : 150 x 100의 특성 맵 200개를 만듬
​
입력: 150X100RGB
​
파라미터 수 : ((필터 \* 채널)+편향) \* 특성맵 개수 = ((5x5x3)+1)x200 = 15200
