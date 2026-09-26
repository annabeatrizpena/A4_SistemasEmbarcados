# Semáforo com IHM

## Descrição

Este projeto consiste no desenvolvimento de um sistema de semáforo utilizando a **Raspberry Pi Pico** como unidade de controle. O sistema integra LEDs, um botão de acionamento e um display de 7 segmentos, simulando o funcionamento de um semáforo veicular com controle manual.

A aplicação permite trabalhar conceitos de sistemas embarcados, controle de fluxo lógico, temporização, manipulação de GPIOs e exibição de informações em um display.

## Componentes utilizados

* Raspberry Pi Pico
* LED verde
* LED amarelo
* LED vermelho
* 3 resistores para os LEDs
* Display de 7 segmentos **cátodo comum**
* 7 resistores de **220 Ω** para os segmentos
* Botão
* Jumpers

## Funcionamento

O sistema possui três estados principais.

### 1. Estado verde

Ao iniciar o programa, a função `semaforo_verde()` é executada. O LED verde é acionado, enquanto os LEDs amarelo e vermelho permanecem desligados. O display também é apagado.

### 2. Estado amarelo

Quando o botão é pressionado, o programa identifica o nível lógico LOW na entrada `BOTAO`. Em seguida, a função `semaforo_amarelo()` é executada, desligando o LED verde e acionando o LED amarelo.

O estado amarelo permanece durante **3 segundos**, controlados pela função:

```python
time.sleep(3)
```

### 3. Estado vermelho e contagem

Após os 3 segundos, o programa executa `semaforo_vermelho()`, desligando os LEDs verde e amarelo e acionando o LED vermelho.

Durante esse estado, o display de 7 segmentos realiza a contagem:

```text
9 → 8 → 7 → 6 → 5
```

Cada valor permanece no display durante aproximadamente **1 segundo**.

## Código

O programa foi desenvolvido em **MicroPython**, utilizando as bibliotecas:

```python
from machine import Pin
import time
```

A biblioteca `machine` é utilizada para configurar e controlar os GPIOs da Raspberry Pi Pico, enquanto a biblioteca `time` é utilizada para implementar as temporizações do sistema.

## Simulação

A simulação foi realizada no ambiente **Wokwi**, permitindo verificar a integração entre a Raspberry Pi Pico, os LEDs, o botão e o display de 7 segmentos.

Durante a simulação, foi possível observar o acionamento sequencial dos LEDs e a contagem numérica no display após o acionamento do botão, validando o funcionamento das entradas, saídas digitais e temporizações implementadas no programa.

https://wokwi.com/projects/476233055822691329

## Autora

Anna Beatriz Pena
