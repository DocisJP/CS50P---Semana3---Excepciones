Lección 3
Excepciones
Errores en Tiempo de Ejecución
try
else
Crear una Función para Obtener un Entero
pass
Resumiendo
Excepciones
Las excepciones son cosas que salen mal dentro de nuestro código.
En nuestro editor de texto, escribe `code hello.py` para crear un nuevo archivo. Escribe lo siguiente (con los errores intencionales incluidos):

```python
print("hello, world)
```

Observa que intencionalmente dejamos fuera una comilla.

Ejecutando `python hello.py` en nuestra ventana de terminal, se muestra un error. El compilador indica que es un "error de sintaxis". Los errores de sintaxis son aquellos que requieren que verifiques que has escrito tu código correctamente.

Puedes aprender más en la documentación de Python sobre Errores y Excepciones.
Errores en Tiempo de Ejecución
Los errores en tiempo de ejecución se refieren a aquellos creados por un comportamiento inesperado dentro de tu código. Por ejemplo, tal vez esperabas que un usuario ingresara un número, pero en su lugar ingresó un carácter. Tu programa puede lanzar un error debido a esta entrada inesperada del usuario.
En tu ventana de terminal, ejecuta `code number.py`. Escribe lo siguiente en tu editor de texto:

```python
x = int(input("What's x? "))
print(f"x is {x}")
```

Observa que al incluir la `f`, le decimos a Python que interpole lo que está en las llaves como el valor de x. Además, al probar tu código, puedes imaginar cómo alguien podría fácilmente escribir una cadena o un carácter en lugar de un número. Aún así, un usuario podría no escribir nada en absoluto, simplemente presionando la tecla Enter.

Como programadores, debemos ser defensivos para asegurarnos de que nuestros usuarios están ingresando lo que esperábamos. Podríamos considerar "casos extremos" como -1, 0, o cat.

Si ejecutamos este programa y escribimos "cat", de repente veremos `ValueError: invalid literal for int() with base 10: 'cat'`. Esencialmente, el intérprete de Python no le gusta que pasemos "cat" a la función print.

Una estrategia efectiva para solucionar este error potencial sería crear "manejo de errores" para asegurarnos de que el usuario se comporte como esperamos.

Puedes aprender más en la documentación de Python sobre Errores y Excepciones.
try
En Python, `try` y `except` son formas de probar la entrada del usuario antes de que algo salga mal. Modifica tu código de la siguiente manera:

```python
try:
    x = int(input("What's x?"))
    print(f"x is {x}")
except ValueError:
    print("x is not an integer")
```

Observa cómo, al ejecutar este código, ingresar 50 será aceptado. Sin embargo, escribir `cat` producirá un error visible para el usuario, indicándole por qué su entrada no fue aceptada.

Esta todavía no es la mejor manera de implementar este código. Observa que estamos intentando hacer dos líneas de código. Para las mejores prácticas, deberíamos intentar solo la menor cantidad de líneas de código posible que creemos que podrían fallar. Ajusta tu código de la siguiente manera:

```python
try:
    x = int(input("What's x?"))
except ValueError:
    print("x is not an integer")

print(f"x is {x}")
```

Observa que, aunque esto logra nuestro objetivo de intentar la menor cantidad de líneas posible, ¡ahora enfrentamos un nuevo error! Enfrentamos un `NameError` donde x no está definido. Observa este código y considera: ¿Por qué x no está definido en algunos casos?

De hecho, si examinas el orden de las operaciones en `x = int(input("What's x?"))`, trabajando de derecha a izquierda, podría tomar un carácter ingresado incorrectamente e intentar asignarlo como un entero. Si esto falla, la asignación del valor de x nunca ocurre. Por lo tanto, no hay x para imprimir en nuestra línea final de código.
else
Resulta que hay otra forma de implementar `try` que podría capturar errores de esta naturaleza.

Ajusta tu código de la siguiente manera:

```python
try:
    x = int(input("What's x?"))
except ValueError:
    print("x is not an integer")
else:
    print(f"x is {x}")
```

