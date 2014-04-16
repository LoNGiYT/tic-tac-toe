tic-tac-toe
===========
int led 1=;
int led 1R=;
int led 1B=;
int led 1G=;
int led 2=;
int led 2R=;
int led 2B=;
int led 2G=;
int led 3=;
int led 3R=;
int led 3B=;
int led 3G=;
int led 4=;
int led 4R=;
int led 4B=;
int led 4G=;
int led 5=;
int led 5R=;
int led 5B=;
int led 5G=;
int led 6=;
int led 6R=;
int led 6B=;
int led 6G=;
int receiverpin =;
#include<IRemote.h>
IRrecv irrecv (receiverpin);
decode_results results;
void setup()
{
Serial.begin(9600);
irrecv.enableIRIn();
}
void loop()
{
  if (irrecv.decode(&results))
  {
    Serial.print();
    Serial.print(" ");
    irrecv.resume();
  }
}
