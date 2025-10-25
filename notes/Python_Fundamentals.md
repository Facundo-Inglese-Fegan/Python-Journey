# Manual Avanzado de Fundamentos de Python para Data Science

## **Introducción: ¿Por Qué Python Domina el Mundo de los Datos?**

Bienvenido a tu manual de referencia completo sobre los fundamentos de Python. Si la ciencia de datos fuera una expedición para descubrir tesoros escondidos en montañas de información, Python sería tu vehículo todo terreno, tu navaja suiza y tu brújula, todo en uno.

Python es un lenguaje de programación de **alto nivel**, **interpretado** y de **propósito general**. Desglosemos esto:

- **Alto Nivel:** Su sintaxis es cercana al lenguaje humano, lo que facilita su lectura y escritura. Te abstrae de las complejidades de la gestión de memoria y el hardware del ordenador.

- **Interpretado:** No necesitas "compilar" tu código en un programa ejecutable antes de correrlo. Un intérprete lee y ejecuta tu código línea por línea, lo que agiliza enormemente el proceso de desarrollo y depuración.

- **Propósito General:** No fue diseñado para una sola tarea. Se utiliza en desarrollo web, automatización, videojuegos y, por supuesto, es el lenguaje rey en el análisis de datos, machine learning e inteligencia artificial.

Su éxito en la ciencia de datos se debe a una combinación de factores: una sintaxis simple, una comunidad masiva y, lo más importante, un ecosistema de **librerías** especializadas (como NumPy, Pandas, Matplotlib, Scikit-learn) que proporcionan herramientas increíblemente potentes para cada etapa del análisis de datos.

### **La Filosofía de Python: El Zen de Python**

Hay un poema de 19 aforismos llamado "El Zen de Python" que encapsula la filosofía del lenguaje. Puedes verlo en cualquier momento en tu consola de Python escribiendo `import this`. Algunos de sus principios clave son:

- Bello es mejor que feo.
- Explícito es mejor que implícito.
- Simple es mejor que complejo.
- La legibilidad cuenta.

Mantén estas ideas en mente. Escribir buen código en Python no solo se trata de que funcione, sino de que sea limpio, elegante y fácil de entender.

## **Capítulo 1: Primeros Pasos - Tu Entorno de Trabajo**

### **1.1. El Intérprete Interactivo (IDLE Shell)**

El Shell es tu campo de pruebas, un diálogo directo con Python. Es ideal para:

- Probar comandos rápidos.
- Realizar cálculos sencillos.
- Explorar la funcionalidad de un objeto o función.

**Ejemplo:**

```Python
>>> 5 + 5
10
>>> print("¡Hola, futuro Data Scientist!")
¡Hola, futuro Data Scientist!
>>> type(10)
<class 'int'>
```

Cada vez que presionas `Enter`, Python evalúa lo que escribiste y te da una respuesta inmediata.

### **1.2. Archivos de Script (.py)**

Para cualquier programa que tenga más de un par de líneas, escribirás el código en un archivo de texto con la extensión `.py`. Esto te permite guardar, editar y reutilizar tu trabajo.

**Analogía:** El Shell es como tener una conversación telefónica. Un archivo `.py` es como escribir una carta. La carta te permite planificar, estructurar tus ideas y entregar un mensaje completo y coherente.

**Ejemplo (archivo **`mi_programa.py`**):**

```Python
# Este es un script que calcula el área de un círculo
# Definimos una variable para el radio
radio = 5
# Usamos la fórmula pi * radio al cuadrado
area = 3.14159 * (radio ** 2)
# Imprimimos el resultado de una forma descriptiva
print(f"El área de un círculo con radio {radio} es: {area}")
```

Cuando ejecutas este archivo, el intérprete lee el fichero de arriba a abajo, ejecuta todas las líneas en orden y muestra el resultado final en la consola.

### **1.3. Comentarios: Dejando Notas en tu Código**

Cualquier texto en una línea que siga al símbolo de almohadilla (`#`) es un **comentario**. Python lo ignora por completo. Su propósito es para los humanos.

**¿Por qué son CRUCIALES los comentarios?**

1. **Explican el "porqué"**: Tu código muestra "qué" hace, pero un comentario explica "por qué" lo hace de esa manera.
2. **Facilitan la colaboración**: Ayudan a otros programadores (y a tu "yo" del futuro) a entender tu lógica.
3. **Depuración**: Puedes "comentar" una línea de código para desactivarla temporalmente sin borrarla.

```Python
# ---- MAL COMENTARIO (obvio y no aporta nada) ----
# Asigna 10 a la variable x
x = 10

# ---- BUEN COMENTARIO (explica la intención) ----
# Establecemos la tasa de descuento inicial al 10%
discount_rate = 0.10
```

## **Capítulo 2: Variables y Tipos de Datos Fundamentales**

### **2.1. Variables: Las Etiquetas de tus Datos**

Una variable es un nombre que le damos a un espacio en la memoria para almacenar un valor. La asignación se realiza con un único signo igual (`=`).

