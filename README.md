# guition480_with_ld2450
guition 4'' display ESP32-S3-4848S040 with LD2450 sensor

### 재료
- guition 4'' display ESP32-S3-4848S040
- LD2450 sensor
- MX 1.25 4pin cable (https://ko.aliexpress.com/item/1005007277110532.html)

### 하드웨어
![20250404_100520](https://github.com/user-attachments/assets/110cf85d-78dd-4490-9936-346bdb5f3f59)

우측 상단에 1.25mm 4pin UART 포트가 존재함.
백패널과 연결포트에도 UART포트가 들어가는데 우측상단의 UART와 UART0핀을 공유하고있음 (GPIO 44, 43) 
백패널로 가는 uart는 저항이 없고, uart포트는 100옴 저항이 달려있음. 

![image](https://github.com/user-attachments/assets/eccc24ef-9188-4089-99c6-754f5f22a104)

100옴 저함 2개를 인두기로 제거후 납을묻혀 연결시켜야함.

![20250404_100418](https://github.com/user-attachments/assets/822efe3d-059b-403a-b36f-22f405a06086)

백패널의 Rx, Tx는 아무데도 연결되지 않은것으로보임.
따라서 4pin UART포트를 사용 가능함.

![image](https://github.com/user-attachments/assets/b6296e05-ef48-4c88-aae4-91ac7f33fd70)
포트 노출을 위해 뒷판을 잘라내야함. (사진 보다 깊게 잘라야 간섭이 없음)

### 어댑터 3D 프린터 출력
![image](https://github.com/user-attachments/assets/7cfcbe32-7a6a-458f-b7b9-c156670a34f7)
![프린팅파츠](https://github.com/wooooooooooook/guition480_with_ld2450/tree/main/printing%20parts)
프린팅 파츠에서 `cover.stl`, `plate.stl`을 출력.

### ESPHome 펌웨어 설치
벽면에 설치후에는 usb포트노출이 안되므로 최초 1회는 USB-C 연결해서 유선으로 펌웨어설치가 필요함.
이후에는 OTA로 업데이트가능. 
![configuration.yaml](https://github.com/wooooooooooook/guition480_with_ld2450/blob/main/esphome%20configuration/guition.yaml)
YAML을 참조하여 ESPHome 펌웨어 설치.

### 설치하기
![image](https://github.com/user-attachments/assets/748dec2e-e754-4aeb-88b1-2e5e764efeb9)

벽면에 사진과 같이 plate에 LD2450에 


