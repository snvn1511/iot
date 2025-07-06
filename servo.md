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
