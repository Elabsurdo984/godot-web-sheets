# Collision Layers/Masks

**Collision Layers y Masks** son el **sistema de filtros** que decide **QUÉ colisiona con QUÉ**. Cada nodo físico tiene **32 capas** (1-32) para organizar colisiones.

**Regla Simple: LAYER = "YO SOY", MASK = "YO BUSCO"**

## Configuracion (¡IMPORTANTE!)

```
Proyecto → Project Settings → Layer Names → 2D Physics
Layer 1: "Mundo"     (suelo, paredes)
Layer 2: "Jugador"   
Layer 3: "Enemigos"  
Layer 4: "Items"     (monedas, powerups)
Layer 5: "Hitbox"    (ataques jugador)
```

## Ejemplos Prácticos:

| Nodo | Layer | Mask | Colisiona con |
| --- | --- | --- | --- |
| **Jugador** | 2 | 1,3 | Mundo + Enemigos |
| **Suelo** | 1 | - | Nada (solo bloquea) |
| **Enemigo** | 3 | 1,2 | Mundo + Jugador |
| **Moneda** | 4 | 2 | Solo Jugador |
| **Hitbox Ataque** | 5 | 3 | Solo Enemigos |

## Visualización Inspector:

```
[ ] 1 Mundo
[✔] 2 Jugador    ← Layer (YO SOY)
[ ] 3 Enemigos
[ ] 4 Items

[✔] 1 Mundo      ← Mask (YO BUSCO)
[ ] 2 Jugador
[✔] 3 Enemigos
[ ] 4 Items

```

## Código para Debug

```python
func _ready():
    print("Layer: ", collision_layer)
    print("Mask: ", collision_mask)
    set_collision_layer_value(2, true)   # Layer 2 ON
    set_collision_mask_value(1, true)    # Mask 1 ON
    set_collision_mask_value(3, false)   # Mask 3 OFF

```

**Regla de oro**: **Primero configura nombres en Project Settings**. **Layer = Identidad, Mask = Visión**. Sin esto, todo colisiona con todo = caos.