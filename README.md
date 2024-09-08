# Simulación del Proceso de Producción de Cerveza

## Objetivo

Optimizar el proceso de fabricación de cerveza desde la llegada de materias primas hasta el envasado final, considerando las restricciones actuales de la planta y su capacidad de producción. La simulación busca identificar cuellos de botella, mejorar el uso de recursos, y maximizar la eficiencia operativa, reduciendo tiempos y costos.

## Descripción del Proceso

El modelo debe representar el proceso completo de producción de cerveza en la planta, incluyendo las siguientes etapas:

1. **Recepción de Materias Primas**: Ingreso de malta, lúpulo, levadura y agua.
2. **Producción en Diferentes Etapas**:
   - Molienda de malta.
   - Maceración del grano en tanques.
   - Hervido y adición de lúpulo.
   - Fermentación del mosto.
   - Maduración de la cerveza.
   - Filtrado
3. **Envasado, Etiquetado, Encajonado y Paletizado**: Llenado de botellas, etiquetado, empaquetado en cajas de 3, 6, o 12 botellas, y finalmente paletizado para su almacenamiento o distribución.

## Restricciones y Condiciones Especiales

- **Turnos de Empleados**: La planta opera en tres turnos de trabajo para asegurar el funcionamiento continuo durante las 24 horas del día. Los recursos humanos en cada turno incluyen operadores, técnicos y supervisores.

- **Tanques de Maduración**: La planta cuenta con **6 tanques de maduración**, cada uno con una capacidad de **2,500 litros**. Estos tanques representan una limitación importante, ya que **no se pueden agregar más tanques** sin realizar una **remodelación significativa del edificio**. Los tiempos de maduración de la cerveza son críticos para el flujo de producción y deben gestionarse cuidadosamente para evitar retrasos o excedentes.

- **Capacidad de Envasado y Almacenamiento**: La simulación debe incluir la capacidad del sistema de envasado para operar de forma sincronizada con el proceso de maduración y fermentación. Los productos envasados se almacenan en palets de forma ordenada para maximizar el uso del espacio.

## Controles de calidad

En la simulación los controles de calidad son esenciales para asegurar que cada etapa del proceso cumple con los estándares necesarios antes de avanzar al siguiente. Estos son los puntos clave donde deberían implementarse procesos de control de calidad:

1. **Recepción de Materias Primas**
    - **Control de calidad**: Verificación de la calidad de las materias primas (malta, lúpulo, levadura, agua). Esto incluye análisis de humedad de la malta, frescura del lúpulo y calidad del agua.
    - **Objetivo**: Garantizar que los ingredientes base cumplan con los requisitos establecidos para evitar problemas en el proceso posterior.
2. Molienda de la Malta
    - **Control de calidad**: Control del tamaño de las partículas de malta molida. Si las partículas son demasiado gruesas o finas, puede afectar la eficiencia de la maceración.
    - **Objetivo**: Asegurar que el tamaño de las partículas es el adecuado para una extracción eficiente de los azúcares durante la maceración.
3. Maceración
    - **Control de calidad**: Control de la temperatura y el pH durante la maceración. Estas variables son cruciales para garantizar la conversión adecuada de los almidones en azúcares fermentables.
    - **Objetivo**: Asegurar que el mosto resultante tiene la concentración de azúcares adecuada para la fermentación.
4. Fermentación
    - **Control de calidad**: Monitoreo de la actividad de la levadura, la temperatura y el desarrollo de CO2. Es importante asegurarse de que la levadura está trabajando correctamente y que no hay contaminación.
    - **Objetivo**: Verificar que el proceso de fermentación se está realizando en condiciones óptimas para obtener la concentración de alcohol deseada.
5. Maduración (Tanques de Maduración)
    - **Control de calidad**: Análisis del perfil de sabor, carbonatación y claridad de la cerveza antes de envasarla. Se deben realizar pruebas sensoriales y físico-químicas para garantizar que la cerveza está lista.
    - **Objetivo**: Asegurar que la cerveza ha alcanzado las características deseadas (sabor, aroma, color y carbonatación) antes de pasar al envasado.
