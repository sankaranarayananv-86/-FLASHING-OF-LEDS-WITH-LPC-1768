# FLASHING-OF-LEDS-WITH-LPC-1768

# AIM: 
   To interface and toggle the led with ARM LPC 1768 microprocessor           
           
# COMPONENTS REQUIRED:
##  HARDWARE:
ARM LPC1768
LED
## SOFTWARE:
KEIL MICRO VISION 4.0 IDE

# PROCEDURE:

## Procedure

1. Open the **Keil µVision** software and select **New µVision Project** from the **Project** menu.
2. Browse to your project folder, provide a project name, and click **Save**.
3. Once saved, a pop-up **“Select Device for Target”** appears. Select the controller **(NXP: LPC1768)** from **NXP (founded by Philips)** and click **OK**.
4. When prompted for the startup file, click **Yes** to include the **LPC17xx Startup** file.
5. Create a new file by selecting **File → New** to write the program.
6. Type the program code.
7. Save the file as **main.c** (for example, `abc.c`).
8. In the project window, right-click **Target 1** and add the appropriate source files to **Source Group 1** and any required header files for the project.
9. Add both **main.c** and **system_LPC17xx.c** files.
10. Build the project and fix any compiler errors or warnings if present.
11. Once the code compiles successfully, note that the **.bin file** is not yet generated.
12. Right-click **Target Options** to configure options for generating the **.bin** file.
13. Set the **IROM1 start address** to **0x2000** (since the bootloader occupies 0x0000–0x2000, the application must start from 0x2000).
14. Write the command to generate the **.bin** file from the **.axf** file:

    ```
    fromelf --bin projectname.axf --output filename.bin
    ```
15. In **C/C++ → Include Paths**, add the path to your library folder (e.g., `Desktop\00-libfiles`).
16. Rebuild the project.
17. The **.bin file** is generated successfully.
18. Check the project folder for the generated **.bin** file.

# ADD FILES:
Target1:
Source group1:
Startuplpc17xx.s, main.c (t), delay.c (t), systemlpc17xx.c (t), gpio.c (t)
Header:
Delay.h, stdutils.h, gpioi.h

# PIN DIAGRAM :

<img width="986" height="647" alt="image" src="https://github.com/user-attachments/assets/ded8de94-3721-4608-b72e-d800e7871d6b" />

# CIRCUIT DIAGRAM:

<img width="1029" height="610" alt="image" src="https://github.com/user-attachments/assets/ce4e78ec-4236-4ec6-8b46-a40ba5a959ba" />
 
# PROGRAM:

```c
#include <lpc17xx.h>
#include "delay.h"	//User defined library which conatins the delay routines #include "gpio.h"
#define LED P1_29	// Led is connected to P1.29
/* start the main program */ int main()
{
SystemInit();	//Clock and PLL configuration GPIO_PinFunction(LED,PINSEL_FUNC_0); // Configure Pin for Gpio GPIO_PinDirection(LED,OUTPUT);	// Configure the pin as OUTPUT GPIO_PinWrite(LED,LOW);
while(1)
{
/* Turn On all the leds and wait for 100ms */ GPIO_PinWrite(LED,HIGH);	// Make all the Port pin as high DELAY_ms(100);

GPIO_PinWrite(LED,LOW);	// Make all the Port pin as low DELAY_ms(100);
}
}
```
 
# Output:

![WhatsApp Image 2025-11-13 at 15 35 43_64c3694e](https://github.com/user-attachments/assets/f5761e69-2e6c-4fd5-bd20-ee89a198c99f)

# Result:

Thus a LED is interfaced with ARM LPC1768 microprocessor and its blinking was verified successfully.
