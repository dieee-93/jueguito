# ETAPA 01-C — CASOS DE ESTUDIO PROFUNDOS DE VIDEOJUEGOS Y SISTEMAS INTERACTIVOS

**Proyecto:** Investigación y diseño de un videojuego experimental  
**Etapa:** 01-C — Casos de estudio profundos  
**Versión:** 1.0  
**Fecha:** Octubre de 2026  
**Estado:** Investigación documental inicial con fuentes primarias, documentación técnica y referencias académicas

---

# 1. OBJETIVO DE LA INVESTIGACIÓN

El propósito de esta etapa es examinar videojuegos concretos para comprender cómo funcionan determinadas mecánicas, cómo se relacionan entre sí y qué puede aprenderse de sus sistemas de diseño y de sus implementaciones.

El catálogo 01-A proporciona las familias de experiencias jugables. La biblioteca 01-B identifica acciones, reglas, interacciones, estados y transformaciones que pueden formar parte de ellas.

La presente etapa conecta ambos documentos con ejemplos reales.

La investigación se concentra en cinco preguntas:

1. ¿Qué hace particular a cada sistema jugable?
2. ¿Qué mecánicas deben colaborar para producir esa experiencia?
3. ¿Qué precedentes permiten comprobar cómo funciona?
4. ¿Qué detalles técnicos, herramientas o estructuras pueden estudiarse directamente?
5. ¿Qué principios podemos reutilizar como conocimiento de diseño, sin asumir que debemos copiar la implementación original?

## 1.1. Criterios de selección

Se priorizaron casos que permiten estudiar al menos una de estas cuestiones:

- Integración entre géneros.
- Cambio de escala de control.
- Reglas manipulables por el jugador.
- Simulación de sistemas complejos.
- Comportamientos emergentes.
- Automatización y economía.
- Progresión basada en conocimiento.
- Cooperación asimétrica.
- Creación de contenido por los usuarios.
- Arquitecturas abiertas o herramientas modificables.

El catálogo incluye tanto juegos comerciales como proyectos de código abierto. Esta distinción es esencial: un videojuego comercial puede demostrar la validez de una idea jugable sin permitirnos inspeccionar sus fuentes, mientras que un repositorio abierto puede facilitar el estudio de implementaciones concretas.

## 1.2. Niveles de evidencia

Cada estudio diferencia entre:

**Hechos documentados:** características descritas por los desarrolladores, las fuentes oficiales, la documentación o las publicaciones académicas.

**Interpretación de diseño:** explicación de por qué esas características pueden ser interesantes para nuestro proyecto.

**Hipótesis experimental:** aplicación nueva que deberíamos validar mediante prototipos.

No se afirmará que una combinación sea inédita sin una investigación específica de antecedentes.

---

# 2. CASO DE ESTUDIO 01 — EXIMIUS: SEIZE THE FRONTLINE

## 2.1. Identificación

**Géneros:** shooter táctico en primera persona y estrategia en tiempo real.

**Desarrollador:** Ammobox Studios.

**Lanzamiento comercial:** 2021.

**Fuente principal:** https://store.steampowered.com/app/505740/

**Sitio oficial:** https://www.seizethefrontline.com/

**Acceso al código fuente:** no se ha localizado un repositorio oficial abierto del juego en las fuentes consultadas.

## 2.2. Problema de diseño que resuelve

El juego combina dos escalas de intervención que normalmente se distribuyen entre productos diferentes.

En la escala individual, el jugador participa en el combate, utiliza armas, se desplaza y coopera con una escuadra.

En la escala estratégica, el comandante administra recursos, construye bases, desarrolla tecnologías, produce unidades y emite órdenes que influyen en el enfrentamiento.

La descripción oficial identifica expresamente el producto como un híbrido FPS/RTS. También describe equipos multijugador con oficiales de escuadra y un comandante, así como la capacidad del comandante de cambiar a una interfaz estratégica desde la que construye instalaciones y dirige unidades.

Fuente: https://store.steampowered.com/app/505740/

## 2.3. Mecánicas que deben colaborar

El híbrido no consiste simplemente en mostrar dos cámaras.

Requiere, como mínimo, sistemas capaces de relacionar:

- Control directo del personaje.
- Selección y mando de unidades.
- Economía compartida.
- Construcción.
- Producción de unidades.
- Investigación tecnológica.
- Combate individual y colectivo.
- Comportamiento de unidades controladas por IA.
- Objetivos territoriales.
- Estados persistentes entre la vista táctica y la estratégica.

Una unidad producida mediante la economía estratégica tiene que existir después como una entidad que participa en los acontecimientos del campo de batalla.

Del mismo modo, las consecuencias del combate pueden repercutir en la situación estratégica.

## 2.4. Integración entre paradigmas

La característica importante es la continuidad entre las distintas escalas.

El jugador no entra simplemente en un minijuego independiente de estrategia. Las decisiones estratégicas modifican las capacidades disponibles para el combate, mientras que la participación individual puede afectar al resultado colectivo.

Esta integración introduce un problema importante de diseño: cada escala requiere una interfaz distinta, pero ambas deben comunicar estados relacionados.

La vista estratégica prioriza información territorial, unidades, recursos y producción.

La primera persona prioriza orientación, movimiento, amenazas inmediatas y ejecución precisa.

Por tanto, el sistema necesita cambiar la presentación y el modelo de control sin perder la coherencia del estado compartido.

## 2.5. Qué podemos aprender

**Primera conclusión:** dos géneros pueden compartir un mundo cuando existe un conjunto de variables comunes entre ellos.

No es necesario que cada sistema comparta todos sus componentes. Lo importante es definir qué información pasa de un modo al otro y qué consecuencias conserva.

**Segunda conclusión:** las transiciones necesitan un motivo jugable.

Construir unidades para después controlarlas o utilizarlas en una batalla establece una relación causal comprensible entre estrategia y acción.

**Tercera conclusión:** la asimetría de roles puede ser más interesante que hacer que todos los jugadores tengan exactamente las mismas capacidades.

Un comandante y un oficial no tienen por qué experimentar el mismo juego para colaborar en una misma partida.

## 2.6. Limitaciones que debemos investigar

El producto no demuestra por sí solo que toda combinación FPS/RTS sea viable o divertida.

En particular, habría que estudiar:

