## Lista de Compras

Supón que tienes la costumbre de hacer una lista de artículos que necesitas del supermercado.

En un archivo llamado grocery.py, implementa un programa que solicite al usuario artículos, uno por línea, hasta que el usuario ingrese control-d (que es una forma común de terminar la entrada a un programa). Luego muestra la lista de compras del usuario en mayúsculas, ordenada alfabéticamente por artículo, precediendo cada línea con el número de veces que el usuario ingresó ese artículo. No es necesario pluralizar los artículos. Trata la entrada del usuario sin importar mayúsculas o minúsculas.

### Pistas

Ten en cuenta que puedes detectar cuando el usuario ha ingresado control-d capturando un EOFError con un código como:

```python
try:
    item = input()
except EOFError:
    ...
```

Lo más probable es que desees almacenar tu lista de compras como un diccionario (dict).
Ten en cuenta que un diccionario (dict) tiene bastantes métodos, según docs.python.org/3/library/stdtypes.html#mapping-types-dict, entre ellos get, y admite operaciones como:

```python
d[key]
```

y

```python
if key in d:
    ...
```

donde d es un diccionario y key es una cadena (str).

Asegúrate de evitar o capturar cualquier KeyError.
Ten en cuenta que puedes ordenar las claves de un diccionario alfabéticamente pasando ese diccionario como argumento a sorted.

## Antes de Comenzar

Inicia sesión en cs50.dev, haz clic en tu ventana de terminal y ejecuta `cd` por sí solo. Deberías ver que el indicador de la ventana de tu terminal se asemeja a lo siguiente:

```bash
$
```

Luego ejecuta

```bash
mkdir grocery
```

para crear una carpeta llamada grocery en tu espacio de código.

Luego ejecuta

```bash
cd grocery
```

para cambiar de directorio a esa carpeta. Ahora deberías ver el indicador de tu terminal como grocery/ $. Ahora puedes ejecutar

```bash
code grocery.py
```

para crear un archivo llamado grocery.py donde escribirás tu programa.

## Cómo Probar

Así es como puedes probar tu código manualmente:

Ejecuta tu programa con

```bash
python grocery.py
```

Escribe mango y presiona Enter, luego escribe strawberry y presiona Enter, seguido de control-d. Tu programa debería mostrar:

```bash
1 MANGO
1 STRAWBERRY
```

Ejecuta tu programa con

```bash
python grocery.py
```

Escribe milk y presiona Enter, luego escribe milk nuevamente y presiona Enter, seguido de control-d. Tu programa debería mostrar:

```bash
2 MILK
```

Ejecuta tu programa con

```bash
python grocery.py
```

Escribe tortilla y presiona Enter, luego escribe sweet potato y presiona Enter, seguido de control-d. Tu programa debería mostrar:

```bash
1 SWEET POTATO
1 TORTILLA
```

Puedes ejecutar lo siguiente para verificar tu código usando check50, un programa que CS50 usará para probar tu código cuando lo envíes. ¡Pero asegúrate de probarlo tú mismo también!

```bash
check50 cs50/problems/2022/python/grocery
```

Las caritas verdes significan que tu programa ha pasado una prueba. Las caritas rojas indicarán que tu programa mostró algo inesperado. Visita la URL que check50 te proporciona para ver la entrada que check50 entregó a tu programa, qué salida esperaba y qué salida dio tu programa realmente.

## Cómo Enviar

En tu terminal, ejecuta lo siguiente para enviar tu trabajo.

```bash
submit50 cs50/problems/2022/python/grocery
```
