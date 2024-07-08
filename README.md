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



MyProject/
├── FreeRTOS/
│   ├── Source/
│   │   ├── include/
│   │   ├── portable/
│   │   │   ├── GCC/
│   │   │   │   └── ARM_CM3/
│   │   │   └── MemMang/
│   │   │       ├── heap_1.c
│   │   │       ├── heap_2.c
│   │   │       ├── heap_3.c
│   │   │       ├── heap_4.c
│   │   │       └── heap_5.c
│   │   ├── croutine.c
│   │   ├── list.c
│   │   ├── queue.c
│   │   ├── tasks.c
│   │   ├── timers.c
│   │   └── ...
│   ├── CMSIS_RTOS/
│   │   ├── include/
│   │   ├── os.h
│   │   ├── os.c
│   │   └── ...
├── Inc/
│   ├── stm32f1xx_hal_conf.h
│   ├── stm32f1xx_it.h
│   ├── main.h
│   ├── FreeRTOSConfig.h
│   └── ...
├── Src/
│   ├── main.c
│   ├── stm32f1xx_hal_msp.c
│   ├── stm32f1xx_it.c
│   ├── startup_stm32f103xx.s
│   ├── system_stm32f1xx.c
│   └── ...
├── Makefile
└── README.md





#include "main.h"
#include "cmsis_os.h"

// Определение светодиода (предполагаем, что он подключен к порту GPIOA, пину 5)
#define LED_PIN GPIO_PIN_5
#define LED_GPIO_PORT GPIOA

void SystemClock_Config(void);
void MX_GPIO_Init(void);
void StartDefaultTask(void *argument);

int main(void)
{
  HAL_Init();
  SystemClock_Config();
  MX_GPIO_Init();

  osKernelInitialize();

  // Создание задачи мигания светодиодом
  osThreadDef(defaultTask, StartDefaultTask, osPriorityNormal, 0, 128);
  osThreadCreate(osThread(defaultTask), NULL);

  osKernelStart();

  while (1)
  {
  }
}

void StartDefaultTask(void *argument)
{
  HAL_GPIO_WritePin(LED_GPIO_PORT, LED_PIN, GPIO_PIN_RESET);

  for (;;)
  {
    HAL_GPIO_TogglePin(LED_GPIO_PORT, LED_PIN);
    osDelay(500);
  }
}

void SystemClock_Config(void)
{
  // Настройка тактового сигнала (этот код обычно генерируется CubeMX)
}

void MX_GPIO_Init(void)
{
  GPIO_InitTypeDef GPIO_InitStruct = {0};
  __HAL_RCC_GPIOA_CLK_ENABLE();

  GPIO_InitStruct.Pin = LED_PIN;
  GPIO_InitStruct.Mode = GPIO_MODE_OUTPUT_PP;
  GPIO_InitStruct.Pull = GPIO_NOPULL;
  GPIO_InitStruct.Speed = GPIO_SPEED_FREQ_LOW;
  HAL_GPIO_Init(LED_GPIO_PORT, &GPIO_InitStruct);
}





#ifndef FREERTOS_CONFIG_H
#define FREERTOS_CONFIG_H

#include "stm32f1xx.h"

// Конфигурация FreeRTOS
#define configUSE_PREEMPTION            1
#define configUSE_IDLE_HOOK             0
#define configUSE_TICK_HOOK             0
#define configCPU_CLOCK_HZ              ( SystemCoreClock )
#define configTICK_RATE_HZ              ( ( TickType_t ) 1000 )
#define configMAX_PRIORITIES            ( 5 )
#define configMINIMAL_STACK_SIZE        ( ( unsigned short ) 130 )
#define configTOTAL_HEAP_SIZE           ( ( size_t ) ( 10 * 1024 ) )
#define configMAX_TASK_NAME_LEN         ( 10 )
#define configUSE_16_BIT_TICKS          0
#define configIDLE_SHOULD_YIELD         1
#define configUSE_MUTEXES               1
#define configQUEUE_REGISTRY_SIZE       8
#define configCHECK_FOR_STACK_OVERFLOW  0
#define configUSE_RECURSIVE_MUTEXES     1
#define configUSE_MALLOC_FAILED_HOOK    0
#define configUSE_APPLICATION_TASK_TAG  0
#define configUSE_COUNTING_SEMAPHORES   1

