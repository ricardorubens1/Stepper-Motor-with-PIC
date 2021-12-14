#include <16F877A.h>
#fuses HS,NOWDT,NOPROTECT,NOLVP
#use delay(clock = 8000000)
#use fast_io(B)
#use fast_io(D)
 
unsigned int8 speed;
void steppermove(short ROT){
  if(ROT){ 
   output_d(0b00000110);
   output_high (pin_d5);
   output_high (pin_d6);
   delay_ms(500);
   output_d(0b00000101);
   output_high (pin_d5);
   output_high (pin_d7);
   delay_ms(500);
   output_d(0b00001001);
   output_high (pin_d4);
   output_high (pin_d7);
   delay_ms(500);
   output_d(0b00001010);
   output_high (pin_d4);
   output_high (pin_d6);
   delay_ms(500);
  }
  else{
   output_d(0b00000101);
   output_high (pin_d5);
   output_high (pin_d7);
   delay_ms(500);
   output_d(0b00000110);
   output_high (pin_d5);
   output_high (pin_d6);
   delay_ms(500);
   output_d(0b00001010);
   output_high (pin_d4);
   output_high (pin_d6);
   delay_ms(500);
   output_d(0b00001001);
   output_high (pin_d4);
   output_high (pin_d7);
   delay_ms(500);
  }
}
void main(){
  output_b(0);
  set_tris_b(0x03);
  port_b_pullups(TRUE);
  output_d(0);
  set_tris_d(0);
  setup_adc(ADC_CLOCK_DIV_32);      
  setup_adc_ports(AN0);             // Configura AN0 como entrada analógica
  set_adc_channel(0);              
  delay_ms(100);                    
  while(TRUE){

   output_d(0);
   while(input(PIN_B0)==0){
    steppermove(0);
   }
   while(input(PIN_B1)==0){
    steppermove(1);
   }
  }
}
