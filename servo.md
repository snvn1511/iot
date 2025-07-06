## 1. Găn động cơ vào mạch
```c
#include <ESP32Servo.h>

Servo myservo;

void setup() {
  myservo.attach(5); // Gắn servo vào chân GPIO số 5
  myservo.write(90);  // Quay đến góc 90 độ
}

void loop() {
  // Không làm gì
}

```
## 2. Quay từ 0 -> 180 độ rồi quay lại
```c
// chú ý về hướng đặt động cơ
#include <ESP32Servo.h>

Servo myservo;

void setup() {
  myservo.attach(5);
}

void loop() {
  //điều chỉnh góc quay từ 0 -> 180 độ
  for (int angle = 0; angle <= 180; angle++) {
    myservo.write(angle);
    delay(15);
  }
  // điều chỉnh góc quay từ vị trí 180 độ về 0
  for (int angle = 180; angle >= 0; angle--) {
    myservo.write(angle);
    delay(15);
  }
}

```