```Python
# La variable 'edad' ahora almacena el valor 25
edad = 25
# La variable 'nombre' almacena el texto "Carlos"
nombre = "Carlos"
# Podemos reasignar un nuevo valor a una variable existente
edad = 26
```

#### **Reglas para Nombrar Variables (Convenciones PEP 8)**

- Usa nombres descriptivos y en minúsculas (ej: `tasa_de_interes` en lugar de `t`).
- Separa las palabras con guiones bajos (`snake_case`).
- Deben empezar con una letra o guion bajo (`_`).
- Son *case-sensitive* (`edad` y `Edad` son diferentes).

### **2.2. Tipos de Datos Numéricos:** `int` **y** `float`

`int` **(Integer):** Números enteros, positivos o negativos, sin decimales.
Python

```Python
año_nacimiento = 1995
temperatura_minima = -5
```

`float` **(Floating-Point):** Números con decimales. Se usa un punto (`.`) como separador.

```Python
precio_producto = 49.99
pi = 3.14159
```

- **Nota sobre precisión:** Debido a cómo se almacenan en binario, las operaciones con `float` a veces pueden tener pequeños errores de redondeo. Para la mayoría de los análisis de datos no es un problema, pero para cálculos financieros de alta precisión se usan librerías especializadas como `Decimal`.

### **2.3. Tipo de Dato de Texto: **`str`** (String)**

Una secuencia de caracteres entre comillas simples (`'`) o dobles (`"`).

```Python
saludo = "Hola, mundo"
frase = 'Python es "increíble"' # Usar comillas distintas evita errores
```

### **2.4. Tipo de Dato Lógico: **`bool`** (Boolean)**

Representa uno de dos valores: `True` o `False`. Son la base de la toma de decisiones en programación.

```Python
es_mayor_de_edad = True
tiene_descuento = False
```

### **2.5. La Función** `type()`

Para saber el tipo de dato de cualquier variable o valor.

```Python
numero = 10
print(type(numero))  # Salida: <class 'int'>

texto = "Python"
print(type(texto))   # Salida: <class 'str'>
```

### **2.6. Conversión de Tipos (Type Casting)**

A veces necesitas convertir un dato de un tipo a otro de forma explícita.

```Python
# String a int
numero_en_texto = "123"
numero_real = int(numero_en_texto)
print(type(numero_real))  # Salida: <class 'int'>

# Int a float
entero = 10
flotante = float(entero)
print(flotante)         # Salida: 10.0

# Número a string
edad = 30
mensaje = "El usuario tiene " + str(edad) + " años."
print(mensaje)          # Salida: El usuario tiene 30 años.
```

### **2.7. Recibiendo Datos del Usuario:** `input()`

Esta función pausa la ejecución del programa, muestra un mensaje al usuario y espera a que escriba algo y presione `Enter`.

**¡Punto Clave!** La función `input()` **siempre** devuelve los datos como un **string (**`str`**)**, incluso si el usuario introduce números.

```Python
# El valor que el usuario escriba se guardará como un string en 'nombre_usuario'
nombre_usuario = input("Por favor, introduce tu nombre: ")
print(f"Hola, {nombre_usuario}!")

# Para usar la edad como un número, debemos hacer un type casting
edad_texto = input("Introduce tu edad: ")
edad_numero = int(edad_texto)
año_nacimiento = 2024 - edad_numero
print(f"Naciste aproximadamente en el año {año_nacimiento}.")
```

## **Capítulo 3: Profundizando en los Strings**

Los strings son una de las estructuras de datos más versátiles.

### **3.1. Indexación y Slicing Avanzado**

**Indexación:** Acceder a un carácter por su posición.

```Python
palabra = "PYTHON"
print(palabra[0])  # 'P' (el primero)
print(palabra[5])  # 'N' (el último)
print(palabra[-1]) # 'N' (forma más robusta de acceder al último)
print(palabra[-2]) # 'O' (el penúltimo)
```

