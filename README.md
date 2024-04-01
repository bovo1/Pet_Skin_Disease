# Pet_Skin_Disease 2024-02-06 ~

#### 데이터: AIhub 반려동물 피부 질환 데이터셋  
#### 훈련모델: YOLOv8-segment-large  

![labels](https://github.com/bovo1/Pet_Skin_Disease/assets/110110403/dde859f5-852c-4249-b621-a6f0c0089299)
![labels_correlogram](https://github.com/bovo1/Pet_Skin_Disease/assets/110110403/ec6be181-ce66-4496-9865-39e7a751f84c)
![images](https://github.com/bovo1/Pet_Skin_Disease/assets/110110403/4ba90f8c-1772-45fa-87ee-501203b8453c)



### <2024.03.16 현재 업데이트 중>  

train dataset은 6006장이며 가장 최근 훈련은 250epoch에 loss 1.01 입니다.  
훈련전에 모델의 성능과 복잡성을 위해 이미지 전처리를 진행했으나 데이터의 특성(반려동물의 털에 묻혀 특징을 잡기가 어려운 피부질환, 반려동물마다 다른 털의 색, 길이 등)으로 훈련에 어려움이 있습니다.  
성능을 개선하기 위해서 여러 하이퍼파라미터를 과적합이 되지 않도록 조정하고 조정 후에도 개선이 잘 되지 않는다면 데이터를 추가 할 예정입니다.  
모델 훈련이 끝나고 원하는 성능을 보여준다면 AWS를 이용하여 웹 혹은 어플을 만들어 서비스화를 해보려고 합니다.  
2024.03.20 데이터를 추가해서 17,000개의 데이터로 추가했습니다.  

### <2024.03.29 중간 점검>  

Colab의 T4 GPU로 훈련 중에 있습니다.  
훈련에서 중요한 학습률을 비롯해서 여러 하이퍼파라미터의 적절한 값을 찾기가 어려웠습니다.  
YOLO에서 제공하는 tune 기능을 사용하면 되지만 resume 기능이 포함되어 있지 않았습니다.  
Colab은 24시간 런타임 제한이 있기 때문에 원하는 fitness를 찾기 전에 종료되어 사용할 수 없었습니다.  
그래서 loss, learning rate, metrics(recall, map 등)의 그래프를 보면서 수동으로 올바른 값을 찾을 수 있도록 하이퍼파라미터 조정을 반복하고 있습니다.  
값이 아주 조금만 틀리더라도 발산하거나 수렴하지 않는 상태가 되어 프로젝트의 진행상황이 느리네요.  
현재 100 epoch 정도 훈련하면서 거의 40epoch 동안 loss값이 1.8정도에 머물러 줄어들지도 늘어나지도 않는 상태입니다.  
머물러 있는 구간은 학습률 7.30E-05, batch 16 입니다.  
local minima에 빠진 것인지 아니면 모델이 학습을 못하고 있는 상태인지 체크하는 과정에 있습니다.  
학습 모델은 large 사이즈 모델로 작지 않은 모델입니다. 그래서 모델의 복잡도가 낮아서 생기는 문제일 확률은 상대적으로 낮다고 생각하고 있습니다.  
학습속도가 빠른편이 아니라 small, medium 사이즈 모델을 먼저 사용했었고 데이터의 instance를 잘 뽑아내지 못하는 것 같아서 large로 사용했습니다.  
학습이 잘 되고 있는 그래프 모양은 둥그런 ㄴ자 모양이지만 모델과 데이터에 따라 어려운 부분도 분명히 있네요.  

## 2024.03.29 모델의 중간 점검 결과는 다음과 같습니다.  
![confusion_matrix_normalized (1)](https://github.com/bovo1/Pet_Skin_Disease/assets/110110403/d4a43dff-7d49-4b6b-8e94-cc913b825bc2)
![BoxPR_curve](https://github.com/bovo1/Pet_Skin_Disease/assets/110110403/2df2af85-fa24-4171-a09b-4d4d8a41d9df)

