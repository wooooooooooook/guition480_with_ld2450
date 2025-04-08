# guition480_with_ld2450
guition 4'' display ESP32-S3-4848S040 with LD2450 sensor

### 하드웨어
![20250404_100520](https://github.com/user-attachments/assets/110cf85d-78dd-4490-9936-346bdb5f3f59)
우측 상단에 1.25mm 4pin UART 포트가 존재함.
백패널과 연결포트에도 UART포트가 들어가는데 우측상단의 UART와 UART0핀을 공유하고있음 (GPIO 44, 43) 
백패널로 가는 uart는 저항이 없고, uart포트는 100옴 저항이 달려있음. 

![20250404_100418](https://github.com/user-attachments/assets/822efe3d-059b-403a-b36f-22f405a06086)
백패널의 Rx, Tx는 아무데도 연결되지 않은것으로보임.
따라서 4pin UART포트를 사용 가능함.

![image](https://github.com/user-attachments/assets/b6296e05-ef48-4c88-aae4-91ac7f33fd70)
포트 노출을 위해 뒷판을 잘라내야함.

### 어댑터 출력
![image](https://github.com/user-attachments/assets/7cfcbe32-7a6a-458f-b7b9-c156670a34f7)
