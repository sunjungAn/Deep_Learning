
# Log
>> https://github.com/kuangliu/pytorch-cifar/blob/master/main.py

### ver 1 
+ **Dropout, Data augmentation, Weight initialization, Data Normalization, Adam optimizer 적용**
+ 실습 4장 참고하여 적용할 것을 선택, Drop out과 Batch normalization을 혼용하면 결과가 좋지 않을 수 있어서 먼저 Drop out부터 적용함
+ Result Accr : 21

### ver 2
+ **Data augmentation, Weight initialization, Data Normalization, Adam optimizer, Batch 적용**
+ Batch normalization은 dropout과 함께 사용하면 결과가 좋지 않을 수 있어서 dropout제외 
+ Result Accr : 25
+ 
### ver 3
+ **ver 2를 적용하여 epoch당 정확도를 출력하여 가장 정확도가 높은 epoch 탐색**
+ ver 2가 ver 1보다 좋은 정확도를 띄어 Batch normalization 채택 
+ 8epoch에서 29까지 찍었다가 다시 감소 
+ Result Accr : 29

![image](https://user-images.githubusercontent.com/55094745/117323616-04acea80-aeca-11eb-8759-7f62e959f371.png)


### ver 4 
+ **ver 3의 연장선으로 learning decay를 포함, Adam대신 SGD 채택하여 가장 정확도가 높은 epoch 탐색**
+ ver3에서 높은 정확도가 나오지 않아 Adam말고 SGD를 선택하여 다시 재학습
+ epoch를 계속 진행해 봐도 40epoch 까지 가는데도 accr 값이 20대를 벗어나지 못해 학습 중지

![image](https://user-images.githubusercontent.com/55094745/117397703-b1718100-af37-11eb-8241-8d1b15ba448b.png)


### ver 5
+ **batch_size = 128수정, 데이터 전처리 수정(padding = 4), epoch 125로 수정**
+ ver 4의 결과를 바탕으로 epoch 수를 늘리는 것보다 데이터 처리, 학습 데이터 모양을 위주로 수정
+ epoch 6정도 돌려봤을 때 꾸준히 accr가 높아져 epoch 125로 수정해 재학습
