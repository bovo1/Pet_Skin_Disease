# Pet_Skin_Disease 2024-02-06 ~

데이터: AIhub 반려동물 피부 질환 데이터셋  
훈련모델: YOLOv8-segment-large  

2024.03.16 현재 업데이트 중  
train dataset은 6006장이며 가장 최근 훈련은 250epoch에 loss 1.01 입니다.  
훈련전에 모델의 성능과 복잡성을 위해 이미지 전처리를 진행했으나 데이터의 특성(반려동물의 털에 묻혀 특징을 잡기가 어려운 피부질환, 반려동물마다 다른 털의 색, 길이 등)으로 훈련에 어려움이 있습니다.  
성능을 개선하기 위해서 여러 하이퍼파라미터를 과적합이 되지 않도록 조정하고 조정 후에도 개선이 잘 되지 않는다면 데이터를 추가 할 예정입니다.  

모델 훈련이 끝나고 원하는 성능을 보여준다면 AWS를 이용하여 웹 혹은 어플을 만들어 서비스화를 해보려고 합니다.  
