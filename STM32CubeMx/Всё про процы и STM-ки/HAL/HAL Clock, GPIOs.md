### Clock
`HAL_RCC_OscConfig (RCC_OscInitTypeDef *RCC_OscInitStruct). `
This function configures/enables multiple clock sources(устройства тактовой частоты) (HSE, HSI, LSE, LSI, PLL).
`HAL_RCC_ClockConfig (RCC_ClkInitTypeDef *RCC_ClkInitStruct, uint32_t FLatency).`
This function: 
– selects the system clock source
– configures AHB, APB1 and APB2 clock dividers 
– configures the number of Flash memory wait states 
– updates the SysTick configuration when HCLK clock changes.

### GPIOs
GPIO HAL APIs are the following:  
`HAL_GPIO_Init() / HAL_GPIO_DeInit() `
`HAL_GPIO_ReadPin() / HAL_GPIO_WritePin()`
`HAL_GPIO_TogglePin ().`

GPIO_InitTypeDef:
field:
Pin, Mode, Pull, Speed
![[Pasted image 20240710144200.png]]
https://www.st.com/resource/en/user_manual/dm00154093-description-of-stm32f1-hal-and-lowlayer-drivers-stmicroelectronics.pdf (стр 27)

