# Ejercicio Hadoop






**Yesenia Rodriguez**
**Karla Medina**

I.	¿Cuántos distritos electorales contiene el archivo votacion.csv?

```
  GNU nano 2.9.3                     Mapper1.py

import sys

for Line in sys.stdin:
        Data = Line.strip().split(",")
        if len(Data) == 4:
                hora, genero, distrito, candidato = Data
                print ("{0}\t".format(distrito))


```

```
  GNU nano 2.9.3                     Reducer1.py

Acumulados = 0
DistAnt = None

for line in sys.stdin:
    DataIn = line.strip()
    esteDist  = DataIn

    if DistAnt and DistAnt != esteDist:
       Acumulados += 1
    DistAnt = esteDist
if DistAnt != None:
  Acumulados += 1

print ('1. El número de registros es {0}' .format(Acumulados))


```

![](pregunta1.png 'label')



II.	¿Cuántas encuestas se obtuvieron por distrito electoral? ¿En qué distrito se capturaron más encuestas? ¿En cuál menos?

```
  GNU nano 2.9.3                      Mapper2.py

#!/usr/bin/python3



import sys

for Line in sys.stdin:
        Data = Line.strip().split(",")
        if len(Data) == 4:
                hora, genero, distrito, candidato = Data
                print ("{0}\t{1}".format(distrito,1))


```


```
  GNU nano 2.9.3                     Reducer2.py

    esteCandidato, esteValor  = DataIn

    if candidatoAnt and candidatoAnt != esteCandidato:
        print (candidatoAnt, "\t", Acumulados)
        candidatoAnt = esteCandidato;
        Acumulados = 0

    candidatoAnt = esteCandidato
    Acumulados += 1

if candidatoAnt != None:
    print (candidatoAnt, "\t", Acumulados)
```

![](pregunta2.png 'label')

