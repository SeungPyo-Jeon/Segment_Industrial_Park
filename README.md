# Segment_Industrial_Park  
phase 1 250813-251015 
## Task & Performance matric
Aihub- [ 대기오염 배출원 공간 분포 데이터 ](https://www.aihub.or.kr/aihubdata/data/view.do?currMenu=115&topMenu=100&searchKeyword=%EB%8C%80%EA%B8%B0%EC%98%A4%EC%97%BC%20%EB%B0%B0%EC%B6%9C%EC%9B%90%20%EA%B3%B5%EA%B0%84%20%EB%B6%84%ED%8F%AC%20%EB%8D%B0%EC%9D%B4%ED%84%B0&aihubDataSe=data&dataSetSn=71805/) 의 산업단지 및 시가지 Sentinel-2 tif, 라벨링 데이터를 기반으로 진행되었습니다.
<img width="1200" height="400" alt="Image" src="https://github.com/user-attachments/assets/73f68035-c261-48a7-8e2c-93de3dd3cddb" /> 

평가지표: 모델 출력에 sigmoid 적용 후 threshold=0.5를 기준으로 MIoU 산정  
 
## Method - 효과적인 Mapping function 𝑓 를 찾기 위해서 
- 입력 이미지의 해상도는 10m로, 하나의10m2 영역이 4개의 값으로 측정됨
  산업단지는 대규모로 이뤄져 있기 때문에 여러 픽셀들이 모여 만들어지는 텍스쳐가 중요함  
   ➥ 주변 local signal부터 global한 signal을 모두 아우르는 receptive field 크기 필요할 것.
    
- 측정 센서와 지표면까지 사이의 여러 영향( 대기 조건, 광량 등 )에 의해 값이 변화될 수 있음
  ➞ 이미 보정이 이뤄진 Sentinel-2 위성 이미지임에도 완전한 제거가 불가능함  
   ➥ noisy value에 대해 흔들리지 않는 robustness
    
- 기존 전통적인 위성 이미지를 통한 분석에서 밴드간 조합이 중요했음 ( NDVI )  
   ➥ 4개의 밴드를 효과적으로 융합하여 특징을 추출할 수 있는 아키텍쳐  
