# Nodos Control mas Usados

Son los nodos básicos para construir interfaces en Godot (menús, HUDs, ventanas).

La idea es combinarlos como “bloques” para crear layouts limpios y fáciles de mantener.

## Tabla de nodos principales

**Button**

- Uso: Botón clicable para menús, confirmaciones, opciones, etc.
- Señales clave: **`pressed`**, **`toggled`** (si es botón tipo switch).
- Ejemplo:

```python
extends Button

func _ready() -> void:
    pressed.connect(_on_pressed)

func _on_pressed() -> void:
    print("Botón presionado")
```

**Label**

- Uso: Mostrar texto estático (puntos, mensajes, títulos, instrucciones).
- Propiedad clave: **`text`**.
- Ejemplo:

```python
$Label.text = "Puntaje: %d" % score
```

**TextureRect**

- Uso: Mostrar imágenes dentro de la UI (íconos, retratos, fondos de panel).
- Propiedades clave: **`texture`**, **`stretch_mode`** para controlar cómo se escala.
- Ejemplo:

```python
$TextureRect.texture = preload("res://ui/icon_coin.png")
```

**Panel / PanelContainer**

- Uso: Fondos y marcos para agrupar otros controles (menús, ventanas, cuadros de diálogo).
- Panel: solo fondo; PanelContainer: además ajusta el contenido con márgenes.
- Ejemplo:

```python
# Cambiar el estilo por código (tema, colores, etc.)
var style := get_theme_stylebox("panel", "Panel")
# Podés duplicar y modificar style si querés un panel custom
```

**HBoxContainer / VBoxContainer**

- Uso: Organizar automáticamente elementos en fila (horizontal) o en columna (vertical).
- Ideal para barras de botones, menús de opciones, listas.
- Ejemplo:

```python
# Agregar botones por código a un HBoxContainer
func _ready() -> void:
    for i in range(3):
        var b := Button.new()
        b.text = "Opción %d" % i
        $HBoxContainer.add_child(b)
```

**MarginContainer**

- Uso: Agregar márgenes alrededor del contenido (separar texto de bordes, darle “aire” a un panel).
- Propiedades clave: **`add_theme_constant_override("margin_left", 16)`**, etc.
- Ejemplo:

```python
$MarginContainer.add_theme_constant_override("margin_left", 16)
$MarginContainer.add_theme_constant_override("margin_right", 16)
```

**LineEdit / TextEdit**

- LineEdit: Entrada de una sola línea (nombre del jugador, campo de búsqueda).
- TextEdit: Texto multilínea (consolas, editores, grandes bloques de texto).
- Señales clave: **`text_submitted`** (LineEdit), **`text_changed`**.

```python
extends LineEdit

func _ready() -> void:
    text_submitted.connect(_on_enter_name)

func _on_enter_name(name: String) -> void:
    print("Nombre ingresado: ", name)
```

**CheckBox / CheckButton**

- Uso: Activar/desactivar opciones (sonido, fullscreen, etc.).
- Propiedad clave: **`button_pressed`** (bool).
- Ejemplo:

```python
extends CheckBox

func _ready() -> void:
    toggled.connect(_on_toggled)

func _on_toggled(pressed: bool) -> void:
    print("Opción activada: ", pressed)
```