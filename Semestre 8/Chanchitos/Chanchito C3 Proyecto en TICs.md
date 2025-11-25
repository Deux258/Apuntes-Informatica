# 1. Flujo de caja
Es la lista ordenada de todos los ingresos y egresos reales de dinero del proyecto, usados para calcular VAN, TIR, PRI, etc.

Su función es aislar los efectos económicos atribuibles exclusivamente al proyecto, eliminando distorsiones contables, costos hundidos o movimientos internos que no representan salidas reales de efectivo.

# 2. Principios clave del Flujo de Caja

-  **2.1 Flujos Relevantes**
Solo movimientos efectivos de dinero, no aquellas operaciones contables o ajustes internos.

- *Reales*: movimiento efectivo de dinero
- *Incrementales*: Cambios que causa el proyecto
- *Diferenciales*: Cuando comparas alternativas

**NO** incluir
- Costos hundidos
- Depreciación como egreso (solo afecta impuestos)
- Movimientos internos sin pago real
- Gastos que existirían igual sin el proyecto

-  **2.2 Flujos Incrementales**
Importan solo los flujos que cambian por el proyecto.

Si un ingreso o costo existiera igual con o sin el proyecto, no se considera.
EJ) Si una máquina nueva reduce costos en $2M al año - Se incluye el ahorro, NO el costo total

-  **2.3 Flujos Diferenciales**
Cuando se comparan alternativas, el flujo relevante es la diferencia entre opciones, no sus valores absolutos.

- **2.4 Costos de Oportunidad**
Si el proyecto utiliza un recurso que podría generar ingresos alternativos, ese ingreso dejado de percibir se considera un *costo*.

- **2.5 Costos Hundidos**
Son costos incurridos antes de analizar el proyecto

# 3. Componentes del Flujo de Caja

##### 3.1 Inversión Inicial $t=0$
la inversión inicial concentra todos los egresos necesarios para poner en marcha el proyecto.
###### Componentes
- Adquisicion de activos fijos
- Instalacion, transporte, pruebas
- gastos pre-operativos
- capital de trabajo inicial
- costos tributarios iniciales (cuando existen)

Esta inversión ocurre generalmente en $t=0$ y corresponde a un egreso grande y único

##### 3.2 Flujos de Operación
Son los flujos durante la vida útil del proyeto y constituyen su núcleo económico

*Ingresos Operacionales*
- Ventas
- Ahorros
*Egresos Operacionales*
- Mano de obra, insumos, servicios
- Mantencion

**Depreciación**
No es egreso real → No se descuenta como salida
Pero si influye en el calculo de impuestos, porque reduce la base imponible

**Impuestos**
El flujo de caja siempre debe evaluarse después de impuestos, para obtener rentabilidad real del inversionista.

![[Pasted image 20251117224300.png]]
##### 3.3 Flujo terminal
Se considera en el último año
- Valor de rescate del activo
- Recuperación del capital de trabajo
- Venta de equipos

Este flujo suele ser beneficioso, ya que incorpora ingresos por venta o devolución de capital de trabajo.

# 4. Capital de Trabajo (CT)
Es el dinero necesario para que el proyecto pueda operar sin interrupciones/weonaje.

*Incluye:*
- inventarios
- cuentas por cobrar
- caja mínima
- necesidades operativas iniciales
*Dinámica en el flujo de caja*:
- Se descuenta como egreso en t=0
- Se recupera como ingreso en el último período

Muchos alumnos olvidan este componente, lo que **distorsiona el VAN**.

# 5. Caja de descuento y consistencia
Representa el costo de oportunidad del capital, riesgo del proyecto y la política de inversión de la empresa.

> El financiamiento NO debe incorporarse en el flujo de caja del proyecto

Primero se evalua el proyecto como si fuese 100% propio, luego se analiza como financiarlo

# 6. Enfoque de valores constantes/corrientes
El flujo de caja debe mantenerse internamente coherente

Valores constantes
- No incluye inflación
- Se descuenta con tasa real
Valores corrientes
- Incluye inflación
- Se descuenta con tasa nominal

X - Nunca mezclar valores constantes con nominales o tasas diferentes

# 7. Indicadores obtenidos del flujo de Caja
Una vez construido, el flujo permite calcular:

### 7.1 VAN (Valor Actual Neto)
Indica cuánto valor genera el proyecto en términos absolutos

$$VAN = \sum \frac{FC_t}{(1+r)^t} \space - \space Inversion \space Inicial $$
Si VAN > 0 el proyecto crea valor

### 7.2 TIR (Tasa Interna de Retorno)
Es la tasa $r$ que hace VAN = 0
_Interpretación:_ Rentabilidad porcentual del proyecto

### 7.3 PRI (Periodo de Recuperación)
Tiempo que tarda en recuperarse la inversión inicial con los flujos netos

### 7.4 IR (Índice de Rentabilidad)

$$ IR = \frac{VAN + Inversion} {Inversion} $$
Mide cuánto valor genera cada peso invertido

# 8. Errores típicos al construir flujos de caja

- Incluir costos hundidos
- Omitir la recuperación del capital de trabajo
- Tratar la depreciación como egreso real
- No considerar impuestos correctamente
- Duplicar beneficios
- Incluir ingresos o costos no incrementales
- Mezclar tasas reales con valores nominales
- Confundir impacto del financiamiento con impacto del proyecto

# 9. Resumen

El flujo de caja es el instrumento más importante en evaluación de proyectos, ya que resume el impacto económico real del proyecto y es la base para los indicadores financieros.  
Su correcta elaboración depende de:

- identificar flujos relevantes e incrementales
- excluir elementos contables no reales
- aplicar consistencia técnica (impuestos, inflación, tasa de descuento)
- considerar capital de trabajo y flujos terminales

Un flujo de caja bien construido permite tomar decisiones racionales y cuantitativas sobre si un proyecto *crea o destruye valor*.