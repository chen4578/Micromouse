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

In the "Device Configuration Tool," we configure the pins that support hardware encoders as follows: 

<p align="center">
  <img src="https://github.com/chen4578/Micromouse/blob/afee51421cf9a5e3446bc452cd8210d0812ebf4e/assets/Screenshot%202025-10-01%20232853.png" width="400">
</p>

Then, we modify the timer settings by expanding the "Timers" dropdown and choose TIM2. After, set "Combined Channels" to "Encoder Mode." Next, in set "Counter Period" to 65535 (the maximum encoder counts that can be stored) in "Parameter Settings" and make "Encoder Mode" be "Encoder Mode TI1" and "Encoder Mode TI2." This is repeated for Timer 1 by following the same steps but selecting TIM1.

In `main.c`, we add `HAL_TIM_Encoder_Start(&htim1, TIM_CHANNEL_ALL)` and `HAL_TIM_Encoder_Start(&htim2, TIM_CHANNEL_ALL)` as well as define `int16_t left_counts = 0` and `int16_t right_counts = 0` ro record encoder counts. Furthermore, `left_counts = getLeftEncoderCounts()` and `right_counts = getRightEncoderCounts()` serves to update the encoder counts.

### Motors

We configure the pins as follows:

<p align="center">
  <img src="https://github.com/chen4578/Micromouse/blob/87a5951ee8dfd804f4a8383eb12899fb9bd77c1c/assets/Screenshot%202025-10-01%20234713.png" width="400">
</p>

Choose TIM4 from "Timers" and set "Channel1" to "PWM Generation CH1." This is repeated for the rest of the channels. In Parameter Settings, set "Counter Period" to 3199 (the maximum PWM frequency for the motor driver).

In "NVIC Settings," enable TIM4 global interrupt.

In `main.c`, we add `HAL_TIM_PWM_Start(&htim4, TIM_CHANNEL_1)` and repeat for the rest of the channels. We can set motor speed and direction by calling `setMotorRPWM` and `setMotorLPWM`.