- El coste cognitivo del cambio de interfaz.
- La frecuencia adecuada de transición.
- La coordinación entre decisiones locales y globales.
- El equilibrio entre el comandante y los demás participantes.
- La coherencia de los estados compartidos.
- Las dificultades de sincronización multijugador.

Al no disponer de fuentes abiertas del código original en esta investigación, no debemos atribuirle una arquitectura interna específica.

## 2.7. Experimento derivado

Construir un prototipo con dos modos:

1. Vista estratégica para colocar unidades y emitir órdenes.
2. Vista individual para controlar una unidad seleccionada.

Ambos modos compartirán un pequeño conjunto de variables: posición, salud, objetivos y recursos.

La prueba deberá comprobar si las decisiones en la vista estratégica producen consecuencias legibles cuando se pasa al control directo.

**Utilidad para el proyecto:** alta para investigar transiciones de escala, interfaces diferenciadas y sistemas compartidos.

---

# 3. CASO DE ESTUDIO 02 — MINDUSTRY

## 3.1. Identificación

**Familias:** automatización industrial, estrategia en tiempo real, defensa por oleadas y construcción.

**Desarrollador:** Anuken y colaboradores.

**Tecnología declarada en el repositorio:** Java.

**Repositorio oficial:** https://github.com/Anuken/Mindustry

**Licencia del repositorio:** GPL-3.0, según la información publicada en GitHub.

## 3.2. Por qué es relevante

Mindustry combina construcción industrial y defensa.

El jugador organiza la producción y el transporte de materiales, establece instalaciones y redes, y utiliza los sistemas construidos para sostener actividades defensivas y ofensivas.

La producción no es un subsistema completamente separado del peligro. Las instalaciones y los flujos de recursos son parte de las condiciones que permiten mantener la partida.

El repositorio oficial describe el proyecto como un juego de automatización, defensa por torres y estrategia en tiempo real.

Fuente: https://github.com/Anuken/Mindustry

## 3.3. Mecánicas principales

- Recolección y transporte de materiales.
- Construcción de instalaciones.
- Conexiones entre edificios.
- Producción automatizada.
- Gestión energética.
- Desarrollo de tecnologías.
- Defensa de posiciones.
- Ataque y desplazamiento de unidades.
- Distribución de recursos.
- Construcción bajo presión.
- Cooperación y juego multijugador.

## 3.4. La relación entre producción y combate

Una observación importante es que la infraestructura tiene un propósito dual.

Por un lado, permite fabricar, transportar y procesar recursos.

Por otro, determina qué capacidades defensivas u ofensivas pueden sostenerse.

Esto evita que la construcción se reduzca a un editor separado del resto del juego: las decisiones de organización industrial afectan a la supervivencia.

También permite crear situaciones donde una solución económica aparentemente eficiente genera vulnerabilidades espaciales o defensivas.

## 3.5. Qué aporta el repositorio

El proyecto distribuye código fuente y separa, entre otros componentes visibles del repositorio, directorios de núcleo, escritorio, servidor, herramientas y pruebas.

El README incluye instrucciones de compilación y explica que ciertas clases y entidades se generan durante el proceso de construcción.

Fuente: https://github.com/Anuken/Mindustry

Esto permite investigar no solo las mecánicas, sino también cómo se estructura un producto que necesita soportar varios entornos y modos de ejecución.

No obstante, la organización de directorios por sí sola no demuestra que todos los sistemas estén desacoplados ni que la arquitectura sea apropiada para nuestro proyecto. Para determinarlo será necesario seguir las dependencias del código.

## 3.6. Lecciones de diseño

- La automatización puede convertirse en una forma de defensa.
- La geometría de las instalaciones puede afectar tanto a la economía como al combate.
- Las restricciones espaciales hacen que la optimización tenga consecuencias visibles.
- Las decisiones sobre producción pueden crear riesgos futuros.
- El estado de la infraestructura es información compartida por varios sistemas.

## 3.7. Experimento derivado

Construir un escenario en el que las mismas instalaciones cumplan tres funciones:

1. Producir recursos.
2. Proporcionar capacidades defensivas.
3. Alterar las rutas y posibilidades de movimiento.

La prueba evaluará si el jugador percibe la relación entre construcción, logística y defensa sin necesidad de separar estas actividades en modos independientes.

## 3.8. Precaución de reutilización

La licencia GPL-3.0 tiene obligaciones de distribución y modificación específicas. No debe confundirse un repositorio disponible públicamente con software que puede incorporarse sin condiciones a cualquier producto comercial.

Mindustry es una referencia de estudio. Su posible reutilización requeriría una revisión de las licencias de código, recursos y dependencias.

**Utilidad para el proyecto:** alta para investigar sistemas interdependientes y para estudiar código abierto de un juego que combina varias actividades.

---

# 4. CASO DE ESTUDIO 03 — CATACLYSM: DARK DAYS AHEAD

## 4.1. Identificación

**Familias:** supervivencia, RPG, exploración, simulación sistémica y sandbox.

**Repositorio:** https://github.com/CleverRaven/Cataclysm-DDA

**Documentación oficial del proyecto:** https://docs.cataclysmdda.org/

**Documento de diseño general:** https://docs.cataclysmdda.org/design-balance-lore/design-doc.html

**Experiencia de usuario y características:** https://docs.cataclysmdda.org/design-balance-lore/design-user-experience.html

## 4.2. Principio de diseño

La documentación describe un mundo de supervivencia persistente y procedural en el que el jugador debe gestionar las consecuencias de sus decisiones en un entorno que continúa existiendo sin depender exclusivamente de sus objetivos.

El documento de diseño expresa una intención clara: presentar al jugador como observador e influenciador de un mundo que puede continuar desarrollándose independientemente de él.

También destaca la combinación de exploración, supervivencia, combate, construcción, vehículos y gestión de grupos de supervivientes.

Fuente: https://docs.cataclysmdda.org/design-balance-lore/design-doc.html

## 4.3. Mecánicas interdependientes

La experiencia combina:

- Exploración.
- Percepción visual y auditiva.
- Desplazamiento espacial.
- Combate cuerpo a cuerpo y a distancia.
- Fabricación.
- Gestión de inventarios.
- Reparación.
- Construcción de estructuras.
- Modificación y conducción de vehículos.
- Gestión de necesidades.
- Relación con facciones y NPC.
- Evolución del mundo.
- Gestión de tiempo y recursos.

