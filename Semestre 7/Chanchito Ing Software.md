
## Metodologías 

## Metodología Ágil

Para proyectos dinámicos (cambio en requisitos) y complejos, cultura organizacional flexible.

- Elementos clave de planificación Ágil:
	- Hojas de ruta
	- Sprints
	- Planes de retroalimentación
	- Historias de usuario

Las horas pueden ser poco precisas
### Scrum 

#### Keywords (Conceptos clave)

- *Sprint*
Ciclo de software (2 a 4 semanas)

- *Sprint Backlog* Backlog del Producto
Lista de funcionalidades ordenadas por prioridad a desarrollar.

- *Velocity*
Estimación cuánto puede hacer el equipo (estimacion de historias completadas)

- *Incremento*
Software entregado en un sprint

- *MVP*
Producto Mínimo Viable

#### Roles principales (equipo)

- Dev team

- Techical Leader
Apoya al equipo junto al Scrum Master y nivelar juniors

- Scrum master
	Lider del equipo de desarrollo

- Product Owner
	Entrega de valor y backlog de sprint a sprint.
	Vela por valor agregado, representando al negocio.

- Product Designer
	Visión más elevada y estratégica incluyendo lucas (presupuesto).
	Vela por todo (hitos) mas que solo cumplir con sprints
### Kanban

Metodologia que optimiza proceso de desarrollo con flujos continuos de trabajo.

- Desarrollo incremental, divide trabajo por partes (Trello)

| Backlog | Stories | To do | In progress | To verify | Done |
| ------- | ------- | ----- | ----------- | --------- | ---- |
**Tarjeta de señal**
Unidad de trabajo que se mueve a traves del flujo de la organización sólo cuando hay capacidad de tomar la tarea en el siguiente paso

==Desventaja==
Puedes perder visibilidad del objetivo final
#### Principios de Kanban

1. Visualiza el trabajo
2. Limita el trabajo en progreso (WIP)
3. Gestionar el flujo (identificar bloqueo)
4. Visualización de políticas}
No puedo moverme a la sgte columna sin que este listo
5. Colaboración, evolución y experimentación

--- 
### Design Thinking

Método para generar ideas innovadoras y dar solución a un problema

- Lluvia de ideas
- Iterar ideas para llegar al prototipo - Relacionado a los requerimientos

*Etapas*
1. Enfatizar
2. Definir
3. Idear
4. Prototipar
5. Testear
### Lean Startup

Enfoque: Crear prototipo/MVP para validar ideas de negocio

Speedrun para construir MVP, medir qué funciona, qué no, feedback y crítica.


___

## Requerimientos

**Funcionales**
Qué debe hacer el sistema: Historias de usuario

- Casos de uso
- Historias de Usuario

**No funcionales**
Cómo debe funcionar
Rendimiento, seguridad, usabilidad, disponibilidad, escalabilidad

**Dominio**
Reglas y restricciones del contexto

**Levantamiento de Requerimientos**
Interactuar, Ordenar, Priorizar, Documentar --> Validar e Iterar

___

## Modelamiento de Sistemas / Diagramas UML

Abstracción del sistema. Diagramas que sirven para representar/diseñar sistemas.
No es necesariamente una representación fiel de la realidad (depende del contexto).

Distintas perspectiva:
- Externa
	Modela contexto o ambiente del sistema
- Interactiva
	Modela interacciones, componentes, ambientes
- Estructural
	Modela datos que son procesados
- Comportamiento
	Modela el comportamiento, acciones y respuesta a eventos

 Diagrama de contexto
- Diagrama de *actividades*
- Diagrama de *casos de uso*
- Diagrama de secuencia
- Diagrama de clases
- Diagrama de *estados*


### Diagrama de Actividades


---
# Solemne 2 

Se debe desarrollar un sistema de registro de usuarios para una aplicación web. El sistema debe permitir a los usuarios registrarse, iniciar sesión y gestionar su perfil. Se requiere realizar pruebas de Component Testing, Testing basado en escenarios y Alpha Testing

1. permitir a los usuarios registrarse
2.  iniciar sesion
3. gestionar su perfil

- Component Testing

*Identificador* CT1
*Nombre Requisito* Registro de usuario e inicio de sesión
*Requisitos asociados* 1 y 2
*Descripción* Se probará el componente de registro e inicio de sesion que incluye las siguientes actividades/unidades: creación de cuenta, registro de cuenta, validación de cuenta, inicio de sesión y validación de inicio de sesión.
Las pruebas incluirán:
- Registro de usuario
- Inicio de sesión
- Intento de registro de usuario con nombre de usuario ya creado
- Intento de inicio de sesión con credenciales mal escritas
*Peor valor aceptable* No cumple
*Valor planificado* Cumple
*Tipo de usuario* Todo tipo de usuario, sobre todo no registrado


- Testing basado en escenarios

*Identificador* TE1
*Nombre requisito* Registro de usuario
*Requisito asociado* 1
*Descripción* Se probará el escenario donde el usuario desee registrarse y crear su propia cuenta para luego iniciar sesión con su cuenta ya creada
*Peor valor aceptable* No cumple
*Valor esperado* Cumple
*Tipo de usuario* Todo usuario, sobre todo no registrado

- Alpha testing

*Identificador* AT1
*Nombre requisito* Gestionar su perfil
*Requisito asociado* 3
*Descripción* 



