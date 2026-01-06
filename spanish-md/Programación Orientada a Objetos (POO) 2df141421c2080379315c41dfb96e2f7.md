# Programación Orientada a Objetos (POO)

La **POO** organiza el código en **objetos** que combinan datos (propiedades) y comportamiento (métodos). Godot usa GDScript con POO nativa desde la versión 4.0.

## 1. Clases y Objetos

**Clase**: Molde o blueprint. **Objeto**: Instancia concreta de una clase.

```python
class_name Auto  # Clase global
var marca: String
var velocidad: float

func _init(m: String, v: float):
    marca = m
    velocidad = v

var mi_auto = Auto.new("Toyota", 180.0)  # Objeto

```

## 2. Encapsulación

Agrupar datos y métodos relacionados, controlando acceso.

```python
class CajaFuerte:
    var _codigo: String = "1234"  # Convención: privado
    
    func abrir(codigo: String) -> bool:
        return _codigo == codigo
    
    func cambiar_codigo(nuevo: String):
        _codigo = nuevo
```

## 3. Herencia (**`extends`**)

Una clase hija hereda propiedades/métodos de la padre.

```python
class_name Vehiculo:
    var ruedas: int = 4
    
    func acelerar():
        print("Acelerando")

class Auto extends Vehiculo:  # Herencia
    func tocar_bocina():
        print("¡BIP BIP!")

class Moto extends Vehiculo:
    var ruedas: int = 2  # Sobrescribe
```

## 4. Polimorfismo

Mismo método, comportamiento diferente según clase.

```python
class Animal:
    func hacer_sonido():
        print("Sonido genérico")

class Perro extends Animal:
    func hacer_sonido():  # Sobrescritura
        print("¡Guau!")

class Gato extends Animal:
    func hacer_sonido():
        print("¡Miau!")
```

## 5. Abstracción

Ocultar detalles complejos, mostrar solo lo esencial.

```python
class Banco:
    func depositar(cantidad: float): pass  # Abstracto
    func retirar(cantidad: float) -> bool: pass
    
class CuentaCorriente extends Banco:
    func depositar(cantidad: float):
        saldo += cantidad  # Implementación concreta
```

## Estructura Completa:

```python
# Item base (abstracción)
class_name Item extends Resource:
    @export var nombre: String
    @export var valor: int
    
    func usar() -> String:
        return "Item usado"

# Herencia + Polimorfismo
class Pocion extends Item:
    func usar() -> String:
        return "¡Vida restaurada!"

class Espada extends Item:
    func usar() -> String:
        return "¡Ataque +20!"

```