6. Envasado
    - **Control de calidad**: Verificación de que las botellas están correctamente selladas y sin contaminantes. Además, control de la cantidad exacta de cerveza en cada botella.
    - **Objetivo**: Garantizar que las botellas cumplen con los estándares de llenado, sellado y etiquetado para evitar devoluciones o problemas en el mercado.
7. Etiquetado
    - **Control de calidad**: Verificación de que las etiquetas están correctamente etiquetadas.
    - **Objetivo**: Garantizar que las botellas cumplen con los estándares etiquetado para evitar devoluciones o problemas en el mercado.
8. Encajonado y Paletizado
    - **Control de calidad**: Verificación de la estabilidad de los paquetes y palets, asegurando que las cajas están correctamente embaladas y los palets están bien estructurados para el transporte.
    - **Objetivo**: Asegurar que el producto final se empaqueta de manera segura y sin defectos que puedan comprometer el transporte o almacenamiento.

> En cualquier etapa del proceso donde se detecten productos que no cumplen con los estándares de calidad, deben existir mecanismos para reprocesar o desechar los productos defectuosos. Esto podría incluir reprocesar el líquido en la fermentación, el envasado o el etiquetado.

## Lógicas principales

En la simulación del proceso de producción de cerveza, estas son las lógicas clave que deben modelarse para representar fielmente el proceso:

1. **Lógica de Recepción de Materias Primas**
   - **Objetivo**: Controlar la llegada de materias primas (malta, lúpulo, levadura, agua) y validar su calidad antes de que ingresen al proceso de producción.
   - **Lógica**:
     - Si el lote de materia prima pasa el control de calidad, se envía a almacenamiento.
     - Si no pasa el control de calidad, se rechaza o se solicita reproceso (si es aplicable).
     - Se actualiza el inventario de materias primas según la recepción aprobada.
2. **Lógica de Molienda de la Malta**
   - **Objetivo**: Procesar la malta para obtener el tamaño adecuado de las partículas.
   - **Lógica**:
     - Se inicia el proceso de molienda al recibir la malta.
     - Si el tamaño de las partículas está dentro del rango óptimo, se envía a maceración.
     - Si el tamaño es incorrecto, se ajusta el molino o se realiza un reproceso.
     - Se registra el tiempo de molienda y la cantidad procesada.
3. **Lógica de Maceración**
   - **Objetivo**: Extraer los azúcares fermentables de la malta.
   - **Lógica**:
     - Se introduce la malta molida en el tanque de maceración junto con agua a la temperatura controlada.
     - Se monitoriza el tiempo de maceración, el pH y la temperatura.
     - Si los valores son correctos, se envía el mosto a la etapa de hervido.
     - Si no se alcanzan los valores deseados, se ajustan los parámetros o se reprograma la maceración.
4. **Lógica de Hervido y Adición de Lúpulo**
   - **Objetivo**: Esterilizar el mosto y añadir los lúpulos necesarios.
   - **Lógica**:
     - El mosto se calienta hasta el punto de ebullición.
     - Se añaden los lúpulos en diferentes momentos para controlar el amargor y los aromas.
     - Si el hervido es correcto, el mosto se enfría para su fermentación.
     - Se registra el tiempo y la cantidad de lúpulo añadida en cada fase.
5. **Lógica de Fermentación**
   - **Objetivo**: Convertir los azúcares del mosto en alcohol mediante la acción de la levadura.
   - **Lógica**:
     - Se transfiere el mosto a los tanques de fermentación y se añade la levadura.
     - Se monitoriza la temperatura y la actividad de la levadura.
     - Si los parámetros son correctos, el proceso avanza hacia la maduración.
     - Si hay anomalías (como bajo rendimiento de la levadura), se ajustan las condiciones o se decide reprocesar el lote.
6. **Lógica de Maduración**
   - **Objetivo**: Envejecer la cerveza en los tanques de maduración para que alcance el perfil de sabor y carbonatación deseado.
   - **Lógica**:
     - La cerveza fermentada se transfiere a uno de los seis tanques de maduración de 2500 litros.
     - Se controla el tiempo, temperatura y presión en los tanques.
     - Si los parámetros son correctos, la cerveza avanza al envasado.
     - Si no se logran los valores esperados (por ejemplo, carbonatación o sabor insuficiente), se extiende el tiempo de maduración o se ajustan las condiciones.
