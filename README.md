# AUTOMATIC-LED-CONTROL-USING-IR-SENSOR
##  AIM
To design and implement a system using the **STM32 microcontroller** where an LED automatically turns ON or OFF based on the input from an **IR sensor**.

---

##  Components Required
- STM32 Nucleo or Discovery Board (e.g., **Nucleo-G071RB**)
- IR Sensor Module
- LED (5mm Green or any color)
- Jumper wires
- Breadboard

---

##  Theory
An **IR sensor** detects the presence of an object by emitting and receiving infrared light.

### IR Sensor Behavior
- When an **object is detected**, the IR sensor output goes **LOW (0V)**.
- When **no object is detected**, the output stays **HIGH (3.3V)**.

### Microcontroller Response
- If **IR output = LOW** → **LED ON**
- If **IR output = HIGH** → **LED OFF**
### **Procedure**

1. Open **STM32CubeIDE**.
  <img width="1919" height="1199" alt="Screenshot 2025-10-28 202412" src="https://github.com/user-attachments/assets/67daa124-5edf-494b-ba61-47d16f642d09" />

2. Click **File → New STM32 Project**.
   <img width="1919" height="1199" alt="Screenshot 2025-10-28 203225" src="https://github.com/user-attachments/assets/735ec58d-0afd-44ae-b2a1-0f6298c2c3ef" />


3. Select the **target microcontroller** or board and click **Next**.
  <img width="1919" height="1199" alt="Screenshot 2025-10-28 203723" src="https://github.com/user-attachments/assets/109bd30f-4806-455b-b1c8-2631166f3efc" />



4. Name the project.
   <img width="1918" height="593" alt="image" src="https://github.com/user-attachments/assets/35b39b05-f754-475b-982a-6038fbb82d8e" />

5. The corresponding `.ioc` file will be generated automatically.
  <img width="1918" height="1199" alt="Screenshot 2025-10-28 203910" src="https://github.com/user-attachments/assets/c682290e-b856-4d8f-8d21-ff1ee7180abf" />
<img width="1736" height="1199" alt="Screenshot 2025-10-28 204329" src="https://github.com/user-attachments/assets/2da585be-047f-4e80-859e-fbdd5586d0b8" />
 

6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
   <img width="1919" height="1199" alt="Screenshot 2025-10-28 204350" src="https://github.com/user-attachments/assets/0a62f6e1-f224-4ecb-8e2e-e726e3cb4f20" />


7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
   <img width="1919" height="1199" alt="Screenshot 2025-10-28 204610" src="https://github.com/user-attachments/assets/f5565dff-516c-4aef-ba81-1548a0f13d41" />
<img width="1919" height="1199" alt="Screenshot 2025-10-28 205054" src="https://github.com/user-attachments/assets/993f6cc7-00dd-4aba-ac61-9bef163dc896" />

8. Edit the generated main program as required.
   <img width="716" height="261" alt="Screenshot 2025-10-28 222542" src="https://github.com/user-attachments/assets/be2169b0-bdcc-4e18-b896-f3f731f29187" />

9. Click **Project → Build All**.
    <img width="725" height="251" alt="Screenshot 2025-10-28 222628" src="https://github.com/user-attachments/assets/359040dc-7abc-48a3-879d-3b82959e990d" />


10. Link the **HEX file** using the post-build process.
    <img width="725" height="251" alt="Screenshot 2025-10-28 222628" src="https://github.com/user-attachments/assets/3763744a-a04b-405a-8a51-733e54eaf5d7" />

11. Click **Debug** and connect the **STM Nucleo Board**.
   <img width="1919" height="1199" alt="Screenshot 2025-10-28 222724" src="https://github.com/user-attachments/assets/4a9f9002-c6b9-47f6-8d6c-994bb9afe012" />

13. Click **Run** to execute the program.
    
---

### 💻 **Program**


```c
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        GPIO_PinState ir = HAL_GPIO_ReadPin(GPIOA, GPIO_PIN_10); // IR OUT at PA10 (D2)

	      if (ir == GPIO_PIN_RESET)  // IR sensor HIGH = object detected
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_SET); // Turn ON LED
	      }
	      else
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_RESET); // Turn OFF LED
	      }

	      HAL_Delay(100);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 
![WhatsApp Image 2025-10-28 at 20 09 22](https://github.com/user-attachments/assets/5dd65df8-4a99-4833-926c-091d8b298b8d)


CASE 2: LED OFF
<img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/c7042b88-c2d2-4a30-96df-d2219c6a8f08" />


---
### RESULT

The experiment on IR Sensor-Based Automatic LED Control using STM32 was successfully carried out. The STM32 microcontroller accurately read the IR sensor output and controlled the LED based on object detection. When an object was detected, the LED glowed (ON) and when no object was present, the LED remained OFF. Thus, the objective of the experiment was achieved.




