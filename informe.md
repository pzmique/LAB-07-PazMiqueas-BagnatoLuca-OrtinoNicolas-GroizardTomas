### Luca Bagnato & Nicolas Ortino & Miqueas Paz
# Informe sobre manipulación de Cadenas en C++ 
## Objetivo

El objetivo de este informe es que los alumnos demuestren su comprensión sobre la
manipulación de cadenas en C++ utilizando tanto arreglos de caracteres (`char[]`) como
la clase ``std::string`` de la biblioteca estándar. Deben incluir ejemplos de código,
explicaciones y comentarios sobre las diferencias y ventajas de cada enfoque.


## Instrucciones
El informe debe estar escrito en formato Markdown y debe incluir las siguientes
secciones:

# 1. Introducción
   
* Breve introducción sobre qué son las cadenas de caracteres en C++.
* Diferencias básicas entre `char`, y `std::string` 


 **En `C++`, una cadena de caracteres es una secuencia de caracteres que se utilizan para representar texto. Hay dos formas principales de trabajar con cadenas de caracteres en C++:**

#### a.  Cadenas de caracteres en estilo C (C-strings): 
   - Se representan como un arreglo de caracteres (`char[]`), que termina con un carácter nulo (`'\0'`). 
   ```cpp
     Ejemplo: char saludo[] = "Hola, mundo!";
   ```  
   - Estas cadenas son gestionadas manualmente y carecen de algunas funcionalidades que tienen otras clases.

#### b.  Cadenas de caracteres en estilo C++ (std::string):
   - Se representan mediante la clase std::string de la biblioteca estándar C++. 
   ```cpp
   - Ejemplo: std::string saludo = "Hola, mundo!";
   ```
   - Ofrecen una interfaz más sencilla y poderosa para manipular texto, incluyendo operaciones como concatenación, comparación, y búsqueda.





# 2. Declaración e Inicialización de Cadenas

* Ejemplo de cómo declarar e inicializar una cadena usando `char[]`.
```cpp
#include <iostream>

int main() {
    // Declarar e inicializar una cadena de caracteres
    char saludo[] = "Hola, mundo!";
    
    // Imprimir la cadena
    std::cout << saludo << std::endl;
    
    return 0;
}

```
* Ejemplo de cómo declarar e inicializar una cadena usando ``std::string``.
```cpp
#include <iostream>
#include <string> // Incluir la cabecera para std::string

int main() {
    // Declarar e inicializar una cadena de caracteres usando std::string
    std::string saludo = "Hola, mundo!";
    
    // Imprimir la cadena
    std::cout << saludo << std::endl;
    
    return 0;
}

```
### Explicación de los ejemplos.
#### Ejemplo 1
* Crea un arreglo de caracteres que contiene la cadena `"Hola, mundo!"` y automáticamente agrega el carácter nulo al final.
```cpp
 char saludo[] = "Hola, mundo!"; 
``` 

#### Ejemplo 2 
* Crea un objeto de tipo `std::string` que contiene la cadena `"Hola, mundo!"`.
```cpp
std::string saludo = "Hola, mundo!";
```


## 3. Concatenación de Cadenas
* Ejemplo de concatenación usando `char[]` y la función `strcat`.

```cpp
#include <iostream>
#include <cstring> // Necesaria para std::strcat

int main() {
    // Declarar e inicializar las cadenas
    char saludo[50] = "Hola, "; // Tamaño suficiente para la concatenación
    char nombre[] = "mundo!";
    
    // Concatenar las cadenas
    std::strcat(saludo, nombre);
    
    // Imprimir la cadena resultante
    std::cout << saludo << std::endl;
    
    return 0;
}

```
* Ejemplo de concatenación usando ``std::string`` y el operador `+`.
```cpp
#include <iostream>
#include <string> // Necesaria para std::string

int main() {
    // Declarar e inicializar las cadenas
    std::string saludo = "Hola, ";
    std::string nombre = "mundo!";
    
    // Concatenar las cadenas
    std::string resultado = saludo + nombre;
    
    // Imprimir la cadena resultante
    std::cout << resultado << std::endl;
    
    return 0;
}

```
* Explicación de los ejemplos y comentarios sobre la facilidad de uso y eficiencia.