La documentación señala que el juego utiliza un sistema de turnos híbrido donde las acciones tienen costes de movimiento. Los actores, incluidos jugadores y criaturas, actúan de acuerdo con sus propios puntos de movimiento y condiciones.

Fuente: https://docs.cataclysmdda.org/design-balance-lore/design-user-experience.html

## 4.4. La importancia de los sistemas compartidos

Cataclysm DDA es un caso interesante porque muchas de sus actividades no requieren una simulación independiente.

Moverse, combatir, desplazarse en vehículos, explorar y manipular objetos pueden operar sobre estados comunes: posiciones, entidades, materiales, tiempo, recursos y condiciones del mundo.

Esto permite que las acciones tengan consecuencias entre sistemas.

Por ejemplo, una decisión de transporte puede afectar la disponibilidad de combustible; esa disponibilidad condiciona futuras expediciones; y las expediciones determinan qué materiales pueden recuperarse.

La cadena de consecuencias es más importante que cada acción individual.

## 4.5. Un modelo de tiempo distinto al tiempo real convencional

En el sistema descrito por la documentación, las acciones consumen puntos de movimiento y los demás actores reciben oportunidades de actuar cuando corresponde.

Este enfoque permite un mundo con numerosos estados, condiciones y acciones detalladas sin exigir que todas las decisiones dependan de reflejos en tiempo real.

Para nuestro proyecto, resulta relevante la idea de separar la complejidad de la simulación de la velocidad a la que el jugador tiene que actuar.

Una simulación rica no necesita adoptar automáticamente una estructura de tiempo real.

## 4.6. Un entorno que no existe solo para presentar desafíos al jugador

La filosofía de diseño documentada es importante: el mundo no debe reaccionar exclusivamente como una secuencia de pruebas diseñadas para el protagonista.

El entorno, los recursos, las amenazas y los procesos deben conservar una lógica relativamente coherente.

Esto puede producir problemas emergentes. Una amenaza no tiene por qué aparecer para generar una misión; puede ser una consecuencia de la simulación y de la interacción entre entidades.

## 4.7. Qué investigar en el código

El repositorio debería estudiarse progresivamente para entender:

- Cómo se representan entidades y objetos.
- Cómo se definen materiales y propiedades.
- Qué datos se pueden modificar externamente.
- Cómo se ejecutan las acciones.
- Cómo se representa el estado del mundo.
- Cómo se guardan y recuperan las partidas.
- Qué sistemas utilizan archivos de datos.
- Qué mecanismos permiten añadir contenido.
- Cómo se organizan las contribuciones de la comunidad.

En esta etapa hemos contrastado documentación oficial del diseño y del funcionamiento. La arquitectura interna todavía requiere una inspección específica de módulos y dependencias.

## 4.8. Experimento derivado

Crear una simulación pequeña con:

- Un personaje.
- Un vehículo.
- Un inventario.
- Un recurso consumible.
- Un mundo persistente.
- Un ciclo de tiempo.

El objetivo es comprobar cómo una acción local —por ejemplo, utilizar el vehículo para transportar recursos— altera otras posibilidades de la simulación.

**Utilidad para el proyecto:** muy alta como referencia de interdependencia sistémica, mundo persistente y simulación de actividades diferentes bajo un estado común.

---

# 5. CASO DE ESTUDIO 04 — OPENTTD

## 5.1. Identificación

**Familias:** estrategia económica, logística, construcción y simulación de transporte.

**Repositorio oficial:** https://github.com/OpenTTD/OpenTTD

**Documentación de desarrollo:** https://www.openttd.org/development

**Documentación del código:** https://docs.openttd.org/source/

**Licencia indicada por el proyecto:** GNU GPL versión 2.

## 5.2. Qué representa

OpenTTD permite construir y gestionar redes de transporte en un mundo simulado.

La experiencia conecta decisiones sobre rutas, estaciones, vehículos, industrias, infraestructuras y recursos. El rendimiento de la red depende de cómo se distribuye el transporte y de cómo se conectan sus componentes.

Aunque no comparte el paradigma de un shooter o un juego de acción en primera persona, constituye un precedente importante para estudiar cómo un sistema global puede influir sobre muchas entidades que operan en el mundo.

## 5.3. Mecánicas principales

- Construcción de infraestructura.
- Diseño de rutas.
- Transporte de mercancías.
- Transporte de pasajeros.
- Gestión de vehículos.
- Planificación logística.
- Economía.
- Expansión territorial.
- Búsqueda de caminos.
- Automatización del transporte.
- Evaluación de rentabilidad.
- Competencia entre redes.

## 5.4. Un punto técnico especialmente relevante

OpenTTD dispone de documentación para varios subsistemas, incluidos economía, vehículos, búsqueda de caminos, scripts y herramientas para crear contenido.

La documentación de desarrollo permite seguir el código del sistema económico y de la navegación, en lugar de estudiar únicamente el comportamiento desde fuera.

Referencias:

- https://docs.openttd.org/source/
- https://docs.openttd.org/source/d9/ddd/economy_8cpp
- https://wiki.openttd.org/en/Development/Script/
- https://wiki.openttd.org/en/Development/NewGRF/Main%20Page

Esta separación ayuda a investigar cómo sistemas relacionados comparten datos sin ser necesariamente el mismo sistema.

Una red de transporte, por ejemplo, necesita un modelo de economía, vehículos, rutas y mercancías. La interacción entre estos componentes produce el resultado global.

## 5.5. Extensibilidad y reglas

OpenTTD permite modificar o ampliar elementos mediante mecanismos como NewGRF y ofrece interfaces de scripting para desarrollar IA y alterar determinados comportamientos.

La documentación oficial explica que los scripts pueden utilizarse para crear competidores controlados por código y modificar objetivos o comportamientos de la partida.

Fuente: https://www.openttd.org/development

Esto ofrece un caso de estudio sobre cómo permitir extensiones sin exigir que cada usuario modifique necesariamente todo el núcleo del producto.

## 5.6. Qué podemos aprender

- Las rutas son sistemas, no simples líneas decorativas.
- La eficiencia depende de interacciones entre infraestructura, vehículos y economía.
- Un sistema de navegación influye sobre la simulación económica.
- La capacidad de modificar reglas amplía la variedad de escenarios.
- Las herramientas de IA pueden estudiar o modificar estrategias dentro de una simulación.
- Las interfaces globales permiten controlar un gran número de entidades mediante órdenes indirectas.

