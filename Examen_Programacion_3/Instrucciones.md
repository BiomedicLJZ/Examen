# Examen de Programación 3

## Parte 1

Para la realización de este examen tendrán que Subir en `Classroom`un archivo README.md con las respuestas a las indicaciones, preguntas y calculos que se tengan que hacer en el siguiente examen. Tendrán un lapso de 12 horas a partir de la publicación del espacio correspondiente en classroom.

### Creación de Clases

En este repositorio de GitHub cuentan con los archivos `.h` y `.cpp` de una clase, estos archivos están incompletos ya que les hace falta una serie de lineas críticas para su funcionamiento, su trabajo en este examen será utilizando la documentación disponible y **apuntes y conocimientos previos**

1. Reparar el archivo de Interfaz `.h`
2. Reparar el archivo de implementación `.cpp`
3. Hacer funcionar el archivo `main.cpp`
4. Responde a las siguientes preguntas:
     1. ¿Qué es un Rvalor y un Lvalor?
     2. ¿Porqué es necesario que una clase tenga constructores y operadores por **copia** y por **referencia**?
     3. ¿Qué función desarrollan los `::` en la implementación de la clase?
     4. ¿Cómo se le denomina a cuando una clase posee un operador puede tener múltiples implementaciones dependiendo de los argumentos que este reciba?
     5. ¿Cúal es la funcion del archivo `.h`?

## Parte 2

### Complejidad Temporal

Calcular la complejidad temporal en **Big(O) Notation** del siguiente algoritmo:

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

int binarySearch(const std::vector<int>& vec, int target) {
    int left = 0;
    int right = vec.size() - 1;
    int count = 0;

    while (left <= right) {
        int mid = left + (right - left) / 2;

        if (vec[mid] == target) {
            count++;
            break;  // Se encontró el objetivo, no es necesario buscar más en este subconjunto.
        } else if (vec[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }

    return count;
}

void algorithm(int n) {
    std::vector<int> vec(n);

    for (int i = 0; i < n; ++i) {
        vec[i] = i;
    }

    int count = 0;
    for (int i = 0; i < n; ++i) {
        for (int j = i; j < n; ++j) {
            std::sort(vec.begin() + i, vec.begin() + j + 1);
            count += binarySearch(vec, 42);
        }
    }

    std::cout << "El resultado es: " << count << std::endl;
}

int main() {
    int n;
    std::cout << "Ingrese el valor de n: ";
    std::cin >> n;

    algorithm(n);

    return 0;
}
```