7. **Lógica de Envasado**
   - **Objetivo**: Llenar las botellas con la cerveza ya madura y lista para su comercialización.
   - **Lógica**:
     - Las botellas pasan por el proceso de llenado automático.
     - Se verifica el nivel de llenado y se ajusta si es necesario.
     - Si las botellas están correctamente llenadas, pasan al sellado.
     - Si alguna botella no cumple con los estándares de llenado o sellado, se envía a reprocesar o desechar.
8. **Lógica de Etiquetado**
   - **Objetivo**: Colocar etiquetas correctamente en cada botella después del proceso de llenado y sellado.
   - **Lógica**:
     - Recepción de Botellas Llenas y Selladas.
     - Verificación de Botellas Antes de Etiquetar.
     - Aplicación de la Etiqueta.
     - Si alguna botella no cumple con los estándares de etiquetado, se envía a reprocesar o desechar.
     - Registro de Botellas Etiquetadas
9. **Lógica de Encajonado**
   - **Objetivo**: Agrupar botellas en cajas de 3, 6 o 12 unidades para facilitar su almacenamiento y distribución.
   - **Lógica**:
     - Se agrupan las botellas llenas y etiquetadas en cajas según el tamaño requerido.
     - Si las cajas están correctamente llenas y no presentan defectos, se pasan al paletizado.
     - Si una caja presenta problemas (botellas defectuosas o mal agrupadas), se envía a reprocesar.
10. **Lógica de Paletizado**
    - **Objetivo**: Organizar las cajas en palets para su almacenamiento o transporte.
    - **Lógica**:
      - Las cajas se apilan en palets siguiendo un patrón predefinido.
      - Si el palet está correctamente ensamblado, se etiqueta y se almacena.
      - Si hay problemas con la estabilidad del palet o con la disposición de las cajas, se corrige antes del almacenamiento.
11. **Lógica de Control de Calidad**
    - **Objetivo**: Verificar la calidad en cada etapa del proceso.
    - **Lógica**:
      - Se realizan pruebas de calidad en puntos clave: recepción de materias primas, molienda, maceración, fermentación, maduración, envasado y encajonado.
      - Si se detectan defectos o problemas en cualquier etapa, el lote correspondiente se puede reprocesar o desechar.
      - Los resultados de las pruebas se registran para el seguimiento y la trazabilidad del producto.
12. **Lógica de Reproceso**
    - **Objetivo**: Manejar botellas o lotes que no cumplen con los estándares de calidad y que deben ser ajustados o desechados.
    - **Lógica**:
      - Si alguna botella, caja o palet no pasa las pruebas de calidad, se decide si puede reprocesarse o debe desecharse.
      - El reproceso puede implicar volver a llenar botellas, ajustar el etiquetado o reorganizar cajas en palets.

## Eventos especiales

## Lógica detallada

## Variables de decision

Variables de decisión usadas para optimizar el proceso, mejorar la eficiencia y cumplir con los objetivos de producción:

1. **Tiempos de Molienda y Maceración**
   - **Descripción**: Ajustar la duración de los procesos de molienda y maceración para optimizar el rendimiento y la calidad del mosto.
   - **Impacto**: Afecta la eficiencia del proceso y la calidad del producto final.

2. **Control de Temperatura en la Fermentación**
   - **Descripción**: Definir los parámetros de temperatura en los tanques de fermentación para maximizar la conversión de azúcares en alcohol.
   - **Impacto**: Afecta la calidad del producto final y el tiempo de fermentación.

3. **Cantidad de Lotes Producidos Simultáneamente**
   - **Descripción**: Decidir cuántos lotes de cerveza se procesan al mismo tiempo, en función de la capacidad de los tanques de maduración (6 tanques de 2500 litros).
   - **Impacto**: Afecta la capacidad de producción y el tiempo de espera para el inicio de nuevos lotes.

4. **Planificación de Uso de Tanques de Maduración**
   - **Descripción**: Definir el orden y el tiempo de uso de los tanques de maduración para optimizar la utilización de la capacidad disponible.
   - **Impacto**: Afecta la producción continua y los tiempos de espera entre lotes.

