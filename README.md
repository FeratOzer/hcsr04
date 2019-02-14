# hcsr04

int trigPin = 6; // sensörün trig pinine bağlanacak arduino pini
int echoPin = 7; // sensörün echo pinine bağlanacak arduino pini
long olcum;
long cm; // sensörümüzden okuduğumuz uzaklık
void setup(){

pinMode(trigPin, OUTPUT);
pinMode(echoPin,INPUT);
Serial.begin(9600);
}
void loop()
{
digitalWrite(trigPin, LOW); // sensör ilk başta ses yollamasın
delayMicroseconds(5);
digitalWrite(trigPin, HIGH); // Burada ses dalgasını yolluyoruz
delayMicroseconds(10);
digitalWrite(trigPin, LOW); // Tek bir ses dalgası yolladık
olcum = pulseIn(echoPin, HIGH); // Eğer ses geri dönerse echo pinine geri dönecektir.
// Burada geçen süreyi hesaplıyoruz.
cm= olcum /29.1/2; // ölçüm değerini zamandan -> CM’ye çeviriyoruz
Serial.println(cm); // sonucu Serial Monitor’den görmek için bilgisayara yolluyoruz
delay(100);
}
