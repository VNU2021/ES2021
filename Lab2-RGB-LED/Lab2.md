# 嵌入式系統 - 實作2: 會呼吸的RGB LED,  按鍵控制, 狀態輸出

## 實作2-1, analogWrite(): 並且觀查LED亮度變化是否有像"呼吸的效果"和示波器的波形有什麼關連性? (互動1), (2021-09-05)

### 電路:
![image](https://user-images.githubusercontent.com/89304181/132113065-8d66f2a8-38d7-47c6-a3c5-56d7c54536a2.png)

### 程式:
````C

void setup()
{
  pinMode(13, OUTPUT);
}

void loop()
{
  // turn the LED on (HIGH is the voltage level)
  digitalWrite(13, HIGH);
  delay(1000); // Wait for 1000 millisecond(s)
  // turn the LED off by making the voltage LOW
  digitalWrite(13, LOW);
  delay(1000); // Wait for 1000 millisecond(s)
}

````

## 實作2-2, RGB LED燈全彩模組, 分別讓LED輪流表現正紅、正綠、正藍，三個顏色，時間間隔1秒鐘。並且觀查LED顏色和波形或是電壓有什麼關連性? 可將個人說明在更新GitHub時一起加入. (互動2), (2021-09-05)

### 電路:
![image](https://user-images.githubusercontent.com/89304181/132113030-13751225-740f-4d4b-bdf3-022da9f9302e.png)


### 程式:
```C

int R = 9;
int G = 10;
int B = 11;

void setup()
{
  pinMode(R, OUTPUT);
  pinMode(G, OUTPUT);
  pinMode(B, OUTPUT);  
}

void loop()
{
	analogWrite(R, 255);
	analogWrite(G, 0);
	analogWrite(B, 0);
  	delay(1000);
	analogWrite(R, 0);
	analogWrite(G, 255);
	analogWrite(B, 0);
  	delay(1000);
	analogWrite(R, 0);
	analogWrite(G, 0);
	analogWrite(B, 255);
  	delay(1000);  
}

````

## 實作2-3, 讓你的RGB LED燈全彩模組也可會"呼吸", LED顏色變化是否有像"呼吸的效果"和示波器的波形有什麼關連性? (互動3), (2021-09-12)

### 電路:
![image](https://user-images.githubusercontent.com/89304181/132967785-9e66ebf3-2ef3-4cf1-ba95-2a7d517e977e.png)



### 程式:
````C
int brightness = 0;

void setup()
{
  pinMode(9, OUTPUT);
}

void loop()
{
  for (brightness = 0; brightness <= 255; brightness += 5) {
    analogWrite(9, brightness);
    delay(50); // Wait for 30 millisecond(s)
  }

  for (brightness = 255; brightness >= 0; brightness -= 5) {
    analogWrite(9, brightness);
    delay(50); // Wait for 30 millisecond(s)
  }
  delay(2000);
}

````
### 參考電路與程式: digitWrite(), analogWrite(), 呼吸效果

![image](https://user-images.githubusercontent.com/89304181/132967814-889df6d4-2861-43e4-9443-214d04c0e3fa.png)

````C
int R = 9;
int G = 10;
int B = 11;

int DR = 2;
int DG = 4;
int DB = 7;

void setup()
{
  pinMode(13, OUTPUT); // pin 13
  
  pinMode(R, OUTPUT);
  pinMode(G, OUTPUT);
  pinMode(B, OUTPUT);  
  
  pinMode(DR, OUTPUT);
  pinMode(DG, OUTPUT);
  pinMode(DB, OUTPUT);   
}

void loop()
{
  // digitalWrite: 2 state (i.e., 0, 1) Only
  digitalWrite(13, 1); // LED @ pin 13, ON
  
  delay(1000); 
  
  digitalWrite(DR, 1);
  digitalWrite(DG, 0);
  digitalWrite(DB, 0);
  delay(1000);
  digitalWrite(DR, 0);
  digitalWrite(DG, 1);
  digitalWrite(DB, 0);  
  delay(1000);
  digitalWrite(DR, 0);
  digitalWrite(DG, 0);
  digitalWrite(DB, 1);  
  delay(1000);

  digitalWrite(13, 0); // OFF
  digitalWrite(DR, 0); // OFF
  digitalWrite(DG, 0); // OFF
  digitalWrite(DB, 0); // OFF  
  delay(1000);
  
  // analogWrite: The brightness can be adjusted with 256 levels
  for (int i = 0; i<= 255; i++)
  {
  	analogWrite(R, i);
		analogWrite(G, 0);
		analogWrite(B, 0);
    delay(10);
  } // from dark to bright 

  for (int i = 255; i>= 0; i--)
  {
  	analogWrite(R, i);
	analogWrite(G, 0);
	analogWrite(B, 0);
    delay(10); // 10ms = 0.01s
  }  // from bright to dark
  delay(1000);
}

````

## 實作2-4, 請參考以下[連結](https://github.com/Grace-TA/ES-Fall2021/blob/main/Lab2-RGB-LED/Lab2-4AB.md):

https://github.com/Grace-TA/ES-Fall2021/blob/main/Lab2-RGB-LED/Lab2-4AB.md
