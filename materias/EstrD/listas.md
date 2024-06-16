# Tema: Listas
## Introducción
Las listas en haskell sigue el orden que se utiliza en gobstones, es decir, uno solo conoce el primero elemento de la lista (head) y la lista sin el primer elemento (tail). Esta es la base de toda operación sobre listas.


## Recursion sobre listas

La recursión sobre listas tiene unicamente dos casos posibles, una lista vacia o una lista con elementos.


El esquema de recursión sobre listas es exactamente el siguiente.
```haskell
f [] = ....
f (x:xs) = x ... f xs 
```

Puede haber algun caso especifico que necesites hacer algo como lo siguiente
```haskell
f (x:[]) = ....
f (x:xs) = x ... f xs 
```

Pero cualquier cosa que hagas que se aleje de estos dos esquema puede estar mal.


## Recursión sobre dos listas

Las operaciones sobre dos estructuras generalmente suelen ser algo engañosas, porque no siempre necesitas hacer recursión sobre ambas.

Veamos el ejemplo de append (++), append junta dos listas, en este caso sí se intenta hacer recursión sobre los dos elementos la implementación va a estar mal porque necesito JUNTAR las listas sin perder la información de ninguna de las dos.


```haskell
append [] []          = []
append [] ys          = ys
append xs []          = xs
append (x:xs) (y:ys)  = x:y : append xs ys
```
Esta sería la implementación de una persona que:

1. No entendió el fin de la función.
2. No consideró si la operación PIERDE o no datos.
3. No entiende nada y se va a comer un dos en el parcial.

Esta operación NO REQUIERE hacer doble recursión, únicamente la hace sobre UNA de las dos listas.
```haskell
append [] ys          = ys
append (x:xs) ys      = x : append xs ys
```

Pero pongamos de ejemplo otra función: zip :: [a] -> [b] -> [(a, b)]. Esta función toma dos listas y las convierte en una lista de pares.

Pensemos los casos y entendamos la ESTRUCTURA:
1.¿Qué pasa si una lista es más larga que la otra?
2. ¿Esta operación pierde información?


En este caso, se hace recursión sobre AMBAS listas al mismo tiempo. ¿Pero por qué?

Entendamos que si quiero, entre dos listas [a] y [b], obtener una lista [(a,b)], no puedo darle al usuario algo inconsistente. Si una lista se queda vacía pero la otra tiene elementos, ¿qué hago? ¿Pongo valores del tipo a y del tipo b que no estaban originalmente en la lista para rellenar los espacios vacíos? ¿Cuáles serían esos valores?

En este caso, la operación:
1. Pierde datos
2. Hace recursión sobre los dos elementos.


```haskell
zip []    []      = []
zip xs    []      = []
zip []     ys     = []
zip (x:xs) (y:ys) = (x,y) : zip xs ys
```

!!! Esta operación como hace recursión sobre dos elementos al mismo tiempo tiene más casos base !!!! 

Mecanizar esta forma de pensar las operaciones sobre CUALQUIER estructura es vital para no llegar al parcial y hacer cualquier mamarracho.