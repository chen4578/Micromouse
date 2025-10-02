# Programming Microcontroller

## Introduction

For the micromouse, we will be using CubeIDE to setup pins, configure clocks, and implement motor control.

### Configuring Pins

In the "Device Configuration Tool" of CubeIDE, we can verify if pin PC13-ANTI_TAMP is set to GPIO-EXTI13, and that pin PA5 is set to GPIO_OUTPUT. Next, we ensure that the "GPIO" tab is selected after expanding "System Core."

For our project, we rename PA5 to "LED." For PC13-ANTI_TAMP, we we change the "GPIO mode" field to "External Interrupt Mode with Rising/Falling edge trigger detection" so that the button is updated when it is pressed.

In the NVIC tab, the EXTI interrupts should be enabled.

Afterwards, we generate the driver code.

### Buttons

In main.c, we have the `HAL-GPIO_EXTI_Callback` function which is called even an interrupt is detected. When called, it passes the pin that caused the interrupt as the GPIO_PIN parameter. 

The function verifies whether the pin that called the interrupt is PC13 which is assigned to PushButton_Pin and turns on or off an LED depending on whether the button is pressed.

### Encoders

In the "Device Configuration Tool," we configure the pins as follows: 