## 5.7. Experimento derivado

Crear una red logística mínima con una interfaz global y una representación física del entorno.

El jugador podría construir una ruta desde la vista táctica y después inspeccionar el resultado desde el punto de vista de una unidad o vehículo.

El experimento debe comprobar qué información puede compartirse entre ambas representaciones y qué decisiones requieren interfaces diferentes.

## 5.8. Precaución sobre la licencia

OpenTTD declara licencia GPL-2.0. Reutilizar su código implica respetar las condiciones de esa licencia y las obligaciones de distribución que puedan resultar aplicables.

La accesibilidad del código no implica que sea un componente libre de restricciones para cualquier arquitectura futura.

**Utilidad para el proyecto:** alta para estudiar simulación económica, logística, búsqueda de rutas, sistemas de IA y contenido extensible.

---

# 6. CASO DE ESTUDIO 05 — FACTORIO

## 6.1. Identificación

**Familias:** automatización, construcción, logística, estrategia y supervivencia industrial.

**Documentación oficial de modding:** https://lua-api.factorio.com/latest/index.html

**Ciclo de vida de los mods:** https://lua-api.factorio.com/latest/auxiliary/data-lifecycle.html

**Documentación de eventos:** https://lua-api.factorio.com/latest/events.html

**Artículo oficial sobre sincronización multijugador:** https://www.factorio.com/blog/post/fff-188

## 6.2. Qué estudiar

Factorio organiza la experiencia alrededor de diseñar procesos de producción, transportar materiales, gestionar energía, construir instalaciones y ampliar la automatización.

Las estructuras construidas por el jugador no son únicamente decorativas: participan en cadenas de producción y transformaciones de recursos.

Esta característica hace que la fábrica sea un sistema dinámico compuesto por muchos procesos relacionados.

## 6.3. Mecánicas relevantes

- Recolección de recursos.
- Fabricación.
- Transformación de materiales.
- Transporte.
- Automatización.
- Distribución de energía.
- Investigación tecnológica.
- Planificación espacial.
- Gestión de inventarios.
- Defensa.
- Optimización de procesos.
- Ampliación de infraestructura.

## 6.4. Arquitectura de extensión: un caso de estudio fundamental

La documentación oficial del API diferencia etapas de configuración, definición de prototipos y ejecución durante la partida.

Durante las etapas de configuración y prototipos, los mods pueden definir o modificar plantillas y propiedades de elementos del juego.

Durante la ejecución, los mods interactúan con un mundo que ya está activo y responden a eventos del sistema.

Fuente: https://lua-api.factorio.com/latest/auxiliary/data-lifecycle.html

Esta separación es especialmente interesante para nuestra investigación.

No es lo mismo añadir una máquina nueva a una simulación que ejecutar una acción cuando una máquina existente termina un proceso.

Son operaciones distintas, con reglas y restricciones diferentes.

## 6.5. Prototipos, datos y ejecución

El concepto de prototipo permite definir plantillas para máquinas, recetas y otros elementos. La documentación oficial describe cómo se cargan y validan esas definiciones.

Los eventos, por otro lado, permiten ejecutar código como respuesta a sucesos determinados.

Referencias:

- https://lua-api.factorio.com/latest/index-prototype.html
- https://lua-api.factorio.com/latest/index-runtime.html
- https://lua-api.factorio.com/latest/events.html

Para nuestro proyecto, esta distinción sugiere que debemos investigar separadamente:

1. La definición de mecánicas disponibles.
2. La configuración de los modos.
3. Los cambios permitidos durante una partida.
4. Los eventos que conectan sistemas.
5. Las restricciones de cada tipo de modificación.

## 6.6. Determinismo y multijugador

En un artículo oficial de desarrollo sobre problemas de sincronización, los desarrolladores explican que Factorio utiliza *deterministic lockstep*: los clientes intercambian entradas y deben simular los mismos ticks de forma idéntica.

También explican que pequeñas diferencias de simulación pueden provocar desincronizaciones.

Fuente: https://www.factorio.com/blog/post/fff-188

Esta observación tiene una consecuencia directa para cualquier juego que combine sistemas complejos y multijugador.

Si cada cliente calcula localmente parte del estado, las reglas y los resultados deben producirse de forma consistente. La generación aleatoria, el orden de las operaciones y la ejecución de los sistemas son aspectos que pueden ser relevantes.

No debemos concluir que nuestro juego necesite obligatoriamente este modelo de sincronización. Hay otras arquitecturas posibles. Lo importante es considerar desde el principio qué significa que dos sistemas tengan que acordar el estado del mundo.

## 6.7. Qué podemos aprender

- Las definiciones de contenido y la ejecución de la partida son responsabilidades distintas.
- Un sistema extensible necesita reglas claras para permitir modificaciones.
- Los eventos pueden conectar subsistemas sin exigir que todos ejecuten constantemente la misma lógica.
- El determinismo puede ser un requisito arquitectónico importante para determinados modelos multijugador.
- La automatización crea desafíos de organización y optimización dentro de una simulación persistente.

## 6.8. Experimento derivado

Diseñar un prototipo con dos tipos de extensión:

- Una que añada una nueva definición de objeto o habilidad.
- Otra que reaccione a un evento durante la partida.

Después evaluar si las responsabilidades están bien separadas y si la extensión puede conectarse a un segundo modo de juego.

**Utilidad para el proyecto:** muy alta para estudiar sistemas de extensibilidad, definición de contenido y coordinación de simulaciones.

**Limitación:** Factorio no es un repositorio abierto del juego completo. La documentación de su API es valiosa para estudiar conceptos de extensión, pero no proporciona automáticamente acceso a toda su implementación interna.

---

# 7. CASO DE ESTUDIO 06 — OPENRA

## 7.1. Identificación

**Categoría:** motor y proyecto abierto de estrategia en tiempo real.

**Lenguaje principal declarado:** C#.

**Tecnologías indicadas por el proyecto:** SDL y OpenGL.

**Repositorio oficial:** https://github.com/OpenRA/OpenRA

**Licencia del repositorio:** GNU GPL versión 3 o posterior, según el archivo de licencia.

## 7.2. Por qué incluir un motor dentro de los casos de estudio

OpenRA no es simplemente un juego con una mecánica interesante: es un proyecto que permite investigar cómo se estructura y extiende una familia de juegos de estrategia.

