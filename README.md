# yangjeon
딥러닝 기반 야간 CCTV 동영상 번호판 빛번짐, 블러를 복원하여 번호판 식별률(OCR) 향상 시스템

## 기술 스택

<p>
  
* YOLOv11 - CCRV 영상 번호판 인식 및 크롭

* Deblur-GAN - 노이즈 있는 번호판 복원

* PaddleOCR - 복원된 번호판 글자 추출
</p>

## 핵심 기능
* **yolo11 학습(yolo11_learning.py)**

  YOLO11 학습된 모델을 불러온 후 데이터셋을 코랩에 다운하여 번호판만 읽는 모델로 학습

  학습 후 가중치 파일은 best.pt, last.pt로 추출되는데 last.pt를 불러와서 추가적인 파인튜닝 가능

* **Deblur-GAN(deblur_gan_learning.py)**

  Deblurgan-v2를 기반으로 만든 신경망을 AI hub에서 다운 받은 데이터를 이용하여 학습

* **모델을 영상에 적용후 OCR로 문자 추출(restoration_detect.py)**

  코랩 드라이브 마운트 후 추출된 가중치 파일에 맞게 파일 위치를 수정하여 사용하면 YOLO로 동영상의 번호판 크롭 후

  Deblur-GAN 적용하여 이미지 복원함 이후 복원 된 이미지에서 OCR이 글자를 추출하여 이미지에 띄움


## dataset
  handmade_labeling - 직접 밤에 핸드폰으로 영상 찍은 거에 번호판과 번호판 글자를 라벨링한 이미지를 증강한게 위치
  
  record_car_plate - 실제 테스트 용 데이터와 영상 원본이 위치


----------
| 데이터셋 이름 | 출처 | 비고 |
| :--- | :--- | :--- |
| **Korea Carplate** | [Roboflow Universe](https://universe.roboflow.com/school-2whgn/korea-carplate) | 한국 자동차 번호판 데이터 |
| **License Plates Data** | [Kaggle Dataset](https://www.kaggle.com/datasets/zakirkhanaleemi/licence-plates-data) | 글로벌 번호판 데이터 |
| **저조도 환경 데이터** | [AI Hub](https://www.aihub.or.kr/aihubdata/data/view.do?pageIndex=1&currMenu=115&topMenu=100&srchOptnCnd=OPTNCND001&searchKeyword=%EC%A0%80%EC%A1%B0%EB%8F%84&srchDetailCnd=DETAILCND001&srchOrder=ORDER001&srchPagePer=20&aihubDataSe=data&dataSetSn=71377) | 야간 및 어두운 환경 이미지 |

## 중간 데모 영상
[![캡스톤디자인 양전했조 시연영상](https://img.youtube.com/vi/7O4k7P8yFiM/0.jpg)]([https://www.youtube.com/watch?v=2CczlAQ-CCU])


## 최종 데모 영상
[![캡스톤디자인 최종발표 시연](https://img.youtube.com/vi/JYj50BlnDSM/0.jpg)]([https://www.youtube.com/watch?v=JYj50BlnDSM])
