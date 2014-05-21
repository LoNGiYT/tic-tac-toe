#include <IRremote.h>

int receiverpin = 11;
#define DATA 6
#define LATCH 8
#define CLOCK 10
#define DATA2 9
#define LATCH2 7
#define CLOCK2 5
#define red 13
#define blue 12

int count;
byte p = 0;
byte r = 0;
byte a = pow(2,0);
byte b = pow(2,1);
byte c = pow(2,2);
byte d = pow(2,3);
byte e = pow(2,4);
byte f = pow(2,5);
byte g = pow(2,6);
byte h = pow(2,7);
byte x = a + b + c + d + e + f + g + h;
byte y = a + b + c + d + e + f + g + h;

IRrecv irrecv(receiverpin);
decode_results results;

void setup(){
    irrecv.enableIRIn();
    pinMode(red,OUTPUT);
    pinMode(blue,OUTPUT);
    pinMode(LATCH,OUTPUT);
    pinMode(CLOCK,OUTPUT);
    pinMode(DATA, OUTPUT);
    pinMode(LATCH2,OUTPUT);
    pinMode(CLOCK2,OUTPUT);
    pinMode(DATA2, OUTPUT);
    Serial.begin(9600);
    updateShiftRegister(p);
updateShiftRegister2(r);
digitalWrite(red, LOW);
digitalWrite(blue, LOW);


}

void updateShiftRegister(int number)
{
digitalWrite(LATCH, LOW);
shiftOut(DATA,CLOCK, LSBFIRST, number);
digitalWrite(LATCH, HIGH);
}
void updateShiftRegister2(int number)
{
digitalWrite(LATCH2, LOW);
shiftOut(DATA2,CLOCK2, LSBFIRST, number);
digitalWrite(LATCH2, HIGH);
} 

void loop(){ 


if(irrecv.decode(&results)){
   
    switch(results.value){ 
    
    Serial.println(results.value);
    

      /////////////////////////////////1 BUTTON//////////////
      case 0x010:
  count+=1;
  Serial.println(count);
  if(count%2 == 1){
      p = p + a;
      updateShiftRegister(p);
    
      }
    else{
      r = r + a;
   updateShiftRegister2(r);
   
    }
  
     if(count == 9){
       delay(5000);
     updateShiftRegister(0);
     updateShiftRegister2(0);
     digitalWrite(red,LOW);
     digitalWrite(blue,LOW);
   }
   
      break;
      
     
    ////////////////////2 BUTTON/////////////////////
      case 0x810:
       count+=1;
       Serial.println(count);
          if(count%2 == 1){
            p = p + b;
    updateShiftRegister(p);
   
          }
    else{
      r = r + b;
     updateShiftRegister2(r);
 
    }

  if(count == 9){
    delay(5000);
     updateShiftRegister(0);
     updateShiftRegister2(0);
     digitalWrite(red,LOW);
     digitalWrite(blue,LOW);
   }
      break;

    ///////////////////////////////////////3 BUTTON/////////////////////
      case 0x410:
    count+=1;
    Serial.println(count);
      if(count%2 == 1){
            p = p + c;
     updateShiftRegister(p); 
     
     }
    else{
       r = r + c;
    updateShiftRegister2(r);
   
    }
  if(count == 9){
    delay(5000);
     updateShiftRegister(0);
     updateShiftRegister2(0);
     digitalWrite(red,LOW);
     digitalWrite(blue,LOW);
   }

     break; 

    ///////////////////////////////////////4 BUTTON/////////////////////
      case 0xC10:
count+=1;
Serial.println(count);
          if(count%2 == 1){
             p = p + d;
     updateShiftRegister(p);
 
          }
    else{
       r = r + d;
     updateShiftRegister2(r);
  
    }
  if(count == 9){
    delay(5000);
     updateShiftRegister(0);
     updateShiftRegister2(0);
     digitalWrite(red,LOW);
     digitalWrite(blue,LOW);
   }

     break;
     ///////////////////////////////////////5 BUTTON/////////////////////
      case 0x210:
 count+=1;
 Serial.println(count);
          if(count%2 == 1){
            
     digitalWrite(blue,HIGH);
     
          }
    else{
     
     digitalWrite(red,HIGH);
     
    }

  if(count == 9){
    delay(5000);
     updateShiftRegister(0);
     updateShiftRegister2(0);
     digitalWrite(red,LOW);
     digitalWrite(red,LOW);
   }
    
     break;
     /////
     //////////////////////////////////6 BUTTON/////////////////////
      case 0xA10:
       count+=1;
       Serial.println(count);
          if(count%2 == 1){
             p = p + e;
    updateShiftRegister(p);
   
          }
    else{
       r = r + e;
     updateShiftRegister2(r);
     
    }
  if(count == 9){
    delay(5000);
     updateShiftRegister(0);
     updateShiftRegister2(0);
     digitalWrite(red,LOW);
     digitalWrite(blue,LOW);
   }

     break;
    ///////////////////////////////////////7 BUTTON/////////////////////
      case 0x610:
       count+=1;
       Serial.println(count);
          if(count%2 == 1){
             p = p + f;
     updateShiftRegister(p);

          }
    else{
       r = r + f;
     updateShiftRegister2(r);

    }
    
  if(count == 9){
    delay(5000);
     updateShiftRegister(0);
     updateShiftRegister2(0);
     digitalWrite(red,LOW);
     digitalWrite(blue,LOW);
   }
     break;
     ///////////////////////////////////////8 BUTTON/////////////////////
      case 0xE10:
count+=1;
Serial.println(count);
          if(count%2 == 1){
             p = p + g;
   updateShiftRegister(p);
 
          }
    else{
       r = r + g;
    updateShiftRegister2(r);
   
    }
  if(count == 9){
    delay(5000);
     updateShiftRegister(0);
     updateShiftRegister2(0);
     digitalWrite(red,LOW);
     digitalWrite(blue,LOW);
   }

     break;
     ///////////////////////////////////////9 BUTTON/////////////////////
      case 0x110:  
 count+=1;
 Serial.println(count);
          if(count%2 == 1){
             p = p + h;
     updateShiftRegister(p);

          }
    else{
       r = r + h;
     updateShiftRegister2(r);
     
    }
    if(count == 9){
      delay(5000);
updateShiftRegister(0);
     updateShiftRegister2(0);
     digitalWrite(red,LOW);
     digitalWrite(blue,LOW);
    }
     break;
    

    }
  //add in lnie of code to remove extra button presses
  for(int z=0; z<2; z++) {
    irrecv.resume();
  
delay(500);
  }
  
  }
}
