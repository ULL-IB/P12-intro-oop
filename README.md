# Práctica 12. Introducción a la Programación Orientada a Objetos. Depuración.

# Factor de ponderación: 10

### Objetivos
Los objetivos de esta práctica son que el alumnado:
- Desarrolle programas sencillos en C++ utilizando programación orientada a objetos, así como todas las características del lenguaje estudiadas anteriormente

### Rúbrica de evaluación de esta práctica
Se señalan a continuación los aspectos más relevantes (la lista no es exhaustiva) que se tendrán en cuenta a la hora de evaluar esta práctica. Se comprobará que el alumnado:
- Conoce los conceptos expuestos en el material de referencia de esta práctica
- Ha realizado todos los ejercicios propuestos en este enunciado
- Es capaz de escribir programas simples en C++ que resuelvan problemas de complejidad similar a los que se proponen en este documento
- Hace que sus programas se estructuren en torno a diferentes funciones (sean modulares)
- Todos sus programas se estructuran en directorios diferentes, cada uno con un fichero `Makefile` que automatice su compilación
- Utiliza en todos sus programas comentarios adecuados en el formato requerido por [Doxygen](https://www.doxygen.nl/index.html)
- Acredita que es capaz de subir programas a la plataforma [Jutge](https://jutge.org/) para su evaluación
- Ha incluido un comentario prólogo en todos los ficheros (`*.cc`, `*.h`) de sus ejercicios
- Que todos los programas que desarrolla imprimen en pantalla un mensaje indicando la finalidad del programa, así como la información que precisará del usuario para su correcta ejecución
- Hace que todos los programas que se presentan para su evaluación cumplan con los estándares definidos en la [Guía de estilo de Google para C++](https://google.github.io/styleguide/cppguide.html)
- Utiliza siempre identificadores significativos en su programa (para constantes, variables, etc.) y no utiliza nunca identificadores de una única letra, excepto tal vez para las variables que utilice para iterar en un bucle
- Acredita que es capaz de editar ficheros remotos en su VM usando Vi
- Ha realizado todos sus ejercicios en la máquina virtual Ubuntu de la asignatura
- Demuestra que es capaz de ejecutar comandos Linux en su VM

### Introducción a la depuración
Probar un programa con un conjunto bien elegido de pruebas de entrada da al programador la seguridad de que el programa es correcto. Durante el proceso de prueba, el programador observa las relaciones entrada-salida, es decir, la salida que produce el programa para cada caso de prueba de entrada. Si el programa produce la salida esperada y obedece la especificación para cada caso de prueba, entonces el programa se ha probado con éxito.

Pero si la salida de uno de los casos de prueba no es la esperada, entonces el programa es incorrecto: contiene errores (también conocidos como *bugs*). En tales situaciones, las pruebas sólo revelan la presencia de errores, pero no indican cuáles son ni cómo hay que corregir el código. En otras palabras, las pruebas revelan los efectos (o síntomas) de los errores, no su causa. La programadora debe entonces acometer un proceso de depuración, para identificar las causas y solucionar los errores.

Tal vez le resulte sorprendente saber que el proceso de depuración consume habitualmente más tiempo que la escritura del código. La mayor parte del tiempo de desarrollo de una aplicación se dedica a depurar y mantener el código, más que a escribirlo.

Es por ello que lo mejor es evitar el fallo al escribir el programa. Es importante sentarse y pensar antes de codificar: decidir exactamente qué se necesita conseguir, cómo se planea conseguirlo, diseñar el algoritmo de alto nivel de forma limpia, convencerse de que es correcto y decidir cuáles son las estructuras de datos concretas que se planea utilizar. Todo el esfuerzo invertido en diseñar y pensar el código antes de escribirlo valdrá la pena más adelante. Las ventajas son dobles: primero, tener un diseño limpio reducirá la probabilidad de defectos del programa; en segundo lugar, incluso si un error aparece durante las pruebas, un diseño limpio hará que sea mucho más fácil de rastrear y corregir el error.

Puede ser muy tentador escribir el programa lo más rápido posible, dejando poco o ningún tiempo para pensar en ello antes. El/la programador/a estará contento/a de ver el programa funcionando en poco tiempo, pero es probable que se frustre poco después: sin una buena reflexión, el programa será complejo y poco claro, por lo que el mantenimiento y la corrección de errores se convertirán en un proceso interminable.

Una vez que el programador empieza a codificar, debe utilizar una programación *defensiva*: desarrollar código de forma que funcione correctamente en los peores escenarios de su entorno. Por ejemplo, al escribir una función, hay que suponer las entradas del peor caso para esa función, es decir, entradas demasiado grandes, demasiado pequeñas o entradas que violen alguna propiedad, condición o invariante; el código debe tratar estos casos, aunque el programador no espere que ocurran en circunstancias normales.

Recuerde que el objetivo no es convertirse en un experto en la corrección de errores, sino mejorar en la escritura de programas robustos y (mayoritariamente) libres de errores. Como cuestión de actitud, los/as programadores/as no deben sentirse orgullosos/as cuando arreglan errores, sino más bien avergonzados/as de que su código contenga errores. Si hay un fallo en un programa, es sólo porque su autor/a cometió errores.

La depuración es una de las tareas más importantes a la hora de programar. Saber cómo utilizar un depurador para establecer puntos de interrupción, cómo pasar por encima y entrar en las funciones que se están utilizando ahorra horas de desarrollo. La depuración no sólo ahorra un valioso tiempo de desarrollo, sino que también ayuda a comprender mejor la lógica del código y el flujo de su ejecución, que no es el objetivo principal de la depuración, pero es un gran efecto adicional.

Se reproducen a continuación algunos consejos extraídos del [tutorial de referencia](https://www.learncpp.com/cpp-tutorial/finding-issues-before-they-become-problems/) de la asignatura, orientados a evitar los errores de programación. Se trata de una lista incompleta pero que puede ser de gran valor:
- Siga siempre las [*Buenas prácticas*](https://github.com/ULL-IB/code-examples/blob/main/coding_standards.md) de programación. Todas esas prácticas están pensadas para minimizar el número de potenciales errores.
- No deje que sus funciones sean demasiado largas (aproximadamente las líneas que caben en una pantalla, a lo sumo)
- Comente razonablemente su código allí donde sea pertinente
- Simplifique los programas
- Siempre que sea posible, prefiera utilizar la biblioteca estándar (STL) a escribir su propio código. En particular en *Informática Básica*, utilice `std::vector`/`std::array` o `std::string` en lugar de arrays o cadenas "al estilo de C"
- No programe cuando esté cansado/a
- Entienda dónde están las trampas comunes en un lenguaje (todo lo que se le advierte no hacer)

> Todo el tiempo que dedique a aprender a depurar será tiempo que ganará en el futuro como profesional.

### Ejercicios
- Al realizar los ejercicios cree dentro de su repositorio de esta práctica un directorio diferente para cada uno de los ejercicios. Asigne a cada uno de esos directorios nombres significativos.
- Automatice la compilación del programa correspondiente a cada ejercicio con un fichero `Makefile` independiente para cada programa e inclúyalo en el correspondiente directorio
- Haga que todos los programas tomen su entrada por la línea de comandos y en caso de que se ejecuten sin pasarles el número adecuado de parámetros impriman en pantalla un mensaje indicando el modo correcto de ejecutar el programa.
- El código de cada uno de los programas deberá organizarse de forma modular, es decir haciendo uso de funciones
- Cada función deberá realizar una única tarea y hacerlo correctamente
- El identificador de una función debe reflejar claramente la finalidad de la función

1. Desarrolle una clase `Point2D` para representar puntos en el espacio bidimensional a través de sus coordenadas. Incluya al menos los siguientes métodos:
    - `Show` para mostrar en pantalla las coordenadas del punto
    - `Move` para cambiar las coordenadas del punto
    - `Distance` para calcular la distancia entre dos puntos. La distancia entre los puntos $\langle a_x,\,a_y\rangle$ y $\langle b_x,\,b_y\rangle$ se calcula como el valor real $\sqrt{\left(a_x - b_x\right)^2 + \left(a_y - b_y\right)^2}.$
    - `Middle` para calcular el punto medio del segmento que une dos puntos. El punto medio entre los puntos $\langle a_x,\,a_y\rangle$ y $\langle b_x,\,b_y\rangle$ se calcula como el punto $\langle\left(a_x + b_x\right)/2,\,\left(a_y + b_y\right)/2\rangle$

2. Diseñe una clase `Circulo` que permita representar círculos utilizando como atributos el centro, el radio y el color del círculo. Utilice una [enumeración](https://www.learncpp.com/cpp-tutorial/unscoped-enumerations/) (`enum`) para representar el color del círculo (incluyendo al menos tres colores a su elección). Incluya métodos `Area`, `Perimetro` y `Print` que permitan calcular el área y el perímetro del círculo, así como imprimir en pantalla la información relativa al círculo en cuestión. Incluya asimismo un método booleano `EsInterior` que determine si un punto del espacio cartesiano $\langle x,\,y\rangle$ está o no dentro del círculo (la distancia entre el punto y el centro del círculo es menor que el radio del mismo).

3. Todo [número complejo](https://es.wikipedia.org/wiki/N%C3%BAmero_complejo) puede representarse como la suma de un número real y un número imaginario, de la forma `a + bi` donde el término `a` es la parte real, `b` la parte imaginaria e `i` la [unidad imaginaria](https://es.wikipedia.org/wiki/Unidad_imaginaria).
    
    En este ejercicio se propone desarrollar una clase `Complejo` que permita representar y operar con números complejos. Separe el diseño de su clase `Complejo` en dos ficheros, `complejo.h` y `complejo.cc` conteniendo respectivamente la declaración y la definición de la clase. Siga las indicaciones del tutorial [Class code and header files](https://www.learncpp.com/cpp-tutorial/89-class-code-and-header-files/) para realizar esta separación de su clase en dos ficheros. Siga igualmente las indicaciones del tutorial [Header guards](https://www.learncpp.com/cpp-tutorial/header-guards/) para incluir *header guards* (guardas de cabecera) en sus ficheros de definiciones (`*.h`), de modo que se evite la inclusión múltiple del mismo fichero.
    
    Desarrolle un programa cliente `complejos.cc` que permita operar con números complejos y haga uso de la clase `Complejo` que diseñe. La clase `Complejo` ha de contener al menos métodos que implementen la sobrecarga de los operadores de suma y resta de números complejos así como de los operadores de inserción y extracción en flujos (*streams*). Así la función `main` del programa `complejos.cc` podría contener (entre otras) sentencias como las siguientes:
    
    ``` cpp
    int main() {
      Complejo complejo1{4, 5}, complejo2{7, -8};
      std::cout << complejo1 + complejo2 << std::endl;
      std::cout << complejo1 - complejo2 << std::endl;
      return 0; 
    }
    ```
    
    Incluya (discrecionalmente) cualesquiera otras operaciones que considere adecuadas como métodos en la clase `Complejo`.

4. Desarrolle una clase `Fecha` que permita representar y gestionar fechas. Incorpore en la clase los miembros de datos y métodos que considere adecuados para la finalidad que se persigue en este ejercicio. Incluya un método que permita determinar si el año correspondiente a una fecha es un año bisiesto o no. Resuelva el problema [Valid Dates](https://jutge.org/problems/P58459_en) de Jutge y súbalo a la plataforma para su evaluación. A partir de la solución de ese problema, haga que el constructor de la clase `Fecha` solo admita una fecha si ésta es válida.
    
    Realice un programa cliente `fechas.cc` que permita declarar, leer y escribir (pantalla, teclado o ficheros) objetos de tipo `Fecha`.