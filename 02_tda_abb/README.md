<details>
    <summary>
		Información
    </summary>
		Martina Garibotti.
		Diciembre 2020.
		Universidad de Buenos Aires, Facultad de Ingeniería.
		7541 - Algoritmos y Programación - Curso 4 Mendez.
</details>

TDA ÁRBOL
==========

Introducción
------------

En el siguiente trabajo se tiene por objetivo cumplir con el contrato pedido 
para recrear la implementación de una biblioteca que permita hacer uso de los
árboles binarios de búsqueda.

Marco Teórico
-------------

### Árbol Binario

Un árbol binario es una estructura compuesta por nodos. Mediante los nodos se 
vinculan a otros sub-árboles. Este tipo de árbol se caracteriza porque sus 
sub-árboles se dividen en izquierdo y derecho.

El árbol guarda una referencia a su nodo raíz y dicho nodo a los sub-árboles 
siguientes, los cuales se denominan hijos. Si un nodo no tiene hijos, dicho
nodo es una hoja del árbol.

Los elementos que se insertan en los árboles, se insertan por sus hojas. Si un 
árbol se encuentra vacío, sin raíz, y el primer elemento en insertarse se 
convertirá en la raíz del árbol.

La altura de un nodo esta dada por la longitud (número de aristas) del camino 
mas largo de dicho nodo a una hoja de sus sub-árboles siguientes.

Sus operaciones son:
- crear
- destruir
- esta_vacio
- insertar
- eliminar
- buscar
- recorrer

Los árboles binarios no son de mucha utilidad ya que no tienen especificado 
ningún tipo de regla para poder insertar en él elementos, pero de ellos derivan 
varios tipos de árboles, como lo son los árboles binarios de búsqueda.

### Árbol Binario de Búsqueda (ABB)

Estos árboles agregan una condición importante a los árboles binarios y es que
mediante una clave, es posible reconocer que en los sub-árboles izquierdos
las claves serán menores a las de los sub-árboles derechos. Ademas los
sub-árboles izquierdos y derechos también son ABB.

Son árboles de comparación, los cuales permiten tener las ventajas de las 
listas enlazadas y ademas obtener la velocidad de la búsqueda binaria mediante 
el aprovechamiento de la estructura misma del árbol.

Tienen las mismas operaciones mencionadas para los árboles binarios.

Sin embargo, es importante en estos árboles hablar de su balance o equilibrio.
Un árbol binario equilibrado es aquel en que la altura de los sub-árboles 
izquierdo y derecho de cualquier nodo nunca difiere en mas de una unidad.
Cuando se pierde esta cualidad, se dice que se encuentra desbalanceado y
su estructura se vuelve desfavorable para la realización de ciertos algoritmos.
En el peor de los casos, dicho árbol puede verse degenerado en lista.

### Sobre el destructor

La ventaja de tener un destructor en el TDA es que la tarea de liberar la 
memoria no va a depender del usuario. La misma estructura del árbol es capaz de 
conservar los punteros a todos los elementos del cual el usuario haga uso, 
durante el tiempo que lo requiera. Ademas es importante que el usuario no haga 
uso o modificaciones de los elementos mientras están en el árbol porque lo 
pueden dejar invalido: si modifica una clave o libera un elemento, dificultará 
el acceso a los nodos siguientes.

### Complejidad de las operaciones

Durante el estudio de algoritmos se han desarrollado distintos enfoques para 
encasillar el estudio de la performance de los programas. Este análisis se
concentra en determinar el crecimiento del peor de los casos en lo que respecta
a la eficiencia de un algoritmo, lo que se denomina el upper-bound.

Se utilizara la notación Bachmann-Landau o notación asintótica o Big-O. Esta
notación matemática describe el comportamiento de una función en el limite, es
decir, cuando el argumento tiende hacia un valor particular o al infinito.
Caracteriza a la función según su tasa de crecimiento, la cual también puede
referirse como orden de una función. Esta notación unicamente provee un límite
superior sobre la tasa de crecimiento de la función en análisis.

Cuando se trabaja con notación asintótica siempre se desprecian las constantes
y las funciones de menor orden.

