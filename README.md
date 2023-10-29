# 23-2_DSL_Modeling_CV_A
---
## 주제
YOLO v5m을 활용한 재활용 가능 페트병 분류: 라벨과 유색 여부를 중심으로
## Team A
신소연(팀장) 김현동 임창재 조세린
# Overview
modeling_CV_A_발표자료.pdf

## 1. Overall Pipeline
![image](https://github.com/shin810/23-2_modeling_CV_A/assets/98678786/2736dbc2-a85b-4dc9-9175-56bf8346b5d8)

## 2. Model
1. Problem & Solution
   ![image](https://github.com/shin810/23-2_modeling_CV_A/assets/98678786/aae3fe68-8f4c-4ce1-bea8-c92706fd3f74)
   - 일반 플라스틱과 페트병의 분리수거 배출 기준이 다름
   - 이를 구분해주는 모델의 필요성을 느낌
2. Data Detail
   ![image](https://github.com/shin810/23-2_modeling_CV_A/assets/98678786/c5087846-e49a-4d7d-878a-e13534e5ddfa)
   - 유색/라벨 유무로 총 4개의 클래스 생성
3. Data Preprocessing
   ![image](https://github.com/shin810/23-2_modeling_CV_A/assets/98678786/56d2598c-edc5-4d00-9dc9-abe6fa7e17de)
   - 직접 데이터를 수집 및 라벨링 작업 진행
   - Data Augmentation 진행
4. Model
   ![image](https://github.com/shin810/23-2_modeling_CV_A/assets/98678786/d14343c0-27c9-4715-9117-56bbce40555e) 
   - 모델: YOLO v5m
   - 선정이유: 높은 정확도, 경량화 모델, 빠른 속도의 탐지
   ![image](https://github.com/shin810/23-2_modeling_CV_A/assets/98678786/b7a1cb25-01f7-47c5-aabd-0ed8b2c909cf)
   ![image](https://github.com/shin810/23-2_modeling_CV_A/assets/98678786/4bc0411a-9bbd-4336-a084-a9f4b90d1520)
1. 입력 이미지 확인
2. S*S 그리드로 분할
3. 각 그리드마다 이미지 분류 및 Localize
4. 객체가 어디 있는지 확인하고, 식별해야 하는 객체에 Bounding Box 표시
5. Bounding Box와 각 개체의 클래스 확률을 통해 객체를 인식하고 예측

## 3. Dataset
https://drive.google.com/file/d/1YWcX5sHgdAWZgI7sthmgAP5wQO_Z_1u1/view?usp=drive_link

# Result
## 1. Final Output
성능 평가
![image](https://github.com/shin810/23-2_modeling_CV_A/assets/98678786/fb96b748-697f-4961-bf32-344f2bbe88ee)
![image](https://github.com/shin810/23-2_modeling_CV_A/assets/98678786/e53fb032-a62b-414b-801f-05f1574c1899)
![image](https://github.com/shin810/23-2_modeling_CV_A/assets/98678786/c61163dc-9017-46f4-9779-0cf925dc1536)

적용 예시
![image](https://github.com/shin810/23-2_modeling_CV_A/assets/98678786/0d2359e9-c9e2-4bbc-90e2-f8f4b7ea1bdd)
![image](https://github.com/shin810/23-2_modeling_CV_A/assets/98678786/92e1baf6-4ad8-4aa2-bd2f-0df970ed5cd3)

## 2. Limitations and Future works
![image](https://github.com/shin810/23-2_modeling_CV_A/assets/98678786/d0c3e8a2-e7ca-4387-babd-dd7343e9cc11)
- 쓰레기 종류별 인식 및 분류
- 페트병 속 내용물 유무 인식
- Segmentation으로의 확

# End-to-End
```


```

# File description
- ```train.py```
- ```val.py```
- ```detect.py```
- train.zip / test.zip / valid.zip
  : train / test / valid 이미지 데이터셋
- ```data.yaml```
- dataset: https://drive.google.com/open?id=1CDNNu1fjAoXkcsULOithIQEZSigQ4dlx&usp=drive_copy 에서 다운 가능
