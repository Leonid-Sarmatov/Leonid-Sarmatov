## My codewars profile:
![Kyu](https://www.codewars.com/users/docent_204/badges/large?logo=false)

## Statistics:
[![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=Leonid-Sarmatov&layout=donut&langs_count=8)](https://github.com/anuraghazra/github-readme-stats)

## Languages:
<div>
  <img src="https://raw.githubusercontent.com/devicons/devicon/1119b9f84c0290e0f0b38982099a2bd027a48bf1/icons/go/go-original-wordmark.svg" title="Go" alt="Go" width="60" height="60"/>&nbsp;
  <img src="https://github.com/devicons/devicon/blob/master/icons/java/java-original-wordmark.svg" title="Java" alt="Java" width="60" height="60"/>&nbsp;
  <img src="https://raw.githubusercontent.com/devicons/devicon/1119b9f84c0290e0f0b38982099a2bd027a48bf1/icons/python/python-original-wordmark.svg" title="Python" alt="Python" width="60" height="60"/>&nbsp;
  <img src="https://github.com/devicons/devicon/blob/master/icons/c/c-original.svg"title="C" alt="C" width="60" height="60"/>&nbsp;
</div>

## Skills:
<div>
  <img src="https://github.com/devicons/devicon/blob/master/icons/postgresql/postgresql-original-wordmark.svg" title="PostgreSQL"  alt="PostgreSQL" width="60" height="60"/>&nbsp;
  <img src="https://github.com/devicons/devicon/blob/master/icons/mysql/mysql-original-wordmark.svg" title="MySQL"  alt="MySQL" width="60" height="60"/>&nbsp;
  <img src="https://github.com/devicons/devicon/blob/master/icons/apachekafka/apachekafka-original-wordmark.svg" title="Apachekafka"  alt="Apachekafka" width="70" height="60"/>&nbsp;
  <img src="https://github.com/devicons/devicon/blob/master/icons/rabbitmq/rabbitmq-original-wordmark.svg" title="RabbitMQ"  alt="RabbitMQ" width="80" height="60"/>&nbsp;
  <img src="https://github.com/devicons/devicon/blob/master/icons/grpc/grpc-original.svg" title="GRPC" **alt="GRPC" width="60" height="60"/>
  <img src="https://github.com/devicons/devicon/blob/master/icons/git/git-original-wordmark.svg" title="Git" **alt="Git" width="60" height="60"/>
  <img src="https://github.com/devicons/devicon/blob/master/icons/docker/docker-original-wordmark.svg" title="Docker" **alt="Docker" width="60" height="60"/>
  <img src="https://github.com/devicons/devicon/blob/master/icons/ubuntu/ubuntu-original.svg" title="Ubuntu" **alt="Ubuntu" width="60" height="60"/>
  <img src="https://github.com/devicons/devicon/blob/master/icons/archlinux/archlinux-original.svg" title="Arch" **alt="Arch" width="60" height="60"/>
</div>

## Desktop applications:
<div>
  <img src="https://github.com/devicons/devicon/blob/master/icons/vscode/vscode-original-wordmark.svg" title="VSCode"  alt="VSCode" width="60" height="60"/>&nbsp;
  <img src="https://github.com/devicons/devicon/blob/master/icons/androidstudio/androidstudio-original.svg" title="androidstudio"  alt="androidstudio" width="60" height="60"/>&nbsp;
  <img src="https://github.com/devicons/devicon/blob/master/icons/jetbrains/jetbrains-original.svg" title="jetbrains"  alt="jetbrains" width="60" height="60"/>&nbsp;
</div>

## My contacts:
- Email: ```chemestru@gmail.com```

## Achievements:
- In May 2024, I completed a course on Golang development from Yandex. [See...](https://github.com/Leonid-Sarmatov/my-images/blob/master/729544474.pdf)
- [Codewars profile](https://www.codewars.com/users/docent_204)

<p align="left"> <img src="https://komarev.com/ghpvc/?username=Leonid-Sarmatov&label=Profile%20views&color=0e75b6&style=flat" alt="Leonid-Sarmatov" /> </p>
<!--
**Leonid-Sarmatov/Leonid-Sarmatov** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->




# toolchain
TOOLCHAIN    = arm-none-eabi-
CC           = $(TOOLCHAIN)gcc
CP           = $(TOOLCHAIN)objcopy
AS           = $(TOOLCHAIN)gcc -x assembler-with-cpp
HEX          = $(CP) -O ihex
BIN          = $(CP) -O binary -S

# define mcu, specify the target processor
MCU          = cortex-m4

# all the files will be generated with this name (main.elf, main.bin, main.hex, etc)
PROJECT_NAME=application

# specify define
DDEFS       =

# define root dir
ROOT_DIR     = .

# define include dir
INCLUDE_DIRS =

# define include dir
USER_DIR =  $(ROOT_DIR)/user

# define stm32f10x lib dir
LIB_DIR      = $(ROOT_DIR)/bsp/libraries

# define freertos dir
FREERTOS_DIR = $(ROOT_DIR)/bsp/middlewares/freertos/source


# link file
LINK_SCRIPT  = $(ROOT_DIR)/ld/AT32F437xM_FLASH.ld

# user code
SRC       =
ASM_SRC   =
SRC      += $(USER_DIR)/main.c
SRC      += $(USER_DIR)/at32f435_437_clock.c
SRC      += $(USER_DIR)/at32f435_437_int.c

# user include
INCLUDE_DIRS  = $(USER_DIR)


# ******************** artery lib begin  *******************
# STD Defines
DDEFS += -DAT32F437VMT7 -DUSE_STDPERIPH_DRIVER# -DHSE_VALUE=8000000

# source director
CORE_DIR    = $(LIB_DIR)/cmsis/cm4/core_support
DEVICE_DIR  = $(LIB_DIR)/cmsis/cm4/device_support
SRC_DIR     = $(LIB_DIR)/drivers/src
INC_DIR_     = $(LIB_DIR)/drivers/inc

# startup
ASM_SRC  += $(DEVICE_DIR)/startup/gcc/startup_at32f435_437.s

# CMSIS
SRC  += $(DEVICE_DIR)/system_at32f435_437.c

# use libraries, please add or remove when you use or remove it.
SRC  += $(SRC_DIR)/at32f435_437_acc.c
SRC  += $(SRC_DIR)/at32f435_437_adc.c
SRC  += $(SRC_DIR)/at32f435_437_can.c
SRC  += $(SRC_DIR)/at32f435_437_crc.c
SRC  += $(SRC_DIR)/at32f435_437_crm.c
SRC  += $(SRC_DIR)/at32f435_437_dac.c
SRC  += $(SRC_DIR)/at32f435_437_debug.c
SRC  += $(SRC_DIR)/at32f435_437_dma.c
SRC  += $(SRC_DIR)/at32f435_437_dvp.c
SRC  += $(SRC_DIR)/at32f435_437_edma.c
SRC  += $(SRC_DIR)/at32f435_437_emac.c
SRC  += $(SRC_DIR)/at32f435_437_ertc.c
SRC  += $(SRC_DIR)/at32f435_437_exint.c
SRC  += $(SRC_DIR)/at32f435_437_flash.c
SRC  += $(SRC_DIR)/at32f435_437_gpio.c
SRC  += $(SRC_DIR)/at32f435_437_i2c.c
SRC  += $(SRC_DIR)/at32f435_437_misc.c
SRC  += $(SRC_DIR)/at32f435_437_pwc.c
SRC  += $(SRC_DIR)/at32f435_437_qspi.c
SRC  += $(SRC_DIR)/at32f435_437_scfg.c
SRC  += $(SRC_DIR)/at32f435_437_sdio.c
SRC  += $(SRC_DIR)/at32f435_437_spi.c
SRC  += $(SRC_DIR)/at32f435_437_tmr.c
SRC  += $(SRC_DIR)/at32f435_437_usart.c
SRC  += $(SRC_DIR)/at32f435_437_usb.c
SRC  += $(SRC_DIR)/at32f435_437_wdt.c
SRC  += $(SRC_DIR)/at32f435_437_wwdt.c
SRC  += $(SRC_DIR)/at32f435_437_xmc.c 

# include directories
INCLUDE_DIRS += $(CORE_DIR)
INCLUDE_DIRS += $(DEVICE_DIR)
INCLUDE_DIRS += $(INC_DIR_)
# ********************* artery lib end  ********************


# ******************** free rtos begin  ********************
# source director
FREERTOS_SRC_DIR     = $(FREERTOS_DIR)
FREERTOS_INC_DIR     = $(FREERTOS_DIR)/include
FREERTOS_ARM_CM4_DIR = $(FREERTOS_DIR)/portable/GCC/ARM_CM4F
FREERTOS_MemMang_DIR = $(FREERTOS_DIR)/portable/memmang

# add freertos source
#SRC  += $(FREERTOS_SRC_DIR)/list.c
#SRC  += $(FREERTOS_SRC_DIR)/queue.c
#SRC  += $(FREERTOS_SRC_DIR)/croutine.c
#SRC  += $(FREERTOS_SRC_DIR)/tasks.c

#SRC  += $(FREERTOS_ARM_CM4_DIR)/port.c

#SRC  += $(FREERTOS_MemMang_DIR)/heap_4.c

# include directories
#INCLUDE_DIRS += $(FREERTOS_INC_DIR)
#INCLUDE_DIRS += $(FREERTOS_ARM_CM4_DIR)
# ********************* free rtos end *********************






INC_DIR  = $(patsubst %, -I%, $(INCLUDE_DIRS))

# run from Flash
DEFS	 = $(DDEFS) -DRUN_FROM_FLASH=1

#C_SRC           := $(wildcard *.c)
#ASM_SRC         := $(wildcard *.S)
#OBJECTS         := $(patsubst %,$(BUILD_DIR)/%.o,$(C_SRC))
#OBJECTS         += $(patsubst %,$(BUILD_DIR)/%.o,$(ASM_SRC))

OBJECTS  = $(ASM_SRC:.s=.o) $(SRC:.c=.o)

# Define optimisation level here
OPT = -Os

MC_FLAGS = -mcpu=$(MCU)

AS_FLAGS = $(MC_FLAGS) -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=fpv4-sp-d16 -O0 -g -gdwarf-2 -mthumb  -Wa,-amhls=$(<:.s=.lst)
CP_FLAGS = $(MC_FLAGS) $(OPT) -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=fpv4-sp-d16 -O0 -g -gdwarf-2 -mthumb -fomit-frame-pointer -Wall -fverbose-asm -Wa,-ahlms=$(<:.c=.lst) $(DEFS)
LD_FLAGS = $(MC_FLAGS) -g -gdwarf-2 -mthumb -nostartfiles -Xlinker --gc-sections -T$(LINK_SCRIPT) -Wl,-Map=$(PROJECT_NAME).map,--cref,--no-warn-mismatch

#
# makefile rules
#
all: $(OBJECTS) $(PROJECT_NAME).elf  $(PROJECT_NAME).hex $(PROJECT_NAME).bin
	$(TOOLCHAIN)size $(PROJECT_NAME).elf

%.o: %.c
	$(CC) -c $(CP_FLAGS) -I . $(INC_DIR) $< -o $@

%.o: %.s
	$(AS) -c $(AS_FLAGS) $< -o $@

%.elf: $(OBJECTS)
	$(CC) $(OBJECTS) $(LD_FLAGS) -o $@

%.hex: %.elf
	$(HEX) $< $@

%.bin: %.elf
	$(BIN)  $< $@

flash: $(PROJECT_NAME).bin
	st-flash write $(PROJECT_NAME).bin 0x8000000

erase:
	st-flash erase

clean:
	-rm -rf $(OBJECTS)
	-rm -rf $(PROJECT_NAME).elf
	-rm -rf $(PROJECT_NAME).map
	-rm -rf $(PROJECT_NAME).hex
	-rm -rf $(PROJECT_NAME).bin
	-rm -rf $(SRC:.c=.lst)
	-rm -rf $(ASM_SRC:.s=.lst)












##########################################################################################################################
# File automatically-generated by tool: [projectgenerator] version: [2.26.0] date: [Fri Apr 13 10:23:08 CST 2018] 
##########################################################################################################################

# ------------------------------------------------
# Generic Makefile (based on gcc)
#
# ChangeLog :
#	2017-02-10 - Several enhancements + project update mode
#   2015-07-22 - first version
# ------------------------------------------------

######################################
# target
######################################
TARGET = stm32proj


######################################
# building variables
######################################
# debug build?
DEBUG = 1
# optimization
OPT = -Og


#######################################
# paths
#######################################
# source path
SOURCES_DIR =  \
bsp/libraries/cmsis/cm4/device_support/startup/gcc \
bsp/libraries/cmsis/cm4/device_support \
bsp/libraries/drivers/src \
src \
bsp/middlewares/freertos/source \
bsp/middlewares/freertos/source/portable/GCC/ARM_CM4F


# firmware library path
PERIFLIB_PATH = 

# Build path
BUILD_DIR = build

######################################
# source
######################################
# C sources
C_SOURCES =  \
bsp/drivers/src/at32f435_437_acc.c \
bsp/drivers/src/at32f435_437_adc.c \
bsp/drivers/src/at32f435_437_can.c \
bsp/drivers/src/at32f435_437_crc.c \
bsp/drivers/src/at32f435_437_crm.c \
bsp/drivers/src/at32f435_437_dac.c \
bsp/drivers/src/at32f435_437_debug.c \
bsp/drivers/src/at32f435_437_dma.c \
bsp/drivers/src/at32f435_437_dvp.c \
bsp/drivers/src/at32f435_437_edma.c \
bsp/drivers/src/at32f435_437_emac.c \
bsp/drivers/src/at32f435_437_ertc.c \
bsp/drivers/src/at32f435_437_exint.c \
bsp/drivers/src/at32f435_437_flash.c \
bsp/drivers/src/at32f435_437_gpio.c \
bsp/drivers/src/at32f435_437_i2c.c \
bsp/drivers/src/at32f435_437_misc.c \
bsp/drivers/src/at32f435_437_pwc.c \
bsp/drivers/src/at32f435_437_qspi.c \
bsp/drivers/src/at32f435_437_scfg.c \
bsp/drivers/src/at32f435_437_sdio.c \
bsp/drivers/src/at32f435_437_spi.c \
bsp/drivers/src/at32f435_437_tmr.c \
bsp/drivers/src/at32f435_437_usart.c \
bsp/drivers/src/at32f435_437_usb.c \
bsp/drivers/src/at32f435_437_wdt.c \
bsp/drivers/src/at32f435_437_wwdt.c \
bsp/drivers/src/at32f435_437_xmc.c \
bsp/middlewares/freertos/source/croutine.c \
bsp/middlewares/freertos/source/event_groups.c \
bsp/middlewares/freertos/source/list.c \
bsp/middlewares/freertos/source/queue.c \
bsp/middlewares/freertos/source/stream_buffer.c \
bsp/middlewares/freertos/source/tasks.c \
bsp/middlewares/freertos/source/timers.c \
src/at32f435_437_clock.c \
src/at32f435_437_int.c \
src/main.c

# CPP sources
CXX_SOURCES = 

# ASM sources
ASM_SOURCES =  \
startup_at32f435_437.s


######################################
# firmware library
######################################
PERIFLIB_SOURCES = 


#######################################
# binaries
#######################################
BINPATH = 
PREFIX = arm-none-eabi-
CC = $(BINPATH)$(PREFIX)gcc
CXX = $(BINPATH)$(PREFIX)g++
AS = $(BINPATH)$(PREFIX)gcc -x assembler-with-cpp
CP = $(BINPATH)$(PREFIX)objcopy
AR = $(BINPATH)$(PREFIX)ar
SZ = $(BINPATH)$(PREFIX)size
HEX = $(CP) -O ihex
BIN = $(CP) -O binary -S
 
#######################################
# CFLAGS
#######################################
# cpu
CPU = -mcpu=cortex-m4

# fpu
# NONE for Cortex-M0/M0+/M3

# float-abi


# mcu
MCU = $(CPU) -mthumb $(FPU) $(FLOAT-ABI)

# macros for gcc
# AS defines
AS_DEFS = 

# C defines
C_DEFS =  \
-DUSE_STDPERIPH_DRIVER \
-DAT32F437VMT7

# C++ defines
CXX_DEFS =

# AS includes
AS_INCLUDES =  \
-Iinc

# C includes
C_INCLUDES =  \
-Iinc \


CXX_INCLUDES =  \
-IMiddlewares/cxxsource \
-IMiddlewares/HARDWARE/include

# compile gcc flags
ASFLAGS = $(MCU) $(AS_DEFS) $(AS_INCLUDES) $(OPT) -Wall -fdata-sections -ffunction-sections

CFLAGS = $(MCU) $(C_DEFS) $(C_INCLUDES) $(OPT) -Wall -fdata-sections -ffunction-sections

CXXFLAGS = -lstdc++ $(CFLAGS) $(CXX_DEFS) $(CXX_INCLUDES) -g -ggdb3 -fno-rtti -fno-exceptions \
-fverbose-asm -fdata-sections -ffunction-sections -fpermissive -Wa,-ahlms=$(BUILD_DIR)/$(notdir $(<:.cpp=.lst))


ifeq ($(DEBUG), 1)
CFLAGS += -g -gdwarf-2
endif


# Generate dependency information
CFLAGS += -MMD -MP -MF"$(@:%.o=%.d)" -MT"$(@:%.o=%.d)"


#######################################
# LDFLAGS
#######################################
# link script
LDSCRIPT = STM32F103C8Tx_FLASH.ld

# libraries
LIBS = -lc -lm -lnosys
LIBDIR =
LDFLAGS = $(MCU) -specs=nano.specs -T$(LDSCRIPT) $(LIBDIR) $(LIBS) -Wl,-Map=$(BUILD_DIR)/$(TARGET).map,--cref -Wl,--gc-sections

# default action: build all
all: $(BUILD_DIR)/$(TARGET).elf $(BUILD_DIR)/$(TARGET).hex $(BUILD_DIR)/$(TARGET).bin


#######################################
# build the application
#######################################
# list of objects
OBJECTS = $(addprefix $(BUILD_DIR)/,$(notdir $(C_SOURCES:.c=.o)))
vpath %.c $(sort $(dir $(C_SOURCES)))

# list of c++ objects
OBJECTS += $(addprefix $(BUILD_DIR)/,$(notdir $(CXX_SOURCES:.cpp=.o)))
vpath %.cpp $(sort $(dir $(CXX_SOURCES)))

# list of ASM program objects
OBJECTS += $(addprefix $(BUILD_DIR)/,$(notdir $(ASM_SOURCES:.s=.o)))
vpath %.s $(sort $(dir $(ASM_SOURCES)))

$(BUILD_DIR)/%.o: %.c Makefile | $(BUILD_DIR) 
	$(CC) -c $(CFLAGS) -Wa,-a,-ad,-alms=$(BUILD_DIR)/$(notdir $(<:.c=.lst)) $< -o $@

$(BUILD_DIR)/%.o: %.cpp Makefile | $(BUILD_DIR) 
	$(CXX) -c $(CXXFLAGS) $< -o $@

$(BUILD_DIR)/%.o: %.s Makefile | $(BUILD_DIR)
	$(AS) -c $(CFLAGS) $< -o $@

$(BUILD_DIR)/$(TARGET).elf: $(OBJECTS) Makefile
	$(CC) $(OBJECTS) $(LDFLAGS) -o $@
	$(SZ) $@

$(BUILD_DIR)/%.hex: $(BUILD_DIR)/%.elf | $(BUILD_DIR)
	$(HEX) $< $@
	
$(BUILD_DIR)/%.bin: $(BUILD_DIR)/%.elf | $(BUILD_DIR)
	$(BIN) $< $@	
	
$(BUILD_DIR):
	mkdir $@		

#---------------------------- write to mcu -----------------------------#
flash: 
	st-flash write build/$(TARGET).bin 0x8000000

#---------------------------- Jlink ---------------------------------#
install:
	JLinkExe -device STM32F103C8 -if swd -speed 4000
	#loadbin build/$(TARGET).bin 0x8000000

#######################################
# clean up
#######################################
clean:
	-rm -fR .dep $(BUILD_DIR)
  
#######################################
# dependencies
#######################################
-include $(shell mkdir .dep 2>/dev/null) $(wildcard .dep/*)

# *** EOF ***
