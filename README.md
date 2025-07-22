Bare metal implementation  of an ADC driver for STM32 development board 
## Features
- ADC1 initialization with tested ADC resolution (6-bits, 8-bits) and peripheral clock = 8MHz.
- Single mode conversion
- Interrupt handling
## Requirements
### Hardware
- STM32 Discovery development board (STM32F411x series)
- Multimeter (optional for debugging)
- Potentiometer ( input Voltage = 3V)
### Software
- STM32CubeIDE or compatible toolchain
## Installation
1. Clone this repository:
   ```bash
   git clone https://github.com/Asma-Prog-Eng/ADC_Interrupt_Driver
   
2. Import project into STM32CubeIDE:
File → Import... → Existing Projects into Workspace

3. Update the include path directories ,  to CMSIS folder ( under Project properties -> C/C++ General -> Includes : delete existing CMSIS path directory and  add the path to CMSIS folder <br />,
   that is included in the project, : Add -> File System <br />

4. Rebuild project dependenciesFile 

## Usage
Initialization : GPIO_init(), ADC1_init (), start_conversion();
Read raw value, and Convert raw value into voltage : ADC_IRQHandler(), adc_callback()

## Project Structure

├── Core<br />
├── Inc<br />  → ADC.h <br />
├── Src<br /> → ADC.c<br /> → main.c

## Troubleshooting

No value could be read from on ADC1->DR:
- Verify clock acess for ADC1 peripheral (RCC->APB2ENR register)
- Verify clock acess for port A (RCC->APHBENR register)
- Verify PA1 mode, should be configured to analog mode (GPIOA->MODER)
- Verify if ADC1 interrupt is enabled in NVIC

## Known Limitations
Limited to 8-bits resolution

## Contributing
Pull requests are welcome. For major changes, open an issue first.

## License
MIT License
Copyright (c) [2025] [Asma Askri]