El repositorio declara que el proyecto permite jugar y modificar juegos basados en títulos clásicos de Westwood, como *Command & Conquer: Red Alert*, *Tiberian Dawn* y *Dune 2000*.

Fuente: https://github.com/OpenRA/OpenRA

## 7.3. Modificación de reglas y contenido

La documentación pública ofrece:

- Un kit de desarrollo para mods.
- Una guía para crear modificaciones.
- Documentación generada de traits y propiedades.
- Herramientas para crear mapas.
- Interfaces de scripting para misiones.
- Recursos de desarrollo y creación de contenido.

La guía del repositorio explica que los mapas y las reglas personalizadas pueden alterar significativamente la jugabilidad.

Fuente: https://github.com/OpenRA/OpenRA

La importancia de este modelo reside en que parte de las capacidades del juego se expresan a través de datos, reglas y extensiones accesibles a quienes desarrollan mods.

Esto permite analizar hasta qué punto una nueva variante requiere cambiar el núcleo del motor o puede componerse con sistemas existentes.

## 7.4. Qué investigar en su implementación

Un estudio de código de OpenRA debería identificar:

- Cómo se representan los actores.
- Cómo se definen las capacidades de las unidades.
- Cómo se evalúan los traits.
- Cómo se configuran las reglas.
- Qué parte se define mediante archivos de datos.
- Qué parte requiere lógica en código.
- Cómo se cargan los mods.
- Cómo se ejecutan las misiones.
- Cómo se validan los contenidos.
- Qué límites existen al combinar extensiones.

Estas cuestiones no se pueden resolver leyendo únicamente la página principal del repositorio. Requieren una inspección posterior de la documentación de traits y del código correspondiente.

## 7.5. Qué podemos aprender

OpenRA es un caso valioso para estudiar un principio: **la posibilidad de modificar reglas y contenido puede formar parte de la arquitectura del juego, en lugar de ser una adaptación tardía**.

Esto no significa que todas las mecánicas deban convertirse en datos o scripts. Algunos cambios necesitarán lógica especializada.

La pregunta es determinar qué aspectos deberían ser configurables, cuáles componibles y cuáles requieren modificaciones del núcleo.

## 7.6. Experimento derivado

Construir una pequeña unidad con capacidades configurables por datos.

Después añadir una segunda variante que cambie sus reglas de comportamiento sin crear una implementación completamente independiente.

El objetivo será comparar el coste de ampliar el sistema mediante configuración frente al coste de introducir nuevo código.

**Utilidad para el proyecto:** muy alta para estudiar contenido extensible, reglas configurables y la separación entre motor y definición de modos.

---

# 8. CASO DE ESTUDIO 07 — BABA IS YOU

## 8.1. Identificación

**Familia:** puzles lógicos con reglas manipulables.

**Desarrollador:** Arvi Teikari, conocido como Hempuli.

**Web del desarrollador:** https://www.hempuli.com/Baba/

**Descripción del proyecto en PLAY18:** https://play18.playfestival.de/en/2018/10/12/2321/

**Investigación académica sobre diseño colaborativo:** https://arxiv.org/abs/2003.14294

**Investigación formal sobre computabilidad:** https://arxiv.org/abs/2205.00127

## 8.2. La mecánica central

En Baba Is You, determinadas reglas del juego se representan mediante bloques de palabras que pueden manipularse físicamente dentro del nivel.

El jugador puede alterar cómo funciona el mundo al reorganizar esos bloques. De esta forma, las reglas no son únicamente instrucciones invisibles que el sistema ejecuta: también forman parte de los objetos con los que se juega.

Fuente: https://play18.playfestival.de/en/2018/10/12/2321/

## 8.3. Qué hace distinto este sistema

En un puzle convencional, el jugador intenta encontrar una solución dentro de reglas relativamente fijas.

En Baba Is You, la propia manipulación de reglas puede ser parte de la solución.

Esto modifica la estructura del problema.

El jugador debe comprender tanto el estado actual como las consecuencias de transformar las reglas que definen ese estado.

La dificultad puede surgir de anticipar cómo afectarán los cambios a otros objetos, objetivos o propiedades.

## 8.4. Implicaciones de diseño

Esta propuesta demuestra la diferencia entre:

- Ejecutar una acción dentro de reglas fijas.
- Elegir entre reglas predefinidas.
- Construir una nueva configuración de reglas.
- Modificar las reglas que determinan qué acciones son posibles.

La cuarta posibilidad es particularmente relevante para nuestro proyecto.

Un juego experimental podría permitir cambios en los controles, la escala, las propiedades de las entidades o las condiciones de victoria. Sin embargo, cada cambio plantea preguntas sobre consistencia y comprensión.

## 8.5. Un antecedente académico sobre herramientas de creación

El artículo *Baba is Y'all: Collaborative Mixed-Initiative Level Design* estudia un sistema colaborativo de creación de niveles inspirado en Baba Is You.

La investigación describe funciones de creación y evolución de niveles, un jugador automático para realizar pruebas y un catálogo que registra qué mecánicas están presentes o ausentes en los niveles.

Fuente: https://arxiv.org/abs/2003.14294

Esto ofrece dos ideas relevantes para la investigación:

1. Las mecánicas pueden catalogarse a nivel de cada escenario.
2. Las herramientas de creación y prueba pueden trabajar con combinaciones de mecánicas, no solo con diseños completos.

## 8.6. Un resultado formal y su límite

La investigación *Baba is You is Undecidable* presenta una demostración formal de indecidibilidad para una generalización del juego bajo las condiciones especificadas por los autores.

Fuente: https://arxiv.org/abs/2205.00127

No debe interpretarse como una afirmación de que todas las partidas originales sean irresolubles ni como un resultado práctico sobre la dificultad de un nivel comercial concreto.

Su relevancia para nuestro proyecto es más limitada y precisa: cuando un sistema permite construir reglas y configuraciones suficientemente expresivas, la complejidad de analizar todas sus posibles configuraciones puede crecer de forma radical.

## 8.7. Qué podemos aprender

- Las reglas pueden representarse mediante objetos manipulables.
- La modificación de reglas puede convertirse en la actividad principal.
- Un sistema puede combinar diferentes mecánicas mediante cambios de propiedades.
- Las herramientas de creación pueden catalogar explícitamente las mecánicas que aparecen en cada nivel.
- Los sistemas con reglas modificables requieren mecanismos sólidos para resolver conflictos, estados inválidos y consecuencias inesperadas.