// Конфигурация системных обработчиков
#define configUSE_PORT_OPTIMISED_TASK_SELECTION 1
#define configUSE_TICKLESS_IDLE                 0
#define configUSE_STATS_FORMATTING_FUNCTIONS    1

// Прерывания
#define configKERNEL_INTERRUPT_PRIORITY         255
#define configMAX_SYSCALL_INTERRUPT_PRIORITY    191 // эквивалент 0xC0, 3 << 5
#define configLIBRARY_KERNEL_INTERRUPT_PRIORITY 15

#endif /* FREERTOS_CONFIG_H */




# Имя исполняемого файла
TARGET = myprogram

# Компилятор и утилиты
CC = arm-none-eabi-gcc
AS = arm-none-eabi-as
OBJCOPY = arm-none-eabi-objcopy

# Директории
SRC_DIR = Src
INC_DIR = Inc
FREERTOS_DIR = FreeRTOS/Source
PORT_DIR = $(FREERTOS_DIR)/portable/GCC/ARM_CM3

# Флаги компиляции и линковки
CFLAGS = -I$(INC_DIR) -I$(FREERTOS_DIR)/include -I$(PORT_DIR) -I$(SRC_DIR) -DSTM32F103xB -DUSE_HAL_DRIVER -O2 -Wall -fdata-sections -ffunction-sections
LDFLAGS = -TSTM32F103C8TX_FLASH.ld -Wl,--gc-sections -Wl,-Map=$(TARGET).map

# Исходные и объектные файлы
SRCS = $(wildcard $(SRC_DIR)/*.c) $(wildcard $(FREERTOS_DIR)/*.c) $(wildcard $(PORT_DIR)/*.c)
OBJS = $(SRCS:.c=.o)

# Правило по умолчанию
all: $(TARGET).elf

# Правило для создания исполняемого файла
$(TARGET).elf: $(OBJS)
	$(CC) $(CFLAGS) $(OBJS) -o $@ $(LDFLAGS)
	$(OBJCOPY) -O binary $@ $(TARGET).bin

# Правило для компиляции исходных файлов
%.o: %.c
	$(CC) $(CFLAGS) -c $< -o $@

# Правило для очистки
clean:
	rm -f $(OBJS) $(TARGET).elf $(TARGET).bin $(TARGET).map






# Имя исполняемого файла
TARGET = myprogram

# Компилятор и утилиты
CC = arm-none-eabi-g++
AS = arm-none-eabi-as
OBJCOPY = arm-none-eabi-objcopy

# Директории
SRC_DIR = Src
INC_DIR = Inc
FREERTOS_DIR = FreeRTOS/Source
PORT_DIR = $(FREERTOS_DIR)/portable/GCC/ARM_CM3

# Флаги компиляции и линковки
CFLAGS = -I$(INC_DIR) -I$(FREERTOS_DIR)/include -I$(PORT_DIR) -I$(SRC_DIR) -DSTM32F103xB -DUSE_HAL_DRIVER -O2 -Wall -fdata-sections -ffunction-sections
LDFLAGS = -TSTM32F103C8TX_FLASH.ld -Wl,--gc-sections -Wl,-Map=$(TARGET).map

# Исходные и объектные файлы
SRCS = $(wildcard $(SRC_DIR)/*.cpp) $(wildcard $(SRC_DIR)/*.c) $(wildcard $(FREERTOS_DIR)/*.c) $(wildcard $(PORT_DIR)/*.c)
OBJS = $(SRCS:.cpp=.o)
OBJS += $(SRCS:.c=.o)

# Правило по умолчанию
all: $(TARGET).elf $(TARGET).hex

# Правило для создания исполняемого файла
$(TARGET).elf: $(OBJS)
	$(CC) $(CFLAGS) $(OBJS) -o $@ $(LDFLAGS)
	$(OBJCOPY) -O binary $@ $(TARGET).bin
	$(OBJCOPY) -O ihex $@ $(TARGET).hex

# Правило для компиляции исходных файлов
%.o: %.cpp
	$(CC) $(CFLAGS) -c $< -o $@

%.o: %.c
	$(CC) $(CFLAGS) -c $< -o $@

# Правило для очистки
clean:
	rm -f $(OBJS) $(TARGET).elf $(TARGET).bin $(TARGET).hex $(TARGET).map

