Solo fichas -> 1 hoja y la otra podria tener el registro en 2 hojas, pero nada mas que eso

# Serpat

Parte operativa 

---
# Yalitech

Imitación de Zoho

Zoho tiene una swet
- Analitics -> Prepararlo en este mismo

Usuario: yalitech@kubobi.cl
Pass: Kubito2026++*+
https://one.zoho.com/zohoone/yalitech/home

Cuenta para probar cositas

## A realizar

1. Normalizacion de base de datos
	1. Carga historica (Junio-mayo se usaba CMR)
	2. Mucho dato pero hay info historica no completa -> LLENAR (dependiendo de la fecha)
	3. No debiera ser tan dificil (exportar y cargas en la misma planilla maestra)
	4. Algunos datos no aparece el nombre si no **ID**
	5. Facilitar visualizacion de los datos
2. Paneles
	1. Que datos necesitan para cada panel
	2. Agentes que diseñen paneles
	3. Pero antes normalizar!

- Planificado para aprox 2 meses 

- Cuidado con mostrar tanta info!
- No mostrar inseguridad

Como cliente -> Planificación con sprints (usuarios) - Gantt
Armar esta semana 

**OJO** -> Yalitech en producción

- Hay harta documentacion de zoho para usar

Ideal especializar en zoho y vender servicio 
Calidad de app es buena y no es tan caro como otras sweets

Primeras 2 semanas -> Propuesta interna
Documentar datos 
Armar carta gantt
Detalle de paneles ir levantando con usuarios

Aplicaciones -> Para obtener datos

- Vistas que puedes cruzar datos 

---
# Reunion 25/09


1. Oportunidad
2. Cotización
Creadas por el vendedor (mayoria)


Reactivacion -> Cliente no hizo compra más de 12 meses

Recurrente -> Ha comprado en menos de 1 año (mas de 3 veces)
Nuevo logo -> Compra por 1ra vez
Desarrollo -> Compro de 1 a 3 veces


Familia -> Quizas no es necesario marcarlo

Si tenemos claro las condiciones -> Podriamos crear regla de necogio dentro del panel y automatizado

- Quizás para cotización -> Tiene el SKU

Esperado en la salida:
- Por ahora sirve para pagar remuneraciones
- Requerido para análisis de compradores

Tabla dinamica resumen de las comisiones
- Detalles
- Descargar detalles con todas las comisiones para validar
- Pasa a remuneración

Reglas y condiciones 
- A definir ajustado a necesidades

## 2da etapa

- Despachos
- Algunos productos que no comisionan (a excluir) 20 por ejemplo - Asociado a una familia 
- 

![[Pasted image 20260929003626.png]]


SELECT DISTINCT
		 /*F."ID de la factura"        AS "ID factura Books",*/ F."Número de factura" AS "Número de factura",
		 F."Fecha de la factura" AS "Fecha factura",
		 F."Estado de la factura" AS "Estado factura",
		 /*F."ID de cliente"           AS "ID cliente Books",*/ C."Nombre del cliente" AS "Nombre Cliente Books",
		 AF."Nombre del artículo" AS "Nombre del artículo",
		 /*IFNULL(c."RUT", CONCAT('SIN RUT ', f."ID de cliente")) AS "RUT del Cliente",*/ F."Subtotal (BCY)" AS "Subtotal factura (BCY)",
		 F."Total (BCY)" AS "Total factura (BCY)",
		 F."Saldo (BCY)" /*AF."ID de artículo"			AS "ID Del articulo",*/
/*AF."Cantidad" 				AS "Cantidad articulo",*/
/*V."ID de vendedor:",*/
/*V."Nombre"					AS "Nombre vendedor"*/
/*A."Subtotal (BCY)"          AS "Base línea (BCY)",*/
/*A."Total (BCY)"             AS "Total línea (BCY)"*/
/*bc."ID de referencia de CRM" AS "ID cuenta CRM referenciada",*/ AS "Saldo factura (BCY)"
FROM  "Facturas" F
LEFT JOIN "Clientes" C ON F."ID de cliente"  = C."ID de cliente" 
LEFT JOIN "Artículos en factura" AF ON F."ID de la factura"  = AF."ID de la factura" 
LEFT JOIN "Vendedores" V ON F."ID de vendedor:"  = V."ID de vendedor:" /*LEFT JOIN "Artículos" A ON AF."ID de la factura" = A."ID de artículo"*/
