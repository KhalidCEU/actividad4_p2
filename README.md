## Actividad 4 - Complejidad de algoritmos

Esta actividad se centra en el análisis de diferentes algoritmos y su complejidad.

## Ejercicios

### Ejercicio 34
> ¿Qué es un algoritmo?

Un **algoritmo** es un conjunto de instrucciones o reglas **definidas**, **ordenadas** y **finitas** que permite realizar una actividad mediante pasos sucesivos.

### Ejercicio 35
> Escriba dos algoritmos en Java y esos mismos dos algoritmos en C para resolver el mismo problema.
  Por ejemplo, puede escribir un algoritmo recursivo y otro iterativo (con un bucle) para resolver el problema de la suma de los n primeros números naturales

**Java - Recursivo**
```
public static int sumaRecursiva(int n) {
    if (n <= 1) {
        return n;
    }
    return n + sumaRecursiva(n - 1);
}
```
**C - Recursivo**
```
int suma_recursiva(int n) {
    if (n <= 1) {
        return n;
    }
    return n + suma_recursiva(n - 1);
}
```

**C - Iterativo**

```
int suma_iterativa(int n) {
    int resultado = 0;

    for (int i = 1; i <= n; i++) { 
        resultado += i;
    }

    return resultado;
}
```

**Java - Iterativo**
```
public static int sumaIterativa(int n) {
    int resultado = 0;

    for (int i = 1; i <= n; i++) {
        resultado += i;
    }

    return resultado;
}
```

### Ejercicio 36

> Defina O(n) en términos de un límite de cociente de funciones.

La **notación O(n)** significa que el **tiempo** o **número de operaciones** crece **linealmente** con el **tamaño de la entrada**. Formalmente, es como si hubiera una constante **C** de tal manera que :
```f(n) / n <= C ``` para **valores grandes** de n.

También podemos decir que la función **f(n) pertenece a O(n)** si existe un **límite finito** de ```f(n) / n``` cuando **n tiende a infinito**.

Esto significa que el algoritmo **no crece más rápido** que una **constante multiplicada por n** cuando **n** es **suficientemente grande**.


### Ejercicio 37

> La fórmula para calcular el espacio recorrido por un móvil que se deja caer al vacío (suponiendo v0 = 0) es e = 1/2 gt^2, donde g es la aceleración de la gravedad en la superficie de la tierra, y t el tiempo que está cayendo el móvil. ¿Cuál es la complejidad temporal de este cálculo en
función de t?

En la operación ```e = 1/2 gt^2```, las constantes 1/2 y g son fijas (no dependen de t), con lo cual la unica operacion que varía con **t** es ```t^2``` (equivalente a **t * t**).

Sabemos que para cualquier valor de **t** esta operación siempre toma el mismo tiempo (se realiza la misma cantidad de operaciones), lo que significa que la **complejidad temporal** de este calculo es **O(1) o tiempo constante**.


### Ejercicio 38

> Indique la complejidad temporal asintótica de los siguientes métodos

```
public static String primero(ArrayList<String> lista) {
    return lista.get(0);
}
```

En este método buscamos un elemento por un indice fijo / en este caso el primero, lo que significa que no tendremos que recorrer toda la lista (el tiempo de ejecución tampoco dependerá del tamaño de la lista).

Con lo cual esto tiene una **complejidad O(1)**.


```
public static String nEsimo(ArrayList<String> lista, int n) {
    return lista.get(n);
}
```

En este caso, al igual que el ejemplo anterior accedemos a un elemento de la lista mediante su indice **n**, lo que significa que no tendremos que recorrer la lista ni su tamño influenciará en el tiempo de ejecución.

Con lo cual tambien tiene una **complejidad O(1)**.


### Ejercicio 39

