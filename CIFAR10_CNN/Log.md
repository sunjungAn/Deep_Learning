
# Log

### ver 1 
+ Dropout, Data augmentation, Weight initialization, Data Normalization, Adam optimizer 적용
+ Result Accr : 21

### ver 2
+ Data augmentation, Weight initialization, Data Normalization, Adam optimizer, Batch 적용
+ Batch normalization은 dropout과 함께 사용하면 결과가 좋지 않을 수 있어서 dropout제외 
+ Result Accr : 25
+ 
### ver 3
+ epoch당 validation 세트의 정확도 그래프로 plot시켜 가장 정확도가 높은 epoch 탐색
+ 8epoch에서 29까지 찍었다가 다시 감소 
+ Result Accr : 29

![image](https://user-images.githubusercontent.com/55094745/117323616-04acea80-aeca-11eb-8759-7f62e959f371.png)


### ver 4 
+ ver 3의 연장선으로 learning decay를 포함시킴
+ 
