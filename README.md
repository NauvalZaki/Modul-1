# Modul-1
![Capture4](https://user-images.githubusercontent.com/79407009/109908655-3db4bd00-7cd7-11eb-86d2-59059e1db3ef.PNG)
int LDR = A0;
int LED = 3;
int dataSensor;
int input1 = 11, input2 = 10;
int motEn = 13;

void setup()
{
  pinMode(LDR, INPUT);//set pin A0 sebagai input
  pinMode(LED, OUTPUT);//set pin 3 sebagai output
  pinMode(input1, OUTPUT);
  pinMode(input2, OUTPUT);
  pinMode(motEn, OUTPUT);
  Serial.begin(9600);//Baud rate standar 9600
}

void left(){
  digitalWrite (input1, HIGH);
  digitalWrite (input2, LOW);
}

void right(){
  digitalWrite (input1, LOW);
  digitalWrite (input2, HIGH);
}

void loop(){
  digitalWrite(motEn, HIGH);
  //nilai terendah LDR = 2 (gelap)
  //nilai tertinggi LDR = 404 (terang)
  dataSensor = analogRead(LDR);
  Serial.println(dataSensor);
  
  //algoritma sistem kendali on/ff pada LED
  if (dataSensor < 100){
    digitalWrite(LED, HIGH);//menyalakan lampu LED
    left();
  }
  else {
    digitalWrite(LED, LOW);//mematikan lampu LED ketika terang
    right();
  }
}