## 8.8. Experimento derivado

Crear un pequeño mundo con tres propiedades modificables y un conjunto de objetos.

El jugador podrá cambiar las propiedades de los objetos y observar cómo cambian sus capacidades.

Después se evaluará qué sucede cuando la misma modificación afecta simultáneamente a movimiento, objetivos y colisiones.

No se requiere diseñar de inmediato un sistema universal capaz de modificar cualquier regla. El primer prototipo debería centrarse en un conjunto pequeño y explícito de propiedades.

**Utilidad para el proyecto:** muy alta para estudiar reglas manipulables, interfaces que expresan sistemas y creación de escenarios mediante combinaciones de mecánicas.

---

# 9. CASO DE ESTUDIO 08 — OUTER WILDS

## 9.1. Identificación

**Familias:** exploración espacial, aventura narrativa, misterio y puzles basados en conocimiento.

**Conferencia de referencia:** Kelsey Beachum, *Sparking Curiosity-Driven Exploration Through Narrative in Outer Wilds*.

**Fuente oficial:** https://www.gdcvault.com/play/1027368/Independent-Games-Summit-Sparking-Curiosity

## 9.2. El problema de diseño

La presentación de GDC describe un objetivo de diseño muy particular: motivar la exploración sin depender principalmente de asignar misiones explícitas u otras formas convencionales de dirección.

El juego utiliza curiosidad, exploración y una historia no lineal para guiar el progreso dentro de un sistema solar dinámico con un bucle temporal.

Fuente: https://www.gdcvault.com/play/1027368/Independent-Games-Summit-Sparking-Curiosity

## 9.3. Progresión basada en conocimiento

El caso resulta especialmente valioso porque diferencia el progreso del personaje del progreso del jugador.

En muchas experiencias, superar un obstáculo requiere conseguir estadísticas, equipamiento, habilidades o recursos.

En un diseño basado en conocimiento, la barrera puede superarse al comprender mejor el mundo.

El jugador descubre información, interpreta sus relaciones y utiliza ese conocimiento para elegir otra ruta o resolver un problema.

## 9.4. La función del bucle temporal

El bucle estructura la exploración y limita el intervalo en el que se producen los acontecimientos de una partida.

No obstante, el objetivo de diseño no consiste únicamente en reiniciar un mundo periódicamente.

El bucle necesita estar conectado a la exploración y a la información que el jugador obtiene. Los conocimientos descubiertos alteran cómo se interpreta y aborda una nueva expedición.

Fuente de referencia: https://www.gdcvault.com/play/1027368/Independent-Games-Summit-Sparking-Curiosity

## 9.5. Qué podemos aprender

- La información puede constituir una forma de progresión.
- Una estructura temporal puede organizar la exploración.
- Los acontecimientos del mundo pueden proporcionar dirección sin depender siempre de objetivos explícitos.
- La narrativa puede funcionar como mecanismo de descubrimiento.
- El conocimiento adquirido puede modificar las decisiones disponibles sin cambiar necesariamente las estadísticas.

## 9.6. Riesgos de diseño

Una estructura de descubrimiento puede fallar cuando:

- El jugador no identifica una pista importante.
- La relación entre información y acción es difícil de comprender.
- La exploración no ofrece feedback suficiente.
- El reinicio destruye información que el jugador necesita.
- El juego depende de una deducción cuya pista no resulta perceptible.

Estos riesgos no son fallos demostrados de Outer Wilds; son preguntas de diseño que cualquier sistema basado en conocimiento debería evaluar.

## 9.7. Experimento derivado

Crear un pequeño entorno con varias puertas o rutas. Cada una parece cerrada por una condición distinta.

La solución no será mejorar estadísticas, sino descubrir información que permita comprender cómo funciona el entorno.

Posteriormente, el mismo conocimiento se utilizará desde un segundo paradigma, por ejemplo, una vista estratégica o una interfaz de investigación.

**Utilidad para el proyecto:** alta para estudiar progresión no estadística, exploración y transferencia de conocimiento entre modos.

---

# 10. CASO DE ESTUDIO 09 — KEEP TALKING AND NOBODY EXPLODES

## 10.1. Identificación

**Familia:** puzles cooperativos y multijugador asimétrico.

**Desarrollador:** Steel Crate Games.

**Sitio oficial:** https://keeptalkinggame.com/

**Manual de desactivación:** https://www.bombmanual.com/

## 10.2. La estructura de información

El juego presenta una bomba que debe desactivarse.

Una persona puede examinarla directamente, mientras las demás tienen acceso al manual que explica cómo resolver sus módulos, pero no pueden ver la bomba.

Por tanto, el éxito requiere intercambiar información mediante comunicación.

Fuente: https://keeptalkinggame.com/

## 10.3. Qué cambia respecto de un puzle convencional

En un puzle tradicional para un solo jugador, el participante normalmente dispone de la información necesaria en su propia pantalla.

En este caso, la información se distribuye entre varias personas.

Ningún participante puede resolver necesariamente la situación de forma aislada: el sistema exige traducir observaciones, comunicar instrucciones e interpretar las respuestas.

El canal de comunicación se convierte así en una parte fundamental de la experiencia.

## 10.4. Mecánicas relevantes

- Información distribuida.
- Comunicación bajo presión temporal.
- Interpretación de instrucciones.
- Descripción de estados.
- Coordinación de roles.
- Verificación mutua.
- Resolución de errores de comunicación.
- Adaptación a módulos con reglas diferentes.
- Aprendizaje progresivo de procedimientos.

## 10.5. Un detalle de diseño importante

El juego no exige que cada participante reciba una interfaz con las mismas capacidades.

La asimetría no es un defecto que haya que eliminar. Es el motivo por el que la cooperación funciona.

Esto amplía la definición de multijugador: dos personas pueden participar en la misma experiencia sin ejecutar las mismas acciones ni ver la misma información.

## 10.6. Qué podemos aprender

- Una perspectiva diferente puede modificar el papel de un jugador.
- La información puede repartirse de manera deliberada.
- Una herramienta externa o un manual puede formar parte del sistema de juego.
- La comunicación tiene reglas, costes y condiciones de éxito.
- Las diferencias entre jugadores pueden crear dependencia mutua.

## 10.7. Experimento derivado

