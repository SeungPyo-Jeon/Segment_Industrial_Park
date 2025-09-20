# Custom Unet3+
## 데이터 전처리
   광센서 값을 갖는 Uint16 raw data ( R, G, B, NIR )  
   ➞ 백분위 2, 98 값을 기준으로 MinMax scaling을 거쳐 0~255로 범위 지정. 4채널을 가진 이미지로 다루기 위함  
   
## 모델 구조
<div class="pull-left">
   <img width="600" height="400" alt="Image" src="https://github.com/user-attachments/assets/f667f3b0-6b20-4d91-9ee8-901f6e90f866" />
</div>
<div class="pull-right">
    - 4번의 down sampling ➞ up sampling  
   Unet3+[1] 구조 차용하여 피라미드 형식의 dense feature map을 얻고, 이것을 5단계에 걸쳐 global에서 local로의 feature 참조하며 up scaling해 모델이 넓은 receptive field를 반영할 수 있게 함

- Skip Connection 사용  
   얻은 피라미드 feature map을 공간 정보 보존과 효율적으로 전달하기 용이함

- Elementwise Convolution 사용  
   위성이미지의 다밴드 특성을 효과적으로 활용할 수 있고, 계산복잡도를 줄여줄 수 있음
      
 Params: 116,147,297 (0.1B)  
</div>

