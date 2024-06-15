# Guia de supervivencia para: Introducción a la programación
## Introducción
Introducción a la programación, a pesar de ser la primera materia de programación, sigue siendo relevante durante toda la carrera. Cuando se organizó la carrera, se pensó en hacer de esta materia un pilar fundamental de la licenciatura.

No subestimen la materia porque el lenguaje sea de "juguete"; la mayoría de los compañeros que ponen el foco en que el lenguaje "no es real" se comen un dos en la nota final y vuelven el próximo cuatrimestre porque no entendieron la verdadera esencia de la materia.

## Cursada
Durante la cursada hay que prestar completa atención a los nombres de los procedimientos, funciones, parámetros y variables, así como a la estructura de la documentación (Propósito, Precondición, Parámetros, Recorrido y Tipo), porque esto es lo que se corrige. No importa si podés solucionar el ejercicio sin ninguna de estas cosas; la idea de la materia es que aprendas a documentar tus soluciones y crear buenas descripciones para solucionar problemas.

Mecanizar la escritura de la documentación es la mitad del proceso para entregar una solución válida. Confundir un "Describe" con un "Indica" puede ser fatal para la nota de tu parcial.

Aquí hay un ejemplo del mismo procedimiento con una documentación correcta e incorrecta.

#### Documentación incorrecta
```javascript
procedure LlenarTablero(bolita){
  /*
  Proposito: Llena el tablero de bolitas
  Precondicion: Ninguna
  Parametros:
    bolita: Color
  */
}
```

#### Documentación correcta
```javascript
procedure LlenarTableroConBolitasDeColor_(colorAponer){
  /*
  Proposito: Llena el tablero de bolitas del color <colorAponer>
  Precondicion: Ninguna
  Recorrido: 
    Es un recorrido del tablero por celdas desde la esquina
    Norte-Este hasta la celda Sur-Oeste.
  Parametros
    colorAponer: Color elegido para poner en el tablero - Color
  */
}
```

Si bien la segunda solución es más extensa y parece engorrosa, hay que entender algo: los programas DESCRIBEN soluciones a problemas y el primer ejemplo es CERO descriptivo.

En el segundo ejemplo, aún sacando el nombre del procedimiento, podríamos entender cuál va a ser el estado final del tablero después de llamarlo.

```javascript
procedure ...(colorAponer){
  /*
  Proposito: Llena el tablero de bolitas del color <colorAponer>
  Precondicion: Ninguna
  Recorrido: 
    Es un recorrido del tablero por celdas desde la esquina
    Norte-Este hasta la celda Sur-Oeste.
  Parametros
    colorAponer: Color elegido para poner en el tablero - Color
  */
}
```

Si le dan bola a esto, la mitad de la materia está aprobada.



## Parcial
Ahora, momento parcial. ¿Qué hago?

Bueno, recomendaciones. No sean ratones con las hojas, una hoja por procedimiento o función, y fundamental: PRIMERO escribo el contrato.

Se consideran desaprobados los ejercicios donde la solución (el código) no haga lo que la documentación describe.

```javascript
procedure ...(){
  /*
  Proposito: Quita todas las bolitas de la celda 
  Precondicion: Ninguna
  */
 if (hayBolitas(Azul)){
  QuitarTodas()
 }
}
```
En este ejemplo, el propósito dice que Quita todas las bolitas de la celda, pero la solución quita todas las bolitas de la celda SOLO SI hay bolitas azules.

Otro tip más, para facilitar la documentación de los ejercicios que impliquen un recorrido, uno puede hablar de la forma del recorrido (si es por celdas, por filas, por columnas, etc.) y qué subtarea ejecuta en cada paso.
Acá dos ejemplos BIEN DOCUMENTADOS e igual de válidos.

### Documentación dificil
```javascript
function contarLosEnanosDelJardin(){
  /*
  Proposito: Describe la cantidad total de enanos en el jardin
  Precondicion: Ninguna
  Recorrido: 
    Es un recorrido del tablero por filas desde la esquina Norte-Oeste sumando la cantidad
    de enanos que hay en cada fila del tablero 
  Tipo: Numero
  */
  IrAlInicioDelRecorrido()
  cantidadTotalEnanos := cantidadDeEnanosDeLaFila()
  while(quedanFilasPorRecorrer()){
    MoverSiguienteFila()
    cantidadTotalEnanos = cantidadTotalEnanos + cantidadDeEnanosDeLaFila()
  }

  return (cantidadTotalEnanos)
}
```


```javascript
function cantidadDeEnanosDeLaFila(){
  /*
  Proposito: Describe la cantidad total de enanos en la fila del jardin
  Precondicion: Ninguna
  Recorrido: 
    Es un recorrido del tablero desde el Oeste hasta el Este sumando
    la cantidad de enanos que hay en cada celda 
  Tipo: Numero
  */
  cantidadTotalEnanos := cantidadDeEnanosDeLaCelda()
  while(puedeMover(Este)){
    Mover(Este)
    cantidadTotalEnanos = cantidadTotalEnanos + cantidadDeEnanosDeLaCelda()
  }

  return (cantidadTotalEnanos)
}
```

### Documentación facil
```javascript
function contarLosEnanosDelJardin(){
  /*
  Proposito: Describe la cantidad total de enanos en el jardin
  Precondicion: Ninguna
  Recorrido: 
    Es un recorrido del tablero por filas desde el Norte-Oeste sumando la
    cantidadDeEnanosDeLaFila() 
  Tipo: Numero
  */
  IrAlInicioDelRecorrido()
  cantidadTotalEnanos := cantidadDeEnanosDeLaFila()
  while(quedanFilasPorRecorrer()){
    MoverSiguienteFila()
    cantidadTotalEnanos = cantidadTotalEnanos + cantidadDeEnanosDeLaFila()
  }

  return (cantidadTotalEnanos)
}
```


```javascript
function cantidadDeEnanosDeLaFila(){
  /*
  Proposito: Describe la cantidad total de enanos en la fila del jardin
  Precondicion: Ninguna
  Recorrido: 
    Es un recorrido del tablero desde el Oeste hasta el Este sumando
    cantidadDeEnanosDeLaCelda()
  Tipo: Numero
  */
  cantidadTotalEnanos := cantidadDeEnanosDeLaCelda()
  while(puedeMover(Este)){
    Mover(Este)
    cantidadTotalEnanos = cantidadTotalEnanos + cantidadDeEnanosDeLaCelda()
  }

  return (cantidadTotalEnanos)
}
```


La abstracción es importante, pero no redefinas cosas que ya existen. Antes del parcial, repasá las prácticas y anotá los procedimientos y funciones que creas convenientes (Siempre que hablen de bolitas o celdas, PUEDE que te sirvan para evitar definir una función/procedimiento). Cuando los uses, poné un comentario al estilo.

```javascript 
Poner_DeColor_(9, Rojo) //Practica x ejercicio y
```


# Conclusiones

Introducción a la programación es una materia dura que castiga mucho a los que no estan al día con las practicas, sí la subestimas la recursas. 

