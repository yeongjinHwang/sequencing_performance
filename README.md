
# 📊 **Sequencing Performance**

### 📝 프로젝트 설명
이 프로젝트는 **Mediapipe**를 활용한 비디오 처리 및 앙상블 모델링을 통해 시퀀싱(sequencing) 성능을 분석하고 향상시키는 데 중점을 둡니다.  
각 프레임별로 추출된 데이터를 처리하고, 다양한 복잡도(Complexity) 모델을 비교하여 **PCK (Percentage of Correct Keypoints)** 기준으로 정확도를 평가합니다.  
ground truth dataset은 저작권상 첨부하지 못합니다.  
sequencing 성능 비교는 IEEE : golfDB swingnet과 비교하며  
raw data 성능향상 비교는 AIHub에서 골프 스윙 데이터를 다운받아서 GT로 사용합니다.


주요 목표는 다음과 같습니다:
- **복잡도(Complexity) 수준별 성능 비교** (0, 1, 2)
- **Mediapipe 모델 앙상블 성능 확인**
- **시각화 및 성능 지표(PCK) 계산**
- **golf sequencing accuracy 성능비교**

---

## 📂 **프로젝트 파일 구조**
```
📦 sequencing_performance
 ┣ 📂 data
 ┃ ┣ 📂 complexity_data
 ┃ ┃ ┣ 📜 {video_name}_{complexity}.json
 ┃ ┃ ┗ Joint data by complexity json
 ┃ ┣ 📂 ground_truth
 ┃ ┃ ┣ 📂 merge_json
 ┃ ┃ ┃ ┣ 📜 {video_name}.json
 ┃ ┃ ┃ ┗ 📜 {video_name}_updated.json
 ┃ ┃ ┣ 📂 {video_name}
 ┃ ┃ ┃ ┣ 📜 {img_name}_{frame}.jpg
 ┃ ┃ ┃ ┣ 📜 {img_name}_{frame}.json
 ┃ ┃ ┣ 📂 {video_name2}
 ┃ ┃ ┃ ┣ 📜 {img_name2}_{frame}.jpg
 ┃ ┃ ┃ ┗ 📜 {img_name2}_{frame}.json
 ┃ ┗ 📂 result
 ┃ ┃ ┣ 📂 {video_name}
 ┃ ┃ ┃ ┣ 📜 joint_pck_comparison.png
 ┃ ┃ ┃ ┗ 📜 pck_results.json
 ┃ ┃ ┣ 📜 aggregated_joint_pck_comparison.png
 ┃ ┃ ┗ 📜 aggregated_pck_results.json
 ┗ 📜 performance.ipynb
```

---


## 📑 **주요 파일 및 설명**

1. **Complexity Data (`data/complexity_data`)**  
   - 각 영상(`{video_name}`)을 Mediapipe의 **complexity (0, 1, 2)** 설정으로 처리한 결과가 JSON 형식으로 저장됩니다.  
     예: `{video_name}_0.json`, `{video_name}_1.json`, `{video_name}_2.json`

2. **Ground Truth (`data/ground_truth`)**  
   - 각 영상의 **프레임별**로 JSON 및 이미지가 저장됩니다.  
     예: `{img_name}_{frame}.json`, `{img_name}_{frame}.jpg`

   - **Merge JSON (`merge_json`)**:  
     개별 프레임에서 추출한 JSON을 **합쳐 하나의 JSON**으로 만듭니다.  
     예: `{video_name}.json`

3. **Result (`data/result`)**  
   - **joint_pck_comparison.png**: 영상의 Ground Truth와 예측값 간의 **PCK@0.2 그래프**입니다.  
   - **pck_results.json**: 각 영상의 **PCK@0.2 계산 결과**가 JSON으로 저장됩니다.  
   - **aggregated_joint_pck_comparison.png**: 모든 영상의 PCK 그래프 평균.  
   - **aggregated_pck_results.json**: 모든 영상의 PCK 결과의 평균.

4. **`performance.ipynb`**  
   - 전체 데이터 처리 및 분석을 수행하는 **메인 소스 코드**입니다.  
   - Ground Truth 데이터 외의 모든 처리(png, json)가 이곳에서 이루어집니다.

---

## 🛠 **사용 방법**

1. **ground truth json 병합**
   - widget에 첫 frame, 마지막 frame json 2개를 선택하면 됩니다.

2. **복잡도 수준별 Mediapipe 결과 생성**
   - 각 영상을 `complexity_data`에 맞게 0, 1, 2 설정으로 처리한 JSON을 생성합니다.

3. **Ground Truth와 예측 비교**
   - 각 프레임의 예측값과 Ground Truth를 비교한 후, PCK@0.2를 계산합니다.

3. **PCK 그래프 및 요약 데이터 생성**
   - `result` 폴더에 각 영상의 PCK 그래프와 결과를 저장합니다.
   - 모든 영상을 종합한 평균 그래프 및 JSON을 생성합니다.

---

## 🔄 **확장 가능성**
- ground truth 데이터는 계속해서 추가될 수 있습니다. 
- **Complexity 수준 및 성능 모델**을 조정하여 더 나은 성능을 실험할 수 있습니다.
- 앙상블 모델을 활용해 **sequential accuracy**를 향상시킬 수 있습니다.

---

## 📌 **프로젝트 목표**
- Mediapipe를 활용한 **시퀀싱 정확도 향상**과 **복잡도 수준 비교**.
- 다양한 성능 지표를 도출하고 이를 **PCK@0.2**로 평가.
- 앙상블 모델링을 통해 **raw data**의 성능 최적화.

---

## 📧 **문의**
해당 프로젝트와 관련된 문의는 아래 이메일로 연락해 주세요:  
**yeongjin.gongjin@gmail.com**

---
