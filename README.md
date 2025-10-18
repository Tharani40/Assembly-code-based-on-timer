# Assembly-code-based-on-timer

## AIM
To write and execute an Embedded C Program for square wave with frequency of 50khz using 8051 in Keil.

## APPARATUS REQUIRED
- Personal Computer  
- Keil µVision Software

## PROGRAM
### i)c program to generate a square wave with frequency of 50khz
~~~
ORG 0000H         
MOV TMOD, #01H    
AGAIN:MOV P1, #0FFH  
CALL DELAY      
MOV P1, #00H    
CALL DELAY      
SJMP AGAIN      
DELAY:MOV TH0, #0FFH
MOV TL0, #0FAH
SETB TR0       
WAIT:JNB TF0, WAIT  
CLR TR0      
CLR TF0      
RET           
END
~~~
### ii)8051 program to genrate a square wave with frequency of 50khz
~~~
#include <reg51.h>  
void delay(void);  
void main(void)
{
    TMOD = 0x01;  
    while(1)
    {
        P1 = 0xFF;  
        delay();   
        P1 = 0x00;  
        delay();
    }
}
void delay(void)
{
    TH0 = 0xFF;    
    TL0 = 0xF6;     
    TR0 = 1;       
    while (TF0 == 0);  
    TR0 = 0;        
    TF0 = 0;        
}
~~~
## OUTPUT
<img width="865" height="871" alt="Screenshot 2025-10-18 144754" src="https://github.com/user-attachments/assets/4b111a58-0ae2-4c0f-b98b-261f2f9f4b3f" />

<img width="1678" height="744" alt="Screenshot 2025-10-18 150342" src="https://github.com/user-attachments/assets/d751ab08-c5c7-4be7-b8b2-0fc6c6f120f7" />

### RESULT:
Thus a square wave with frequency of 50khz using 8051 KEIL was done and shown the output.