**Slicing:** `[inicio:fin:paso] \

```Python
palabra = "PROGRAMACION"
print(palabra[0:4])     # 'PROG' (del índice 0 al 3)
print(palabra[:4])      # 'PROG' (lo mismo, inicio se asume 0)
print(palabra[4:])      # 'RAMACION' (del índice 4 al final)
print(palabra[1:8:2])   # 'RGAI' (del 1 al 7, saltando de 2 en 2)
print(palabra[::-1])    # 'NOICAMARGORP' (un truco para invertir la cadena)
```

### **3.2. Métodos de Strings Indispensables**

Los métodos son funciones que "pertenecen" a un objeto. Se llaman con `objeto.metodo()`.

- .upper(): Convierte toda la cadena a mayúsculas.
  - Ejemplo: 'hola'.upper() -> 'HOLA'
- .lower(): Convierte toda la cadena a minúsculas.
  - Ejemplo: 'HOLA'.lower() -> 'hola'
- .capitalize(): Pone en mayúscula solo el primer carácter de la cadena.
  - Ejemplo: 'hola mundo'.capitalize() -> 'Hola mundo'
- .strip(): Elimina espacios en blanco al principio y al final.
  - Ejemplo: ' hola '.strip() -> 'hola'
- .replace(viejo, nuevo): Reemplaza todas las ocurrencias de viejo por nuevo.
  - Ejemplo: 'Python es lento'.replace('lento', 'rápido') -> 'Python es rápido'
- .split(delimitador): Divide la cadena en una lista de subcadenas usando un delimitador.
  - Ejemplo: 'manzana,pera,uva'.split(',') -> ['manzana', 'pera', 'uva']
- .join(iterable): Une los elementos de un iterable (como una lista) en una sola cadena.
  - Ejemplo: '-'.join(['a', 'b', 'c']) -> 'a-b-c'
- .find(subcadena): Devuelve el índice de la primera aparición de subcadena (-1 si no la encuentra).
  - Ejemplo: 'hola'.find('la') -> 2
- .startswith(prefijo): Devuelve True si la cadena empieza con prefijo.
  - Ejemplo: 'Python'.startswith('Py') -> True
- .endswith(sufijo): Devuelve True si la cadena termina con sufijo.
  - Ejemplo: 'archivo.csv'.endswith('.csv') -> True
- .isalpha(), .isnumeric(): Devuelven True si todos los caracteres son alfabéticos o numéricos, respectivamente.
  - Ejemplo: 'abc'.isalpha() -> True, '123'.isnumeric() -> True

### **3.3. Formato de Strings: F-Strings**

Introducidos en Python 3.6, los f-strings son la forma más moderna, legible y eficiente de incrustar expresiones dentro de cadenas de texto.

```Python
nombre = "Lucía"
edad = 32
profesion = "Data Scientist"

# Forma antigua (concatenación, propensa a errores)
# print("Nombre: " + nombre + ", Edad: " + str(edad))

# Forma moderna y recomendada (f-string)
mensaje = f"Nombre: {nombre}, Edad: {edad}, Profesión: {profesion}"
print(mensaje)

# Se pueden poner expresiones complejas dentro de las llaves
print(f"Lucía tendrá {edad + 5} años en 5 años.")
```

## **Capítulo 4: Operadores - Las Herramientas del Lenguaje**

### **4.1. Operadores Aritméticos**

Realizan operaciones matemáticas.

```Python
a = 15
b = 4

print(f"{a} + {b} = {a + b}")    # Suma -> 19
print(f"{a} - {b} = {a - b}")    # Resta -> 11
print(f"{a} * {b} = {a * b}")    # Multiplicación -> 60
print(f"{a} / {b} = {a / b}")    # División -> 3.75 (siempre float)
print(f"{a} // {b} = {a // b}")  # División Entera -> 3 (trunca el decimal)
print(f"{a} ** {b} = {a ** b}")  # Exponente -> 50625 (15^4)
print(f"{a} % {b} = {a % b}")    # Módulo (resto) -> 3 (15 dividido 4 es 3 con resto 3)
```

### **4.2. Operadores de Asignación**

Combinan una operación aritmética con la asignación.

```Python
x = 10
x += 5  # Equivalente a x = x + 5  -> x es 15
x -= 3  # Equivalente a x = x - 3  -> x es 12
x *= 2  # Equivalente a x = x * 2  -> x es 24
x /= 6  # Equivalente a x = x / 6  -> x es 4.0
```

### **4.3. Operadores de Comparación (Relacionales)**

Comparan valores y siempre devuelven un booleano (`True` o `False`).

```Python
a = 10
b = 5

print(a == 10) # Igual a -> True
print(a != b)  # Diferente de -> True
print(a > b)   # Mayor que -> True
print(a < b)   # Menor que -> False
print(a >= 10) # Mayor o igual que -> True
print(b <= 4)  # Menor o igual que -> False

# Comparación de strings (orden lexicográfico/alfabético)
print("hola" == "hola") # True
print("manzana" < "pera") # True (m viene antes que p en el alfabeto)
```

### **4.4. Operadores Lógicos**

Operan sobre valores booleanos.

- `and`: `True` solo si **ambos** lados son `True`.
- `or`: `True` si **al menos uno** de los lados es `True`.
- `not`: Invierte el valor booleano.

```Python
edad = 25
tiene_licencia = True

# Ejemplo 1: ¿Puede alquilar un coche? (mayor de 21 y con licencia)
if edad >= 21 and tiene_licencia == True:
    print("Puede alquilar un coche.")

# Ejemplo 2: ¿Tiene descuento? (es estudiante o es mayor de 65)
es_estudiante = False
if es_estudiante or edad > 65:
    print("Tiene descuento.")
else:
    print("No tiene descuento.")

# Ejemplo 3: Negación
esta_lloviendo = False
if not esta_lloviendo:
    print("El día está soleado.")
```

### **4.5. Orden de Precedencia (PEMDAS)**

Python sigue un orden estricto al evaluar expresiones complejas:

1. **P**aréntesis `()`
2. **E**xponentes `**`
3. **M**ultiplicación `*`, **D**ivisión `/`, `//`, `%` (de izquierda a derecha)
4. **A**dición `+`, **S**ustracción `-` (de izquierda a derecha)
5. **C**omparación `==`, `!=`, `<`, `>`...
6. **L**ógicos `not`, `and`, `or`