5. **Turnos de Trabajo**
   - **Descripción**: Decidir la cantidad de empleados por turno y cómo distribuir los recursos humanos entre las tres fases del proceso (molienda/maceración, fermentación, envasado).
   - **Impacto**: Afecta la eficiencia de producción y los costos operativos.

6. **Velocidad de Envasado y Sellado**
   - **Descripción**: Ajustar la velocidad de la máquina de llenado y sellado de botellas para balancear la producción y minimizar fallos.
   - **Impacto**: Afecta la tasa de producción y la calidad del sellado.

7. **Frecuencia y Tipo de Control de Calidad**
   - **Descripción**: Definir la frecuencia con que se realizan controles de calidad (etiquetado, sellado, producto final) y qué tipo de pruebas se ejecutan.
   - **Impacto**: Afecta la calidad del producto y la tasa de defectos/reprocesos.

8. **Tamaño del Lote en el Empacado**
    - **Descripción**: Decidir si las botellas se empacan en cajas de 3, 6, o 12 unidades, dependiendo de la demanda y los pedidos.
    - **Impacto**: Afecta la velocidad de empacado y el uso de recursos de almacenamiento.

9. **Reasignación de Botellas Defectuosas**
    - **Descripción**: Decidir qué hacer con las botellas defectuosas (reproceso inmediato, descarte, o almacenado temporal).
    - **Impacto**: Afecta el reproceso, los costos de materiales y la eficiencia.

10. **Capacidad y Frecuencia del Paletizado**
    - **Descripción**: Definir la frecuencia con la que se agrupan cajas en palets y la cantidad de cajas por palet.
    - **Impacto**: Afecta la logística de almacenamiento y la preparación para el transporte.

11. **Mantenimiento Preventivo de Máquinas**
    - **Descripción**: Decidir con qué frecuencia y en qué momentos se deben realizar mantenimientos preventivos de las máquinas (molienda, envasado, paletizado).
    - **Impacto**: Afecta la disponibilidad de máquinas y evita fallas inesperadas.

12. **Gestión de Lotes de Reproceso**
    - **Descripción**: Definir cuántas veces un lote defectuoso puede ser reprocesado antes de ser descartado.
    - **Impacto**: Afecta la eficiencia de la producción y los costos de reprocesado.

13. **Almacenamiento de Producto Final**
    - **Descripción**: Decidir cuántos productos finales (cajas de cerveza) se almacenan antes de ser distribuidos, basado en la capacidad de almacenamiento y la demanda.
    - **Impacto**: Afecta los costos de almacenamiento y la logística de distribución.

## Variables de referencia (KPI)

1. **Tasa de Producción (litros por hora)**
   - **Descripción**: Mide la cantidad de cerveza que la planta produce en un período de tiempo específico.
   - **Relevancia**: Permite evaluar la eficiencia de las modificaciones en las etapas productivas y la capacidad de la planta para responder a la demanda.

2. **Rendimiento de Materia Prima (%)**
   - **Descripción**: La proporción de cerveza producida en relación con la cantidad de materia prima utilizada.
   - **Relevancia**: Ayuda a identificar mejoras en la eficiencia del uso de materias primas como malta, lúpulo, y agua tras los cambios implementados.

3. **Tasa de Defectos en el Producto (%)**
   - **Descripción**: Porcentaje de botellas o lotes de cerveza que no cumplen con los estándares de calidad y requieren reprocesamiento o descarte.
   - **Relevancia**: Mide el impacto de los controles de calidad y la optimización del proceso para reducir productos defectuosos.

4. **Tiempo de Ciclo de Producción (horas o minutos)**
   - **Descripción**: Tiempo total desde la entrada de materias primas hasta que el producto final está envasado y listo para la distribución.
   - **Relevancia**: Permite evaluar la eficiencia del sistema, midiendo la reducción de tiempos tras las modificaciones.

