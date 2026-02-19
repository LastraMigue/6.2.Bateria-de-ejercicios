# 6.2.BATERIA DE EJERCICIOS

## Ejercicio 1:

**Supuesto:** Diseña una clase para gestionar un **Usuario** de una plataforma de streaming.

  - **Atributos:** nombre de usuario (privado), contraseña (privada), correo (público).
  - **Métodos:** cambiarPassword(String nueva) (público) y validarEmail() (privado).


```mermaid
classDiagram
direction TB
    class Usuario {
        - nombre : String
        - contraseña : String
        + correo : String
        + cambiarPassword(nueva : String) void
        - validarEmail() boolean
    }
```

## Ejercicio 2:

**Supuesto:** En un sistema escolar, tenemos **Personas** y **Estudiantes**.

  - Una Persona tiene nombre y DNI.
  - Un Estudiante es una Persona, pero además tiene un numeroExpediente y una notaMedia.


```mermaid
classDiagram
direction BT

    class Persona {
        # nombre : String
        # dni : String
    }

    class Estudiante {
        - numeroExpediente() int
        - notaMedia() double
    }

Estudiante --|> Persona
```

## Ejercicio 3:

**Supuesto:** Modelar una **Computadora**.

  - Una Computadora tiene una **PlacaBase**. Si la computadora se destruye, la placa base también se considera destruida (vínculo fuerte).
  - Una Computadora tiene periféricos como un **Raton**. Si la computadora desaparece, el ratón puede usarse en otra (vínculo débil).


```mermaid
classDiagram
direction TB

    class Computadora {
        - placaBase : PlacaBase
        - raton : Raton
    }

    class PlacaBase {
        - nombre : String
        - modelo : String
    }

    class Raton {
        - nombre : String
        - marca : String
    }

Computadora *-- PlacaBase : tiene
Computadora o-- Raton : tiene
```

## Ejercicio 4:

**Supuesto:** Un **CentroComercial** y sus **Tiendas**.

  - Un CentroComercial puede albergar de 1 a muchas tiendas.
  - Cada Tienda pertenece exactamente a un CentroComercial.


```mermaid
classDiagram
direction TB

    class CentroComercial {
        - nombre : String
        - direccion : String
    }

    class Tienda {
        - nombre : String
        - tipo_tienda : String
    }

CentroComercial "1" *-- "1..*" Tienda : alberga
```

## Ejercicio 5:

**Supuesto:** Sistema de pagos.

  - Crea una interfaz **MetodoPago** con el método procesar(double importe).
  - Las clases **Tarjeta** y **Paypal** deben implementar dicho contrato.
  - La clase **Carrito** tiene un método pagar(MetodoPago miMetodo) (Uso puntual).


```mermaid
classDiagram
direction TB

    class MetodoPago {
        <<interface>>
        + procesar(double importe) boolean
    }

    class Tarjeta {
        + procesar(double importe) boolean
    }

    class Paypal {
        + procesar(double importe) boolean
    }

    class Carrito {
        + pagar(MetodoPago miMetodo) void
    }

MetodoPago <|.. Tarjeta
MetodoPago <|.. Paypal
Carrito ..> MetodoPago : usa
```
    
## Ejercicio 6:

**Supuesto:** Sistema de Gestión de una Biblioteca Universitaria

**Contexto:** La biblioteca necesita un sistema básico para gestionar su catálogo de recursos y los préstamos a los usuarios.

**Requisitos del diseño (UML):**

  - **Clase Recurso (Padre):**
    - **Atributos:** id (int) y titulo (String), ambos privados.
    - **Métodos:** prestar() y devolver(), ambos públicos.
  - **Clases Libro y Revista (Hijas):**
    - Ambas son tipos de Recurso (herencia).
    - Libro tiene un atributo propio: isbn (String).
    - Revista tiene un atributo propio: numeroEdicion (int).
  - **Clase Usuario:**
    - **Atributos:** nombre (String) y numCarnet (int).
    - **Relación:** Un Usuario puede tener **uno o varios** Recurso prestados en un momento dado (1 a 0..*).


```mermaid
classDiagram
direction TB

    class Recurso {
        - id : int
        - titulo : String
        + prestar() void
        + devolver() void
    }

    class Libro {
        - isbn : String
    }

    class Revista {
        - numeroEdicion : int
    }

    class Usuario {
        - nombre : String
        - numCarnet : int
    }

Recurso <|-- Libro
Recurso <|-- Revista
Usuario "1" --> "0..*" Recurso : tiene prestado
```