```Python
resultado = (5 + 3) * 2 ** 2 / 4 - 1
# 1. Paréntesis: (8) * 2 ** 2 / 4 - 1
# 2. Exponente:  8 * 4 / 4 - 1
# 3. Multi/Div: 32 / 4 - 1 -> 8.0 - 1
# 4. Suma/Resta: 7.0
print(resultado) # 7.0
```

## **Capítulo 5: Estructuras de Datos - Colecciones**

### **5.1. Listas** `[]`

La estructura más común. Son secuencias **ordenadas** y **mutables**.

**Creación:**

```Python
numeros = [1, 2, 3, 4, 5]
mixta = ["hola", 10, True, 3.14]
vacia = []
```

**Acceso y Modificación:**

```Python
frutas = ["manzana", "pera", "banana", "naranja"]
print(frutas[1])        # 'pera'
frutas[2] = "kiwi"      # Cambia 'banana' por 'kiwi'
print(frutas)           # ['manzana', 'pera', 'kiwi', 'naranja']
```

**Métodos de Listas:**

- `.append(elemento)`: Añade un elemento al **final** de la lista.

```Python
frutas.append("mango")
print(frutas) # [... 'naranja', 'mango']
```

- `.insert(indice, elemento)`: Inserta un elemento en una posición específica.

```Python
frutas.insert(1, "fresa")
print(frutas) # ['manzana', 'fresa', 'pera', ...]
```

- `.remove(elemento)`: Elimina la **primera aparición** del elemento especificado.

```Python
frutas.remove("pera")
```

- `.pop(indice)`: Elimina y **devuelve** el elemento en un índice. Si no se especifica índice, elimina el último.

```Python
ultima_fruta = frutas.pop()
print(f"La última fruta era {ultima_fruta}")
```

- `.sort()`: Ordena la lista **in-place** (modifica la lista original).

```Python
numeros = [4, 1, 8, 3]
numeros.sort()
print(numeros) # [1, 3, 4, 8]
```

- `.reverse()`: Invierte el orden de la lista **in-place**.

### **5.2. Tuplas** `()`

Son secuencias **ordenadas** e **inmutables**. Una vez creadas, no se pueden modificar.

**Creación:**

```Python
coordenadas = (10.0, 25.5)
colores_rgb = (255, 0, 128)
# Para una tupla de un solo elemento, la coma es obligatoria
tupla_unica = ("elemento",)
```

**¿Por qué usar Tuplas?**

1. **Seguridad/Integridad:** Para datos que no deben cambiar accidentalmente.
2. **Rendimiento:** Son ligeramente más rápidas que las listas.
3. **Claves de Diccionario:** Las tuplas pueden ser claves de diccionario (las listas no, porque son mutables).

**Desempaquetado (Unpacking):**

```Python
punto = (100, 200)
x, y = punto  # Asigna 100 a 'x' y 200 a 'y'
print(f"Coordenada X: {x}, Coordenada Y: {y}")
```

### **5.3. Diccionarios** `{}`

Colecciones **no ordenadas** (en versiones de Python < 3.7) de pares **clave-valor**. Son increíblemente eficientes para buscar datos.

**Creación:**

```Python
estudiante = {
    "nombre": "Ana",
    "edad": 22,
    "curso": "Ciencia de Datos",
    "es_becada": True
}
```

**Acceso y Modificación:** Se accede a los valores a través de sus claves.

```Python
print(estudiante["nombre"]) # 'Ana'

# Modificar un valor existente
estudiante["edad"] = 23

# Añadir un nuevo par clave-valor
estudiante["universidad"] = "Universidad Politécnica"
```

**Métodos de Diccionarios:**

- `.get(clave, valor_por_defecto)`: Forma segura de acceder a una clave. Si la clave no existe, devuelve `None` (o el valor por defecto) en lugar de un `KeyError`.

```Python
print(estudiante.get("apellido", "No especificado")) # 'No especificado'
```

- `.keys()`: Devuelve una vista de todas las claves.

- `.values()`: Devuelve una vista de todos los valores.

- `.items()`: Devuelve una vista de todos los pares (clave, valor) como tuplas.

**Eliminar Elementos:**

```Python
# Usando la palabra clave 'del'
del estudiante["es_becada"]
```

## **Capítulo 6: Control de Flujo - Bucles y Repetición**

Los bucles son una de las herramientas más poderosas de la programación. Nos permiten ejecutar un bloque de código múltiples veces sin tener que reescribirlo.

### **6.1. Bucle **`for`**: Iterando sobre Secuencias**

El bucle `for` se utiliza cuando quieres recorrer cada elemento de un objeto iterable (como una lista, tupla, diccionario o string) o cuando sabes de antemano cuántas veces quieres que se repita el bloque de código.

**Sintaxis:**

```Python
for variable_temporal in iterable:
    # Código a ejecutar en cada iteración
```

**Iterando sobre una lista:**

```Python
frutas = ["manzana", "pera", "kiwi"]
for fruta in frutas:
    print(f"Me gusta comer {fruta}")
```