Observa que si no ocurre ninguna excepción, entonces se ejecutará el bloque de código dentro de `else`. Al ejecutar `python number.py` y suministrar 50, notarás que el resultado se imprimirá. Intentándolo de nuevo, esta vez suministrando `cat`, notarás que el programa ahora captura el error.

Considerando mejorar nuestro código, observa que estamos siendo un poco groseros con nuestro usuario. Si nuestro usuario no coopera, actualmente simplemente terminamos nuestro programa. Considera cómo podemos usar un bucle para pedirle al usuario `x` y, si no lo hace, ¡pedirle de nuevo! Mejora tu código de la siguiente manera:

```python
while True:
    try:
        x = int(input("What's x?"))
    except ValueError:
        print("x is not an integer")
    else:
        break

print(f"x is {x}")
```

Observa que `while True` hará un bucle para siempre. Si el usuario logra suministrar la entrada correcta, podemos romper el bucle y luego imprimir la salida. Ahora, un usuario que ingrese algo incorrecto será solicitado nuevamente.

Crear una Función para Obtener un Entero
Seguramente, hay muchas veces que querríamos obtener un entero de nuestro usuario. Modifica tu código de la siguiente manera:

```python
def main():
    x = get_int()
    print(f"x is {x}")


def get_int():
    while True:
        try:
            x = int(input("What's x?"))
        except ValueError:
            print("x is not an integer")
        else:
            break
    return x


main()
```

Observa que estamos manifestando muchas propiedades geniales. Primero, hemos abstraído la capacidad de obtener un entero. Ahora, todo este programa se reduce a las primeras tres líneas del programa.

Aún así, podemos mejorar este programa. Considera qué más podrías hacer para mejorar este programa. Modifica tu código de la siguiente manera:

```python
def main():
    x = get_int()
    print(f"x is {x}")


def get_int():
    while True:
        try:
            x = int(input("What's x?"))
        except ValueError:
            print("x is not an integer")
        else:
            return x


main()
```

Observa que `return` no solo te sacará de un bucle, sino que también devolverá un valor.

Algunas personas pueden argumentar que podrías hacer lo siguiente:

```python
def main():
    x = get_int()
    print(f"x is {x}")


def get_int():
    while True:
        try:
            return int(input("What's x?"))
        except ValueError:
            print("x is not an integer")


main()
```

Observa que esto hace lo mismo que la iteración anterior de nuestro código, simplemente con menos líneas.

pass
Podemos hacer que nuestro código no advierta a nuestro usuario, sino que simplemente le vuelva a pedir la pregunta de solicitud modificando nuestro código de la siguiente manera:

```python
def main():
    x = get_int()
    print(f"x is {x}")


def get_int():
    while True:
        try:
            return int(input("What's x?"))
        except ValueError:
            pass


main()
```

Observa que nuestro código seguirá funcionando, pero no informará repetidamente al usuario de su error. En algunos casos, querrás ser muy claro con el usuario sobre qué error se está produciendo. Otras veces, podrías decidir que simplemente quieres pedirle al usuario la entrada nuevamente.

Una última mejora que podría mejorar la implementación de esta función `get_int`. Ahora mismo, observa que estamos confiando actualmente en el sistema de honor que x está en ambas funciones, main y get_int. Probablemente queramos pasar un mensaje que el usuario vea cuando se le pida la entrada. Modifica tu código de la siguiente manera:

```python
def main():
    x = get_int("What's x? ")
    print(f"x is {x}")


def get_int(prompt):
    while True:
        try:
            return int(input(prompt))
        except ValueError:
            pass


main()
```

Puedes aprender más en la documentación de Python sobre `pass`.

Resumiendo
Los errores son inevitables en tu código. Sin embargo, tienes la oportunidad de usar lo que aprendiste hoy para ayudar a prevenir estos errores. En esta lección, aprendiste sobre…

- Excepciones
- Errores de Valor
- Errores en Tiempo de Ejecución
- try
- else
- pass
