# Utilización de Arquitectura hexagonal en todos los servicios

* Status: accepted
* Deciders: gamousques
* Date: 2022-06-13

## Context and Problem Statement

El estilo basado en mini/mico servicios independiza a los equipos de desarrollo brindando libertad al momento de estructurar cada servicio. No contamos con una estructura básica para los servicios, lo cual afecta la mantenibilidad, el proceso de testeabilidad y el mantenimiento.

## Decision Drivers

* Mantenibilidad -> al no contar con una arquitectura de aplicación básica cada equipo adopta su estilo o no utiliza ninguno
* Testeabilidad  -> al no existir una estructura canónica para diseñar arquitecturas, el desarrollo de pruebas automatizadas no es uniforme lo cual impacta en que cada pipeline de CI/CD sea difícil de comprender y mantener.

## Considered Options

* Layers técnicos
* Arquitectura Hexagonal
* Clean Architecture

## Decision Outcome

Chosen option: "Arquitectura Hexagonal", because Favorece la mantenibilidad y sirve como estructura base para cualquier servicio que no tenga requerimientos especiales

### Positive Consequences

* Se uniformiza la estructura de los servicios y se favorece la mantenibilidad
* Se facilita la testeabilidad y el diseño de los pipelines de CI/CD

### Negative Consequences

* Es necesario tocar el tema en el onboarding técnico

## Pros and Cons of the Options

### Layers técnicos

* Good, because Estilo conocido y que muchas herramientas  que utiliza la empresa (Express, .NET. etc) por defecto imponen como estructura tipo para los proyectos
* Bad, because Con esta estructura tiende a perderse el modelo del dominio
* Bad, because Es necesario que los equipos se preocupen por distribuir las responsabilidades bien

### Arquitectura Hexagonal

* Good, because Arquitectura que define claramente las responsabilidades de cada layer
* Good, because Orientada al cambio de tecnologías y protege las entidades del negocio
* Bad, because A veces es necesario adaptar la estructura tipo que utilizan las tecnologías (layers tecnológicos)
* Bad, because No todos los equipos manejan los conceptos de esta arquitectura

### Clean Architecture

Similar a Hexagonal

* Good, because Idem hexagonal
* Bad, because Idem hexagonal

## Links

* https://en.wikipedia.org/wiki/Hexagonal_architecture_(software)
* https://netflixtechblog.com/ready-for-changes-with-hexagonal-architecture-b315ec967749
