
/*SLAVE* 
	 
#include <avr/io.h>
#include<avr/delay.h>

  int main (void)
  {
	  uint8_t data;
	  DDRC |= (1<<PINC7);    // SCK, MOSI and SS as outputs
	  PORTC &= ~(1<<PINC7);                 // MISO as input

	  DDRB &= ~((1<<PINB1)|(1<<PINB2)|(1<<PINB0));   // SCK, MOSI and SS as inputs
	  DDRB |= (1<<PINB3);                    // MISO as output

	  SPCR &= ~(1<<MSTR);                // Set as slave
	  SPCR |= (1<<SPR0)|(1<<SPR1);       // divide clock by 128
	  SPCR |= (1<<SPE);                  // Enable SPI

	  while(1)
	  {
		  while(!(SPSR & (1<<SPIF)));    // wait until all data is received
		  data = SPDR;                   // hurray, we now have our data
	  
	  
	  if((data>=1)&& (data<100)){
		  
		  PORTC ^= (1<<PINC7);  
		  _delay_ms(30);
	  }
	  else if((data>=100)&& (data<200)){
		  
		    PORTC ^= (1<<PINC7);
		    _delay_ms(1000);
	  }
	 else  PORTC &= ~(1<<PINC7);  
	  
  }
 }


/* MASTER */
 
 #include <avr/io.h>


 int main (void)
 {
	 uint8_t data =1;
	 DDRB |= ((1<<PINB1)|(1<<PINB2)|(1<<PINB0));   // SCK, MOSI and SS as inputs
	 DDRB &= ~(1<<PINB3);                    // MISO as output

	 SPCR |= (1<<MSTR);               // Set as Master
	 SPCR |= (1<<SPR0)|(1<<SPR1);     // divided clock by 128
	 SPCR |= (1<<SPE);                // Enable SPI
	 
	 while(1)
	 {
		 SPDR = data;                 // send the data
		 while(!(SPSR & (1<<SPIF)));  // wait until transmission is complete
		 data++;
		 if(data>200) data=1;

		 // if you have multiple slaves, this is where you want to switch
	 }
 }
 
