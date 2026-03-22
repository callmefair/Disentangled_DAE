# Disentangled_DAE

## Orthogonal Regularization 기반의 Disentangled 추천 시스템

본 프로젝트는 Latent Vector의 각 차원이 독립적인 의미를 갖도록 설계하여 추천 시스템의 해석력을 높이고, 
이를 기반으로 Deep Clustering을 구현하여 성능을 분석한 연구이다.

## 제안 기법
- **직교 정규화(Orthogonal Regularization)**: Weight Matrix의 수직성을 강제하여 Disentanglement를 통한 특징 간 독립성 확보
- **Denoising AutoEncoder(DAE)**: 노이즈 복원을 통해 Latent Vector 수직성 강화 기대
- **Deep Clustering**: 축이 분리된 Latent Vector를 활용한 user/item 군집화 및 비교 분석

## 결과
- Latent Vector 차원의 직교성 오차가 거의 0.000000에 수렴함을 확인
- 유사도 기반 추천은 유의미하게 작동하나 복원에 치중된 AE 특성상 평가지표는 개선 여지가 확인됨
- 음원의 직접적인 특징 데이터 없이도 Latent Vector만으로 클러스터링을 성공적으로 수행

## 한계점 및 특이사항
- Epoch 진행 중 반복적으로 큰 간격으로 Loss가 폭발한 뒤 다시 자정 작용을 거쳐 축소되는 현상 관찰
- csr-matrix를 통해 메모리 문제를 해결했으나, 데이터가 sparse할 때 AutoEncoder의 성능 저하로 인해 SVD 등 다른 모델 연동 고려
