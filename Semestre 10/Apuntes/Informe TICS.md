\section{Objetivo del Proyecto}

\subsection{Objetivo General}
Implementar en RESTS el módulo de Automatización de Viajes de la plataforma AutoTravel, que permita cargar planillas Excel o imágenes con múltiples viajes y registrarlos en el sistema GRLOG de forma masiva, reduciendo el tiempo y los errores asociados al ingreso manual uno a uno, manteniendo trazabilidad del proceso y habilitando la corrección de registros fallidos.

\subsection{Objetivos Específicos}
\begin{itemize}
    \item \textbf{Carga masiva de viajes:} permitir la carga de viajes desde archivos Excel (\texttt{.xlsx}, \texttt{.xls}) hacia GRLOG, con selección de cliente y PGR operativo.
    
    \item \textbf{Normalización de datos:} normalizar automáticamente columnas y valores de planillas con formatos heterogéneos, reduciendo la preparación manual del archivo.
    
    \item \textbf{Resolución de entidades GRLOG:} interpretar datos operativos como patentes, nombres, RUT, rutas, productos y ciudades, para resolver las entidades requeridas por GRLOG.
    
    \item \textbf{Gestión de resultados:} informar el estado de procesamiento por fila, indicando éxitos, errores o pendientes, y permitir la corrección y reenvío de viajes fallidos sin reprocesar todo el archivo.
    
    \item \textbf{Trazabilidad del proceso:} registrar en base de datos propia cada intento de carga, incluyendo usuario, datos de entrada, estado de procesamiento y respuesta de GRLOG.
    
    \item \textbf{Control de acceso:} restringir el acceso al módulo según roles y permisos definidos por RESTS, diferenciando administradores, operadores y usuarios autorizados.
\end{itemize}

\section{Alcances del Proyecto}

El alcance de esta etapa comprende el desarrollo del módulo \textbf{Automatización de Viajes} de la plataforma AutoTravel, orientado exclusivamente a resolver la carga masiva de viajes hacia GRLOG. El proyecto no busca reemplazar a GRLOG, sino actuar como una capa intermedia que recibe planillas Excel o imágenes, normaliza la información, resuelve entidades y ejecuta el alta masiva de viajes en el TMS contratado.

\subsection*{Incluido en el alcance}
\begin{itemize}
    \item Desarrollo del módulo de Automatización de Viajes (\texttt{/auto-viagem}).
    
    \item Carga de archivos Excel (\texttt{.xlsx}, \texttt{.xls}) con múltiples viajes.
    
    \item Procesamiento de imágenes de planillas mediante OCR, considerado como extensión prevista.
    
    \item Integración con GRLOG para autenticación, consulta de maestros y alta de viajes.
    
    \item Normalización de columnas y valores provenientes de planillas con formatos heterogéneos.
    
    \item Mapeo de datos operativos hacia entidades GRLOG, tales como cliente, PGR, vehículo, remolque, conductores, ruta, producto y ciudades.
    
    \item Ejecución de carga paralela con límite de concurrencia para no saturar el TMS externo.
    
    \item Pantalla de resultados con resumen de viajes registrados, pendientes y fallidos.
    
    \item Edición y reenvío de registros fallidos sin necesidad de volver a cargar el archivo completo.
    
    \item Persistencia en base de datos propia del historial de cada procesamiento.
    
    \item Control de acceso según perfil de usuario y módulo habilitado.
    
    \item Interfaz web \textit{responsive}, priorizando el uso desde navegador de escritorio.
\end{itemize}

\subsection*{Excluido del alcance}
\begin{itemize}
    \item Desarrollo de otros módulos de AutoTravel, como viajes activos, reportes, incidentes, turnos, BI o alertas.
    
    \item Reemplazo del sistema GRLOG, ya que este continúa siendo el TMS oficial de RESTS.
    
    \item Desarrollo de una aplicación móvil nativa.
    
    \item Integración con ERP o sistemas contables de RESTS.
    
    \item Sincronización bidireccional completa con GRLOG, ya que el alcance contempla principalmente el alta de viajes y la corrección de registros fallidos.
    
    \item Capacitación formal de usuarios en GRLOG, ya que se asume que los operadores cuentan con acceso y conocimientos básicos del sistema.
    
    \item Definición de SLA o soporte 24x7 para producción, debido a que el proyecto se encuentra en etapa académica e inicial de formalización.
    
    \item Arquitectura \textit{multi-tenant} para otras empresas, ya que el enfoque está centrado en RESTS y su instancia contratada de GRLOG.
\end{itemize}

\subsection*{Metas medibles asociadas al alcance}
Para establecer criterios verificables de cumplimiento, se consideran las siguientes metas orientativas de desempeño:

\begin{itemize}
    \item \textbf{Tiempo de carga de $N$ viajes:} se espera lograr una reducción mayor o igual al \textbf{70\%} en el tiempo total de carga respecto del ingreso manual uno a uno, considerando una misma cantidad de viajes.
    
    \item \textbf{Tasa de éxito en primer intento:} se estima que al menos el \textbf{85\%} de las filas válidas del archivo deben ser registradas correctamente en GRLOG sin necesidad de corrección posterior.
    
    \item \textbf{Corrección de registros fallidos:} el \textbf{100\%} de las filas con error deben poder visualizarse, editarse y reenviarse desde la plataforma sin necesidad de volver a cargar el archivo completo.
    
    \item \textbf{Adopción operativa:} el módulo debe posicionarse como el método principal para cargas superiores a 5 viajes, dejando el registro manual de GRLOG para casos puntuales o excepcionales.
\end{itemize}

Estas metas son de carácter orientativo y podrán ser ajustadas durante la fase de validación de requerimientos con RESTS, considerando el volumen real de viajes, la calidad de las planillas recibidas y la disponibilidad de los servicios externos de integración.