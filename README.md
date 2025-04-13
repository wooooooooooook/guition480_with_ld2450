# guition480_with_ld2450
guition 4'' display ESP32-S3-4848S040 with LD2450 sensor

### 재료
- guition 4'' display ESP32-S3-4848S040 (3 relay 모델 기준)
- LD2450 sensor
- MX 1.25 4pin cable (https://ko.aliexpress.com/item/1005007277110532.html) : guition display에 연결
- ZH 1.5 4pin cable (https://ko.aliexpress.com/item/1005007277030322.html) : LD2450에 연결
- M4 둥근머리 볼트 25mm (더 길어도 관계없음. 스위치 고정에 쓰이는 볼트 재활용가능)
- [3D 프린팅 파츠](https://github.com/wooooooooooook/guition480_with_ld2450/tree/main/printing%20parts)

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

[프린팅파츠](https://github.com/wooooooooooook/guition480_with_ld2450/tree/main/printing%20parts)
프린팅 파츠에서 `cover.stl`, `plate.stl`을 출력.

### ESPHome 펌웨어 설치
벽면에 설치후에는 usb포트노출이 안되므로 최초 1회는 USB-C 연결해서 유선으로 펌웨어설치가 필요함.
이후에는 OTA로 업데이트가능. 
[configuration.yaml](https://github.com/wooooooooooook/guition480_with_ld2450/blob/main/esphome%20configuration/guition.yaml)
YAML을 참조하여 ESPHome 펌웨어 설치.

### 설치하기
![image](https://github.com/user-attachments/assets/748dec2e-e754-4aeb-88b1-2e5e764efeb9)

벽면에 사진과 같이 plate에 LD2450를 장착하고(그냥 걸쳐져있는 방식) 케이블을 잘 정리해서 볼트로 고정시킨다.
케이블의 경우 MX1.25와 ZH1.5케이블을 5V->5V, Rx->Tx, Tx->Rx, Gnd->Gnd가 되도록 연결했음. 

![image](https://github.com/user-attachments/assets/58a36884-8bc0-4e73-afeb-f3ff0228e65f)

주의해서 L, N, L1~3을 연결하고 LD2450케이블은 위쪽으로 위치시켜서 디스플레이를 장착한다.

![image](https://github.com/user-attachments/assets/76d232d0-d741-4f59-ac8e-7e8499bfe7e6)

M4 볼트로 고정된 모습. (3D 프린팅에 나사를 밀어넣는 방식이므로 너무 세게 조이면 안됩니다.)

![image](https://github.com/user-attachments/assets/33ef70d4-cff1-4161-bc7d-31d5e897e3f9)

LD2450케이블을 본체에 연결한뒤 결합하면 완성

![image](https://github.com/user-attachments/assets/3f13a045-a6b8-484e-acb1-1dd9a4206324)
![image](https://github.com/user-attachments/assets/31ea0772-27b0-45b8-b8c5-89d06812b5d4)
![image](https://github.com/user-attachments/assets/d90dffc9-d535-4843-857b-d76246447aa5)


### 펌웨어 기본 기능
- Light 1~3은 후면 L1~3의 릴레이를 작동시킴
- Switch 1~3은 HA에서 자동화를통해 연동시켜 사용
- LD2450을 활용해 접근시 (2m이내) 화면이 켜짐. (딜레이가 있어 답답할 수도 있습니다)
- [Guition](https://devices.esphome.io/devices/Guition-ESP32-S3-4848S040) 공식문서의 아날로그시계, 날짜, IP주소 표시기능은 유지
- 우측하단의 Radar모양 버튼 클릭시 실시간 레이더 화면
