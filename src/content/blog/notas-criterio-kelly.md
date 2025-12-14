---
title: "Notas sobre el criterio de Kelly"
description: "Una introducción a la herramienta clave para position sizing."
pubDate: 2021-10-25
---

Un amigo millonario les ofrece un juego, lanzan una moneda al aire y adivinás cara o ceca.

Si ganas, te llevas el triple.
Si no, perdés lo que invertiste.

Podemos jugar muchas veces, solo con $100 iniciales. Cómo dividir las jugadas?
Entra el criterio de Kelly.

J. L. Kelly usó los conceptos de la Teoría de la Información de Claude Shannon aplicados a los tamaños óptimos de apuestas. El criterio fue usado por grandes magnates como Edward Thorp (alumno de Shannon) para ganar al blackjack y fundar su propio hedge fund.


### Volviendo a nuestro juego:
> invertimos $100.

Esperamos recibir
> $100 x 3 = $300 si ganamos
> $100 x 0 = $0 si perdemos

El valor esperado de la apuesta es:
VE = 50% x $300 + 50% x $0 = $150

Como es mayor que nuestra inversión, es un buen negocio. ¿Vamos all in?
Si buscamos maximizar el valor esperado, SI: ALL IN, jugamos todo nuestro monto, todas las veces.

### El problema: 
### esto nos lleva a la RUINA. 
Después de muchos juegos eventualmente perdemos todo y no podemos seguir jugando

Como optimizar el crecimiento evitando la ruina?
Si invertimos una fracción (f) de nuestro capital obtenemos

> $100 x 3 x f + (1-f) x $100 si ganamos

> $100 x 0 x f + (1-f) x $100 si perdemos   

Kelly propone maximizar el valor esperado *del logaritmo* del capital. Esto es porque el logaritmo es aditivo en jugadas repetidas y aplica la ley de grandes números.

Invertir según lo que indica esta fórmula maximiza el crecimiento geométrico de nuestro capital (en el largo plazo).

#### Cuidado
El criterio de Kelly es "máximamente agresivo":  muchos usuarios de la fórmula la usan para obtener un techo, y suelen invertir una fracción de lo que sugiere (eg. half-Kelly)
