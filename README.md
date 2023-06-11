# EXPERIMENT-06-INTERRUPT-GENERATION-USING-PUSHBUTTON-AND-SIMULATING-THE-OUTPUT

### Aim:
To Interface a push button and generate an interrupt , simulate it using an led and simuate it on  proteus 

### Components required:
STM32 CUBE IDE, Proteus 8 simulator .

### Theory:

ARM v7 Core supports multiple great features for handling exceptions and interrupts. Which includes the Nested Vectored Interrupt Controller (NVIC).

Micro-Coded Architecture So that interrupt stacking, entry, and exit are done automatically in hardware. Which offloads this work overhead from the CPU
### Processor Mode

The processor mode can change when exceptions occur. And it can be in one of the following modes:
Thread Mode: Which is entered on reset.
Handler Mode: Which is entered on all other exceptions.
![image](https://github.com/vasanthkumarch/EXPERIMENT-06-INTERRUPT-GENERATION-USING-PUSHBUTTON-AND-SIMULATING-THE-OUTPUT-/assets/36288975/4f52f2d6-4cdb-4315-b2b2-b55dc1639c43)
The STM32 ARM microcontroller interrupts are generated in the following manner:

The system runs the ISR and then goes back to the main program. The NVIC and EXTI are configured. The Interrupt Service Routine (ISR) also known as the interrupt service routine handler is defined to enable the external interrupts.

Let us learn about the important features which are needed to configure external interrupts in STM32 microcontrollers

Interrupt Lines (EXTI0-EXTI15)
The STM32 ARM microcontroller features 23 event sources which are divided into two sections. The first section corresponds t external pins on each port which are P0-P15. The second section corresponds to RTC, ethernet, USB interrupts. Therefore, in the first section, we have 16 lines corresponding to line0 till line15. All of these map to a pin number.
The diagram below shows how the GPIO pins are connected to the 16 interrupt lines:

![image](https://github.com/vasanthkumarch/EXPERIMENT-06-INTERRUPT-GENERATION-USING-PUSHBUTTON-AND-SIMULATING-THE-OUTPUT-/assets/36288975/3e1ededb-144c-4103-a64e-9132b7e06e1b)

One important thing to note here is that same number pins are connected to line with the same number. All of these then join to form a single line. Additionally, we can not use two pins one one line at the same time. For example out of PA1, PB1, PC1, PD1, PE1, PF1 and PG1 you can only use a single pin out of all these. This is because they are all connected to the same line EXTI1. However you can use PA1 and PA2 at the same time as they are connected with different lines.

Now each of these lines EXTI0-EXTI15 can be used to trigger an interrupt on different modes of the signal : rising edge, falling edge or rising_falling edge.
## Procedure:
 1. click on STM 32 CUBE IDE, the following screen will appear 
 
 2. click on FILE, click on new stm 32 project 
 ![2](https://github.com/vidhyadharan-03/EXPERIMENT-06-INTERRUPT-GENERATION-USING-PUSHBUTTON-AND-SIMULATING-THE-OUTPUT-/assets/114286357/b7b6fca1-f798-499d-95bf-b4f9efaaa26c)
![3](https://github.com/vidhyadharan-03/EXPERIMENT-06-INTERRUPT-GENERATION-USING-PUSHBUTTON-AND-SIMULATING-THE-OUTPUT-/assets/114286357/27c7272f-5f86-4a49-ae84-badaa74a4443)


 3. select the target to be programmed  as shown below and click on next 
![4](https://github.com/vidhyadharan-03/EXPERIMENT-06-INTERRUPT-GENERATION-USING-PUSHBUTTON-AND-SIMULATING-THE-OUTPUT-/assets/114286357/7da86376-a312-4c5d-9ccc-aa862dcde0f2)
![5](https://github.com/vidhyadharan-03/EXPERIMENT-06-INTERRUPT-GENERATION-USING-PUSHBUTTON-AND-SIMULATING-THE-OUTPUT-/assets/114286357/8acc2dde-8de4-4249-a7be-aec363d2cfc0)

4.select the program name 

5. corresponding ioc file will be generated automatically 
![6](https://github.com/vidhyadharan-03/EXPERIMENT-06-INTERRUPT-GENERATION-USING-PUSHBUTTON-AND-SIMULATING-THE-OUTPUT-/assets/114286357/c3e657c8-a54a-47d6-b69e-463c2454277f)

6.select the appropriate pins as gipo, in or out, USART or required options and configure 
![7](https://github.com/vidhyadharan-03/EXPERIMENT-06-INTERRUPT-GENERATION-USING-PUSHBUTTON-AND-SIMULATING-THE-OUTPUT-/assets/114286357/e6e034ab-e130-4b6d-a8db-100f4f152d96)
![8](https://github.com/vidhyadharan-03/EXPERIMENT-06-INTERRUPT-GENERATION-USING-PUSHBUTTON-AND-SIMULATING-THE-OUTPUT-/assets/114286357/cceb88e3-900c-46cd-95ea-8e3ac6483cb2)


7.click on cntrl+S , automaticall C program will be generated 

![9](https://github.com/vidhyadharan-03/EXPERIMENT-06-INTERRUPT-GENERATION-USING-PUSHBUTTON-AND-SIMULATING-THE-OUTPUT-/assets/114286357/47d6bffc-4e1d-42fc-8256-8461400d0b33)

![10](https://github.com/vidhyadharan-03/EXPERIMENT-06-INTERRUPT-GENERATION-USING-PUSHBUTTON-AND-SIMULATING-THE-OUTPUT-/assets/114286357/3a44e291-a767-4de0-ba90-c4ae5f7afed4)

8. edit the program and per required
![11](https://github.com/vidhyadharan-03/EXPERIMENT-06-INTERRUPT-GENERATION-USING-PUSHBUTTON-AND-SIMULATING-THE-OUTPUT-/assets/114286357/cbfc2e92-eaf2-4f48-a85e-44a105a210ab)


9. Select EXTI pin configuration and clock configuration 

![12](https://github.com/vidhyadharan-03/EXPERIMENT-06-INTERRUPT-GENERATION-USING-PUSHBUTTON-AND-SIMULATING-THE-OUTPUT-/assets/114286357/09f0fec6-f87d-4ea0-9200-8ac51a588026)

10. once the project is bulild 
![13](https://github.com/vidhyadharan-03/EXPERIMENT-06-INTERRUPT-GENERATION-USING-PUSHBUTTON-AND-SIMULATING-THE-OUTPUT-/assets/114286357/d9782717-0281-47cb-9356-af5c779df1cf)

11. click on debug option 
![14](https://github.com/vidhyadharan-03/EXPERIMENT-06-INTERRUPT-GENERATION-USING-PUSHBUTTON-AND-SIMULATING-THE-OUTPUT-/assets/114286357/5435a8f8-397e-4c7c-a14b-f59e58d8d5b3)

12.  Creating Proteus project and running the simulation
We are now at the last part of step by step guide on how to simulate STM32 project in Proteus.

13. Create a new Proteus project and place STM32F40xx i.e. the same MCU for which the project was created in STM32Cube IDE. 
14. After creation of the circuit as per requirement as shown below 

![15](https://github.com/vidhyadharan-03/EXPERIMENT-06-INTERRUPT-GENERATION-USING-PUSHBUTTON-AND-SIMULATING-THE-OUTPUT-/assets/114286357/ede9b0cb-71dd-4b39-be19-5f9e5594e08f)


15. Double click on the the MCU part to open settings. Next to the Program File option, give full path to the Hex file generated using STM32Cube IDE. Then set the external crystal frequency to 8M (i.e. 8 MHz). Click OK to save the changes.
https://engineeringxpert.com/wp-content/uploads/2022/04/26.png

16. click on debug and simulate using simulation as shown below 


![16](https://github.com/vidhyadharan-03/EXPERIMENT-06-INTERRUPT-GENERATION-USING-PUSHBUTTON-AND-SIMULATING-THE-OUTPUT-/assets/114286357/8af7f652-bdd7-4c5c-a1a8-a7d54cdde2ef)


  

## STM 32 CUBE PROGRAM :
```
#include "main.h"
#include "stdio.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
  
  HAL_Init();
  SystemClock_Config();
  MX_GPIO_Init();

void HAL_GPIO_EXTI_Callback(uint16_t GPIO_Pin)
{
	if((GPIO_Pin==GPIO_PIN_1))
	{
		HAL_GPIO_TogglePin(GPIOA,GPIO_PIN_0);
	}
}

  HAL_GPIO_WritePin(GPIOA, GPIO_PIN_0, GPIO_PIN_RESET);
```
## Output screen shots of proteus  :
## ON STATE:
  
  ![exp-6 0n](https://github.com/vidhyadharan-03/EXPERIMENT-06-INTERRUPT-GENERATION-USING-PUSHBUTTON-AND-SIMULATING-THE-OUTPUT-/assets/114286357/f879233b-c0d4-4a6f-8981-8f2fc5649769)

  
 ## OFF STATE:
 
 
 ![off exp-6](https://github.com/vidhyadharan-03/EXPERIMENT-06-INTERRUPT-GENERATION-USING-PUSHBUTTON-AND-SIMULATING-THE-OUTPUT-/assets/114286357/a669d05b-673a-4442-8f82-81a1318cb45c)

 

 ## CIRCUIT DIAGRAM (EXPORT THE GRAPHICS TO PDF AND ADD THE SCREEN SHOT HERE): 
 
 ![exp-6graph](https://github.com/vidhyadharan-03/EXPERIMENT-06-INTERRUPT-GENERATION-USING-PUSHBUTTON-AND-SIMULATING-THE-OUTPUT-/assets/114286357/73a9667e-4fa9-4c63-989f-e569368b7707)

## Result :
Interfacing a push button and interrupt genrateion is simulated using proteus 
