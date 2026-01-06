# Palabras Clave de Control de Flujo

| Palabra | Dónde se usa | Acción |
| --- | --- | --- |
| **`break`** | Bucles (`for`, `while`) | **Sale completamente** del bucle |
| **`continue`** | Bucles (`for`, `while`) | **Salta a siguiente iteración** |
| **`pass`** | Cualquier bloque | **No hace nada** (placeholder) |
| **`return`** | Funciones | **Termina función + devuelve valor** |

## Ejemplos prácticos:

```python
# BREAK - Salir temprano
for i in range(10):
    if i == 5:
        break  # Termina el bucle en 5
    print(i)  # Imprime 0,1,2,3,4

# CONTINUE - Saltar iteración
for i in range(5):
    if i == 2:
        continue  # Salta el 2
    print(i)  # Imprime 0,1,3,4

# PASS - Placeholder (función vacía)
func funcion_futura():
    pass  # No hace nada aún

# RETURN - Salir de función
func validar_edad(edad: int) -> String:
    if edad < 18:
        return "Menor"  # Sale YA
    return "Adulto"  # Sale al final

```

## **Combinaciones Poderosas**

```python
func procesar_lista(numeros: Array):
    for num in numeros:
        if num < 0:
            continue  # Salta negativos
        if num > 100:
            break     # Termina si muy grande
        print(num * 2)
```