### Explicación del ejemplo 1:

* char saludo[50] = "Hola, "; declara un arreglo de caracteres con suficiente espacio para almacenar el resultado concatenado.

* std::strcat(saludo, nombre); concatena la cadena nombre al final de saludo. La función strcat requiere que el arreglo de destino (saludo) tenga suficiente espacio para almacenar la cadena concatenada más el carácter nulo final.

* Facilidad de uso: Es menos intuitiva y más propensa a errores si el tamaño del arreglo no se maneja adecuadamente.

* Eficiencia: strcat puede ser menos eficiente en ciertos casos debido a la necesidad de recorrer la cadena de destino para encontrar el final, además de que la gestión del tamaño del arreglo debe ser manual.

### Explicacion del ejemplo 2:

* std::string saludo = "Hola, "; y std::string nombre = "mundo!"; crean objetos std::string que contienen las cadenas deseadas.

* std::string resultado = saludo + nombre; utiliza el operador + para concatenar las dos cadenas de manera sencilla y directa.

* Facilidad de uso: Mucho más intuitiva y segura. La clase std::string maneja automáticamente el tamaño y la memoria, reduciendo el riesgo de errores.

* Eficiencia: Generalmente, std::string puede ser más eficiente y ofrece una mejor gestión de memoria, ya que maneja internamente las operaciones de concatenación y ajuste de tamaño.


# 4. Longitud de una Cadena
* Ejemplo de cómo obtener la longitud de una cadena usando `char[]` y la función `strlen`.

```cpp 
#include <iostream>
#include <cstring> // Necesaria para std::strlen

int main() {
    // Declarar e inicializar la cadena
    char saludo[] = "Hola, mundo!";
    
    // Obtener la longitud de la cadena
    size_t longitud = std::strlen(saludo);
    
    // Imprimir la longitud
    std::cout << "La longitud de la cadena es: " << longitud << std::endl;
    
    return 0;
}

```
* Ejemplo de cómo obtener la longitud de una cadena usando ``std::string`` y el método `length`.

```cpp
#include <iostream>
#include <string> // Necesaria para std::string

int main() {
    // Declarar e inicializar la cadena
    std::string saludo = "Hola, mundo!";
    
    // Obtener la longitud de la cadena
    std::size_t longitud = saludo.length();
    
    // Imprimir la longitud
    std::cout << "La longitud de la cadena es: " << longitud << std::endl;
    
    return 0;
}

```

### Explicación de los ejemplos.

#### Explicacion  del ejemplo 1:

* char saludo[] = "Hola, mundo!"; crea una cadena de caracteres en estilo C.

* std::strlen(saludo); calcula la longitud de la cadena, excluyendo el carácter nulo de terminación ('\0'). La función strlen devuelve un valor de tipo size_t, que es el tamaño de la cadena.

* Notas: strlen recorre la cadena hasta encontrar el carácter nulo, por lo que la eficiencia puede verse afectada por la longitud de la cadena. Además, la cadena debe estar bien formada con el carácter nulo al final para evitar errores.

#### Explicacion del ejemplo 2:

* std::string saludo = "Hola, mundo!"; crea un objeto std::string.

* saludo.length(); devuelve la longitud de la cadena, incluyendo todos los caracteres y excluyendo el carácter nulo (internamente, std::string maneja la longitud y el carácter nulo automáticamente). El método length devuelve un valor de tipo std::size_t, que es el tipo adecuado para representar tamaños.

* Notas: El método length de std::string es generalmente más eficiente y fácil de usar, ya que la clase std::string maneja internamente la longitud y otros detalles de la cadena.

# 5.Subcadenas
* Ejemplo de cómo obtener una subcadena usando ``std::string`` y el método `substr`.

