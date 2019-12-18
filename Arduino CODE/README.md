Arduino IDE CODE


```c
#include <SoftwareSerial.h>

#define BT_RXD 12 // 아두이노 12번
#define BT_TXD 11 // 아두이노 11번
#define button 4  // SOS 택트스위치 4번



SoftwareSerial HM10(BT_RXD, BT_TXD);  // 블루투스 소프트웨어 시리얼 지정

int buttonState = 0; //버튼상태 지정

void setup()
{
  pinMode(button, INPUT_PULLUP); // 풀업스위치로 지정
  Serial.begin(9600); //통신속도 9600으로 지정
  HM10.begin(9600);  //통신속도 9600으로 지정

}


void loop() {
    buttonState = digitalRead(button); 

    if(buttonState==HIGH){
    Serial.println("OFF");
    delay(1000);
  }
  else{
    Serial.println("ON"); // 버튼을 누르게 되면 시리얼에 ON 문자를 보내고
    HM10.write('1');      // 블루투스에는 '1'을 스마트폰으로 보냄
    delay(1000);
  }
}
```
