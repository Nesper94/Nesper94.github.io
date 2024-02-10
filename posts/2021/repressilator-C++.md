---
title: 'Simulando el Represilador en C++'
date: 2021-12-21
author: Juan Camilo Arboleda Rivera
categories:
  - Systems biology
  - ODEs
  - Synthetic circuits
---

En este tutorial vamos a simular el comportamiento del circuito genético 
conocido como Represilador. Este circuito fue descrito por Elowitz et. al en 
el año 2000 en su artículo ["A synthetic oscillatory network of 
transcriptional regulators"](https://doi.org/10.1038/35002125).

## ¿Qué es el Represilador?

El Represilador es una red de regulación genética sintética, es decir, no 
existe en la naturaleza sino que fue diseñada y creada en el laboratorio. 
Esta red consiste básicamente en 3 genes: *LacI*, *tetR* y *cI*, los cuales
son todos ellos represores de la expresión genética. Cada gen produce una
proteína que reprime al siguiente gen como se muestra en la siguiente
imagen:

![](repressilator.png){alt="Represilador" width="400" fig-align="center"}

## Código fuente

Puedes descargar el código fuente del represilador 
[aquí](https://github.com/Nesper94/represilador_cpp). Brevemente, lo que 
hacemos es definir una función en la cual le asignamos valores a los 
parámetros del sistema y luego definimos las ecuaciones diferenciales.

Para compilar nuestro código, ejecutamos el siguiente comando:

```bash
g++ -I /path/to/boost/ -o represilador represilador.cpp
```

Para ejecutar el programa y guardar los resultados de la simulación en un 
archivo llamado `rep.tsv`, ejecutamos el siguiente comando:

```bash
./represilador > rep.tsv
```

Ya que tenemos los datos de la simulación, vamos a visualizarlos usando Python.

```python
import matplotlib.pyplot as plt
from pandas import read_csv

df = read_csv('rep.tsv', sep='\t')

plt.figure(figsize=(15,5))
plt.plot(df.Tiempo, df.LacI, 'r', label='LacI')
plt.plot(df.Tiempo, df.TetR, 'y', label='TetR')
plt.plot(df.Tiempo, df.cI, 'b', label='cI')
plt.legend()
```
