~~~
#define	 F_CPU 16000000

#include <avr/io.h>

#include <avr/interrupt.h>

#include <compat/deprecated.h>

#include <util/delay.h>



volatile unsigned char seg7[] = {0xc0,0xf9,0xa4,0xb0,0x99,0x92,0x83,0xf8,0x80,0x98};

volatile unsigned char data[3] = {0,0,0};



volatile unsigned char led=0xff;

volatile unsigned int count=0x00;


void init_port(){

	sbi(DDRD,1);

	sbi(DDRD,2);

	sbi(DDRD,3);

	DDRF = 0xff;

	cbi(DDRD,0);



	DDRA=0xff;//1111 1111 output port

	PORTA=0xff;//led 8 -off

}

void init_seg(){

	sbi(PORTD,1);

	sbi(PORTD,2);

	sbi(PORTD,3);

	PORTF = 0xff;

}

void inc_d(){

	data[2]++;

	if(data[2]>=10){

		data[2] = 0;

		data[1]++;

		if (data[1]>=10){

			data[1] = 0;

			data[0]++;

			if(data[0]>=10){

				data[0] = 0;

			}

		}

	}

}




ISR(TIMER0_OVF_vect){ //2msec interrupt,10msec

	//	TCNT0=256-250;

	TCNT0=256-250;

	

	count++;

	if(count>=150){ //300msec

		count=0x00;

		inc_d();

	}



}







void init_timer0_ovf(){

	//TCCR0=0x04;// 0000 0100 64분주,오버플로우 타이머0 인터럽트

	TCCR0=0x05;//0000 0101 128분주 f=125000hz

	//TCNT0=256-250;//250분주

	TCNT0=256-250; // 125000hz/250=500hz t=2msec

	TIFR=0x00;//0000 0000

	TIMSK=0x01;//0000 0001 timer0/overflow	

}







int main(void)

{

    init_port();

	init_seg();

	init_timer0_ovf();

	

	sei();

	int i,j;

    while (1) 

    {


		cbi(PORTD,1);

		PORTF = seg7[data[0]];

		_delay_ms(1);

		sbi(PORTD,1);

		cbi(PORTD,2);

		PORTF = seg7[data[1]];

		_delay_ms(1);

		sbi(PORTD,2);

		cbi(PORTD,3);

		PORTF = seg7[data[2]];

		_delay_ms(1);

		sbi(PORTD,3);

		

    }

}
~~~
