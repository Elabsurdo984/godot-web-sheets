# Constantes

Las **constantes** declaran valores que **nunca cambian** durante la ejecución, mejorando rendimiento y evitando errores accidentales.

```python
const VELOCIDAD_JUGADOR: float = 300.0  # Convención: MAYÚSCULAS
const PUNTOS_POR_MONEDA: int = 100
const NOMBRE_JUEGO: String = "Mi Juego"

```

| `var` | `const` |
| --- | --- |
| **Mutable** (puede cambiar) | **Inmutable** (nunca cambia) |
| `var vida = 100; vida = 50` | `const MAX_VIDA = 100; MAX_VIDA = 50` **❌ Error** |
| Inicialización flexible | **Debe inicializarse inmediatamente** |

## Constantes de Godot

```python
const PI: float = 3.14159  # Matemáticas
const TAU: float = PI * 2  # 2π (360°)

# Constantes físicas predefinidas
const GRAVEDAD: float = 980.0
const FPS: int = 60
```