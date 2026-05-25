# Segunda parte: barrido del espectro FM en Bogotá

En esta segunda parte del laboratorio se usa el RTL-SDR junto con una antena para observar el espectro electromagnético de Bogotá dentro de la banda de radio FM comercial.

El objetivo ya no es solamente escuchar una emisora, sino recorrer la banda FM, detectar las emisiones presentes, estimar su frecuencia central, calcular su ancho de banda aproximado y organizar los resultados en un reporte.

La banda analizada corresponde a FM comercial, entre:

```text
88 MHz a 108 MHz
```

## Objetivo de la segunda parte

Detectar y clasificar las señales de radio FM presentes en Bogotá usando un barrido de frecuencia con SDR.

Para cada emisión encontrada se busca estimar:

| Parámetro | Qué significa |
|---|---|
| Frecuencia central | Punto principal donde está ubicada la emisora |
| Ancho de banda | Espacio aproximado que ocupa la señal en el espectro |
| Potencia relativa | Qué tan fuerte se observa la señal en la medición |
| Estado normativo | Si la señal parece estar dentro de lo esperado o no |

El resultado final es una tabla de emisiones detectadas y un reporte sencillo sobre qué tan ordenado se observa el uso de la banda FM.

De forma general, para este laboratorio se tienen en cuenta estas ideas:

| Criterio | Referencia usada |
|---|---|
| Banda FM comercial | 88 MHz a 108 MHz |
| Canalización | Frecuencias centrales separadas cada 100 kHz |
| Parámetros importantes | Frecuencia de operación, potencia, clase de emisión y ancho de banda |
| Revisión práctica | Comparar si cada señal cae dentro de la banda FM y si su ancho de banda es razonable |

## Metodología de barrido

El sistema realiza un recorrido por la banda FM comercial. En cada paso del barrido, el SDR se sintoniza en una frecuencia central y captura un bloque de muestras I/Q.

Con esas muestras se calcula la PSD para observar dónde hay energía concentrada. Si aparece un pico de potencia suficientemente alto, el sistema lo marca como una posible emisión FM.

El proceso general es:

```text
Inicio del barrido
    │
    ▼
Sintonizar una frecuencia
    │
    ▼
Capturar muestras I/Q
    │
    ▼
Calcular PSD
    │
    ▼
Detectar picos de potencia
    │
    ▼
Estimar Fc, BW y potencia
    │
    ▼
Guardar emisión encontrada
    │
    ▼
Avanzar a la siguiente frecuencia
```

## Clasificación de emisiones detectadas

Cada señal encontrada se clasifica de forma sencilla según su posición y su forma espectral.

| Clasificación | Descripción |
|---|---|
| Emisión válida | Está dentro de 88-108 MHz y tiene un ancho de banda esperado para FM |
| Emisión débil | Se detecta, pero con baja potencia relativa |
| Emisión ancha | Ocupa más ancho de banda del esperado |
| Emisión desplazada | Su frecuencia central no coincide bien con la canalización esperada |
| Posible interferencia | Señal irregular, ruido fuerte o energía fuera de lugar |
| No concluyente | La medición no permite decidir con claridad |

Esta clasificación es aproximada, porque depende de la antena, la ubicación, la ganancia del SDR y el ruido del ambiente.

## Reporte 

- ¿Cuántas emisiones se encontraron?
- ¿Cuántas parecen estar dentro de la banda FM comercial?
- ¿Cuántas tienen una frecuencia central bien ubicada?
- ¿Cuántas ocupan un ancho de banda razonable?
- ¿Se observan señales solapadas o posibles interferencias?
- ¿Hay emisiones que deberían revisarse con un equipo de medición más preciso?

## Posible Conclusión

Durante el barrido de la banda FM comercial en Bogotá se detectaron varias emisiones entre 88 MHz y 108 MHz. La mayoría de señales observadas se ubicaron cerca de frecuencias esperadas y presentaron un ancho de banda razonable para FM. Algunas señales mostraron mayor ocupación espectral o baja separación respecto a emisiones cercanas, por lo que se clasifican como señales a revisar. Debido a que la medición fue realizada con un SDR de bajo costo y una antena de laboratorio, los resultados deben tomarse como una estimación académica y no como una certificación oficial.
