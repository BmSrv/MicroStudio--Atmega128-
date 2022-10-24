~~~
#define  F_CPU 16000000
#include <avr/io.h>
#include <avr/interrupt.h>
#include <compat/deprecated.h>

volatile unsigned char led=0x01;

void init_port(){
DDRA=0xff;
PORTA=0xff;
sbi(DDRB,4);
cbi(DDRD,7);
}

void init_timer0(){
TCCR0=0x1d; //16000000/64/250=1000,0x1d=128 분주
TIMSK=0x00;
TIFR=0x00;
TCNT0=0x00;
OCR0=250; //2msec 설정
}

void init_timer2(){
TCCR2=0x06;
TIMSK=0x40;
TIFR=0x00;
TCNT2=256-250; //펄스 하나에 4msec * 250 = 1sec
}

ISR(TIMER2_OVF_vect){
TCNT2=6;
PORTA=~led;
led=led<<1;
if (led==0b00000000)
{
led=0x01;
}
}


int main(void)
{
init_port();
init_timer0();
init_timer2();
sei();
    /* Replace with your application code */
    while (1)
    {
    }
}
~~~