5. **Capacidad de Producción Utilizada (%)**
   - **Descripción**: La proporción de la capacidad de la planta que está en uso en relación con su capacidad máxima.
   - **Relevancia**: Indica qué tan bien está optimizado el uso de recursos (como los tanques de maduración), ayudando a identificar cuellos de botella.

6. **Tasa de OEE (Overall Equipment Effectiveness) (%)**
   - **Descripción**: Eficiencia global del equipo, que mide la disponibilidad, el rendimiento y la calidad en la utilización del equipo.
   - **Relevancia**: Permite analizar el impacto de las modificaciones en la maquinaria y la eficiencia operativa.

7. **Tasa de Reprocesos (%)**
   - **Descripción**: Porcentaje de productos defectuosos que necesitan ser reprocesados antes de ser empaquetados o enviados.
   - **Relevancia**: Mide la calidad del proceso y el impacto de la optimización en las tasas de defectos.

8. **Tasa de Utilización de Tanques de Maduración (%)**
   - **Descripción**: Porcentaje de tiempo que los tanques de maduración están en uso durante el ciclo de producción.
   - **Relevancia**: Ayuda a determinar la eficiencia en el uso de los tanques y a identificar si hay subutilización o cuellos de botella.

9. **Tasa de Disponibilidad de Maquinaria (%)**
    - **Descripción**: Porcentaje de tiempo que las máquinas están operativas en comparación con el tiempo planificado para su uso.
    - **Relevancia**: Permite evaluar el impacto de las modificaciones en la reducción de tiempos de inactividad por fallos o mantenimiento.

10. **Tiempo de Reprocesamiento (minutos)**
    - **Descripción**: El tiempo promedio que se tarda en corregir un lote o botella defectuosa.
    - **Relevancia**: Mide el impacto de las mejoras en el proceso de control de calidad para reducir tiempos de reprocesado.

11. **Tiempo de Espera en los Buffers (minutos o horas)**
    - **Descripción**: Tiempo que los lotes o botellas pasan en los buffers (almacenamientos temporales) antes de continuar al siguiente proceso.
    - **Relevancia**: Ayuda a identificar cuellos de botella y medir la optimización en la gestión del flujo de producción.

12. **Nivel de Inventario de Producto Terminado (litros o unidades)**
    - **Descripción**: La cantidad de producto terminado en almacenamiento antes de su distribución.
    - **Relevancia**: Sirve para medir el impacto de las modificaciones en la cadena de producción en la logística de distribución.

## Variables de estado

## Entidades

1. **Lúpulo**
   - **Descripción**: Los insumos que se utilizan para producir la cerveza, como la malta, el lúpulo, la levadura y el agua.
   - **Atributos**: Tipo de materia prima, cantidad, calidad, fecha de recepción.

2. **Malta**
   - **Descripción**: Específica de la malta, una de las materias primas clave que se somete a procesos de molienda y maceración.
   - **Atributos**: Tipo de malta, grado de molienda, humedad.

3. **Líquido en Proceso**
   - **Descripción**: Representa la mezcla en diferentes etapas de producción, desde la maceración hasta la maduración.
   - **Atributos**: Estado (maceración, fermentación, maduración), volumen, temperatura, grado alcohólico.

4. **Levadura**
   - **Descripción**: Los tanques donde se llevan a cabo diferentes etapas del proceso, como la maceración, fermentación, y maduración.
   - **Atributos**: Capacidad, estado de ocupación, temperatura, presión.

5. **Botellas**
   - **Descripción**: Las botellas en las que se envasará la cerveza.
   - **Atributos**: Capacidad, estado (vacía, llena), integridad (intacta, defectuosa), fecha de llenado.

6. **Cajas**
   - **Descripción**: Contenedores que agrupan las botellas para su almacenamiento y transporte.
   - **Atributos**: Capacidad (3, 6, 12 botellas), estado (llena, vacía), integridad (intacta, defectuosa).

7. **Paletas (Pallets)**
   - **Descripción**: Paletas donde se almacenan las cajas para facilitar su manejo y transporte.
   - **Atributos**: Capacidad (número de cajas), estado (llena, vacía), integridad.

8. **Lotes**
   - **Descripción**: Un conjunto de productos (cerveza) que se procesa en una misma tanda.
   - **Atributos**: Identificador de lote, fecha de producción, cantidad de producto, destino final.