```cpp
#include <iostream>
#include <string>

int main() {
    // Crear una cadena de caracteres
    std::string texto = "Hola, mundo!";
    
    // Obtener una subcadena usando el método substr
    // sintaxis: substr(posicion, longitud)
    std::string subcadena = texto.substr(0, 4);  // Desde el índice 0, tomar 4 caracteres

    // Mostrar la subcadena
    std::cout << "La subcadena es: " << subcadena << std::endl;

    return 0;
}

```
* Explicación del ejemplo.

```cpp
#include <iostream>
#include <string>

```
* #include <iostream> permite usar std::cout para la salida de datos.

* #include <string> incluye la definición de la clase std::string.

```cpp
std::string texto = "Hola, mundo!";
```

* Se crea una variable texto de tipo std::string e inicializa con el valor "Hola, mundo!".

```cpp
std::string subcadena = texto.substr(0, 4);
```

* texto.substr(0, 4) obtiene una subcadena de texto.

* El primer argumento 0 indica la posición de inicio (índice 0 en este caso).

* El segundo argumento 4 es la longitud de la subcadena que queremos extraer.

* Imprime en la consola la subcadena obtenida.
```cpp
std::cout << "La subcadena es: " << subcadena << std::endl;
```
# 6. Comparación de Cadenas
* Ejemplo de comparación usando `char[]` y la función `strcmp`.
```cpp
#include <iostream>
#include <cstring>

int main() {
    char str1[] = "apple";
    char str2[] = "orange";

    if (strcmp(str1, str2) == 0) {
        std::cout << "Las cadenas son iguales." << std::endl;
    } else if (strcmp(str1, str2) < 0) {
        std::cout << "str1 es menor que str2." << std::endl;
    } else {
        std::cout << "str1 es mayor que str2." << std::endl;
    }

    return 0;
}
```
* Ejemplo de comparación usando ``std::string`` y operadores relacionales.
```cpp
#include <iostream>
#include <string>

int main() {
    std::string str1 = "apple";
    std::string str2 = "orange";

    if (str1 == str2) {
        std::cout << "Las cadenas son iguales." << std::endl;
    } else if (str1 < str2) {
        std::cout << "str1 es menor que str2." << std::endl;
    } else {
        std::cout << "str1 es mayor que str2." << std::endl;
    }

    return 0;
}
```
### Explicación de los ejemplos y comentarios sobre la facilidad de uso y seguridad.
 * __Facilidad de Uso__:

`std::string` es más fácil y seguro de usar, ya que proporciona operadores de comparación intuitivos y sobrecargados, a diferencia de `char[]` que requiere el uso de la función strcmp

* __Seguridad__:

`std::string`: maneja automáticamente la memoria y evita errores comunes como el desbordamiento de búfer, mientras que `char[]` es más propenso a errores de manejo de memoria.

# 7. Otras  Operaciones Útiles
* Ejemplo de cómo convertir una cadena a mayúsculas o minúsculas usando `std::string` y las funciones `toupper` y `tolower`.
```cpp 

#include <iostream>
#include <string>
#include <algorithm>

int main() {
    std::string str = "Hello, World!";

    // Convertir a mayúsculas
    std::transform(str.begin(), str.end(), str.begin(), ::toupper);
    std::cout << "Mayúsculas: " << str << std::endl;

    // Convertir a minúsculas
    std::transform(str.begin(), str.end(), str.begin(), ::tolower);
    std::cout << "Minúsculas: " << str << std::endl;

    return 0;
}

``` 

* Ejemplo de cómo buscar caracteres o subcadenas en una `std::string` usando el método `find`.

```cpp 
#include <iostream>
#include <string>

int main() {
    std::string str = "Hello, World!";
    std::string sub = "World";

    size_t found = str.find(sub);
    if (found != std::string::npos) {
        std::cout << "Subcadena encontrada en la posición: " << found << std::endl;
    } else {
        std::cout << "Subcadena no encontrada." << std::endl;
    }

    return 0;
}
```

* Conversión de cadenas a números
```cpp 
#include <iostream>
#include <string>

int main() {
    std::string str = "1234";
    int num = std::stoi(str);
    std::cout << "Número convertido: " << num << std::endl;

    return 0;
}
```