Crear un prototipo con dos participantes:

- Uno controla una entidad en el mundo.
- Otro solo puede consultar un mapa con información que el primer participante no ve.

El objetivo exige que ambos coordinen sus acciones para resolver una situación.

En una segunda prueba, se cambiará el paradigma de uno de los participantes. Por ejemplo, el primero controla movimiento directo mientras el segundo interviene mediante órdenes estratégicas.

**Utilidad para el proyecto:** muy alta para estudiar información asimétrica, roles distintos e interacción entre interfaces.

---

# 11. CASO DE ESTUDIO 10 — TRACKMANIA

## 11.1. Identificación

**Familias:** carreras arcade, precisión, competición y creación de circuitos.

**Documentación oficial del editor:** https://www.ubisoft.com/en-us/help/trackmania/gameplay/article/accessing-the-track-editor-in-trackmania/000066700

## 11.2. La mecánica más interesante para esta investigación

Trackmania es relevante no solo por las carreras, sino también por las herramientas que permiten crear y editar pistas.

La documentación oficial explica que el editor de pistas sirve para crear circuitos personalizados y que la disponibilidad de sus funciones varía según el acceso disponible.

Fuente: https://www.ubisoft.com/en-us/help/trackmania/gameplay/article/accessing-the-track-editor-in-trackmania/000066700

Esto permite estudiar la creación de contenido como una actividad distinta del control de vehículos.

## 11.3. Dos paradigmas relacionados

En el modo de carrera, el jugador debe dominar movimiento, velocidad, trazadas, tiempo y precisión.

En el modo de creación, debe pensar en geometría, configuración de módulos, conectividad, recorridos y comportamiento esperado del vehículo.

El segundo modo exige otras habilidades y otra relación con el mundo, aunque ambos operen sobre el mismo tipo de contenido.

## 11.4. Qué podemos aprender

- El jugador puede ser tanto participante como diseñador.
- Un editor puede reutilizar componentes del sistema de ejecución.
- Crear contenido tiene sus propias reglas y condiciones de éxito.
- La validación de contenido puede ayudar a garantizar que una creación sea recorrible.
- El contenido generado por usuarios puede ampliar las experiencias que admite un mismo juego.

## 11.5. Lo que todavía debemos investigar

La existencia de un editor no demuestra cómo está estructurado internamente.

Para estudiar esa cuestión necesitaríamos analizar la documentación disponible de las herramientas, los formatos de los circuitos, las restricciones de construcción y los mecanismos de publicación de contenido.

Tampoco debemos asumir que el acceso al editor sea gratuito o idéntico en todas las versiones y plataformas.

## 11.6. Experimento derivado

Crear un sistema en el que el jugador construye una ruta y después debe recorrerla mediante control directo.

Posteriormente, incorporar otro paradigma de evaluación, como una vista estratégica que permita inspeccionar la ruta, identificar riesgos y optimizarla antes de ejecutarla.

**Utilidad para el proyecto:** alta para estudiar herramientas de creación, transición entre diseño y ejecución y validación de contenido.

---

# 12. CASO DE ESTUDIO 11 — SUPERLIMINAL

## 12.1. Identificación

**Familia:** puzles en primera persona y percepción espacial.

**Desarrollador:** Pillow Castle Games.

**Página oficial de prensa:** https://pillowcastle.org/presskits/superliminal/

## 12.2. La mecánica central

Superliminal utiliza perspectiva forzada y ambigüedad de profundidad para convertir la percepción espacial en parte central de los puzles.

Su documentación de prensa describe una experiencia en la que los objetos pueden manipularse en el espacio físico en función de la perspectiva desde la que se observan.

Fuente: https://pillowcastle.org/presskits/superliminal/

## 12.3. La representación no es solo presentación

En muchos juegos, la cámara muestra un mundo cuyas reglas funcionan de forma relativamente independiente del punto de vista.

En Superliminal, la perspectiva forma parte de las reglas que el jugador aprende a utilizar.

La relación entre la imagen observada, el objeto seleccionado y su posición espacial produce el comportamiento que permite resolver los puzles.

La distinción importante es que el sistema de representación interviene en las acciones disponibles.

## 12.4. Mecánicas relacionadas

- Inspección espacial.
- Manipulación de objetos.
- Perspectiva forzada.
- Cambio de tamaño aparente.
- Selección de objetos.
- Colocación.
- Transformación espacial.
- Resolución mediante observación.
- Aprendizaje de reglas perceptivas.

## 12.5. Qué podemos aprender

- La cámara puede ser una regla jugable.
- La representación puede condicionar la interacción y no limitarse a mostrar sus consecuencias.
- Una misma entidad puede adquirir propiedades distintas según cómo se integra en la representación.
- Un cambio de perspectiva puede alterar las posibilidades de resolución sin introducir necesariamente un nuevo género.

## 12.6. Experimento derivado

Construir un puzle con dos cámaras que presentan el mismo escenario de forma distinta.

La prueba debe determinar si cambiar la perspectiva modifica únicamente la información disponible o si también modifica las acciones y resultados posibles.

En un experimento posterior, ese cambio podría conectarse con otro paradigma, como control estratégico o manipulación de reglas.

**Utilidad para el proyecto:** alta para investigar perspectiva como mecánica y separación entre estado del mundo y su representación.

---

# 13. CASO DE ESTUDIO COMPLEMENTARIO — DWARF FORTRESS

## 13.1. Identificación

**Familias:** simulación de sociedades, gestión de colonias, generación procedural y comportamientos emergentes.

**Conferencia de referencia:** *Practices in Procedural Generation*, GDC.

**Fuente:** https://www.gdcvault.com/play/1023372/Practices-in-Procedural

## 13.2. Interés de investigación

Dwarf Fortress es un referente para estudiar mundos simulados con numerosos procesos y relaciones entre entidades.

El material de GDC documenta una sesión sobre prácticas concretas de generación procedural en la que participan Tarn Adams, de Bay 12 Games, y Tanya Short, de Kitfox Games.

La descripción destaca que la generación procedural cambia el enfoque de diseño de los sistemas que toca y que la sesión explora herramientas y métodos reales para implementarla.

Fuente: https://www.gdcvault.com/play/1023372/Practices-in-Procedural

## 13.3. Qué podemos aprender

El interés para nuestro proyecto es el vínculo entre generación, reglas y simulación.

