
# Clase 3
17703/26

## Requerimientos Funcionales
## Requerimientos NO Funcionales

### Performance
.
	- Throughput
	- Tiempo de respuesta
	- Plazos
- Sistema debe tener pocos componentes
- Operaciones criticas concentradas en uno o dos componentes
- Disminuir la comunicación entre componentes
- Bajo uso de la red y operaciones de entrada/salida

### Escalabilidad
Aceptar mayor carga sin degradación - Subir
- Carga (tps)
- Conexiones simultaneas
- Volumen de datos
- Despliegue
-> Componentes auto-contenidos
-> Componentes con vajo acoplamiento
-> Crecimiento horizontal

### Mantenibilidad
Nuevos requerimientos funcionales requieren ser:
- Modificables
- Nuevos requerimientos fáciles de implementar
- Componentes auto-contenidos
- Especificación detallada
- Componentes reemplazables
- Evitar datos compartidos

### Seguridad

**A nivel usuario**
- Autenticació
- Autorización
- Perfilamiento

**Datos**
- Encriptación
- Integridad
- No repudio

### Confiabilidad
Siempre activo
- Disponibilidad
- Recuperable
- Regla de los cinco 9 (99,5%)
-> Componentes redundantes
-> Fácil migración de componentes
-> Bajo acoplamiento
-> Control distribuido
-> Operación activo-activo o activo-pasivo

	


# Clase 15
15/05/26

## Patrones

1. Capas
2. Tubos y filtros
3. Pizarron 
4. Repositorio

## Implementación de Patrones

### Capas

1. Aplicaciones de usuario
2. Biblioteca de funciones
3. Funciones del sistema (SCI)
4. Kernel
5. Driver layer
6. Hardware layer

# Clase 19
29/05/26

### Modelo Vista Controlador
El sistema se divide en 3 partes:

1. Modelo: Datos y funcionalidad esencial
2. Vista: Comunicación con el usuario
3. Controlador: Controla cambios al modelo

- Interfaz de usuario = Vista + controlador
- Lógica del negocio = controlador + modelo
- Controlador desacopla la vista del modelo

RNF -> Atributos Flexibilidad, mantenibilidad, adaptabilidad

EJ) Asistencia MVC

- Modelo = model.js
- Vista = view.js (index.html)
- Controlador = controler.js (main.js)

### Implementación

1. Separar la funcionalidad de la interacción del usuario
2. Diseñar e implementar:
	- Modelo
	- VIstas
	- Controladores
	- Relacion entre vistas y controladores

- [p] Modelo soporta multiples vistas
- [p] Flexible,mantenible, adaptable
- [p] Frameworks implementan MVC

- [c] Vistas sin acceso a los datos
- [c] Difícil de modificar


### Ejercicio

1. Vista
	- Recepción de pedidos
	- Muestra estadisticas de venta
	- Selección de medios de pago (visual)
	- Interacción de pedidos online (nivel usuario)
2. Controlador
	- Medios de pago (metodo externo)
	- Gestión de consultas 
	- Gestión de repartidores (conexión entre vista y modelo)
	- 

3. Modelo
	- Procesamiento de pedidos
	- Cálculos de estadísticas de venta
	- Procesamiento de envíos a domicilio
	- Gestión de repartidores (cálculos)

Modelo:
- Catalogo de productos
- Gestión de clientes
- Gestión de pedidos
- Gestión de repartidores
- Gestión de envios
- Estadisticas

Vista:
- Administrador
- Cliente
- Repartidor

Controlador
- Control pedidos
- pagos
- envios


## Patrones de Arquitectura: Sist. Interactivo

