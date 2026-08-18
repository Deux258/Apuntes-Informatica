
# Abstract

DHTs es capaz de distribuir largas aplicaciones para P2P. Sin embargo su limitante es que busca matches exactas, por lo que para buscar aproximados, se requiere indexar estructuras adicionales.

PHT son interesantes aproximados a conseguir esto en vez de DHT. Sin embargo, generan trafico innecesario que degrada el performance de busqueda

Lo que se propone finalmente es desarrollar cache distribuido llamado *Tabu prefix table Cache* TPT-C, que apunta a mejorar el performance de prefix-trees.
Se logra reducir un 70% de latencia

# Introduccion

Dado que P2P es ampliamente usado para informacion distribuida, DHTs es una solucion muy eficiente para disrtibuciones a larga escala.

DHTs
- Escalable
- Tolera caidas
- Carga de balance
Cada nodo tiene un unico id creado con hash cifrado SHA-1

Se usa una llave con objeto, que se provee al peer correspondiente.

*Ventaja* -> Provee distribucion uniforme independiente del espacio
*Desventaja* -> Destruye data local

### Porqué interesa usar P2P?
Es requerido para aplicaciones como musica, pelicula, data mining y varios tipos de gran escala  con bases de datos distribuidas.

Una solucion que mejora menor menor latencia para busquedas sobre index no es trivial.
las propiedades de DHT debiera ser trade-off entre la mejora y la solucion

---

Se presenta una solucion basada en PHT que es incluir cache basado en las tablas de tabu search. Esto con el fin de reducir el espacio de busqueda, añadiendo nodos internos.

La novedad es que mejora el performance de busqueda sin degradar en escenarios dinamicos, dado que no almacena referencias estaticas hasta en un 70%