Generar una ciudad no es necesariamente equivalente a generar una ciudad que contenga sistemas coherentes de historia, recursos, relaciones y comportamiento.

Cuantas más partes del mundo dependen de la generación, más importante resulta comprender sus relaciones y restricciones.

## 13.4. Experimento derivado

Generar un escenario que incluya:

- Varias entidades.
- Recursos.
- Relaciones.
- Un pequeño historial de acontecimientos.
- Un conjunto de reglas de interacción.

Después comprobar si las entidades pueden utilizar esos estados y relaciones para producir situaciones coherentes sin depender de una secuencia narrativa completamente predeterminada.

Este experimento no intentaría reproducir la complejidad de Dwarf Fortress. Buscaría validar una propiedad mucho más limitada: que la generación pueda alimentar otros sistemas durante la partida.

**Utilidad para el proyecto:** alta para estudiar generación y sistemas interdependientes, pero la implementación concreta necesitará investigación adicional.

---

# PARTE XIX. COMPARACIÓN ENTRE CASOS

# 14. MATRIZ DE MECÁNICAS Y PRINCIPIOS REUTILIZABLES

| Caso | Capacidad distintiva | Tipo de integración | Principal aprendizaje |
|---|---|---|---|
| Eximius | Mando estratégico y combate individual | Híbrido de géneros | Cambiar de escala e interfaz sin perder coherencia del estado. |
| Mindustry | Construcción industrial y defensa | Sistemas interdependientes | Las instalaciones deben afectar a la economía y al peligro. |
| Cataclysm DDA | Supervivencia y mundo persistente | Simulación común | Distintas actividades pueden compartir entidades, recursos y tiempo. |
| OpenTTD | Logística y economía | Simulación de red | Rutas, vehículos y recursos forman un sistema conectado. |
| Factorio | Automatización y extensibilidad | Definiciones más ejecución | Separar prototipos, eventos y lógica de la partida. |
| OpenRA | Reglas y contenido modificables | Motor extensible | Diseñar extensibilidad desde la arquitectura. |
| Baba Is You | Reglas manipulables | Metarreglas | El jugador puede modificar el sistema, no solo actuar dentro de él. |
| Outer Wilds | Conocimiento y bucle temporal | Progresión basada en información | Aprender puede desbloquear posibilidades sin mejorar estadísticas. |
| Keep Talking | Información asimétrica | Cooperación entre roles | Perspectivas diferentes pueden crear dependencia mutua. |
| Trackmania | Creación y ejecución de circuitos | Herramientas del jugador | Crear contenido puede ser un paradigma separado. |
| Superliminal | Perspectiva como regla | Representación jugable | Cambiar cómo se ve puede cambiar qué puede hacerse. |
| Dwarf Fortress | Generación y simulación sistémica | Mundo generado e interactivo | El contenido procedural necesita relaciones coherentes. |

La matriz no establece un ranking de calidad. Indica qué problema de diseño resulta especialmente útil estudiar en cada caso.

---

# 15. HALLAZGOS TRANSVERSALES

## 15.1. El estado compartido es un principio recurrente

En los casos de híbridos, simulación y automatización, las actividades distintas necesitan compartir parte de su estado.

Sin embargo, no necesitan compartir todas sus reglas o sus controles.

Una entidad puede representarse de manera diferente en una vista estratégica y en una vista física. Lo importante es que las acciones resultantes respeten las reglas definidas para cada modo.

**Consecuencia para el proyecto:** debemos investigar qué datos pueden ser comunes y cuáles pertenecen exclusivamente a cada paradigma.

## 15.2. Las reglas pueden ser contenido, no solo código invisible

Baba Is You demuestra una forma explícita de representar reglas como objetos manipulables. OpenRA y Factorio muestran, desde perspectivas de implementación distintas, que las definiciones de contenido y determinadas modificaciones pueden expresarse mediante herramientas de extensión.

Estas ideas no son idénticas, pero apuntan a una pregunta común:

¿Qué partes de un sistema podrían definirse o modificarse sin tener que reescribir todo el núcleo?

La respuesta determinará la flexibilidad real de la arquitectura.

## 15.3. La progresión no necesita reducirse a estadísticas

Outer Wilds utiliza la exploración y el descubrimiento como parte esencial de la progresión.

Este enfoque puede combinarse con otros sistemas donde el jugador descubre información que altera las decisiones disponibles.

**Hipótesis para el proyecto:** una transición entre géneros podría depender de lo que el jugador comprende, no únicamente de una misión completada o un nivel alcanzado.

Esta hipótesis necesitaría un prototipo para determinar si produce una experiencia clara.

## 15.4. Cambiar de paradigma exige cambiar la interfaz

En Eximius, las decisiones estratégicas requieren información distinta del combate individual.

En Keep Talking, los roles se diferencian por la información disponible.

En Superliminal, la representación es parte del mecanismo de interacción.

Por tanto, cambiar de paradigma puede implicar modificar el tipo de información disponible, no solo cambiar los botones o la cámara.

## 15.5. Una economía puede convertirse en un sistema espacial

Mindustry y Factorio muestran cómo la organización espacial de instalaciones, redes y recursos puede influir sobre los resultados de la simulación.

Esto permite explorar la posibilidad de que una actividad estratégica o económica tenga consecuencias físicas que el jugador pueda experimentar directamente.

La integración concreta de esa posibilidad queda como hipótesis.

## 15.6. La extensibilidad debe evaluarse por capas

Factorio diferencia fases de definición del contenido y fases de ejecución durante la partida. OpenRA ofrece mecanismos para modificar reglas, mapas y contenido.

Estas soluciones sugieren una distinción útil entre:

- Configurar un modo.
- Definir entidades y capacidades.
- Cambiar reglas.
- Responder a acontecimientos.
- Añadir nuevos sistemas.
- Modificar el código central.

No todos los cambios deberían requerir el mismo tipo de operación.

---

# 16. LIMITACIONES DE LA INVESTIGACIÓN ACTUAL

Este documento representa una investigación documental inicial, no una auditoría exhaustiva de todas las implementaciones.

En particular:

1. No se ha inspeccionado todavía cada subsistema de los repositorios línea por línea.
2. No se han ejecutado benchmarks comparables.
3. No se han desarrollado prototipos derivados de los casos.
4. No se ha comprobado empíricamente la calidad de las transiciones propuestas.
5. No se ha hecho una búsqueda exhaustiva de