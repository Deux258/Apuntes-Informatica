
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



