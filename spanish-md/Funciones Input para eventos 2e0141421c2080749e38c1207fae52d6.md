# Funciones Input para eventos

Para seguir la sección de Input, el siguiente paso natural es **manejar eventos con `_input(event)` y `_unhandled_input(event)`**, que es el otro enfoque principal además del polling con **`Input`**. 

## **`_input(event)`** vs **`_unhandled_input(event)`**

- **`_input(event)`** se llama en cualquier nodo con ese método cuando llega un evento de entrada (tecla, ratón, gamepad, etc.).
- **`_unhandled_input(event)`** se llama después, solo con los eventos que no fueron “consumidos” por la interfaz (UI) u otros nodos, y es ideal para controles generales del juego.

## Ejemplo con `_input(event)`

```python
func _input(event: InputEvent) -> void:
    if event.is_action_pressed("jump"):
        jump()

    if event.is_action_released("shoot"):
        stop_shooting()

    if event is InputEventMouseButton and event.pressed:
        print("Click en: ", event.position)
```

**Puntos clave:**

- **`event.is_action_pressed("jump")`** usa las acciones que configuraste en el Input Map.
- También se puede filtrar por tipo (**`InputEventMouseButton`**, **`InputEventKey`**, etc.) para acceder a datos específicos (posición del ratón, qué botón, qué tecla).

## Ejemplo con `_unhandled_input(event)`

```python
func _unhandled_input(event: InputEvent) -> void:
    if event.is_action_pressed("pause"):
        toggle_pause()

    if event.is_action_pressed("ui_cancel"):
        open_back_menu()
```

Uso típico:

- Se coloca en un nodo “global” (por ejemplo, un autoload o el nodo raíz de la escena principal).
- Sirve para cosas como pausa, abrir menús, salir al título, que deben funcionar incluso con UI en pantalla.

---

## Tipos de InputEvent más comunes

- **`InputEventKey`** → teclas de teclado (propiedades: **`keycode`**, **`pressed`**, **`echo`**).
- **`InputEventMouseButton`** → botones del ratón (**`button_index`**, **`position`**, **`pressed`**, **`double_click`**).
- **`InputEventMouseMotion`** → movimiento del ratón (**`position`**, **`relative`**).
- **`InputEventJoypadButton`** → botones de mando (**`button_index`**, **`pressed`**).
- **`InputEventJoypadMotion`** → ejes de joystick (**`axis`**, **`axis_value`**).