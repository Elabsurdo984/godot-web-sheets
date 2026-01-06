# Comentarios y Regiones

Los **comentarios** en GDScript documentan código sin ejecutarse, mejorando legibilidad. Hay **tres tipos** más **regiones plegables**.

## Tipos de Comentarios:

```python
# 1. Línea única estándar
# Nota rápida

## 2. Documentación (##) ← GENERA TOOLTIPS
## Esta función calcula daño basado en nivel
## @param: nivel (int) - Nivel del jugador
func calcular_daño(nivel: int):

# 3. Inline
var vida = 100  # Puntos de vida máximos

"""
4. Multilínea (docstring)
Explicación detallada de funciones complejas
Aparece en autocompletado del editor
"""

```

## **Regiones Plegables (Code Folding)**

```python
#region NOMBRE_REGION    ← Inicio (se pliega)
var enemigo_vida = 100
var jugador_vida = 200
#endregion               ← Fin

#region FUNCIONES_UTILES
func sumar(a, b):
    return a + b
#endregion

```