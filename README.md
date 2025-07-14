# Reto-10
```python

```

## 1. Desarrolle un programa que permita realizar la suma/resta de matrices. El programa debe validar las condiciones necesarias para ejecutar la operación.
```python
# Función para imprimir la matriz
def impmatriz(matriz):
    for f in matriz:
        print(f)

# Función para pedir los datos de una matriz
def ingmatriz(filas, columnas, nombre):
    matriz = []
    print("Ingrese los datos para la matriz", nombre)
    for n in range(filas):
        fila = []
        for i in range(columnas):
            print("Elemento en la fila", n + 1, ", y en la columna", i + 1, ": ")
            valor = float(input())
            fila.append(valor)
        matriz.append(fila)
    return matriz

# Función para sumarlas
def sumarmatrices(A, B):
    resultado = []
    for i in range(len(A)):
        fila_resultado = []
        for j in range(len(A[i])):
            fila_resultado.append(A[i][j] + B[i][j])
        resultado.append(fila_resultado)
    return resultado

# Función para restarlas
def restar_matrices(A, B):
    resultado = []
    for n in range(len(A)):
        fila_resultado = []
        for i in range(len(A[n])):
            fila_resultado.append(A[n][i] - B[n][i])
        resultado.append(fila_resultado)
    return resultado

# Función principal
if __name__ == "__main__":
    filas = int(input("Ingrese el número de filas: ")) # Para tener más control de las otras funciones
    columnas = int(input("Ingrese el número de columnas: "))

    matriz_A = ingmatriz(filas, columnas, "A") # Se llaman la función anterior pero con su respectivo nombre
    matriz_B = ingmatriz(filas, columnas, "B")

    print("¿Qué operación desea realizar?") # Para que se ejecute la operación deseada
    print("sumar")
    print("restar")
    opcion = input("Eliga sumar o restar: ")

    if opcion == "sumar":
        resultado = sumarmatrices(matriz_A, matriz_B)
        print("Resultado:")
        impmatriz(resultado)
    elif opcion == "restar":
        resultado = restar_matrices(matriz_A, matriz_B)
        print("Resultado de la resta:")
        impmatriz(resultado)
```
## 2. Desarrolle un programa que permita realizar el producto de matrices . El programa debe validar las condiciones necesarias para ejecutar la operación.
```python
# Esta función pide ingresar los datos de una matriz
def pedir_matriz(nombre_matriz):
    # Pedimos cuántas filas y columnas tiene la matriz
    filas = int(input("Cuántas filas tiene la matriz " + nombre_matriz + ": "))
    columnas = int(input("Cuántas columnas tiene la matriz " + nombre_matriz + ": "))
    print("Ingresar los valores de la matriz " + nombre_matriz + ":")
    matriz = []  # Aquí vamos a guardar toda la matriz
    # Recorremos cada fila
    for fila_actual in range(filas):
        fila_nueva = []  # Lista vacía para guardar los valores de una fila
        # Recorremos cada columna
        for columna_actual in range(columnas):
            mensaje = "Valor en la posición [" + str(fila_actual) + "][" + str(columna_actual) + "]: "
            numero = float(input(mensaje))  # Ingresar numero
            fila_nueva.append(numero)  # Se agrega a la fila
        matriz.append(fila_nueva)  # Se agrega la fila completa a la matriz

    return matriz, filas, columnas  # Se devuelve la matriz y su tamaño

# Esta función muestra en pantalla cualquier matriz
def mostrar_matriz(matriz):
    for fila in matriz:
        linea = ""  # Cadena para mostrar cada fila
        for valor in fila:
            linea += str(valor) + "  "  # Convertimos cada número a texto y lo agregamos a la línea
        print(linea)  # Mostramos la fila completa

# Esta función resta dos matrices del mismo tamaño
def restar(matriz1, matriz2):
    resultado = []  # Aquí se guardará la nueva matriz restada
    # Recorremos cada fila
    for fila_actual in range(len(matriz1)):
        fila_resta = []  # Lista para la fila resultante
        # Recorremos cada columna
        for columna_actual in range(len(matriz1[0])):
            resta = matriz1[fila_actual][columna_actual] - matriz2[fila_actual][columna_actual]
            fila_resta.append(resta)  # Guardamos el resultado de la resta
        resultado.append(fila_resta)  # Agregamos la fila restada al resultado final

    return resultado  # Devolvemos la matriz con la resta

# Parte principal del codigo
print("Resta de dos matrices")
# Pedimos los datos de ambas matrices
matrizA, filasA, columnasA = pedir_matriz("A")
matrizB, filasB, columnasB = pedir_matriz("B")
# Verificamos que las matrices tengan el mismo tamaño
if filasA != filasB or columnasA != columnasB:
    print("Error: Las matrices deben tener el mismo tamaño.")
else:
    # Hacemos la resta si las dimensiones coinciden
    resultado = restar(matrizA, matrizB)
    print("La matriz resultado de la resta es:")
    mostrar_matriz(resultado)  # Mostramos el resultado final
```
## 3. Desarrolle un programa que permita obtener la matriz transpuesta de una matriz ingresada. El programa debe validar las condiciones necesarias para ejecutar la operación.
```python
# Función para imprimir una matriz
def impmatriz(matriz):
    for f in matriz:
        print(f)

# Función para pedir los datos de una matriz
def ingmatriz(filas, columnas):
    matriz = []
    print("Ingrese los elementos de la matriz:")
    for n in range(filas):
        fila = []
        for j in range(columnas):
            print("Elemento en la fila", n + 1, "y columna", j + 1, ":")
            valor = float(input())
            fila.append(valor)
        matriz.append(fila)
    return matriz

# Función para calcular la matriz transpuesta
def transpuesta(matriz):
    filas = len(matriz)
    columnas = len(matriz[0])
    resultado = []
    for n in range(columnas):  # columnas se vuelven filas
        nueva_fila = []
        for i in range(filas):  # filas se vuelven columnas
            nueva_fila.append(matriz[i][n])
        resultado.append(nueva_fila)
    return resultado

# Función principal
if __name__ == "__main__":
    filas = int(input("Ingrese el número de filas: "))
    columnas = int(input("Ingrese el número de columnas: "))

    matriz = ingmatriz(filas, columnas)

    matriz_transpuesta = transpuesta(matriz)

    print("Matriz transpuesta:")
    impmatriz(matriz_transpuesta)
```
## 4. Desarrollar un programa que sume los elementos de una columna dada de una matriz.
```python
# Esta función es para ingresar los datos de una matriz
def pedir_matriz(nombre_matriz):
    filas = int(input("¿Cuántas filas tiene la matriz " + nombre_matriz + "? "))
    columnas = int(input("¿Cuántas columnas tiene la matriz " + nombre_matriz + "? "))
    print("Ingresar los valores de la matriz " + nombre_matriz + ":")
    matriz = []
    for fila_actual in range(filas):
        fila_nueva = []
        for columna_actual in range(columnas):
            mensaje = "Valor en la posición [" + str(fila_actual) + "][" + str(columna_actual) + "]: "
            numero = float(input(mensaje))
            fila_nueva.append(numero)
        matriz.append(fila_nueva)

    return matriz, filas, columnas

# Esta función muestra la matriz en pantalla
def mostrar_matriz(matriz):
    for fila in matriz:
        linea = ""
        for valor in fila:
            linea += str(valor) + "  "
        print(linea)

# Esta función suma los elementos de una columna específica
def sumar_columna(matriz, numero_columna):
    suma = 0
    for fila in matriz:
        suma += fila[numero_columna]

    return suma

# -Parte principal
print("Sumar los elementos de una columna específica de una matriz")
# Pedimos la matriz
matriz_usuario, filas, columnas = pedir_matriz("A")
# Mostramos la matriz para que el usuario se ubique
print("La matriz ingresada es:")
mostrar_matriz(matriz_usuario)

# Ingresar el numero de la columna a sumar
columna_a_sumar = int(input("¿Qué número de columna desea sumar? (Empieza desde 0): "))
# Validamos que la columna exista
if columna_a_sumar < 0 or columna_a_sumar >= columnas:
    print("Error: Esa columna no existe en la matriz.")
else:
    # Calculamos la suma
    resultado = sumar_columna(matriz_usuario, columna_a_sumar)
    print("La suma de los elementos de la columna " + str(columna_a_sumar) + " es: " + str(resultado))
```
## 5. Desarrollar un programa que sume los elementos de una fila dada de una matriz.
```python
# Función para sumar los elementos de una fila específica
def sumaf(matriz, fila):
    suma = 0
    for valor in matriz[fila]:
        suma += valor
    return suma

# Función para ingresar los datos de una matriz
def ingmatriz(filas, columnas):
    matriz = []
    print("Ingrese los elementos de la matriz:")
    for n in range(filas):
        fila = []
        for i in range(columnas):
            print("Elemento en la fila", n + 1, ", columna", i + 1, ":")
            valor = float(input())
            fila.append(valor)
        matriz.append(fila)
    return matriz


# Función principal
if __name__ == "__main__":
    filas = int(input("Ingrese el número de filas: "))
    columnas = int(input("Ingrese el número de columnas: "))

    matriz = ingmatriz(filas, columnas)

    print("¿Qué fila desea sumar?:")
    n = int(input())

    if 1 <= n <= filas:
        print("La suma de los elementos en la fila", n, "es:", sumaf(matriz, n))
```
