# Algoritmo_Jhonsson
Implementación del algoritmo de Jhonsson para secuenciación de 3 máquinas en un sistema Flowshop con n tareas.
Se aplica el algoritmo de Johnson para determinar la secuenciación.
Pseudocodígo:

**1° Paso Matriz temporal para aplicar la secuenciación**


```
m(n,3) #donde n corresponde al número de trabajos a procesar
    -En la primer columna se asigna el indicativo de la tarea
    -En la segunda columna los tiempos de procesamiento de la primer máquina
    -En la tercer columna los tiempos de procesamiento de la tercer máquina

Sec(n) #Vector que almacena la secuenciación final
```
**2° Paso Adaptar el problema de 3 Máquinas a 2 Máquinas**

```
  For i=1 -> n
    m[i,1]= M1(i)+M2(i)
    m[i,2]= M2(i)+M3(i)
```
**3° Paso: Definir la función de búsqueda para el indicativo de la tarea**


```
Busqueda(Tarea a buscar [x],Matriz de búsqueda [M],Indicativo de la máquina a realizar búsqueda [j])
  k1=0 #contador
  While x diferente m[k1,j[
    k1=k1+1
  Retornar (k1)# se devuelve la posición de la tarea a asignar
```
**4° Paso: Aplicar la regla de Johnson**


```
k=0 #contador de las tareas a asignar en orden ascendente
l=n #contador de las tareas a asignar en orden descendente
Mientras k <= n #Critero para la detención del algortimo
  k=k+1
  l=l+1
    #buscar los tiempos mínimos de las actividades por programar en la matriz temporal
  n1=MinP(m(M1))
  n2=MinP(m(M2))
    #Condicional para identificar la máquina con mínimo tiempo de procesamiento en la actividad
  If n1 >= n2
    x=n1
    j=1
  else
    x=n2
    j=n2
    #Aplicar la función de búsqueda
  mm=buscar(x,m,j) #tarea a secuenciar
    #Aplicar la regla de secuenciación 
  If j=1 
    sec[i+1] = mm # se organiza en orden ascendente
  else if j=2
    sec[i-1]=mm # se organiza de forma descendente
  #eliminar la tarea que ya fue asignada de la matriz temporal
  delete(m(mm))
  ```
Repetir el paso 4 hasta que todas las tareas sean asignadas