**Iterando sobre un string:**

```Python
for letra in "Python":
    print(letra)
```

**Iterando sobre las claves de un diccionario:**

```Python
estudiante = {"nombre": "Ana", "edad": 22}
for clave in estudiante:
    print(f"{clave}: {estudiante[clave]}")

# Forma más idiomática usando .items()
for clave, valor in estudiante.items():
    print(f"{clave}: {valor}")
```

### **6.2. La Función** `range()`

`range()` es el compañero perfecto del bucle `for` cuando necesitas repetir una acción un número específico de veces. Genera una secuencia de números enteros.

**Sintaxis:** `range(inicio, fin, paso)`

- `inicio` **(opcional):** El primer número de la secuencia (por defecto es 0).
- `fin` **(obligatorio):** La secuencia llega **hasta** este número, pero **no lo incluye**.
- `paso` **(opcional):** El incremento entre números (por defecto es 1).

**Ejemplos:**

```Python
# Imprimir números del 0 al 4
for i in range(5):
    print(i) # 0, 1, 2, 3, 4

# Imprimir números del 2 al 6
for i in range(2, 7):
    print(i) # 2, 3, 4, 5, 6

# Imprimir números pares del 10 al 20
for i in range(10, 21, 2):
    print(i) # 10, 12, 14, 16, 18, 20
```

### **6.3. Bucle **`while`**: Repetición Basada en una Condición**

El bucle `while` se ejecuta **mientras** una condición sea `True`. Se utiliza cuando no sabes cuántas iteraciones necesitarás, pero sí sabes cuándo debe detenerse el bucle.

**Sintaxis:**

```Python
while condicion:
    # Código a ejecutar
    # ¡Importante! Actualizar la variable de control
```

**¡Advertencia!** Es crucial que dentro del bucle `while` haya una línea que, eventualmente, haga que la condición se vuelva `False`. De lo contrario, crearás un **bucle infinito**.

```Python
# Ejemplo: Cuenta atrás desde 5
contador = 5
while contador > 0:
    print(contador)
    contador -= 1  # Actualizamos la variable de control
print("¡Despegue!")
```

Si olvidas la línea `contador -= 1`, `contador` siempre sería `5`, la condición `5 > 0` siempre sería `True` y el programa imprimiría "5" indefinidamente.

### **6.4. Controlando Bucles:** `break` **y** `continue`

A veces necesitas un control más fino sobre el flujo de tus bucles.

- `break`: Termina el bucle **inmediatamente**, sin importar la condición. El programa salta a la primera línea después del bucle.

```Python
# Buscar el primer número divisible por 7
numeros = [2, 13, 21, 8, 35]
for num in numeros:
    if num % 7 == 0:
        print(f"Encontrado el primer número divisible por 7: {num}")
        break # Salimos del bucle
```

- `continue`: Termina la **iteración actual** y salta directamente al **inicio de la siguiente iteración**.

```Python
# Imprimir solo los números impares
for i in range(1, 11):
    if i % 2 == 0: # Si el número es par...
        continue   # ...saltamos esta iteración y no lo imprimimos
    print(i)
```

## **Capítulo 7: Funciones - Bloques de Código Reutilizables**

