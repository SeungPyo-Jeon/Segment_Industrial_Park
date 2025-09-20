## Custom Unet3+
<img width="1174" height="822" alt="Image" src="https://github.com/user-attachments/assets/29cd11f9-a451-48e0-9aa0-3d8415ab5701" />

4번의 down sampling ➞ up sampling
Unet3+[1] 구조 차용하여 피라미드 형식의 dense feature map을 얻고, 이것을 5단계에 걸쳐 global에서 local로의 feature 참조하며 up scaling해 모델이 넓은 receptive field를 반영할 수 있게 함

   Skip Connection 사용
얻은 피라미드 feature map을 공간 정보 보존과 효율적으로 전달하기 용이함

   Elementwise Convolution 사용
위성이미지의 다밴드 특성을 효과적으로 활용할 수 있고, 계산복잡도를 줄여줄 수 있음
      
 Params: 116,147,297 (0.1B)
<img width="2335" height="461" alt="image" src="https://github.com/user-attachments/assets/6349e206-6cd2-4fb9-9d9f-d555d90a03d9" />
