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