Una función es un bloque de código organizado y reutilizable que realiza una tarea específica. Las funciones ayudan a que tu código sea más modular, legible y fácil de mantener, siguiendo el principio **DRY (Don't Repeat Yourself)**.

### **7.1. Definición y Llamada a una Función**

Se definen con la palabra clave `def`.

**Sintaxis:**

```Python
def nombre_de_la_funcion(parametro1, parametro2):
    # Cuerpo de la función (código indentado)
    # ...
    return valor_de_retorno
```

**Llamada a la función:** Para ejecutar el código dentro de la función, la "llamas" por su nombre, pasándole los valores necesarios.

```Python
# Definición de la función
def saludar(nombre):
    mensaje = f"¡Hola, {nombre}! Bienvenido."
    print(mensaje)

# Llamada a la función
saludar("Marcos") # Salida: ¡Hola, Marcos! Bienvenido.
saludar("Laura")  # Salida: ¡Hola, Laura! Bienvenido.
```

### **7.2. Parámetros vs. Argumentos**

Aunque a menudo se usan indistintamente, tienen una diferencia sutil:

- **Parámetro:** Es la **variable** que se lista dentro de los paréntesis en la **definición** de la función. Es un marcador de posición.
- **Argumento:** Es el **valor real** que se pasa a la función cuando esta es **llamada**.

En el ejemplo anterior, `nombre` es el parámetro y `"Marcos"` es el argumento.

### **7.3. La Crucial Diferencia:** `print` **vs.** `return`

Este es uno de los conceptos más importantes.

- `print()`: Es una función que **muestra información en la consola**. Su propósito es la visualización para el usuario. **No entrega ningún valor** de vuelta al programa para que pueda ser utilizado.
- `return`: Es una sentencia que **finaliza la ejecución de una función y envía un valor de vuelta** al código que la llamó. Este valor puede ser guardado en una variable, usado en una operación, etc.

**Analogía:** Imagina que le pides a un amigo que calcule `5 + 3`.

- Si usa `print`, te **gritaría el resultado** "8" en voz alta para que lo oigas, pero no podrías hacer nada más con ese número.
- Si usa `return`, te **escribiría el número "8" en un papel** y te lo entregaría. Ahora puedes tomar ese papel, guardarlo en tu bolsillo (una variable) y usarlo para otros cálculos.

```Python
# Función que usa PRINT
def sumar_y_mostrar(a, b):
    resultado = a + b
    print(f"El resultado es: {resultado}")

# Función que usa RETURN
def sumar_y_devolver(a, b):
    resultado = a + b
    return resultado

# --- Uso ---
sumar_y_mostrar(5, 3) # Muestra "El resultado es: 8" en la consola
# valor_mostrado = sumar_y_mostrar(5, 3) # 'valor_mostrado' sería None

# El valor devuelto por la función se guarda en una variable
valor_devuelto = sumar_y_devolver(5, 3)
print(f"El valor que recibí fue: {valor_devuelto}") # Muestra "El valor que recibí fue: 8"
print(f"Puedo usarlo en otro cálculo: {valor_devuelto * 2}") # Muestra 16
```

### **7.4. Alcance de Variables (Scope)**

El alcance determina en qué partes de tu programa una variable es accesible.

- **Variables Locales:** Se definen **dentro** de una función. Solo existen y pueden ser usadas dentro de esa función. Se crean cuando la función es llamada y se destruyen cuando termina.
- **Variables Globales:** Se definen en el cuerpo principal del programa, **fuera** de cualquier función. Son accesibles desde cualquier parte del código, incluyendo dentro de las funciones.

```Python
variable_global = "Soy global" # Variable global

def mi_funcion():
    variable_local = "Soy local" # Variable local
    print(variable_local)
    print(variable_global) # Podemos LEER una variable global desde dentro

mi_funcion()
# Salida:
# Soy local
# Soy global

print(variable_global) # Salida: Soy global
# print(variable_local) # Esto daría un NameError, porque 'variable_local' no existe aquí fuera.
```

**Buena práctica:** Es preferible que las funciones operen con los datos que reciben como parámetros y devuelvan resultados, en lugar de modificar variables globales. Esto las hace más predecibles y reutilizables.

## **Capítulo 8: Un Vistazo a la Recursión**

La recursión es un concepto en el que una función se llama a sí misma para resolver un problema. Es una forma de pensar en la resolución de problemas que consiste en descomponer un problema grande en versiones más pequeñas y simples del mismo problema.

Toda función recursiva debe tener dos componentes:

1. **Caso Base:** Una condición que **detiene** la recursión. Es la versión más simple del problema, que se puede resolver directamente sin más llamadas recursivas. Sin un caso base, la función se llamaría a sí misma infinitamente, causando un `RecursionError`.
2. **Caso Recursivo:** La parte de la función donde se llama a sí misma, pero con un argumento que la acerca un paso más al caso base.

### **Ejemplo Clásico: La Sucesión de Fibonacci**

La sucesión de Fibonacci es una secuencia de números donde cada número es la suma de los dos anteriores: 0, 1, 1, 2, 3, 5, 8, 13, ...

- fib(n) = fib(n-1) + fib(n-2)

```Python
def fibonacci(n):
    # --- CASO BASE ---
    # La definición dice que fib(0) es 0 y fib(1) es 1.
    if n == 0 or n == 1:
        return n
    # --- CASO RECURSIVO ---
    # Para cualquier otro número, lo definimos en términos de sí mismo.
    else:
        return fibonacci(n - 1) + fibonacci(n - 2)

# Calcular el 7º número de la sucesión (empezando en 0)
resultado = fibonacci(7)
print(resultado) # Salida: 13
```

**Cómo funciona **`fibonacci(4)`**:**

1. `fib(4)` llama a `fib(3)` y `fib(2)`.
2. `fib(3)` llama a `fib(2)` y `fib(1)`. `fib(1)` es un caso base y devuelve `1`.
3. `fib(2)` llama a `fib(1)` y `fib(0)`. Ambos son casos base y devuelven `1` y `0`.
4. Los resultados se van sumando hacia arriba hasta resolver la llamada original.

Aunque elegante, la recursión puede ser ineficiente para algunos problemas (como este de Fibonacci, que recalcula muchas veces los mismos valores). A menudo, una solución con bucles (iterativa) es más rápida.

## **Capítulo 9: Interacción con Archivos**

La mayoría de los proyectos de ciencia de datos implican leer datos de archivos (CSV, TXT, JSON, etc.) y/o escribir resultados en ellos.

### **9.1. La Sentencia** `with open()`

Esta es la forma **estándar y recomendada** para trabajar con archivos en Python. Su gran ventaja es que **maneja automáticamente el cierre del archivo** cuando el bloque de código indentado termina, incluso si ocurren errores.

**Sintaxis:**

```Python
with open("ruta/al/archivo.txt", "modo", encoding="utf-8") as variable_archivo:
    # Trabajar con el archivo a través de 'variable_archivo'
```

- `ruta/al/archivo.txt`: Si el archivo está en la misma carpeta que tu script `.py`, solo necesitas el nombre del archivo. Si no, necesitas proporcionar la ruta completa.
- `modo`: Un string que indica qué quieres hacer con el archivo.
- `encoding="utf-8"`: Es una excelente práctica especificar siempre la codificación. `utf-8` es un estándar universal que maneja correctamente tildes, eñes y otros caracteres especiales.

### **9.2. Modos de Apertura de Archivos**

- 'r': Read | Leer. Es el modo por defecto. El archivo debe existir, de lo contrario da un FileNotFoundError.
- 'w': Write | Escribir. Si el archivo existe, borra todo su contenido. Si no existe, lo crea.
- 'a': Append | Añadir. Si el archivo existe, escribe al final del mismo sin borrar nada. Si no existe, lo crea.
- '+': Plus | Se puede añadir a los otros modos ('r+', 'w+') para permitir lectura y escritura simultáneamente.

### **9.3. Leer de un Archivo**

```Python
# Leer un archivo línea por línea
try:
    with open("frases_famosas.txt", "r", encoding="utf-8") as file:
        for linea in file:
            # .strip() es útil para quitar saltos de línea invisibles (\n)
            print(linea.strip())
except FileNotFoundError:
    print("El archivo no fue encontrado. Por favor, verifica la ruta.")
```

### **9.4. Escribir en un Archivo**

```Python
# Datos que queremos guardar
frases = {
    'Siempre que llovió paró': 'Facu',
    'Aunque la mona se vista de seda, mona queda': 'Mati',
    'Más vale pájaro en mano que cien volando': 'Caro'
}

# Usamos el modo 'w' para crear/sobrescribir el archivo
with open("frases_guardadas.txt", "w", encoding="utf-8") as file:
    file.write("=== Mis Frases Favoritas ===\n")
    for frase, autor in frases.items():
        # file.write() solo acepta un string como argumento
        linea_a_escribir = f'"{frase}" - {autor}\n' # \n para un nuevo renglón
        file.write(linea_a_escribir)

print("¡Archivo guardado con éxito!")
```

## **Capítulo 10: Modularidad - Importaciones**

A medida que tus programas crecen, es insostenible mantener todo el código en un solo archivo. Los **módulos** son simplemente archivos `.py` que contienen código Python (funciones, clases, variables) que puedes importar y usar en otros archivos.

### **10.1. El Ecosistema de Python**

Python viene con una **Biblioteca Estándar** (`Standard Library`) que incluye cientos de módulos para tareas comunes, como `math` para matemáticas, `datetime` para fechas y horas, y `random` para números aleatorios.

Además, existe un repositorio gigantesco de paquetes de terceros llamado **PyPI** (Python Package Index), donde encontrarás las librerías de Data Science como `pandas`, `numpy`, etc.

### **10.2. Formas de Importar Módulos**

- `import modulo` **(Recomendado)**: Importa el módulo completo. Para usar sus contenidos, debes usar el nombre del módulo como prefijo. \

```Python
import math

raiz_cuadrada = math.sqrt(25)
valor_pi = math.pi
print(f"La raíz de 25 es {raiz_cuadrada} y el valor de pi es {valor_pi}")
```

- `import modulo as alias`: Igual que el anterior, pero le da un alias (un apodo más corto) al módulo. Es extremadamente común en Data Science. \

```Python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# mi_array = np.array([1, 2, 3])
```

- `from modulo import elemento`: Importa un elemento específico (una función, una clase) de un módulo. Puedes usarlo directamente sin el prefijo. \

```Python
from math import sqrt, pi

raiz_cuadrada = sqrt(25)
valor_pi = pi
print(f"Ahora puedo usar sqrt directamente. Raíz: {raiz_cuadrada}")
```

- `from modulo import *` **(No Recomendado)**: Importa **todos** los elementos de un módulo al espacio de nombres actual. **Se debe evitar** porque "contamina" tu espacio de nombres, puede causar colisiones de nombres (que dos módulos tengan una función con el mismo nombre) y hace muy difícil saber de dónde proviene cada función.

## **Capítulo 11: Manejo de Errores y Excepciones**

Un programa robusto no es aquel que nunca falla, sino aquel que sabe cómo manejar las fallas con elegancia.

### **11.1. Errores de Sintaxis vs. Excepciones**

- `SyntaxError`: Ocurre cuando tu código no sigue las reglas gramaticales de Python. El intérprete detecta esto **antes** de que el programa empiece a ejecutarse. Ejemplos: olvidar los dos puntos `:` después de un `if`, una comilla sin cerrar.

- **Excepción**: Ocurre **durante la ejecución** de un programa que es sintácticamente correcto. Sucede cuando el programa encuentra una situación que no puede manejar.

### **11.2. Excepciones Comunes**

- `ZeroDivisionError`: Intentar dividir por cero.
- `NameError`: Intentar usar una variable que no ha sido definida.
- `TypeError`: Realizar una operación en un tipo de dato inadecuado (ej: `'5' + 10`).
- `ValueError`: El tipo del dato es correcto, pero su valor es inapropiado (ej: `int('hola')`).
- `IndexError`: Intentar acceder a un índice de una secuencia que no existe.
- `KeyError`: Intentar acceder a una clave de un diccionario que no existe.
- `FileNotFoundError`: Intentar abrir un archivo que no se encuentra en la ruta especificada.

### **11.3. La Estructura** `try...except...else...finally`

Este bloque te permite "atrapar" excepciones y ejecutar código de respaldo.

**Sintaxis y Flujo:**

```Python
try:
    # 1. Código propenso a errores. Python "intenta" ejecutar esto.
except TipoDeError as e:
    # 2. Si ocurre 'TipoDeError' en el bloque try, se ejecuta este bloque.
    #    'e' es una variable opcional que captura el objeto de la excepción.
else:
    # 3. Si NO ocurre ninguna excepción en el bloque try, se ejecuta este bloque.
finally:
    # 4. Este bloque se ejecuta SIEMPRE, haya habido una excepción o no.
```

**Ejemplo Completo:**

```Python
try:
    numerador = int(input("Introduce el numerador: "))
    denominador = int(input("Introduce el denominador: "))
    
    resultado = numerador / denominador

except ValueError:
    # Se ejecuta si el usuario no introduce un número válido
    print("Error: Debes introducir números enteros.")
except ZeroDivisionError as e:
    # Se ejecuta si el denominador es 0
    print(f"Error matemático: No se puede dividir por cero. ({e})")
else:
    # Se ejecuta solo si la división fue exitosa
    print(f"El resultado de la división es: {resultado}")
finally:
    # Se ejecuta siempre, para tareas de "limpieza"
    print("El programa de cálculo ha finalizado su ejecución.")
```

## **Capítulo 12: Introducción a la Programación Orientada a Objetos (POO)**

La POO es un paradigma de programación que estructura el código en torno a "objetos" que agrupan datos (atributos) y comportamientos (métodos). Es una forma de modelar entidades del mundo real en tu código.

### **12.1. Clases y Objetos**

- **Clase:** Es el **plano** o la plantilla para crear objetos. Define las propiedades y acciones que todos los objetos de ese tipo tendrán. Por convención, los nombres de las clases usan `CamelCase` (ej: `CuentaBancaria`).
- **Objeto (o Instancia):** Es una **entidad concreta creada a partir de una clase**. Puedes tener muchos objetos del mismo tipo, cada uno con sus propios datos.

### **12.2. Atributos y Métodos**

- **Atributos:** Son las **variables** que pertenecen a un objeto. Almacenan el estado o las características del objeto.
- **Métodos:** Son las **funciones** que pertenecen a un objeto. Definen su comportamiento o las acciones que puede realizar.

### **12.3. El Constructor** `__init__` **y** `self`

- `__init__(self, ...)`**:** Es un método especial llamado **constructor**. Se ejecuta **automáticamente** cada vez que se crea un nuevo objeto de la clase. Su función principal es **inicializar los atributos** del objeto.
- `self`: Es el primer parámetro de cualquier método dentro de una clase. Se refiere a la **instancia u objeto específico** que está llamando al método. A través de `self`, un objeto puede acceder a sus propios atributos y métodos.

**Ejemplo Práctico:** `CuentaBancaria`

```Python
# --- Definición de la CLASE (el plano) ---
class CuentaBancaria:
    # 1. El constructor: se ejecuta al crear una cuenta nueva.
    def __init__(self, num_cuenta, nombre_titular, balance_inicial):
        # 2. Atributos: se guardan usando 'self'.
        self.num_cuenta = num_cuenta
        self.nombre_titular = nombre_titular
        self.balance = balance_inicial
        print(f"Cuenta {self.num_cuenta} para {self.nombre_titular} creada con éxito.")

    # 3. Métodos: definen el comportamiento.
    def depositar(self, monto):
        if monto > 0:
            self.balance += monto
            print(f"Depósito de ${monto} realizado. Nuevo balance: ${self.balance}")
        else:
            print("El monto a depositar debe ser positivo.")

    def retirar(self, monto):
        if monto > 0 and monto <= self.balance:
            self.balance -= monto
            print(f"Retiro de ${monto} realizado. Nuevo balance: ${self.balance}")
        else:
            print("Monto inválido o fondos insuficientes.")

    def generar_balance(self):
        print(f"El balance actual de la cuenta {self.num_cuenta} es: ${self.balance}")


# --- Creación y uso de OBJETOS (instancias) ---
# Creamos dos objetos diferentes a partir de la misma clase.
cuenta_nora = CuentaBancaria('105-356-643', 'Nora Smith', 5600)
cuenta_juan = CuentaBancaria('105-356-644', 'Juan Pérez', 1200)

print("\n--- Operaciones con la cuenta de Nora ---")
cuenta_nora.generar_balance()
cuenta_nora.depositar(400)
cuenta_nora.retirar(1000)

print("\n--- Operaciones con la cuenta de Juan ---")
cuenta_juan.generar_balance()
cuenta_juan.retirar(1500) # Esto dará un error de fondos insuficientes
```