### Recursos

1. **Máquinas**
    - **Descripción**: Equipos utilizados en el proceso de producción, como molinos, tanques de maceración, fermentadores, llenadoras, etiquetadoras.
    - **Atributos**: Tipo de máquina, capacidad, estado (en operación, en mantenimiento), tasa de producción.

2. **Sensores y Medidores**
    - **Descripción**: Dispositivos que monitorean variables como temperatura, presión, niveles de líquido, etc., en los tanques y otros equipos.
    - **Atributos**: Tipo de sensor, rango de medición, ubicación, estado (activo, inactivo).

3. **Tanques de Maceración**
    - **Descripción**: Los tanques donde se lleva a cabo el proceso, como la maceración.
    - **Atributos**: Capacidad, estado de ocupación, temperatura, presión.

4. **Molino de Malta**
    - **Descripción**: Tritura la malta para obtener una textura adecuada para la maceración.
    - **Atributos**: Capacidad, Tipo de molienda, Estado, Tasa de Producción

5. **Hervidor**
    - **Descripción**: Hierve el líquido de la maceración y añade lúpulo para el sabor y aroma.
    - **Atributos**: Capacidad, Temperatura,Tiempo de Proceso, Estado, Consumo Energético

6. **Tanque de Fermentación**
    - **Descripción**: Permite que la levadura fermente los azúcares en alcohol y dióxido de carbono.
    - **Atributos**: Capacidad, Temperatura, Tiempo de Fermentación, Estado, Presión

7. **Tanque de Maduración**
    - **Descripción**: Almacena la cerveza fermentada para desarrollar su sabor y madurar.
    - **Atributos**: Capacidad, Temperatura, Tiempo de Maduración, Estado

8. **Sistema de Filtrado**
    - **Descripción**: Elimina impurezas y sedimentos del líquido antes del envasado.
    - **Atributos**:Capacidad, Tipo de Filtro, Estado, Consumo Energético:

9. **Llenadora de Botellas**
    - **Descripción**: Llena las botellas con la cerveza.
    - **Atributos**: Capacidad, Precisión de Llenado, Estado, Tipo de Tapado

10. **Etiquetadora**
    - **Descripción**: Coloca etiquetas en las botellas.
    - **Atributos**: Capacidad, Precisión de Etiquetado, Estado, Tipo de Etiquetas

11. **Empacadora**
    - **Descripción**: Coloca las botellas en cajas o empaques.
    - **Atributos**: Capacidad, Tipo de Empaque, Estado

12. **Paletizadora**
    - **Descripción**: Organiza las cajas en paletas para el almacenamiento y transporte.
    - **Atributos**: Capacidad, Tipo de Paletización, Estado:

### Recursos Humanos

- **Técnicos de Mantenimiento**: Encargados de la reparación y mantenimiento de la maquinaria.
- **Operadores de Maquinaria**: Manejan las máquinas y equipos durante el proceso de producción.
- **Controladores de Calidad**: Inspeccionan la calidad del producto en diferentes etapas.

### Buffers de Materias Primas

1. **Buffer de Malta**
   - **Descripción**: Almacena malta antes de la molienda.
   - **Capacidad**: Cantidad máxima de malta que puede almacenar.
   - **Ubicación**: Cerca del molino de malta.

2. **Buffer de Lúpulo**
   - **Descripción**: Almacena lúpulo antes de la adición al hervidor.
   - **Capacidad**: Cantidad máxima de lúpulo que puede almacenar.
   - **Ubicación**: Cerca del hervidor.

3. **Buffer de Levadura**
   - **Descripción**: Almacena levadura antes de la fermentación.
   - **Capacidad**: Cantidad máxima de levadura que puede almacenar.
   - **Ubicación**: Cerca del tanque de fermentación.

4. **Buffer de Agua**
   - **Descripción**: Almacena agua utilizada en el proceso de producción.
   - **Capacidad**: Cantidad máxima de agua que puede almacenar.
   - **Ubicación**: Cerca de los tanques de maceración y hervido.

## Buffers o colas

### Buffers de Productos Intermedios