> Calcule la complejidad temporal de los algoritmos del [ejercicio 35](#ejercicio-35)

**Iterativo**
```
public static int sumaIterativa(int n) {
    int resultado = 0;

    for (int i = 1; i <= n; i++) {
        resultado += i;
    }

    return resultado;
}
```

En este algoritmo el numero de iteraciones dependerá de n (cuanto mas grande sea n, mas tardará) y la operación que se realiza dentro de este bucle es una simple suma (operacion de tiempo constante), esto significa que el **tiempo de ejecución crece** de manera **lineal** con n, con lo cual es de complejidad **O(n).**

**Recursivo**
```
public static int sumaRecursiva(int n) {
    if (n <= 1) {
        return n;
    }
    return n + sumaRecursiva(n - 1);
}
```

Al igual que de manera iterativa, aqui el numero de llamadas a la función depende de n , y la operación que se realiza sigue siendo de suma (tiempo constante), con lo cual es de complejidad **O(n)**.


### Ejercicio 40

> Resuelva cualquiera de los apartados del ejercicio 11 y calcule su complejidad temporal

**Metodo elegido**: La potencia n-esima de un numero natural. (iterativo)


```
public static int potencia(int nb, int exponente) {
    int resultado = 1;

    for (int i = 1; i <= exponente; i++) {
        resultado *= nb;
    }

    return resultado;
}
```

En este metodo realizamos una **multiplicacion** dentro del bucle `resultado *= nb;` que es de tiempo constante, es decir de complejidad O(1). Este bucle itera el mismo numero de veces que el exponente, lo que hace que la complejidad de este metodo sea **O(exponente)**;

### Ejercicio 41

> Calcule la complejidad temporal y espacial de cualquiera de los algoritmos (recursivos) del ejercicio 2 (salvo los referentes a la serie de Fibonacci). Compare dichas complejidades con el algoritmo iterativo para resolver el mismo problema

**Metodo elegido**: La desviación típica de una lista de números. (recursivo)

```
public static double desviacionElementosLista(int[] listaNumeros, double media,
        int tallaInicial, int index, double sumaDiferencias) {

    if (index == listaNumeros.length) {
        double varianza = sumaDiferencias / tallaInicial;
        return Math.sqrt(varianza); // retorno desviacion
    }

    double diferenciaCuadrado = Math.pow(listaNumeros[index] - media, 2);
    sumaDiferencias += diferenciaCuadrado;

    return desviacionElementosLista(listaNumeros, media, tallaInicial, index + 1, sumaDiferencias);
}
```

En este caso:
- El método se llama recursivamente hasta que **index** sea igual a la **listaNumeros.length**
- En cada llamada se realizan operaciones de tiempo constante **O(1)** (division, suma, multiplicacion)
- No hay ningún bucle dentro del metodo

El **numero de llamadas** es igual a la **longitud de la lista** y cada llamada realiza un numero **constante** de operaciones, con lo cual es de **complejidad O(n)** donde n = numero de elementos de la lista.

### Ejercicio 42

> Sea un conjunto A con cardinalidad n, y sea l un algoritmo que ejecuta una instrucción para cada elemento del producto cartesiano de A × A. Calcule la complejidad temporal de l en función de n.

El producto cartesiano de un conjunto generará n ^ 2 pares
Supongamos que tenemos un conjunto de **3 elementos** **A = {1, 2, 3}**, esto significa que obtendríamos 3 ^ 2 pares (= 9 pares):
**(1,1) (1,2) (1,3) (2,1) (2,2) (2,3) (3,1) (3,2) (3,3)**

Por lo tanto, la complejidad temporal de l en funcion de n es **O(n^2)** (suponiendo que la insstruccion por cada elemento es una operación de tiempo constante **O(1)**)


### Ejercicio 43

> Calcule la complejidad temporal del siguiente método

```
public static double sumaEltosMatriz(double matriz[][]) {
    double suma = 0;

    for(int i = 0; i < matriz.length; i++) {
        for(int j = 0; j < matriz[i].length; j++) {
            suma += matriz[i][j];
        }
    }
    return suma;
}
```

Analizando este metodo podemos observar que tenemos

- 2 bucles anidados (un **for** dentro de un **for**)
    - El primero itera hasta ```matriz.length``` -> numero de filas, denominemoslo **n**
    - El segundo itera hasta ```matriz[i].length``` -> numero de columnas, denominemoslo **m**
- Una suma dentro del bucle (operacion tiempo constante, complejidad **O(1)**)

El número total de operaciones será **n * m**, con lo cual la complejidad temporal de este método es **O(n*m)**.


### Ejercicio 44

> Escriba un algoritmo que busque un número en un array de enteros. Calcule su complejidad temporal en el caso peor, en el caso mejor y en el caso promedio. Su cabecera será la siguiente: ```public static boolean buscar(int e, int[] array)```

**Implementación**
```
public static boolean buscar(int e, int[] array) {
    for (int i = 0; i <= array.length - 1; i++) {
        if (array[i] == e) {
            return true;
        }
    }
    return false;
}
```

Analizamos los 3 casos:
- Caso **mejor**: Encontramos el elemento en la primera posicion = recorrerá unicamente un elemento, **complejidad O(1)**, tiempo constante.
- Caso **promedio**: Encontramos el elemento en la mitad = recorrerá n/2 elementos, **complejidad O(n)**, tiempo constante. (En Big O notation, **O(n/2)** se simplifica a **O(n)**)
- Caso **peor**: Encontramos el elemento en la ultima posicion = recorrerá todos los elementos de la lista, **complejidad O(n)**

### Ejercicio 45

> Escriba un algoritmo recursivo para buscar un número en un array ordenado de enteros. Su cabecerá será la misma que la del ejercicio 44. Calcule su complejidad en el caso peor.


```
private static boolean buscar(int e, int[] array, int index) {
    if (index >= array.length) {
        return false;
    }

    if (array[index] == e) {
        return true;
    }
    return buscarRecursivo(e, array, index + 1);
}
```

**Caso peor**: cuando el elemento no está en el array o está al final, se recorre el array **únicamente 1 vez**, y se hace una comparacion constante sin más, con lo cual la compejidad sería de **O(n)** .

Si queremos dejar estrictamente la misma cabecera como el ejercicio anterior (**yo personalmente no lo haría de esta manera**), el método quedaría así:

```
public static boolean buscar(int e, int[] array) {
    if (array.length == 0) {
        return false;
    }
    if (array[0] == e) {
        return true;
    }

    int[] nuevoArray = new int[array.length - 1];
    System.arraycopy(array, 1, nuevoArray, 0, array.length - 1);

    return buscar(e, nuevoArray);
}
```

Si lo hacemos de esta manera, el **peor caso** es cuando el elemento no está en el array o está al final, y **se crea un nuevo array** en cada llamada recursiva, lo que genera una complejidad **O(n^2)**.

### Ejercicio 46

> Calcule las complejidades temporal y espacial del algoritmo recursivo para calcular el elemento n-ésimo de la sucesión de Fibonacci.

```
public static int fibonacci(int n) {
    if (n <= 1) {
        return n;
    }
    return fibonacci(n - 1) + fibonacci(n - 2);
}
```

El número total de llamadas recursivas crece exponencialmente con **n**. La complejidad temporal en el caso peor es **O(2^n)** (en cada llamada se hacen 2 llamadas recursivas y es ineficiente para valores grandes de n)

### Ejercicio 47


> Se tiene el siguiente método:

```
public static int sumaNPrimeros(int n) {
    int suma = 0;
    for (int i = 1; i <= n; i++) {
        suma += i;
    }
    return suma;
}
```
> Utilizando el profiler de Netbeans se han medido los tiempos de ejecución
de diferentes llamadas al método (véase el cuadro 1). Explique los resultados

El **tiempo de ejecución** del metodo **sumaNPrimeros(n)** aumenta aproximadamente de forma **lineal** con el tamaño de la entrada debido a su **complejidad temporal O(n)**, lo que se refleja en los resultados del profiler.


### Ejercicio 48

> Se tiene el siguiente método:

```
public static int sumaNMPrimeros(int n) {
    int suma = 0;
    for (int i = 1; i <= n; i++) {
        for(int j = 1; j <= i; j++)
            suma += j;
    }
    return suma;
}
```
> Utilizando el profiler de Netbeans se han medido los tiempos de ejecución
de diferentes llamadas al método (véase el cuadro 2). Explique los resultados


El metodo **sumaNMPrimeros(n)** tiene una **complejidad temporal de O(n^2)** debido a sus **bucles anidados**, lo que explica el crecimiento cuadrático en los tiempos de ejecución. A medida que n aumenta **x 10**, el tiempo de ejecución tambien aumenta.


### Ejercicio 49

> Explique la definición que se muestra a continuación
Sean dos funciones T : N → N y f : N → N. Se dice que T (n) es de orden
f (n), y se escribe T (n) ∈ O(f (n)), si y sólo si existen dos números naturales
k y n0 tales que, para todo m, también natural, que cumpla m > n0, entonces
T (m) ≤ k · f (m)


Esta definicion describe la **Big O notation** que hemos visto hasta ahora para poder medir la **complejidad temporal** de los algoritmos según su **comportamiento** para **entradas grandes**.

Nos explica que **T(n)** es de orden **f(n)** si existe una **constante k** y un **valor n0** a partir del cual **T(n)** **nunca supera** `k * f(n)` para **todos** los **valores de n mayores que n0**.

Es decir, podemos ver **f(n)** como el **límite superior asintótico** para **T(n)**, permitiendo comparar el comportamiento de diferentes algoritmos para entradas grandes.

### Ejercicio 50

> Asumiendo la definición del ejercicio 48, se pide

> 1 . Encontrar k y n0 que muestren que la siguiente función, T : N → N,
es de orden O(log2(n)).
T (n) = 3 · log2(n) + 2.

> 2 . ¿Si T (n) ∈ O(log2(n)), entonces T (n) ∈ O(n)? Justifique la respuesta.

> 3 . ¿Si T (n) ∈ O(log3(n)), entonces T (n) ∈ O(log2(n))? Justifique la respuesta


**R1 :** T (n) = 3 · log2(n) + 2 es **O(log2(n))** porque para **k = 4**  y **n0 = 2** se cumple `T(n) <= k⋅log2(n)` para n > n0

**R2 :** Sí, ```T(n) ∈ O(log2(n))``` implica ```T(n) ∈ O(n)```, porque **log2(n) < n** para n suficientemente grande.
Por ejemplo, si ```T(n) <= k * log2(n)``` para un k y n grandes, entonces ```T(n) <= k⋅n``` también se cumple, ya que ```log2(n)``` **siempre es menor que n** para todo **n >= 1**.


**R3 :** Sí, ```T (n) ∈ O(log3(n))``` implica ```T (n) ∈ O(log2(n))```, porque los logaritmos en diferentes bases solo cambian por una **constante multiplicativa**, es decir ```log3(n) = log2(n) / log2(3)``` lo que significa que los dos **crecen de la misma manera asintóticamente**.


### Ejercicio 51

> Estudie de forma comparativa entre ellas el crecimiento de las siguientes funciones reales de variable real

```
 1. f0(x) = 1
 2. f1(x) = x
 3. f2(x) = x^2
 4. f3(x) = log2(x), y
 5. f4(x) = 2^x
```

1. `f0(x) = 1` : Es una **constante**, no importa cuánto crezca x, siempre vale 1. No tiene crecimiento.
2. `f1(x) = x` : Es una funcion **lineal**, cuanto mas va creciendo **x**, mas crece **f1(x)**. Crece mas rapido que una constante, pero no mas que una cuadratica / exponencial.
3. `f2(x) = x^2` : Es una funcion **cuadratica**, crece mucho mas rapido que una funcion lineal, porque **x^2** crece mucho mas rapido confome **x** vaya aumentando.
4. `f3(x) = log2(x), y` : Es es una funcion **logarítmica**, es mas lenta que la lineal o cuadratica.
5. `f4(x) = 2^x` : Es una funcion **exponencial**, es **la mas rapida** de todas ya que **f4(x)** se **duplica** cada vez que **x aumenta de 1**.

### Ejercicio 52

> Calcule la complejidad temporal asintótica del método f :

```
public static int f(int n) {
    if (n == 0)
        return 1;
    else if (n < 0)
        return -1;
    else {
        int m = 1 / f(n/2) + f(n/2);
        return sumaNPrimeros(m);
    }
}
```

Analicemos los posibles casos:
- Si n = 1 retornamos 1 , lo que implicaría O(1)
- Si n < 0 retornamos -1 , lo que implicaría O(1)
- En el caso recursivo: hacemos **dos llamadas recursivas** a `f(n/2)` (recurrencia **T(n) = 2T(n/2) + O(1)**) y luego realiza la operacion `1 / f(n/2) + f(n/2)` y finalmente llama a otro metodo `sumaNPrimeros(m)`.

Suponiendo que es **m** es proporcional a **n**, `sumaNPrimeros(m)` depende de **m**, podriamos suponer que `sumaPrimeros(m)` es de complejidad **O(n^2)**, con lo cual la recurrencia total sería:

`T(n) = 2T(n/2) + O(n^2)`

Y por lo tanto la complejidad final sería de **O(n^2)**.

### Ejercicio 53

> La complejidad en el caso peor de la inserción en un arraylist es diferente si el array list está ordenado de si no lo está. ¿Es cierta esta afirmación? Justifique la respuesta.

Si el **orden importa** (= si queremos mantener el ArrayList ordenado) entonces la complejidad en el peor caso es
**O(n)** ya que necesitaríamos buscar la posición correcta y **desplazar elementos**.
(PS: la **busqueda** en los elementos puede ser puede ser **O(log n)**, pero el **deplazamiento de elementos** sigue siendo O(n))

Si el **orden no importa**, la complejidad es **O(1) al final** y **O(n) en otras posiciones** debido al desplazamiento de elementos.

Con lo cual podemos decir que la afirmación de que en el **caso peor** de insercion en un ArrayList ordenado vs un ArrayList no ordenado es **diferente** es **falsa**, ya que para ambos casos la complejidad es **O(n)**.

### Ejercicio 54
> Suponga que una instrucción tarda en ejecutarse 10 ns, y que
el tamaño de la entrada es n = 100, se pide calcular el tiempo requerido para
los siguientes números de ejecuciones:

```
 1. log(n)
 2. n
 3. nlog(n)
 4. n^2
 5. n^8 y
 6. 10^n
```

> Realice los cálculos anteriores, pero ahora bajo los siguientes supuestos:

```
1. n = 100.000
2. n = 100.000 y el tiempo de instrucción (o bloque de instrucciones) 1
ms
```

1. `log(n)` = log(100) = 2 * 10 ns = **Z0 ns**
1. `n` = 100 = 100 * 10ns = **1000 ns o 1 microsegundo**
1. `n * log(n)` = 100 * log(100) = 100 * 2 = 200 * 10 ns = **2000 ns o 2 microsegundos**
4. `n ^ 2` = 100 ^ 2 = 10000 * 10ns = **100000 ns o 100 microsegundos**
5. `n ^ 8 y` = (100 ^ 8) y = 10^16 * 10ns * y = **10^17 ns * y**
6. `10^n` = 10 ^ 100 = 10^100 * 10 ns = **10^101 ns** (computacionalmente infinito)

**Suponiendo n = 100.000**

1. `log(n)` = log(10^5) = 5 * 10ns = **50 ns**
1. `n` = 10^5 = 10^5 * 10ns = **10^6 ns o 1 milisegundo**
1. `n * log(n)` = 10^5 * log(10^5) = 10^5 * 5 * 10ns = 5 * 10^6 ns = **5 microsegundos**
4. `n ^ 2` = 10^5 ^ 2 = 10^10 * 10ns = **10^11 ns o 100 segundos**
5. `n ^ 8 y` = (10^5 ^ 8) * 10 = 10^40 * 10ns = **10^41 ns * y** (computacionalmente infinito)
6. `10^n` = 10 ^ (10^5) = 10^100000 * 10ns= **10^100001 ns** (computacionalmente infinito)

**Suponiendo n = 100.000 y tiempo de ejecución 1ms**

1. `log(n)` = log(10^5) = 5 * 1ms = **5 ms**
1. `n` = 10^5 = 10^5 * 1ms = **10^5 ms** o **100 segundos**
1. `n * log(n)` = 10^5 * log(10^5) = 10^5 * 5 * 1ms = **500 segundos**
4. `n ^ 2` = 10^5 ^ 2 = 10^10 * 1ms = **10^7 segundos**
5. `n ^ 8 y` = (10^5 ^ 8) * 10 = 10^40 * 1ms = **10^37 segundos** (computacionalmente infinito)
6. `10^n` = 10 ^ (10^5) = 10^100000 * 1ms = **10^99997 segundos** (computacionalmente infinito)


### Ejercicio 55

> Explique por qué el problema del ajedrez todavía no está resuelto.

El problema del ajedrez todavía no está resulto ya que hay un número de **jugadas posibles por movimiento** tan grande  que computacionalmente es imposible hacer una gran cantidad de calculos en tan poco tiempo para encontrar la solución perfecta. En terminos de **complejidad**, podemos decir que el crecimiento es **exponencial** (el numero de jugadas posibles por movimiento se multiplica).

PS : Por lo menos con el **hardware** que tenemos **hoy en día**, no es posible. Puede que el día que tengamos [ordenadores cuanticos](https://es.wikipedia.org/wiki/Computaci%C3%B3n_cu%C3%A1ntica) eso sea algo muy facil de resolver ;)