# CharacterBody2D

**CharacterBody2D** es el nodo para **personajes controlables** (jugador, NPCs) con **movimiento preciso + colisiones**. Reemplaza KinematicBody2D de Godot 3.

## Propiedades Esenciales

```
velocity: Vector2        # Velocidad actual (pixels/segundo)
move_and_slide()         # **FUNCIÓN MÁGICA**: mueve + colisiona
floor_snap_length        # Para plataformas
up_direction: Vector2    # Para detectar suelo (0, -1)

```

## Codigo Completo (Estandar):

```python
extends CharacterBody2D

const VELOCIDAD: float = 300.0
const SALTO_VELOCIDAD: float = -400.0
const GRAVEDAD: float = 980.0

func _physics_process(delta):
    # Gravedad
    if not is_on_floor():
        velocity.y += GRAVEDAD * delta
    
    # Movimiento horizontal
    var direccion = Input.get_axis("ui_left", "ui_right")
    velocity.x = direccion * VELOCIDAD
    
    # Salto
    if Input.is_action_just_pressed("ui_accept") and is_on_floor():
        velocity.y = SALTO_VELOCIDAD
    
    # ¡MÁGICO! Mueve + maneja colisiones automáticamente
    move_and_slide()

```

## Métodos Poderosos

```
is_on_floor()                    # ¿En suelo?
get_slide_collision_count()      # Cuántas colisiones esta frame
get_slide_collision(0).get_normal()  # Dirección de colisión
```

**Cuándo usar**: **TODOS** los personajes (jugador, enemigos, NPCs). Es **el nodo 2D más importante** para juegos de plataformas/action. **Nunca** uses **`position.x +=`** con CharacterBody2D.