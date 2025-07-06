## 1. Nối bóng led vào esp32 và tự bật bóng
```c
#define LED_PIN 2. // Khai báo hằng chỉ định chân dương của let
 
void setup() {
  // put your setup code here, to run once:
  Serial.begin(115200);
  Serial.println("Hello..."); // in thử ra log xem esp32 chạy tốt không
  

  pinMode(LED_PIN, OUTPUT);  // chỉ định điện ra từ esp32 là đổ vào chân 2
  digitalWrite(LED_PIN, HIGH); // HIGH là dòng điện cao --> bật led, LOW là tắt
}

void loop() {
  // vòng lặp vĩnh viễn
  delay(100); // để cái delay để giảm tần suất lặp
 
}
```
## 2. Bật tắt bóng để cho bóng nhấp nháy
```c
#define LED_PIN 2

void setup() {

  pinMode(LED_PIN, OUTPUT);
}

void loop() {
  digitalWrite(LED_PIN, HIGH); // bật bóng
  delay(300);  // đợi 3s thì tắt
  digitalWrite(LED_PIN, LOW); // tắt bóng
  delay(300);
}
```
## 3. Bật tắt bằng nút bấm
```c
#define LED_PIN 2
#define BUTTON_PIN 4

void setup() {
  pinMode(LED_PIN, OUTPUT);
  pinMode(BUTTON_PIN, INPUT_PULLUP); // Nút nối với GND, bật điện trở kéo lên
}

void loop() {
  int state = digitalRead(BUTTON_PIN);
  digitalWrite(LED_PIN, !state); // Bấm nút thì LED sáng
}
```


