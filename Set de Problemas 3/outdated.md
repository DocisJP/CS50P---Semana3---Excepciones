# Outdated

En los Estados Unidos, las fechas suelen formatearse en orden mes-día-año (MM/DD/YYYY), también conocido como orden middle-endian, lo cual es, posiblemente, un mal diseño. Las fechas en ese formato no pueden ordenarse fácilmente porque el año viene al final en lugar de al principio. Intenta ordenar, por ejemplo, 2/2/1800, 3/3/1900 y 1/1/2000 cronológicamente en cualquier programa (por ejemplo, una hoja de cálculo). Las fechas en ese formato también son ambiguas. Harvard fue fundada el 8 de septiembre de 1636, pero 9/8/1636 también podría interpretarse como el 9 de agosto de 1636.

Afortunadamente, las computadoras tienden a usar ISO 8601, un estándar internacional que prescribe que las fechas deben formatearse en orden año-mes-día (YYYY-MM-DD), sin importar el país, formateando los años con cuatro dígitos, los meses con dos dígitos y los días con dos dígitos, "rellenando" cada uno con ceros a la izquierda según sea necesario.

En un archivo llamado outdated.py, implementa un programa que solicite al usuario una fecha, anno Domini, en orden mes-día-año, formateada como 9/8/1636 o September 8, 1636, donde el mes en el último caso podría ser cualquiera de los valores en la lista a continuación:

```python
[
    "January",
    "February",
    "March",
    "April",
    "May",
    "June",
    "July",
    "August",
    "September",
    "October",
    "November",
    "December"
]
```

Luego, muestra esa misma fecha en formato YYYY-MM-DD. Si la entrada del usuario no es una fecha válida en ninguno de los formatos, solicita nuevamente al usuario. Supón que cada mes no tiene más de 31 días; no es necesario validar si un mes tiene 28, 29, 30 o 31 días.

### Pistas

Recuerda que una cadena (str) tiene bastantes métodos, según docs.python.org/3/library/stdtypes.html#string-methods, incluyendo split.
Recuerda que una lista tiene bastantes métodos, según docs.python.org/3/tutorial/datastructures.html#more-on-lists, entre los cuales se encuentra index.
Ten en cuenta que puedes formatear un número entero con ceros a la izquierda con un código como

```python
print(f"{n:02}")
```

donde, si n es un dígito, se le antepondrá un 0, según docs.python.org/3/library/string.html#format-string-syntax.

## Antes de Comenzar

Inicia sesión en cs50.dev, haz clic en tu ventana de terminal y ejecuta `cd` por sí solo. Deberías ver que el indicador de la ventana de tu terminal se asemeja a lo siguiente:

```bash
$
```

Luego ejecuta

```bash
mkdir outdated
```

para crear una carpeta llamada outdated en tu espacio de código.

Luego ejecuta

```bash
cd outdated
```

para cambiar de directorio a esa carpeta. Ahora deberías ver el indicador de tu terminal como outdated/ $. Ahora puedes ejecutar

```bash
code outdated.py
```

para crear un archivo llamado outdated.py donde escribirás tu programa.

## Cómo Probar

Así es como puedes probar tu código manualmente:

Ejecuta tu programa con

```bash
python outdated.py
```

Escribe 9/8/1636 y presiona Enter. Tu programa debería mostrar:

```bash
1636-09-08
```

Ejecuta tu programa con

```bash
python outdated.py
```

Escribe September 8, 1636 y presiona Enter. Tu programa debería mostrar:

```bash
1636-09-08
```

Ejecuta tu programa con

```bash
python outdated.py
```

Escribe 23/6/1912 y presiona Enter. Tu programa debería solicitar nuevamente al usuario.

Ejecuta tu programa con

```bash
python outdated.py
```

Escribe December 80, 1980 y presiona Enter. Tu programa debería solicitar nuevamente al usuario.

Puedes ejecutar lo siguiente para verificar tu código usando check50, un programa que CS50 usará para probar tu código cuando lo envíes. ¡Pero asegúrate de probarlo tú mismo también!

```bash
check50 cs50/problems/2022/python/outdated
```

Las caritas verdes significan que tu programa ha pasado una prueba. Las caritas rojas indicarán que tu programa mostró algo inesperado. Visita la URL que check50 te proporciona para ver la entrada que check50 entregó a tu programa, qué salida esperaba y qué salida dio tu programa realmente.

## Cómo Enviar

En tu terminal, ejecuta lo siguiente para enviar tu trabajo.

```bash
submit50 cs50/problems/2022/python/outdated
```