1. **Buffer de Mosto**
   - **Descripción**: Almacena el mosto después de la maceración y antes del hervido.
   - **Capacidad**: Volumen máximo de mosto que puede almacenar.
   - **Ubicación**: Entre el tanque de maceración y el hervidor.

2. **Buffer de Cerveza Fermentada**
   - **Descripción**: Almacena la cerveza después de la fermentación y antes de la maduración.
   - **Capacidad**: Volumen máximo de cerveza fermentada que puede almacenar.
   - **Ubicación**: Entre el tanque de fermentación y el tanque de maduración.

3. **Buffer de Cerveza Madurada**
   - **Descripción**: Almacena la cerveza después de la maduración y antes del filtrado.
   - **Capacidad**: Volumen máximo de cerveza madurada que puede almacenar.
   - **Ubicación**: Entre el tanque de maduración y el sistema de filtrado.

### Buffers de Productos Terminados

1. **Buffer de Botellas Vacías**
   - **Descripción**: Almacena botellas vacías antes de su llenado.
   - **Capacidad**: Cantidad máxima de botellas vacías que puede almacenar.
   - **Ubicación**: Cerca de la llenadora de botellas.

2. **Buffer de Cerveza Llenada**
   - **Descripción**: Almacena botellas llenas de cerveza antes del etiquetado.
   - **Capacidad**: Cantidad máxima de botellas llenas que puede almacenar.
   - **Ubicación**: Después de la llenadora y antes de la etiquetadora.

3. **Buffer de Botellas Etiquetadas**
   - **Descripción**: Almacena botellas etiquetadas antes del empaquetado.
   - **Capacidad**: Cantidad máxima de botellas etiquetadas que puede almacenar.
   - **Ubicación**: Después de la etiquetadora y antes de la empacadora.

4. **Buffer de Cajas Empaquetadas**
   - **Descripción**: Almacena cajas empaquetadas antes del paletizado.
   - **Capacidad**: Cantidad máxima de cajas empaquetadas que puede almacenar.
   - **Ubicación**: Después de la empacadora y antes de la paletizadora.

5. **Buffer de Paletas de Cerveza**
   - **Descripción**: Almacena paletas con cajas antes del almacenamiento o distribución.
   - **Capacidad**: Cantidad máxima de paletas que puede almacenar.
   - **Ubicación**: Después de la paletizadora y antes del área de almacenamiento.

### Buffers de Residuos

1. **Buffer de Residuos de Maltas**
   - **Descripción**: Almacena residuos generados durante la molienda y maceración.
   - **Capacidad**: Cantidad máxima de residuos de maltas que puede almacenar.
   - **Ubicación**: Cerca del molino de malta y el tanque de maceración.

2. **Buffer de Residuos de Filtrado**
   - **Descripción**: Almacena los residuos sólidos eliminados durante el filtrado.
   - **Capacidad**: Cantidad máxima de residuos de filtrado que puede almacenar.
   - **Ubicación**: Cerca del sistema de filtrado.

### Buffers de errores

1. **Buffer de Reprocesado**
   - **Descripción**: Almacena productos defectuosos o no conformes que necesitan ser corregidos o refinados antes de su reincorporación al proceso de producción. Los productos almacenados aquí son aquellos que no cumplen con los estándares de calidad pero pueden ser ajustados o mejorados.
   - **Capacidad**: Cantidad máxima de productos defectuosos que puede almacenar, especificada en litros o unidades.
   - **Ubicación**: Situado cerca del área de inspección de calidad y el proceso de reprocesado. Esto facilita el acceso rápido para realizar las correcciones necesarias.

2. **Buffer de Descarte**
   - **Descripción**: Almacena productos que no cumplen con los estándares de calidad y no pueden ser recuperados. Estos productos están destinados a ser eliminados de manera segura. El buffer asegura que los productos defectuosos no interfieran con el stock de productos de calidad.
   - **Capacidad**: Cantidad máxima de productos que puede almacenar antes de proceder con su eliminación, especificada en litros o unidades.
   - **Ubicación**: Ubicado en una zona designada para la disposición segura, lejos de las áreas de producción activa para evitar la contaminación cruzada con productos en buen estado.
