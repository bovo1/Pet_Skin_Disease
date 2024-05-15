# Pet_Skin_Disease 2024-02-06 ~ 

#### 데이터: AIhub 반려동물 피부 질환 데이터셋  
#### 훈련모델: YOLOv8-segment-large  

![labels](https://github.com/bovo1/Pet_Skin_Disease/assets/110110403/dde859f5-852c-4249-b621-a6f0c0089299)
![labels_correlogram](https://github.com/bovo1/Pet_Skin_Disease/assets/110110403/ec6be181-ce66-4496-9865-39e7a751f84c)
![images](https://github.com/bovo1/Pet_Skin_Disease/assets/110110403/4ba90f8c-1772-45fa-87ee-501203b8453c)

#### 결과
데이터의 특성 상 훈련에 필요한 부위만 crop 해서 복잡성을 줄이는 데이터 전처리를 했습니다.  
![confusion_matrix_normalized (1)](https://github.com/bovo1/Pet_Skin_Disease/assets/110110403/65402bf1-4a4e-4dbb-9c86-1cf236a7adc9)  
![BoxF1_curve](https://github.com/bovo1/Pet_Skin_Disease/assets/110110403/0eaf26d9-1a09-450c-a103-a1fd2facca44)

데이터는 총 17005장입니다.  

그렇게 되면 대부분의 클래스의 질환 탐지 확률이 90%가 되지 않을까 싶습니다.  
T4, A100 GPU로 도합 750 epoch 정도 훈련했습니다.  
중간에 데이터를 추가해서 ovefitting을 피했으나 데이터의 특성(털, disease 증상 부위에서 Feature 뽑기 힘듬) 상 다시 overfitting이 생겨서 훈련은 여기서 종료하기로 했습니다.  

A2 클래스를 포함하여 몇몇 클래스는 질환의 정도가 심하지 않는 이상 일반인의 눈으로 질환을 판단하기가 어렵습니다.  
피부에 병변이 생겨 질환 부위의 색이 다르다던가의 확실한 특징이 없는 경우에 특징 추출을 하기 어렵습니다.  
최대한 질환 부위를 집중적으로 학습하기 위해서 데이터의 사이즈를 줄였지만 역부족이네요.  
아마 다음에 다시 재도전을 할 때에는 문제가 되는 클래스를 제거한 다음 더 많은 학습을 할 것 같습니다.  
