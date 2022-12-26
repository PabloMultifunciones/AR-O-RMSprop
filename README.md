# AR-O-RMSprop

### Introduccion

RMSprop es un metodo de Taza de Aprendizaje Adaptativo. Los metodos de Taza de Aprendizaje Adaptativo son una mejora de los metodos de descenso de gradiente tradicionales.

### ¿Que es Rprop?
Es un metodo de algoritmo usado para optimizacion de lotes (full-batch). Este algoritmo intenta resolver el problema de que el gradiente puede variar ampliamente. Algunos gradientes pueden ser muy grandes y otros muy pequeños lo cual puede hacer dificil encontrar un Learning Rate correcto para el algoritmo.

Si usamos aprendizaje de lote completo podemos afrontar este problema con solo utilizar el signo del gradiente. Con esto podemos garantizar que todas las actualizaciones de los pesos van a tener el mismo ancho. Estos ajustes ayudan mucho con los puntos altos y las mesetas porque tomamos pasos suficientemente grandes, incluso con pequeños gradientes. 

Sin embargo no podemos simplemente incrementar los ratios de aprendizaje, porque los pasos vamos tomando con grandes gradientes van a ir siendo incluso mas grandes, lo cual va a resultar en una divergencia.

Rprop combina la idea de solo usar el signo del gradiente con la idea de adaptar el ancho del paso individualmente para cada peso. Entonces en vez de mirar por la magnitud del gradiente, vamos a mirar por el ancho del paso que es definido para un peso en particular. Y ese ancho de paso se adapta individualmente con el tiempo. Para ajustar el ancho del paso para algun peso, debemos seguir el siguiente algoritmo usado:
* Miramos el signo de los ultimos dos gradientes para cada peso.
* Si los dos gradientes tienen el mismo signo significa que vamos en la direccion correcta y que deberiamos acelerar una pequeña fraccion, significando que incrementaremos el ancho del paso miltiplicativamente (Por un factor de 1.2, por ejemplo). Pero si son los signos de los dos ultimos gradientes son diferentes, significa que saltamos sobre el minimo local, por lo tanto deberiamos decrementar el ancho del paso multiplicativamente (Por un factor de 0.5, por ejemplo).
