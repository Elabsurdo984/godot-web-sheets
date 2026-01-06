# Funciones de Godot

## physics process

Es un método especial de Godot que se ejecuta automáticamente a **tasa fija** (por defecto 60 veces por segundo) para manejar lógica de **física** estable y consistente, ideal para movimiento de personajes como CharacterBody2D.

**Siempre multiplica por `delta`** para movimiento suave independientemente del rendimiento. Sin ella, objetos rápidos "saltan" en PCs lentos.

**Ejemplo practico con CharacterBody2D:** 

```python
@export var velocidad: float = 300.0

func _physics_process(delta):
    var direccion = Input.get_axis("ui_left", "ui_right")
    velocity.x = direccion * velocidad
    velocity.y += GRAVEDAD * delta  # Gravedad frame-independiente
    move_and_slide()  # Aplica física + colisiones

```

## ready:

La función **`_ready()`** se ejecuta **una sola vez** cuando un nodo (y todos sus hijos) terminan de cargarse en la escena del árbol de nodos. Es el lugar perfecto para inicializaciones seguras, como conectar señales o asignar referencias a nodos hijos.

```python
@onready var sprite = $Sprite2D
@export var vida_max: int = 100

func _ready():
    vida_actual = vida_max  # Seguro: todos los nodos hijos existen
    sprite.visible = true
    print("¡Personaje listo!")
```