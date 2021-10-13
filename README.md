# POSCO AI / Big Data Academy AI Project by B2

![스크린샷 2021-10-13 오후 2 58 52](https://user-images.githubusercontent.com/45709140/137075583-d78e60d0-fd28-4ecd-a128-a785015bc298.png)

## 자율주행 차량을 이용한 드론 배송 서비스
자율주행 택배차량이 배송지 근처에 도착하면 드론으로 분산 배송하는 시스템
### 선행 연구
#### Pixhawk
#### YOLO (You Only Look Once)

## 동작 및 기능 설명

![스크린샷 2021-10-13 오후 2 56 44](https://user-images.githubusercontent.com/45709140/137075343-5304ffac-df57-4fcb-b99f-09992f4fa2a5.png)
)

* 자율주행 차량을 이용하여 택배를 대량으로 분산 배송하고, 필요 시 배터리를 충전하여 장시간 운송이 가능케 하는 드론 택배 배송 시스템 구축
* 차량이 Face Detection 기능을 통해 관리자를 인식하면 목적지(배송지)를 향해 출발
* 목적지 근처에 도착하면 SERVER에게 도착 신호 전송
* SERVER에서는 드론에게 비행 신호를 전송하고, 드론은 목적지로 택배를 가지고 이동
* 드론은 착륙 시에는 Home Point를 Object Detection을 통해 인식하고 이동거리를 계산하여 정확한 지점에 착륙함

![스크린샷 2021-10-13 오후 2 57 24](https://user-images.githubusercontent.com/45709140/137075419-eadf673d-9e89-49c2-aab6-498e1008d80f.png)
)

* 드론이 다시 차량으로 복귀할 때는 차량에 있는 충전 스테이션 위에 안착하여 짧은 비행 시간이라는 한계점을 극복함
* 원 위치로 복귀할 때에도 Home Point를 Object Detection을 통해 인식하여 착륙

## System Architecture

![스크린샷 2021-10-13 오후 2 53 13](https://user-images.githubusercontent.com/45709140/137075235-09124e3b-0c16-44dc-8800-cb2c1e6f7824.png)

## 사용 도구 및 구축 환경

#### 서버 - Workstation
Python 3.6
Module
import socket (파이썬 내장 소켓 통신 모듈)
import subprocess (파이썬에서 외부 파일 실행시키기)
import Threading (파이썬 내장 쓰레드 모듈)

#### 드론 - 휴스타 2기 드론 이용

- HW
jetson nano
Pixhawk4
Intel RealSense D450
Drone

- SW
Python 3.6.2
Jet Pack 4.5 (jetson nano OS + CUDA + CuDNN 등)
YOLO v5
MAVSDK (드론 MAVLink 라이브러리)
pyrealsense2 (카메라 파이썬 라이브러리)
QGroundControl
Gazebo

#### 차량 - 13기 포틀리, 포미니 이용

- HW
Raspberry pi4
Logitech Webcam
DC Motor * 4

- SW
Python 3.6
CNN (Face Detection)

## Reference
이지원, 이동진, 장성진, 최동규, & 장종욱. (2021). 최적화된 차량 탑승인원 감지시스템 개발을 위한 딥러닝 모델 분석. 한국정보통신학회논문지, 25(1), 146-151.
Bae, J.-W., & Lee, S.-J. (2019). LTE/WiFi 기반 소형 무인기용 영상 전송 시스템 개발. 항공우주시스템공학회지, 13(2), 10–18.
Kang, B. H. (2019). LTE 통신을 이용한 실시간 원격주행 드론 시스템. 한국인터넷방송통신학회논문지, 19(6), 35–40.
Choi, J.-W., Hwang, D.-K., An, J.-W., & Lee, J.-M. (2019). Object Detection Using CNN for Automatic Landing of drones. Journal of the Institute of Electronics and Information Engineers, 56(5), 82–90.
