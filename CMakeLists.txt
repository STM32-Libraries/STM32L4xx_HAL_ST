cmake_minimum_required(VERSION 3.22)

project(stm32l4xx_hal_st)

set(CMAKE_C_COMPILER $ENV{HOME}/Tools/gcc-arm/gcc-arm-none-eabi-10.3-2021.10/bin/arm-none-eabi-gcc)


set(HAL_DIR stm32l4xx_hal_driver)
set(SRC_DIR ${HAL_DIR}/Src)

# Set include directories and sources
set(INCLUDE_DIRS 
    ${HAL_DIR}/Inc
    ${HAL_DIR}/Inc/legacy
    ${CMAKE_CURRENT_SOURCE_DIR}/conf
    ${CMAKE_CURRENT_SOURCE_DIR}/cmsis
    ${CMAKE_CURRENT_SOURCE_DIR}/cmsis/device
    ${CMAKE_CURRENT_SOURCE_DIR}/cmsis/core
)

set(SOURCES
    ${SRC_DIR}/stm32l4xx_hal_adc.c
    ${SRC_DIR}/stm32l4xx_hal_adc_ex.c
    ${SRC_DIR}/stm32l4xx_hal.c
    ${SRC_DIR}/stm32l4xx_hal_can.c
    ${SRC_DIR}/stm32l4xx_hal_comp.c
    ${SRC_DIR}/stm32l4xx_hal_cortex.c
    ${SRC_DIR}/stm32l4xx_hal_crc.c
    ${SRC_DIR}/stm32l4xx_hal_crc_ex.c
    ${SRC_DIR}/stm32l4xx_hal_cryp.c
    ${SRC_DIR}/stm32l4xx_hal_cryp_ex.c
    ${SRC_DIR}/stm32l4xx_hal_dac.c
    ${SRC_DIR}/stm32l4xx_hal_dac_ex.c
    ${SRC_DIR}/stm32l4xx_hal_dcmi.c
    ${SRC_DIR}/stm32l4xx_hal_dfsdm.c
    ${SRC_DIR}/stm32l4xx_hal_dfsdm_ex.c
    ${SRC_DIR}/stm32l4xx_hal_dma2d.c
    ${SRC_DIR}/stm32l4xx_hal_dma.c
    ${SRC_DIR}/stm32l4xx_hal_dma_ex.c
    ${SRC_DIR}/stm32l4xx_hal_dsi.c
    ${SRC_DIR}/stm32l4xx_hal_exti.c
    ${SRC_DIR}/stm32l4xx_hal_firewall.c
    ${SRC_DIR}/stm32l4xx_hal_flash.c
    ${SRC_DIR}/stm32l4xx_hal_flash_ex.c
    ${SRC_DIR}/stm32l4xx_hal_flash_ramfunc.c
    ${SRC_DIR}/stm32l4xx_hal_gfxmmu.c
    ${SRC_DIR}/stm32l4xx_hal_gpio.c
    ${SRC_DIR}/stm32l4xx_hal_hash.c
    ${SRC_DIR}/stm32l4xx_hal_hash_ex.c
    ${SRC_DIR}/stm32l4xx_hal_hcd.c
    ${SRC_DIR}/stm32l4xx_hal_i2c.c
    ${SRC_DIR}/stm32l4xx_hal_i2c_ex.c
    ${SRC_DIR}/stm32l4xx_hal_irda.c
    ${SRC_DIR}/stm32l4xx_hal_iwdg.c
    ${SRC_DIR}/stm32l4xx_hal_lcd.c
    ${SRC_DIR}/stm32l4xx_hal_lptim.c
    ${SRC_DIR}/stm32l4xx_hal_ltdc.c
    ${SRC_DIR}/stm32l4xx_hal_ltdc_ex.c
    ${SRC_DIR}/stm32l4xx_hal_mmc.c
    ${SRC_DIR}/stm32l4xx_hal_mmc_ex.c
    ${SRC_DIR}/stm32l4xx_hal_msp_template.c
    ${SRC_DIR}/stm32l4xx_hal_nand.c
    ${SRC_DIR}/stm32l4xx_hal_nor.c
    ${SRC_DIR}/stm32l4xx_hal_opamp.c
    ${SRC_DIR}/stm32l4xx_hal_opamp_ex.c
    ${SRC_DIR}/stm32l4xx_hal_ospi.c
    ${SRC_DIR}/stm32l4xx_hal_pcd.c
    ${SRC_DIR}/stm32l4xx_hal_pcd_ex.c
    ${SRC_DIR}/stm32l4xx_hal_pka.c
    ${SRC_DIR}/stm32l4xx_hal_pssi.c
    ${SRC_DIR}/stm32l4xx_hal_pwr.c
    ${SRC_DIR}/stm32l4xx_hal_pwr_ex.c
    ${SRC_DIR}/stm32l4xx_hal_qspi.c
    ${SRC_DIR}/stm32l4xx_hal_rcc.c
    ${SRC_DIR}/stm32l4xx_hal_rcc_ex.c
    ${SRC_DIR}/stm32l4xx_hal_rng.c
    ${SRC_DIR}/stm32l4xx_hal_rng_ex.c
    ${SRC_DIR}/stm32l4xx_hal_rtc.c
    ${SRC_DIR}/stm32l4xx_hal_rtc_ex.c
    ${SRC_DIR}/stm32l4xx_hal_sai.c
    ${SRC_DIR}/stm32l4xx_hal_sai_ex.c
    ${SRC_DIR}/stm32l4xx_hal_sd.c
    ${SRC_DIR}/stm32l4xx_hal_sd_ex.c
    ${SRC_DIR}/stm32l4xx_hal_smartcard.c
    ${SRC_DIR}/stm32l4xx_hal_smartcard_ex.c
    ${SRC_DIR}/stm32l4xx_hal_smbus.c
    ${SRC_DIR}/stm32l4xx_hal_smbus_ex.c
    ${SRC_DIR}/stm32l4xx_hal_spi.c
    ${SRC_DIR}/stm32l4xx_hal_spi_ex.c
    ${SRC_DIR}/stm32l4xx_hal_sram.c
    ${SRC_DIR}/stm32l4xx_hal_swpmi.c
    ${SRC_DIR}/stm32l4xx_hal_tim.c
    ${SRC_DIR}/stm32l4xx_hal_timebase_tim_template.c
    ${SRC_DIR}/stm32l4xx_hal_tim_ex.c
    ${SRC_DIR}/stm32l4xx_hal_tsc.c
    ${SRC_DIR}/stm32l4xx_hal_uart.c
    ${SRC_DIR}/stm32l4xx_hal_uart_ex.c
    ${SRC_DIR}/stm32l4xx_hal_usart.c
    ${SRC_DIR}/stm32l4xx_hal_usart_ex.c
    ${SRC_DIR}/stm32l4xx_hal_wwdg.c
    ${SRC_DIR}/stm32l4xx_ll_adc.c
    ${SRC_DIR}/stm32l4xx_ll_comp.c
    ${SRC_DIR}/stm32l4xx_ll_crc.c
    ${SRC_DIR}/stm32l4xx_ll_crs.c
    ${SRC_DIR}/stm32l4xx_ll_dac.c
    ${SRC_DIR}/stm32l4xx_ll_dma2d.c
    ${SRC_DIR}/stm32l4xx_ll_dma.c
    ${SRC_DIR}/stm32l4xx_ll_exti.c
    ${SRC_DIR}/stm32l4xx_ll_fmc.c
    ${SRC_DIR}/stm32l4xx_ll_gpio.c
    ${SRC_DIR}/stm32l4xx_ll_i2c.c
    ${SRC_DIR}/stm32l4xx_ll_lptim.c
    ${SRC_DIR}/stm32l4xx_ll_lpuart.c
    ${SRC_DIR}/stm32l4xx_ll_opamp.c
    ${SRC_DIR}/stm32l4xx_ll_pka.c
    ${SRC_DIR}/stm32l4xx_ll_pwr.c
    ${SRC_DIR}/stm32l4xx_ll_rcc.c
    ${SRC_DIR}/stm32l4xx_ll_rng.c
    ${SRC_DIR}/stm32l4xx_ll_rtc.c
    ${SRC_DIR}/stm32l4xx_ll_sdmmc.c
    ${SRC_DIR}/stm32l4xx_ll_spi.c
    ${SRC_DIR}/stm32l4xx_ll_swpmi.c
    ${SRC_DIR}/stm32l4xx_ll_tim.c
    ${SRC_DIR}/stm32l4xx_ll_usart.c
    ${SRC_DIR}/stm32l4xx_ll_usb.c
    ${SRC_DIR}/stm32l4xx_ll_utils.c
    ${SRC_DIR}/Legacy/stm32l4xx_hal_can.c
    
)

# Create static library
add_library(${PROJECT_NAME} STATIC ${SOURCES})

# Configure library compilation options
target_include_directories(${PROJECT_NAME} PUBLIC ${INCLUDE_DIRS})

# Configure additional compilation options, if needed
target_compile_options(${PROJECT_NAME} PRIVATE 
                                        -c 
                                        -mcpu=cortex-m4
                                        -std=c11 
                                        -Wall
                                        -mthumb
                                        )

# Configure linking options, if needed
# target_link_libraries(${PROJECT_NAME} ...)

# Configure installation options, if needed
# install(TARGETS ${PROJECT_NAME} DESTINATION lib)
# install(FILES ... DESTINATION include)