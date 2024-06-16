# Tema: Recursion
## Introducción

Entender que todas las estructuras pueden ser operadas por recursión es crucial, no importa si es un numero, una lista o algo más elaborado como un Arbol. 

Toda recursión necesita: Un caso base, y uno o más casos recursivos.


Por ejemplo, la recusión más simple que podemos hacer es sobre numeros, tiene un caso base (0) y un caso recursivo.
```haskell

factorial 0 = 1
factorial n = n * factorial (n-1)
```

## Como pensar recursivo

Al momento de implementar una función recursiva SIEMPRE se debe pensar en las partes ya resueltas. 
Algo como ¿sí la recursión esta bien implementada qué deberia devolverme la recursión? pensar operacionalmente (es decir, que pasa en cada recursión) puede confundirnos al momento de usar estructuras más complejas.

Por ejemplo, sí yo quiero la sumatoria de un numero, es decir la suma de un `n` por cada numero que lo conforma hasta el 0 ¿qué tendria que darnos el resultado recursivo de hacer `sumatoria 5`? 

Facil, la sumatoria de 5 + la sumatoria de 4

entonces, podemos hacer una definicion recursiva de sumatoria como:

```haskell
sumatoria 0 = 0
sumatoria n = n + sumatoria (n-1)
```


Consejo fundamental al momento de escribir funciones recursivas, el caso base se define ultimo a todo.

