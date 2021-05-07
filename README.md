Blinky project
==============

The **Blinky** project can be easily used to verify the basic tool setup.

It is compliant to the [Cortex Microcontroller Software Interface Standard (CMSIS)](https://arm-software.github.io/CMSIS_5/General/html/index.html)
and uses the [CMSIS-RTOS v2 API](https://arm-software.github.io/CMSIS_5/RTOS2/html/index.html) for RTOS functionality. The CMSIS-RTOS v2 API
is supported by various real-time operating systems, for example [Keil RTX5](https://arm-software.github.io/CMSIS_5/RTOS2/html/rtx5_impl.html) or [FreeRTOS](https://github.com/ARM-software/CMSIS-FreeRTOS).

Operation
---------

 - At start the `vioLED0` blinks in 1 sec interval.
 - The `vioBUTTON0` changes the blink frequency and start/stops `vioLED1`.

The board hardware mapping of `vioLED0`, `vioLED1`, and `vioBUTTON0` depends on the 
configuration of the [CMSIS-Driver VIO](https://arm-software.github.io/CMSIS_5/Driver/html/group__vio__interface__gr.html).

RTOS: FreeRTOS Real-Time Operating System
-----------------------------------------
The real-time operating system [FreeRTOS](https://github.com/ARM-software/CMSIS-FreeRTOS) implements the resource management.

It is configured with the following settings:

- Minimal stack size \[words]: 768
- Total heap size \[bytes]: 24000
- Preemption interrupt priority: 128
- Event Recorder configuration
  - Initialize Event Recorder: 1

Refer to [Configure CMSIS-FreeRTOS](https://arm-software.github.io/CMSIS-FreeRTOS/General/html/cre_freertos_proj.html#cmsis_freertos_config) for a detailed description of all configuration options.

Board: STMicroelectronics STM32H745I-DISCO
------------------------------------------

The tables below list the device configuration for this board.

The heap/stack setup is in configuration files of related software components.

The example project can be re-configured to work on custom hardware. Refer to ["Migrate STM32 Based Example Projects to Custom Hardware"](https://github.com/MDK-Packs/Documentation/tree/master/Porting_to_Custom_Hardware) for information. 

### System Configuration

| System Component        | Setting
|:------------------------|:----------------------------------------
| Device                  | STM32H745XIHx
| ICACHE                  | enabled
| DCACHE                  | enabled
| Heap                    | 64 kB (configured in startup file)
| Stack (MSP)             | 1 kB (configured in startup file)

### Clock Configuration

| Clock                   | Setting
|:------------------------|:----------------------------------------
| SYSCLK                  | 400 MHz (Cortex-M7 CPU Clock)
| HCLK                    | 200 MHz (Cortex-M4 CPU, Bus matrix Clocks)
| APB1                    | 100 MHz
| APB2                    | 100 MHz
| APB3                    | 100 MHz

### CMSIS-Driver mapping

| CMSIS-Driver VIO  | Physical board hardware
|:------------------|:-----------------------
| vioBUTTON0        | Button USER (PC13)
| vioLED0           | LD6 RED (PJ2)
| vioLED1           | LD7 RED (PI13)
