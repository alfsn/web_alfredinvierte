---
title: "Deterioro de ETFs apalancados"
description: "Un riesgo a conocer en un producto especializado."
pubDate: 2020-08-31
---


En el presente estudio, repasaremos el proceso conocido como deterioro o beta decay para fondos apalancados.

A tal propósito proponemos un proceso estocástico como índice benchmark. En segunda instancia, evaluamos los rendimientos de un fondo apalancado, basado en este benchmark.
Luego, estimamos su deterioro y sugerimos la aproximación para su eliminación.

# Armado del índice

![Caminata aleatoria Gaussiana](/blog-images/apalancados/1.png)


Para representar el índice, el proceso estocástico a utilizar es una caminata aleatoria Gaussiana. Esta se caracteriza por ser un proceso discreto en el cual:










Es decir, ante cada paso, hay una innovación normal independiente de las previas.

Este proceso, en el límite, converge a un proceso de Weiner, en tiempo contínuo.

La caminata aleatoria es una martingala, lo cual implica que su valor esperado para el próximo paso es igual a su valor presente.

En la práctica, esto implica que el proceso es una colocación "actuarialmente justa", no tiene expectativa condicional de ganancia o pérdida respecto al valor actual.

Existen diversos índices financieros que pueden tomarse como ejemplos alternativos, por ejemplo el S&P500 (replicado por el ETF SPY), el NASDAQ (ETF: QQQ), o el Merval.

Sin embargo, el comportamiento de estos índices difiere fuertemente de la caminata aleatoria ya que las distribuciones marginales no son normales y existe heterocedasticidad condicional autorregresiva (efectos ARCH), entre otras diferencias.

![Rendimiento acumulado del índice](/blog-images/apalancados/2.png)


El retorno acumulado a través de los 1000 dias fue de 10.36%

## Fondos apalancados
A su vez, existen fondos que apuntan a generar un múltiplo de los rendimientos diarios de estos índices.
Por ejemplo, para el índice S&P500:

El ETF UPRO busca triplicar el rendimiento diario
    Factor de apalancamiento = 3x
El ETF SH busca tener el rendimiento inverso al índice
    Apalancamiento = -1x

Mostramos los rendimientos apalancados por un factor de relativos al índice.

### Advertencia
Estos fondos, dadas sus características de apalancamiento y deterioro, son de altísimo riesgo, y sólo deberán ser utilizados previa asesoría por un profesional financiero. Este trabajo tiene como objetivo exclusivo la divulgación y no constituye una recomendación de inversión.

![Rendimientos apalancados](/blog-images/apalancados/3.png)
El rendimiento del índice fue de 10.36% mientras que el fondo apalancado 3 veces rindió 1.95%
## Deterioro
Al sostener estos activos en el largo plazo, nos exponemos al deterioro.  
Esto ocurre por la capitalización diaria de estos productos.
Imaginemos dos días con subas del 2%.
(1+2%)(1+2%)-1=4.04%

Si no hubiera deterioro, esperaríamos que nuestro fondo $3$x rinda
3x(4.04%)=12.12%

Sin embargo, nos encontramos que rindió:
(1+3x2%)(1+3x2%)-1=12.36%

### La causa
Esta diferencia se debe a que el fondo apalancado capitalizó más rápidamente.
Es decir, si poníamos 100 en ambos fondos, los saldos serían de 102 y 106 luego del primer día. Entonces, las ganancias del segundo día se generan sobre distintos montos.  
Es decir, 102x2%=2.04 mientras que 106 (3x2%)=6.36 > 2.04x3

Vemos que el deterioro aumenta con el tiempo de tenencia sin rebalanceo.
![Deterioro del fondo apalancado](/blog-images/apalancados/4.png)
El deterioro al final de la muestra fue de -29.13%
### La complicación
El deterioro tiene la característica de ser dependiente en trayectoria (path dependent). Es decir, el deterioro que se observe depende de la secuencia específica de rendimientos.

#### A mas volatilidad, más deterioro
Comparamos el deterioro de un fondo con un índice subyacente con el doble de volatilidad y la misma realización de pasos. Observamos rápidamente que el deterioro es una función creciente de la volatilidad.
![Deterioro con doble volatilidad](/blog-images/apalancados/5.png)
Por lo tanto, un fondo como TECL, que busca generar un rendimiento 3x del índice de tecnológicas del NASDAQ está mucho más expuesto al deterioro que un fondo como TMF, que busca triplicar el rendimiento de bonos del Tesoro de larga duración.
## La solución
El fondo ideal no tendría desvío. Cómo aproximar esta característica?

El desvío se produce por la capitalización diaria del fondo.
Por esto, para corregirlo, debemos hacer rebalanceos: correcciones diarias en el monto del fondo que reestablezcan la base original para el próximo día.

Volviendo a nuestro ejemplo anterior:
Esperábamos que nuestro fondo 3x rinda
3⋅(4.04%)=12.12%
Por lo tanto, deberiamos rebalancear entre el primer día y el segundo:
(1+3⋅2%)⋅(1−0.214%)⋅(1+3⋅2%)−1=12.12%
Esta resta de fondos que debemos hacerle es equivalente al deterioro generado entre un día y otro.

Para mantener el deterioro en 0, cuando el fondo genera ganancias, deberemos restar fondos, e incorporarlos cuando genera pérdidas.
Este rebalanceo logra que el monto de base sobre el cual buscamos generar los rendimientos sea siempre el mismo.
![Rendimiento del fondo apalancado y rebalanceado](/blog-images/apalancados/6.png)
El rendimiento del índice fue de 10.36% mientras que el fondo apalancado 3 veces y rebalanceado rindió 31.08%.
