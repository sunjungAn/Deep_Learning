## ver 1
+ 방법 : Dropout, Data augmentation, Weight initialization, Data Normalization, Adam 
optimizer 적용
+ 실습 4 장 참고하여 적용할 것을 선택, Drop out 과 Batch normalization 을 혼용하면
결과가 좋지 않을 수 있어서 먼저 Drop out 부터 적용함
+ Result Accr : 21

## ver 2
+ 방법 : Data augmentation, Weight initialization, Data Normalization, Adam optimizer, 
BatchNorm 적용
+ Batch normalization 은 dropout 과 함께 사용하면 결과가 좋지 않을 수 있어서
dropout 제외
+ Result Accr : 25

## ver 3
+ 방법 : ver 2 를 적용하여 epoch 당 정확도를 출력하여 가장 정확도가 높은 epoch 탐색
+ ver 2 가 ver 1 보다 좋은 정확도를 띄어 Batch normalization 채택
+ 8epoch 에서 29 까지 찍었다가 다시 감소
+ Result Accr : 29

## ver 4
+ 방법 : ver 3 의 연장선으로 learning decay 를 포함, Adam 대신 SGD 채택하여 가장 정확도가
높은 epoch 탐색
+ ver3 에서 높은 정확도가 나오지 않아 Adam 말고 SGD 를 선택하여 다시 재학습
+ epoch 를 계속 진행해 봐도 40epoch 까지 가는데도 accr 값이 20 대를 벗어나지 못해
학습 중지
+ Result Accr : 27

## ver 5
+ 방법 : ver4 에서 batch_size = 128 수정, 데이터 전처리 수정(padding = 4)
+ ver 4 의 결과를 바탕으로 epoch 수를 늘리는 것보다 데이터 처리, 학습 데이터 모양을
위주로 수정
+ epoch 40 정도부터 train 데이터에 과대적합
+ Result accr : 56

## ver 6
+ 방법: ver5 에서 learning_late = 0.01, SGD 의 파라미터( lr=0.01, momentum=0.9, 
weight_decay=5e-4)로 수정
+ 50 epoch 부터 과대적합이 발생
+ Result accr = 71

## ver 7
+ 방법: ver6 에서 마지막 fully connected 의 부분 Dropout 을 Batchnorm 으로 바꾸어 줌
+ 15 epoch 부터 과대적합이 발생
+ Result accr = 69

## ver 8 (최종본)
+ 방법: ver7 에서 batch_size = 32 로 조정, Data augmentation 제거, scheduler 제거,
BatchNorm 과 Dropout 동시 사용
+ Colab gpu 사용
+ 에포크 37 정도에서 78.08 이라는 정확도가 나옴
+ Result Accr : 78.08