| Operación | Complejidad | Motivo
|:---:|:---:|:---:
| arbol_crear | O(1) | Alocar la memoria e inicializar los valores se suponen de O(1)
||||
| arbol_destruir | O(n) | Liberar la memoria del árbol se supone O(1) pero también
||| deben liberarse los nodos que puedan permanecer en el árbol, por lo cual para n nodos
||| se repite la acción de liberar nodos (O(1)) n veces.
||||
| arbol_insertar | O(n) | Los elementos que se insertan deben insertarse en hojas, por
||| lo cual insertar un nodo en un árbol desbalanceado y degenerado en lista alcanza una
||| complejidad de O(n) al deber iterar sobre n nodos.
||||
| arbol_borrar | O(n) | Eliminar un elemento en un árbol desbalanceado y degenerado en
||| lista, alcanza la complejidad de O(n) cuando se desea eliminar un nodo hoja al deber
||| iterarse sobre n nodos.
||||
| arbol_buscar | O(n) | Buscar un elemento en un árbol desbalanceado y degenerado en lista
||| tiene una complejidad O(n) por las mismas razones antes enunciadas.
||||
| arbol_raiz | O(1) | El árbol conoce su raíz, por lo cual devolver su valor es O(1)
||||
| arbol_vacio | O(1) | Basta comprobar que se tenga un árbol y el árbol tenga raíz para
||| devolver verdadero o falso a la pregunta si está vacío, por lo cual su complejidad es O(1)
||||
| arbol\_recorrer\_* | O(n) | Se recorre cada elemento del árbol por lo cual en una correcta
||| implementación, iterar n elementos llevan a una complejidad O(n)
||||
| abb_con_cada_elemento | O(n) | Se itera sobre cada elemento del arbol por lo cual en una
||| correcta implementación, iterar sobre n elementos llevan a una complejidad O(n)

Compilación
-----------

En el directorio encontrarás un archivo Makefile que te permitirá una
compilación más sencilla. Se explican las reglas que contiene:

- `make lint`
  - Revisa los archivos .c en el directorio en busca de errores de
sintaxis. Requiere `cppcheck`

- `make %.o`
  - Compila los archivos .c junto a su cabecera para obtener un
programa objeto. Si ya existía en el directorio, es actualizado.
Requiere `gcc`

- `make minipruebas`
  - Compila y ejecuta las minipruebas recomendadas por la
cátedra, las cuales no son exhaustivas ni suficientes para probar las
implementaciones.

- `make maspruebas`
  - Compila y ejecuta más pruebas.

- `make debug`
  - Se corre el ejecutable junto al debugger.

- `make clean`
  - Elimina los archivos producidos por las reglas del Makefile

Ejecución
---------

En la sección anterior se describieron los comandos definidos para
compilar y ejecutar el programa.

Es recomendable que el usuario tenga instalado Valgrind para verificar que
no haya pérdidas de memoria en su programa.

Sobre la implementación
----------------------

Al publicar un TDA, es recomendable no incluir la estructura del TDA
para que el usuario sólo haga uso de las operaciones diseñadas por el
implementador. De esta forma, si la implementación es buena, se evitan
problemas que surgen al hacer uso del TDA.

Las operaciones deben estar fuertemente testeadas, es decir, sometidas a 
distintas pruebas bajo distintos casos, para asegurarle al usuario que no 
encontrará fallas en la ejecución del programa producidas por las 
implementaciones del TDA.

Algunas menciones para hacer sobre las implementaciones son:

- En el árbol se insertan punteros, por lo cuál es necesario que los elementos
sigan en memoria para que el árbol siga siendo válido. Con esto en cuenta,
una vez que se insertan los elementos, quedan ordenados de forma creciente por
su clave, por lo cuál es importante que el usuario no la modifique o no manipule
al elemento mientras este esté en el árbol porque lo puede invalidar.

- `arbol_insertar()`: depende del comparador implementado por el usuario. 
Cuando se desee insertar dos claves iguales, la segunda se insertará a en el
sub-árbol izquierdo a la primera.

- `arbol_borrar()`: se distinguen 4 casos que se pueden dar cuando se desee 
borrar un elemento. Si el nodo donde se encuentra no tiene hijos, eliminarlo no 
llevará más complicaciones que liberar el elemento, el nodo y reemplazarlo por 
NULL en la estructura. Si el nodo tiene un hijo, deberá ser reemplazado en la 
estructura por este y mantendrá los sub-árboles que tenga. Si el nodo tiene dos 
hijos, se busca que en la estructura lo reemplace el predecesor inorden.

- `arbol_recorrido_[in|pre|post]orden()`: estas funciones son realizadas por la 
misma función nodo_abb_recorrer() que reciben por parámetro el recorrido que 
desea realizarse. Esta implementación sólo sirve para estos recorridos, por lo 
cuál si a futuro se desea ampliar los tipos de recorridos admitidos por el TDA, 
será necesario plantear otra implementación.

- `abb_con_cada_elemento()`: lo mismo que el punto anterior, la implementación
sólo sirve para los recorridos inorden, preorden o postorden. Si se desea
ampliar los tipos se deberá añadir otra implementación que los pueda
satisfacer.
