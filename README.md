tic-tac-toe
===========
int led1R=;
int led1B=;
int led2R=;
int led2B=;
int led3R=;
int led3B=;
int led4R=;
int led4B=;
int led5R=;
int led5B=;
int led6R=;
int led6B=;
int led7R=;
int led7B=;
int led8R=;
int led8B=;
int led9R=;
int led9B=;
int receiverpin =;
#include<IRemote.h>
IRrecv irrecv (receiverpin);
decode_results results;
void setup()
pinMode(led1R, OUTPUT);
pinMode(led1B, OUTPUT);
pinMode(led2R, OUTPUT);
pinMode(led2B, OUTPUT);
pinMode(led3R, OUTPUT);
pinMode(led3B, OUTPUT);
pinMode(led4R, OUTPUT);
pinMode(led4B, OUTPUT);
pinMode(led5R, OUTPUT);
pinMode(led5B, OUTPUT);
pinMode(led6R, OUTPUT);
pinMode(led6B, OUTPUT);
pinMode(led7R, OUTPUT);
pinMode(led7B, OUTPUT);
pinMode(led8R, OUTPUT);
pinMode(led8B, OUTPUT);
pinMode(led9R, OUTPUT);
pinMode(led9B, OUTPUT);
pinMode(LATCH, OUTPUT);
pinMode(CLOCK, OUTPUT);
pinMode(DATA, OUTPUT);
}

{
Serial.begin(9600);
irrecv.enableIRIn();
}
void loop()
{
  int i;
  for(i = 0;i<256;i++)
  {
    digitalWrite(LATCH, LOW);
    shiftOut(DATA, CLOCK, MSBFIRST, a);
    digitalWrite(LATCH, HIGH);
    delay(200);
{
  if (irrecv.decode(&results))
  {
    Serial.print();
    Serial.print(" ");
    irrecv.resume();
  }
}
