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
## 3. Điều khiển servo bằng nút bấm
```c
#include <ESP32Servo.h>

Servo myservo; // khai báo biến 
const int buttonPin = 4; // khai báo chân nút bấm
int angle = 0;  // góc quay ban đầu của servo

void setup() {
  pinMode(buttonPin, INPUT_PULLUP); // khởi tạo nút bấm
  myservo.attach(5);  // gắn đối tượng servo vào cổng 5
  // myservo.write(angle); //test
}

void loop() {
  Serial.println(digitalRead(buttonPin));
  if (digitalRead(buttonPin) == LOW) { // đang bấm nút
    angle += 10; // tăng góc quay lên 10 độ
    if (angle > 180) 
      angle = 0; //servo này chỉ quay được tối đa 180 độ nên phải gán về 0 độ
    myservo.write(angle); // ra lệnh cho servo quay theo giá trị góc 
    delay(300); // debounce đơn giản
  }
}
```