* **Pasaje de Cadenas a Funciones en C++**

_Pasaje de Cadenas Usando `char[]`_
```cpp
#include <iostream>
#include <cstring>

void printMessage(char message[]) {
    std::cout << "Mensaje: " << message << std::endl;
}

int main() {
    char message[] = "Hello, World!";
    printMessage(message);
    return 0;
}
```

_Pasaje de Cadenas Usando `std::string`_

```cpp 
#include <iostream>
#include <string>

void printMessage(const std::string &message) {
    std::cout << "Mensaje: " << message << std::endl;
}

int main() {
    std::string message = "Hello, World!";
    printMessage(message);

    return 0;
}

  ```

* __Explicación de los ejemplos.__

    - **Conversión a mayúsculas/minúsculas:** Usar `std::transform` con `::toupper` y `::tolower` es simple y seguro.
    
    - **Búsqueda de subcadenas:** El método `find` de `std::string` es intuitivo y devuelve la posición de la subcadena.

    - **Conversión de cadenas a números:** `std::stoi` permite una conversión segura de `std::string` a enteros.

    - **Pasaje de cadenas a funciones:** Usar `std::string` facilita el manejo de cadenas, evitando errores de punteros y proporcionando una interfaz más moderna y segura.

# 8. Conclusión
* Resumen de las principales diferencias entre `char[]` y `std::string`.
    - **Facilidad de Uso:** `std::string` es más fácil de usar gracias a sus métodos y operadores sobrecargados.
    - **Seguridad:**  `std::string` proporciona manejo automático de memoria, reduciendo la posibilidad de errores de desbordamiento.
    - **Flexibilidad:** `std::string` ofrece más funcionalidades y es parte de la biblioteca estándar C++, lo que facilita su uso y compatibilidad.
 
* Ventajas y desventajas de usar cada uno.

    `char[]`
    -
    * **Ventajas:** Mayor control sobre la memoria, puede ser más eficiente en ciertos casos. 
    * **Desventajas:** Propenso a errores de manejo de memoria, más complejo de usar correctamente.

    `std::string`
    -
    * **Ventajas:** Manejo automático de memoria, métodos y operadores intuitivos, mayor seguridad.
    * **Desventajas:** Puede ser menos eficiente en términos de uso de memoria y rendimiento en comparación con `char[]` en casos específicos.

* Recomendaciones personales sobre cuándo usar cada enfoque.
    - Personalmente prefiero usar `std::string` en la mayoria de los casos, debido a su facilidad de uso y seguridad. 
    - Pero se puede usar `char[]` cuando el control sobre la memoria y el rendimiento es crítico y se tiene experiencia suficiente para evitar errores comunes.
    
    Conclusion
    -
    - En la mayoría de los casos, `std::string` es la opción recomendada debido a su seguridad, facilidad de uso y funcionalidad extendida. Es ideal para aplicaciones generales y desarrollo rápido. Sin embargo, `char[]` puede ser preferible en sistemas embebidos o cuando el rendimiento y el control de memoria son críticos, y el equipo tiene la experiencia necesaria para manejar manualmente la memoria.


# 9. Referencias

_Fuente_
-
#### _ChatGPT-4o_
* Usamos mayormente para crear nuestro informe sobre la manipulación de Cadenas en `C++`
la inteligencia artificial _**ChatGPT-4o**_, ya que actualmente no suele dar errores y es una de las fuentes más usadas por programadores aunque no esté especializada exactamente para esto. Pero nos ha servido con eficacia y practicidad para concretar nuestro informe.

_Estructura_
-
* Tratamos de lograr una estructura y coherencia entendible y ordenada, con sus correspondientes
  (esperamos) trucos del MarkDown(`MD`) para seccionar cada tema y consigna.

_Argumentación_
-
- Hemos tratado de explicar el _"¿por qué?"_ de esto en forma de ejemplos con código y comentarios para entender.

Fin
-
Esperamos que pueda entender nuestro informe sobre la manipulación de cadenas en C++
