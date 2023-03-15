# Refactoreo de la clase InventoryManager para cumplir SRP (NO DE ARQ)

* Status: proposed
* Deciders: gamosques
* Date: 2022-10-02

## Context and Problem Statement

Actualmente, el sistema está contenido en una sola aplicación monolítica, lo que dificulta realizar cambios y mantener el sistema. 
La clase InventoryManager es responsable de manejar todos los aspectos de la gestión de inventario, lo que la hace demasiado compleja y con demasiadas responsabilidades y, por lo tanto, candidata a cambiar con mucho impacto. Refactorear la clase puede tener un alto costo de cambio y despliegue.

## Decision Drivers

* Los cambios a la clase InventoryManager son frecuente y, por lo tanto, el impacto en las demás aplicaciones es recurrente.

## Considered Options

* Introducir un adaptador
* Refactorear la clase para cumplir SRP

## Decision Outcome

Chosen option: "Refactorear la clase para cumplir SRP", because Evitamos los costos recurrentes por cambios solicitados por distintas unidades de negocio

### Positive Consequences

* Menos impacto a futuro

### Negative Consequences

* Más clases para mantener

## Pros and Cons of the Options

### Introducir un adaptador

Crear una clase adaptadora que permita aislar el cambio de InventoryManager

* Good, because se pueden realizar cambios paulatinos y refactorear la clase problemática con tiempo
* Bad, because Se agrega una nueva indirección
* Bad, because La clase adaptadora puede terminar teniendo los mismos problemas

### Refactorear la clase para cumplir SRP

la clase se divide en tres, manteniendo la misma como fachada que delega
InventoryTracker: responsable de realizar un seguimiento de los niveles de inventario y para las demás responsabilidades delega a las otras. 
OrderPlacer: responsable de ejecutar pedidos.
ReportGenerator: responsable de generar informes.

* Good, because El refactoreo va a minimizar el impacto de futuros cambios,
* Good, because Las responsabilidades del negocio se corresponden con las de las tres clases.
* Bad, because Tenemos tres clases en lugar de una
