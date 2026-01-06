# Bucle For

Repite un bloque de código para cada elemento de una secuencia (array, rango numérico o string), automatizando tareas repetitivas de forma ordenada.

## Sintaxis Básica

```python
# Recorrer array
var colores = ["rojo", "verde", "azul"]
for color in colores:
    print(color)  # Imprime cada color

# Rango numérico con "range()"
for i in range(5):  # 0, 1, 2, 3, 4
    print("Número: ", i)

# Range personalizado
for i in range(2, 8, 2):  # 2, 4, 6 (inicio, fin, paso)
    print(i)
```

## Casos de Uso Comunes

- **Procesar listas**: Sumar puntajes, validar items
- **Contadores**: Generar niveles, delays
- **Animaciones**: Rotar elementos secuencialmente