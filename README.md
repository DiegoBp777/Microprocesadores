# Informe 1. Diseño de la tarjeta de entrenamiento

# Integrantes

* Diego Alexander Barón Pacheco / 140932
* Fredy Vicente Patiño Garzon / 140753
* Santiago Escamilla Marquez / 140843

# Informe

## Índice

1. [Introducción](#1-introducción)
2. [Objetivos](#2-objetivos)
3. [Marco teórico](#3-marco-teórico)
4. [Materiales y componentes](#4-materiales-y-componentes)
5. [Diseño del circuito esquemático](#5-diseño-del-circuito-esquemático)
6. [Esquema realizado en Proteus](#6-esquema-realizado-en-proteus)
7. [Diseño de la PCB](#7-diseño-de-la-pcb)
8. [Evidencias](#8-evidencias)
9. [Verificación del diseño](#9-verificación-del-diseño)
10. [Dificultades encontradas](#10-dificultades-encontradas)
11. [Conclusiones](#11-conclusiones)




## 1. Introducción

En este laboratorio se realizó el diseño de una tarjeta de entrenamiento para microprocesadores utilizando el software Proteus. El objetivo principal fue desarrollar el esquema electrónico de una tarjeta basada en el microcontrolador PIC16F877A, incorporando los elementos necesarios para su funcionamiento y comunicación con dispositivos externos.

El diseño incluye el circuito de alimentación, sistema de reloj mediante cristal de cuarzo, circuito de reset, conectores para los diferentes puertos de entrada y salida del microcontrolador y una interfaz de comunicación serial implementada mediante el circuito integrado MAX232.

Posteriormente, el circuito esquemático fue utilizado como base para realizar el diseño de la PCB, organizando físicamente los componentes y sus conexiones para obtener una tarjeta funcional y apta para fabricación.

## 2. Objetivos

* **2.1 Objetivo general**

Diseñar una tarjeta de entrenamiento basada en el microcontrolador PIC16F877A, utilizando Proteus para desarrollar el esquema electrónico y el diseño de la PCB.

* **2.2 Objetivos específicos**

* Diseñar el circuito esquemático de la tarjeta de entrenamiento en Proteus.
* Implementar correctamente las conexiones del microcontrolador PIC16F877A.
* Incorporar el circuito de reloj mediante cristal de cuarzo.
* Implementar el circuito de reset mediante pulsador y resistencia.
* Incorporar conectores para los puertos de entrada y salida.
* Implementar una interfaz de comunicación serial mediante el MAX232.
* Diseñar la PCB a partir del circuito esquemático.
* Verificar que las conexiones del diseño sean coherentes antes de su fabricación.
  
## 3. Marco teórico

* **3.1 Microcontrolador PIC16F877A**

El **PIC16F877A** es un microcontrolador de la familia PIC que integra en un solo dispositivo una unidad de procesamiento, memoria y diferentes periféricos para el desarrollo de sistemas electrónicos.

El microcontrolador dispone de diferentes puertos de entrada y salida, entre ellos:

* PORTA
* PORTB
* PORTC
* PORTD
* PORTE

Estos puertos permiten conectar sensores, actuadores, módulos de comunicación y otros dispositivos externos.

En la tarjeta diseñada, los diferentes puertos son llevados a conectores para facilitar su utilización durante las prácticas de laboratorio.

* **3.2 Circuito de reloj**

Para que el microcontrolador pueda ejecutar instrucciones necesita una señal de reloj.

En el diseño se utiliza un cristal de cuarzo, conectado a los pines correspondientes al oscilador del PIC16F877A.

El circuito incluye además dos capacitores asociados al cristal:

```text
        C1
         |
OSC1 ----X1---- OSC2
         |
        C2
```
Los capacitores ayudan al correcto funcionamiento del oscilador.

* **3.3 Circuito de reset**

El circuito de reset permite reiniciar el microcontrolador y llevarlo a un estado inicial conocido.

En el diseño se utiliza:

* Un pulsador.
* Una resistencia de aproximadamente 10 kΩ.
* La conexión al pin MCLR/VPP del PIC.

La resistencia mantiene el pin en el nivel lógico correspondiente durante el funcionamiento normal, mientras que el pulsador permite realizar el reinicio manual.

* **3.4 Comunicación serial**

La tarjeta también incorpora una interfaz para comunicación serial mediante el circuito integrado **MAX232.**

El MAX232 permite adaptar los niveles de señal utilizados por el microcontrolador a los niveles requeridos por una interfaz RS-232.

En el diseño se utilizan las señales:

* TX
* RX

que permiten realizar transmisión y recepción de datos.

También se utilizan capacitores externos asociados al MAX232 para su funcionamiento.

## 4. Materiales y componentes

Para la construcción del diseño se utilizaron los siguientes componentes principales:

| Componente           | Cantidad | Función                                        |
| -------------------- | -------: | ---------------------------------------------- |
| PIC16F877A           |        1 | Microcontrolador principal                     |
| MAX232               |        1 | Conversión de niveles para comunicación RS-232 |
| Cristal de cuarzo    |        1 | Generación de señal de reloj                   |
| Capacitores de 15 pF |        2 | Circuito del oscilador                         |
| Capacitor de 1 µF    |   Varios | Circuito del MAX232                            |
| Capacitor de 100 nF  |        1 | Desacoplamiento                                |
| Resistencia de 10 kΩ |        1 | Circuito de reset                              |
| Pulsador             |        1 | Reset del microcontrolador                     |
| Conectores           |   Varios | Acceso a puertos y comunicación                |



## 5. Diseño del circuito esquemático

El circuito fue desarrollado utilizando Proteus, tomando como referencia el esquema suministrado para el laboratorio.

La tarjeta se organizó alrededor del microcontrolador PIC16F877A, al cual se conectaron los diferentes elementos necesarios para su funcionamiento.


* **5.1 Microcontrolador**

El componente principal del circuito es el PIC16F877A.

Sus diferentes pines se conectan a los conectores correspondientes para permitir el acceso a los puertos del microcontrolador.

En el esquema desarrollado se observan conexiones correspondientes a:

* PORTA
* PORTB
* PORTC
* PORTD
* PORTE

Esto permite utilizar la tarjeta como plataforma de pruebas para diferentes aplicaciones de microcontroladores.

* **5.2 Conexión del reset**

El pin **MCLR/VPP** se conecta al circuito de reset mediante una resistencia de **10 kΩ** y un pulsador.

El pulsador permite generar manualmente la señal de reinicio del microcontrolador.

* **5.3 Circuito de oscilador**

El cristal se conecta entre los pines:

```text
OSC1
OSC2
```

del PIC16F877A.

Se utilizan dos capacitores de **15 pF** asociados al cristal.

Esta configuración permite proporcionar al microcontrolador la señal necesaria para ejecutar el programa.

* **5.4 Conectores de los puertos**

Los puertos del microcontrolador fueron llevados a conectores externos.

Esto facilita la conexión de elementos externos durante futuras prácticas.

Los conectores permiten acceder a señales de los diferentes puertos sin necesidad de modificar directamente el circuito principal.

* **5.5 Comunicación mediante MAX232**

El MAX232 se conecta al PORTC del PIC, específicamente utilizando las líneas asociadas a la comunicación serial.

Las señales principales son:
```text
PIC16F877A          MAX232

RC6/TX  ----------> TX
RC7/RX  <---------- RX
```
El MAX232 realiza la adaptación necesaria para la comunicación mediante RS-232.

La salida del MAX232 se conecta posteriormente al conector DB9.

## 6. Esquema realizado en Proteus

El resultado del diseño esquemático realizado en Proteus fue:

***Figura 1. Esquema electrónico de la tarjeta de entrenamiento*** 

![Esquema electrónico](imagenes/esquema_proteus.png)


## 7. Diseño de la PCB

Una vez finalizado y verificado el esquema electrónico, se procedió al diseño de la PCB.

El objetivo de esta etapa fue distribuir físicamente los componentes sobre la placa y realizar las pistas correspondientes entre los diferentes elementos.

Durante el diseño se tuvo en cuenta:

* Distribución organizada de los componentes.
* Facilidad de conexión de los puertos.
* Ubicación del microcontrolador.
* Ubicación del circuito MAX232.
* Ubicación de los conectores.
* Separación adecuada entre las diferentes pistas.
* Facilidad de montaje y posterior utilización de la tarjeta.

* **7.1 Distribución de componentes**

El PIC16F877A se ubicó como componente principal de la tarjeta, mientras que los conectores se distribuyeron alrededor de este para facilitar el acceso a los puertos.

El MAX232 se ubicó cerca del conector de comunicación serial, reduciendo la longitud de las conexiones asociadas a TX y RX.

* **7.2 Pistas de la PCB**

Las pistas fueron diseñadas para conectar eléctricamente los componentes de acuerdo con el esquema desarrollado previamente.

Antes de considerar terminado el diseño se debe verificar:

* Continuidad de las conexiones.
* Ausencia de cortocircuitos.
* Correspondencia entre esquemático y PCB.
* Correcta conexión de alimentación.
* Correcta conexión de GND.
* Correcta conexión del cristal.
* Correcta conexión del circuito de reset.
* Correctas conexiones TX/RX.
* 
## 8. Evidencias

* **8.1 Esquemático en Proteus**
![Esquemático en Proteus](Microprocesadores/Imagenes/esquema proteus)

***Figura 1. Esquemático de la tarjeta de entrenamiento desarrollado en Proteus.***

* **8.2 Diseño PCB**
![Diseño PCB](Imagenes/esquema pcb)

***Figura 2. Diseño de la PCB de la tarjeta de entrenamiento.***

* **8.3 Vista de la PCB**
* 
![Vista 3D de la PCB](Imagenes/diseño pcb)

***Figura 3. Vista tridimensional de la tarjeta diseñada.***

## 9. Verificación del diseño

Una vez realizado el esquemático, se revisaron las conexiones de los principales bloques del circuito.

| Bloque       | Verificación |
| ------------ | ------------ |
| PIC16F877A   | ✅            |
| Alimentación | ✅            |
| Reset        | ✅            |
| Oscilador    | ✅            |
| PORTA        | ✅            |
| PORTB        | ✅            |
| PORTC        | ✅            |
| PORTD        | ✅            |
| PORTE        | ✅            |
| MAX232       | ✅            |
| Conector DB9 | ✅            |
| Diseño PCB   | ✅            |

La verificación permitió comprobar que los diferentes bloques se encuentran interconectados de acuerdo con el diseño planteado.

## 10. Dificultades encontradas

Durante el desarrollo del laboratorio se presentaron algunos aspectos que requirieron especial atención.

Uno de los principales retos fue realizar correctamente las conexiones entre los numerosos pines del PIC16F877A y los diferentes conectores de la tarjeta.

También fue necesario verificar cuidadosamente las conexiones del circuito de reloj y del circuito de reset, debido a que estos elementos son fundamentales para el funcionamiento del microcontrolador.

Otro aspecto importante fue la conexión del MAX232, debido a que las señales de transmisión y recepción deben conectarse correctamente para permitir la comunicación serial.

Finalmente, durante el diseño de la PCB fue necesario organizar adecuadamente los componentes y las pistas para evitar cruces y posibles cortocircuitos.

## 11. Conclusiones

El desarrollo de este laboratorio permitió aplicar conceptos relacionados con el diseño de sistemas basados en microcontroladores, utilizando Proteus como herramienta para la elaboración del circuito esquemático y la PCB.

Se logró desarrollar una tarjeta de entrenamiento basada en el PIC16F877A, incorporando los elementos fundamentales para su funcionamiento, como el circuito de reloj, el sistema de reset, los conectores de los puertos y la interfaz de comunicación serial mediante el MAX232.

El proceso también permitió comprender la importancia de realizar una correcta organización de los componentes y las conexiones antes de pasar del esquemático al diseño físico de la PCB.

Finalmente, el laboratorio permitió adquirir experiencia en el diseño electrónico orientado a sistemas con microcontroladores, dejando como resultado una tarjeta que puede ser utilizada posteriormente para realizar diferentes prácticas y aplicaciones.
