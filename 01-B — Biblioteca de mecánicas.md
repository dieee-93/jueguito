# BIBLIOTECA MAESTRA DE MECÁNICAS E INTERACCIONES DE VIDEOJUEGOS

**Proyecto:** Investigación y diseño de un videojuego experimental  
**Etapa:** 01-B — Biblioteca de mecánicas  
**Versión:** 1.0  
**Fecha:** Octubre de 2026  
**Estado:** Base de investigación documentada, ampliable mediante casos de estudio y experimentación  
**Dependencia previa:** Etapa 01-A — Catálogo de géneros, subgéneros y paradigmas de videojuego

---

# 1. PROPÓSITO

El objetivo de esta biblioteca es identificar, clasificar y documentar las piezas que constituyen las experiencias jugables.

Mientras el catálogo 01-A organizaba familias de videojuegos, esta biblioteca estudia los mecanismos que permiten construirlas, modificarlas y combinarlas.

No se pretende enumerar únicamente las acciones visibles del jugador, como saltar, disparar o construir. También se investigarán los mecanismos que determinan cómo cambian los estados del mundo, cómo se distribuye la información, qué consecuencias producen las decisiones, cómo actúan los personajes autónomos y qué ocurre cuando las reglas o los controles se transforman.

La biblioteca deberá responder:

1. ¿Qué mecánicas y variantes pueden identificarse?
2. ¿Qué reglas y estados necesita cada una?
3. ¿Qué acciones permiten al jugador?
4. ¿Qué resultados producen y cómo se comunican?
5. ¿Qué otras mecánicas necesitan para funcionar?
6. ¿Qué formas alternativas de implementación existen?
7. ¿Qué precedentes documentados pueden estudiarse?
8. ¿Qué dificultades técnicas y de diseño presentan?
9. ¿Cómo pueden combinarse con mecánicas de otras familias?
10. ¿Cómo podemos comprobar mediante prototipos si una combinación resulta interesante?

El resultado debe servir simultáneamente como referencia conceptual, inventario de diseño, base para experimentos y futura especificación de requisitos técnicos.

## 1.1. Alcance y limitaciones

Esta versión constituye una taxonomía de trabajo amplia, no una enciclopedia exhaustiva de todas las mecánicas concebidas en la historia de los videojuegos.

Las categorías se solapan deliberadamente. Una mecánica de sigilo puede utilizar percepción, información oculta, navegación, comportamiento de agentes y gestión del riesgo. No sería útil obligarla a pertenecer exclusivamente a una categoría.

La biblioteca también distingue entre tres clases de conocimiento:

- **Documentado:** respaldado por bibliografía, documentación oficial, implementaciones observables o código verificable.
- **Síntesis de diseño:** clasificación o interpretación elaborada a partir de los antecedentes investigados.
- **Hipótesis experimental:** combinación, variante o comportamiento que todavía necesita ponerse a prueba.

No se declarará inédita una mecánica porque no se haya encontrado rápidamente un precedente. La novedad se evaluará más adelante mediante investigaciones específicas.

---

# 2. FUNDAMENTO TEÓRICO Y METODOLÓGICO

## 2.1. Qué entendemos por mecánica

En su artículo *Defining Game Mechanics*, publicado en Game Studies en 2008, Miguel Sicart define las mecánicas como métodos que los agentes invocan para interactuar con el estado del juego.

Esta perspectiva resulta especialmente útil para nuestro proyecto porque permite analizar las acciones disponibles, sus consecuencias sobre el estado de la simulación y su relación con los objetivos y desafíos.

Fuente: https://gamestudies.org/0802/articles/sicart

Sin embargo, no existe una definición universalmente aceptada de mecánica que resuelva todos los casos límite. Por eso utilizaremos una definición operativa:

**Una mecánica es una regla o procedimiento de interacción que permite a un agente realizar acciones o responder a acontecimientos, produciendo o condicionando cambios relevantes en el estado de una experiencia jugable.**

No todas las mecánicas tienen que producir un cambio visible inmediato. Observar información, esperar, declarar una hipótesis o reservar un recurso también pueden ser acciones significativas si afectan a las decisiones posteriores.

## 2.2. Distinción entre acción, mecánica, sistema y dinámica

Para evitar que la biblioteca se vuelva imprecisa, distinguiremos los siguientes conceptos.

**Acción o verbo de juego:** lo que un agente puede hacer. Ejemplos: mover, apuntar, recoger, negociar o programar.

**Mecánica:** el procedimiento y las reglas que determinan cómo se ejecuta una acción, en qué condiciones está disponible y cuáles son sus consecuencias.

**Sistema de juego:** conjunto de componentes y reglas que interactúan. Ejemplos: inventario, combate, economía, percepción de los enemigos o progresión.

**Dinámica:** comportamiento que emerge cuando jugadores, entidades, reglas y sistemas interactúan durante una partida.

**Patrón de diseño:** estructura o solución recurrente que ayuda a describir un problema de diseño y una manera de resolverlo.

**Subsistema técnico:** implementación que proporciona capacidades a las mecánicas. Ejemplos: detección de colisiones, pathfinding, animación, audio o sincronización de red.

Estas distinciones son importantes. Un árbol de comportamiento es una técnica para organizar decisiones de IA; detectar a un jugador, perseguirlo o abandonar su búsqueda son comportamientos que pueden formar parte de mecánicas de percepción y amenaza.

Del mismo modo, una cámara en primera persona no constituye por sí sola una mecánica de disparo: es una forma de representar el mundo que condiciona la información, la orientación y los controles.

## 2.3. Fuentes metodológicas utilizadas

### A. MDA: Mechanics, Dynamics, Aesthetics

El marco MDA, desarrollado por Robin Hunicke, Marc LeBlanc y Robert Zubek, conecta las mecánicas, las dinámicas que emergen de ellas y las experiencias que produce el juego.

Referencia: https://www.cs.northwestern.edu/~hunicke/MDA.pdf

Aplicación a nuestra biblioteca:

- Identificar las reglas y acciones implementadas.
- Observar los comportamientos que surgen al interactuar.
- Analizar qué experiencia generan y en qué circunstancias.
- Modificar el diseño según los resultados.

### B. Game Ontology Project

El proyecto de ontología de videojuegos de José P. Zagal y colaboradores propone una jerarquía de conceptos para describir y analizar juegos. Entre los componentes de nivel superior que presenta están la interfaz, las reglas, los objetivos, las entidades y la manipulación de entidades.

Referencia: https://dl.digra.org/index.php/dl/article/view/136

Aplicación a nuestra biblioteca: evitar que todas las mecánicas se reduzcan a verbos; también debemos documentar las entidades sobre las que actúan, las reglas que restringen su funcionamiento y los objetivos que les dan sentido.

### C. Patrones de diseño de videojuegos

Los trabajos de Staffan Björk, Jussi Holopainen y otros investigadores analizan patrones de interacción recurrentes y su relación con los componentes del juego.

Referencia introductoria: https://www.researchgate.net/publication/236157130_Patterns_in_Game_Design

Aplicación a nuestra biblioteca: registrar relaciones entre mecánicas, en lugar de tratar cada entrada como una pieza aislada.

### D. Modelado de recursos y economía

La documentación del marco Machinations describe recursos, fuentes, acumulaciones, consumos, conversiones, intercambios, compuertas y conexiones que determinan cómo circulan los recursos y cambian los estados.

Referencia: https://machinations.io/docs/framework-basics

Aplicación a nuestra biblioteca: analizar los recursos como flujos y estados, en lugar de limitarnos a enumerar monedas, salud, munición o experiencia.

### E. Generación procedural

Las investigaciones sobre generación procedural de contenido distinguen diversos tipos de contenido generado y los métodos que pueden utilizarse para producirlo.

Fuentes:

- Hendrikx y colaboradores, *Procedural Content Generation for Games: A Survey*: https://doi.org/10.1145/2422956.2422957
- Farrokhi Maleki y Zhao, *Procedural Content Generation in Games: A Survey with Insights on Emerging LLM Integration*: https://ojs.aaai.org/index.php/AIIDE/article/view/31877

Aplicación a nuestra biblioteca: separar las mecánicas que crean contenido durante el juego de las herramientas que generan ese contenido antes de iniciar una partida.

---

# 3. FICHA NORMALIZADA DE CADA MECÁNICA

Cada entrada de la biblioteca deberá utilizar una ficha con los siguientes campos.

| Campo | Descripción |
|---|---|
| ID | Identificador único. |
| Nombre | Denominación de la mecánica. |
| Categoría | Familia principal. |
| Variantes | Formas alternativas de funcionamiento. |
| Definición | Qué hace y qué la distingue. |
| Agente | Quién puede activarla: jugador, NPC, sistema, equipo o entorno. |
| Estado inicial | Qué condiciones deben cumplirse antes de utilizarla. |
| Entrada | Acción, decisión o acontecimiento que la activa. |
| Procedimiento | Reglas que determinan la resolución. |
| Estado resultante | Qué puede cambiar en el mundo. |
| Restricciones | Límites, requisitos, costes o incompatibilidades. |
| Feedback | Cómo percibe el jugador el resultado. |
| Precedentes | Juegos, artículos o implementaciones que la utilizan. |
| Dependencias técnicas | Subsistemas que podrían ser necesarios. |
| Riesgos de diseño | Problemas que conviene estudiar. |
| Combinaciones | Otras mecánicas con las que podría interactuar. |
| Prueba mínima | Prototipo o experimento que permita evaluar su funcionamiento. |
| Estado de investigación | Documentada, parcialmente documentada o pendiente de verificar. |

No es necesario que todas las fichas estén completas desde el principio. Los campos desconocidos deben quedar pendientes, en lugar de rellenarse mediante suposiciones.

---

# PARTE I. ACCIONES DEL JUGADOR Y CONTROL

# 4. ACCIONES FUNDAMENTALES

## 4.1. Desplazamiento y locomoción

Acciones mediante las que un agente cambia su posición u orientación dentro del espacio jugable.

Mecánicas y variantes:

- Caminar.
- Correr.
- Acelerar y desacelerar.
- Saltar.
- Saltar con altura variable.
- Doble salto.
- Esprintar.
- Deslizarse.
- Agacharse.
- Gatear.
- Trepar.
- Escalar superficies.
- Nadar.
- Bucear.
- Volar.
- Planear.
- Impulsarse.
- Balancearse mediante cuerdas o puntos de anclaje.
- Agarrarse a bordes.
- Colgarse.
- Empujar el propio cuerpo desde superficies.
- Rebotar.
- Teletransportarse.
- Cambiar de carril.
- Caminar sobre superficies especiales.
- Desplazarse mediante vehículos.
- Moverse mediante control indirecto.
- Desplazarse automáticamente.
- Moverse mediante instrucciones programadas.

## 4.2. Manipulación de orientación y dirección

- Girar.
- Apuntar.
- Orientar un arma.
- Cambiar la dirección de movimiento.
- Bloquear la orientación hacia un objetivo.
- Mirar independientemente del desplazamiento.
- Orientar un vehículo.
- Controlar una torreta.
- Seleccionar una dirección cardinal.
- Seleccionar una trayectoria.
- Controlar una dirección mediante el ratón.
- Controlar la orientación mediante cámara.
- Definir un vector de movimiento.
- Mantener una orientación mientras se realizan otras acciones.

Estas acciones no son equivalentes: mover la cámara, orientar el personaje y modificar la trayectoria pueden utilizar entradas diferentes y producir consecuencias distintas.

## 4.3. Selección y mando

- Seleccionar una entidad.
- Seleccionar múltiples entidades.
- Seleccionar una unidad por tipo.
- Seleccionar un grupo guardado.
- Seleccionar un objetivo.
- Emitir una orden.
- Cancelar una orden.
- Cambiar prioridades.
- Establecer formación.
- Marcar una posición.
- Asignar una tarea.
- Transferir el control.
- Cambiar de entidad controlada.
- Alternar entre control directo e indirecto.
- Programar acciones.
- Encolar órdenes.
- Interrumpir una secuencia.
- Emitir instrucciones condicionadas a acontecimientos.
- Definir objetivos colectivos.
- Crear una cadena de órdenes.

## 4.4. Interacción contextual

- Interactuar con un objeto.
- Abrir o cerrar.
- Activar o desactivar.
- Recoger.
- Depositar.
- Equipar.
- Desequipar.
- Inspeccionar.
- Examinar.
- Leer.
- Usar una herramienta.
- Manipular un dispositivo.
- Operar una máquina.
- Activar una palanca.
- Introducir una clave.
- Seleccionar una opción contextual.
- Combinar objetos.
- Separar componentes.
- Entregar un objeto.
- Utilizar un objeto sobre otro.
- Ejecutar una acción condicionada al entorno.

## 4.5. Acciones de información

- Observar.
- Buscar.
- Escuchar.
- Detectar.
- Escanear.
- Analizar.
- Identificar.
- Comparar.
- Medir.
- Seguir rastros.
- Consultar un mapa.
- Examinar registros.
- Interrogar.
- Investigar.
- Formular hipótesis.
- Marcar información.
- Compartir información.
- Registrar descubrimientos.
- Reconstruir acontecimientos.
- Confirmar o descartar una hipótesis.

## 4.6. Acciones de comunicación

- Hablar.
- Elegir diálogo.
- Escribir.
- Emitir comandos.
- Negociar.
- Amenazar.
- Persuadir.
- Mentir.
- Interrogar.
- Pedir ayuda.
- Emitir señales.
- Hacer gestos.
- Compartir información.
- Ocultar información.
- Votar.
- Establecer acuerdos.
- Romper acuerdos.
- Comunicar intenciones mediante acciones dentro del mundo.

## 4.7. Acciones de creación y transformación

- Construir.
- Colocar.
- Eliminar.
- Editar.
- Rotar.
- Escalar.
- Conectar.
- Desconectar.
- Pintar.
- Dibujar.
- Tallar.
- Perforar.
- Moldear.
- Destruir.
- Reparar.
- Ensamblar.
- Desensamblar.
- Programar.
- Configurar.
- Transformar propiedades.
- Modificar reglas.
- Generar entidades.
- Crear rutas.
- Diseñar escenarios.
- Crear comportamientos.

## 4.8. Acciones de compromiso y decisión

- Elegir entre alternativas.
- Apostar recursos.
- Reservar recursos.
- Aceptar un riesgo.
- Renunciar a una oportunidad.
- Sacrificar una entidad.
- Tomar una decisión irreversible.
- Elegir una estrategia.
- Comprometer una secuencia de acciones.
- Elegir un objetivo a largo plazo.
- Cambiar de objetivo.
- Abandonar una misión.
- Extraer recursos.
- Reiniciar una partida.
- Mantener un estado presente en lugar de avanzar.

---

# PARTE II. MOVIMIENTO, ESPACIO Y FÍSICA

# 5. MECÁNICAS DE MOVIMIENTO

## 5.1. Modelo de locomoción

Cada forma de movimiento puede variar según:

- Velocidad máxima.
- Aceleración.
- Desaceleración.
- Inercia.
- Fricción.
- Resistencia del entorno.
- Control aéreo.
- Impulso.
- Estabilidad.
- Capacidad de detenerse.
- Conservación del momento.
- Capacidad de cambiar de dirección.
- Dependencia de una superficie.
- Coste energético.
- Riesgo de caída.
- Precisión del control.

## 5.2. Movimiento basado en impulso

La trayectoria depende parcialmente del movimiento que el agente ya posee.

Variantes:

- Saltos que conservan velocidad.
- Impulso mediante superficies.
- Rebotar contra obstáculos.
- Ganar velocidad en pendientes.
- Transferencia de impulso entre objetos.
- Impulso por explosiones.
- Movimiento basado en balanceo.
- Acumulación y liberación de energía.
- Conservación de velocidad entre modos.

Aplicación experimental: una habilidad adquirida durante una sección de plataformas podría convertirse en una ventaja para una carrera o una interacción física.

## 5.3. Movimiento condicionado al entorno

- Terreno resbaladizo.
- Superficies pegajosas.
- Agua.
- Corrientes.
- Viento.
- Gravedad variable.
- Zonas de baja fricción.
- Zonas de alta resistencia.
- Superficies deformables.
- Paredes escalables.
- Plataformas móviles.
- Obstáculos dinámicos.
- Entornos que alteran velocidades.
- Espacios con movimiento relativo.
- Terrenos que cambian durante la partida.

## 5.4. Teletransporte y discontinuidad espacial

- Teletransporte a posiciones fijas.
- Teletransporte hacia objetivos.
- Intercambio de posiciones.
- Portales.
- Desplazamiento entre dimensiones.
- Cambio instantáneo de escala.
- Cambio de plano.
- Sustitución de entidad.
- Movimiento mediante puntos de anclaje.
- Reubicación mediante comandos.
- Transferencia del control a otra ubicación.

Cada variante debe especificar cómo trata colisiones, orientación, inercia, continuidad de cámara y entidades que atraviesan el espacio.

---

# 6. COLISIONES, FUERZAS Y FÍSICA INTERACTIVA

## 6.1. Interacción física básica

- Detección de contacto.
- Bloqueo por colisión.
- Rebote.
- Empuje.
- Arrastre.
- Fricción.
- Fuerza aplicada.
- Impulso.
- Rotación.
- Torque.
- Equilibrio.
- Caída.
- Gravedad.
- Flotación.
- Densidad.
- Resistencia.
- Movimiento de cuerpos rígidos.
- Restricciones entre objetos.

La documentación oficial de Godot distingue los objetos de colisión y los procedimientos de detección y respuesta, lo que ilustra la separación entre el efecto jugable que buscamos y el subsistema físico que puede implementarlo.

Referencia: https://docs.godotengine.org/en/stable/tutorials/physics/physics_introduction.html

## 6.2. Física como mecánica principal

- Apilar objetos.
- Construir estructuras estables.
- Mantener el equilibrio.
- Lanzar objetos.
- Usar objetos como contrapesos.
- Desviar proyectiles.
- Crear reacciones en cadena.
- Aprovechar la gravedad.
- Transportar objetos pesados.
- Destruir estructuras.
- Crear rutas mediante objetos físicos.
- Utilizar vehículos como herramientas.
- Resolver puzles con fuerzas.
- Manipular fluidos.
- Transformar el estado físico de un objeto.
- Provocar colapsos.
- Alterar las propiedades físicas de materiales.

## 6.3. Transformación de la física

- Cambiar gravedad global.
- Cambiar gravedad local.
- Invertir direcciones de gravedad.
- Alterar masa.
- Alterar fricción.
- Modificar elasticidad.
- Cambiar resistencia.
- Hacer que determinados objetos floten.
- Hacer que objetos atraviesen superficies.
- Modificar dimensiones.
- Cambiar propiedades por reglas.
- Establecer excepciones a la física normal.

Estas posibilidades pueden utilizarse como mecánicas directas, poderes temporales, reglas de puzles o transformaciones entre paradigmas.

---

# PARTE III. COMBATE Y CONFLICTO

# 7. MECÁNICAS DE COMBATE

## 7.1. Ataque y selección de objetivos

- Ataque directo.
- Ataque cargado.
- Ataque continuo.
- Ataque automático.
- Ataque dirigido.
- Ataque por área.
- Ataque de proximidad.
- Ataque de oportunidad.
- Ataque condicionado.
- Ataque en cadena.
- Ataque combinado entre unidades.
- Ataque desde cobertura.
- Ataque mediante entorno.
- Ataque con efectos retardados.
- Ataque mediante entidades autónomas.
- Ataque que modifica el terreno.
- Ataque que genera recursos.
- Ataque que transfiere estados.

## 7.2. Proyectiles y trayectorias

- Disparo instantáneo.
- Proyectil físico.
- Proyectil dirigido.
- Proyectil con seguimiento.
- Proyectil que rebota.
- Proyectil que atraviesa objetivos.
- Proyectil explosivo.
- Proyectil que deja un área persistente.
- Proyectil controlable.
- Dispersión.
- Retroceso.
- Recarga.
- Munición limitada.
- Munición regenerativa.
- Munición que se fabrica.
- Munición que cambia de propiedad.
- Proyectiles que interactúan entre sí.
- Patrones de proyectiles.

## 7.3. Defensa y evasión

- Bloquear.
- Parar.
- Desviar.
- Esquivar.
- Rodar.
- Cubrirse.
- Contratacar.
- Interrumpir.
- Cancelar una acción.
- Dispersarse.
- Buscar cobertura.
- Cambiar de posición.
- Absorber daño.
- Reflejar daño.
- Compartir daño.
- Redirigir daño.
- Evitar la detección.
- Escapar.
- Retirarse estratégicamente.

## 7.4. Salud, daño y estados

- Puntos de salud.
- Escudo.
- Armadura.
- Resistencia.
- Heridas localizadas.
- Daño acumulativo.
- Recuperación.
- Regeneración.
- Sangrado.
- Veneno.
- Quemadura.
- Congelación.
- Aturdimiento.
- Lentitud.
- Ceguera.
- Desorientación.
- Inmovilización.
- Vulnerabilidad.
- Invulnerabilidad temporal.
- Daño por tiempo.
- Daño por entorno.
- Estados acumulables.
- Estados que se transforman entre sí.

## 7.5. Combate basado en información

- Línea de visión.
- Detección por sonido.
- Detección por movimiento.
- Detección por olor o rastros.
- Sospecha.
- Alerta.
- Búsqueda.
- Identificación de amenazas.
- Lectura de patrones.
- Anticipación de ataques.
- Información sobre intenciones.
- Puntos ciegos.
- Cobertura visual.
- Engaño.
- Señuelos.
- Enemigos que ocultan información.
- Sistemas que recuerdan encuentros anteriores.

## 7.6. Combate táctico

- Puntos de acción.
- Turnos individuales.
- Turnos por equipo.
- Iniciativa.
- Alcance.
- Flanqueo.
- Altura.
- Cobertura.
- Formación.
- Sinergia de unidades.
- Orden de activación.
- Interrupciones.
- Acciones condicionadas.
- Reacciones automáticas.
- Ataques de oportunidad.
- Línea de fuego compartida.
- Control de territorio.
- Coste de reposicionamiento.

## 7.7. Alternativas al combate

- Evitar.
- Convencer.
- Negociar.
- Engañar.
- Distraer.
- Desactivar.
- Inmovilizar.
- Separar adversarios.
- Alterar incentivos.
- Cambiar las condiciones del conflicto.
- Convertir un enemigo en aliado.
- Resolver el conflicto mediante un objetivo externo.
- Utilizar el entorno para neutralizar una amenaza.

---

# PARTE IV. REGLAS, ESTADOS Y CAUSALIDAD

# 8. MECÁNICAS DE REGLAS

## 8.1. Condiciones y restricciones

- Precondiciones.
- Restricciones de acción.
- Requisitos de recursos.
- Requisitos de posición.
- Dependencia temporal.
- Dependencia de estado.
- Dependencia de equipo.
- Dependencia de reputación.
- Dependencia de habilidades.
- Restricciones territoriales.
- Reglas de acceso.
- Prioridades.
- Excepciones.
- Conflictos entre reglas.

## 8.2. Estados y transiciones

- Estados mutuamente excluyentes.
- Estados simultáneos.
- Cambios de estado por acción.
- Cambios por acontecimiento.
- Cambios por tiempo.
- Cambios por condición.
- Estados persistentes.
- Estados temporales.
- Estados que se acumulan.
- Estados que se cancelan.
- Estados que alteran las acciones posibles.
- Estados que modifican las reglas.
- Estados que dependen de otros agentes.

## 8.3. Acontecimientos y desencadenantes

- Entrada en una región.
- Contacto entre entidades.
- Agotamiento de recursos.
- Cumplimiento de una condición.
- Pérdida de una unidad.
- Aparición de una amenaza.
- Cambio de hora.
- Activación de un dispositivo.
- Cambio de reglas.
- Completación de una misión.
- Acción de otro jugador.
- Resultado aleatorio.
- Resultado de una simulación.
- Condición detectada por un agente autónomo.

## 8.4. Reglas manipulables

- Cambiar propiedades de objetos.
- Cambiar quién puede actuar.
- Cambiar qué objetos son sólidos.
- Cambiar condiciones de victoria.
- Cambiar requisitos para ejecutar acciones.
- Cambiar relaciones causales.
- Cambiar el coste de recursos.
- Cambiar las prioridades de los sistemas.
- Cambiar el orden de resolución.
- Activar y desactivar reglas.
- Crear reglas.
- Eliminar reglas.
- Cambiar la duración de una regla.
- Crear excepciones.
- Transformar las reglas mediante acciones dentro del mundo.

*Baba Is You* es un caso de estudio útil porque hace visibles y manipulables ciertas reglas del juego. Para estudiar implementaciones, pueden inspeccionarse proyectos independientes que recrean mecánicas inspiradas en él, sin confundirlos con el código oficial del título.

Ejemplos de referencia:

- https://github.com/Getnetsh/Baba-Is-You-Project
- https://github.com/Foreii/BabaIsYou

Antes de reutilizar cualquier repositorio, deben examinarse su licencia, alcance, calidad y estado de mantenimiento.

---

# PARTE V. TIEMPO Y SECUENCIAS

# 9. MECÁNICAS TEMPORALES

## 9.1. Resolución de acciones

- Tiempo real.
- Turnos discretos.
- Turnos simultáneos.
- Turnos alternados.
- Tiempo real con pausa.
- Pausa que permite emitir órdenes.
- Planificación seguida de ejecución.
- Secuencias automatizadas.
- Acciones que se resuelven al completar una animación.
- Acciones que pueden interrumpirse.
- Acciones que terminan después de un plazo.
- Acciones que esperan un acontecimiento.
- Acciones que dependen de la latencia o sincronización entre participantes.

## 9.2. Manipulación temporal

- Ralentizar.
- Acelerar.
- Detener.
- Rebobinar.
- Repetir un intervalo.
- Establecer un bucle.
- Saltar un intervalo.
- Congelar entidades seleccionadas.
- Alterar la velocidad de entidades concretas.
- Desfasar temporalmente dos simulaciones.
- Repetir una secuencia.
- Guardar y restaurar un estado.
- Cambiar las reglas de avance del tiempo.

## 9.3. Planificación y programación temporal

- Encolar acciones.
- Definir prioridades.
- Programar órdenes condicionales.
- Establecer secuencias.
- Programar acciones simultáneas.
- Crear ciclos de trabajo.
- Asignar horarios.
- Coordinar varios agentes.
- Preparar una acción durante una pausa.
- Ejecutar un plan bajo incertidumbre.
- Interrumpir un plan al producirse un evento.

## 9.4. Tiempo como recurso

- Límite de tiempo.
- Ventanas de oportunidad.
- Recarga temporal.
- Enfriamiento.
- Tiempo de fabricación.
- Tiempo de desplazamiento.
- Tiempo de espera.
- Coste temporal de acciones.
- Tiempo utilizado como apuesta.
- Tiempo que se gana o pierde al ejecutar acciones.
- Tiempo como moneda intercambiable con otros recursos.

## 9.5. Ritmo y sincronización

- Ejecutar acciones siguiendo un compás.
- Sincronizar movimientos.
- Repetir secuencias temporales.
- Coordinar varios participantes.
- Mantener un ritmo.
- Interrumpir un patrón.
- Anticipar un patrón.
- Combinar ritmos.
- Sincronizar objetos y acontecimientos.
- Usar el ritmo como condición de activación.

---

# PARTE VI. INFORMACIÓN, PERCEPCIÓN Y DEDUCCIÓN

# 10. MECÁNICAS DE INFORMACIÓN

## 10.1. Visibilidad

- Visión completa.
- Campo visual limitado.
- Niebla de guerra.
- Visión compartida.
- Visión individual.
- Visión temporal.
- Revelado permanente.
- Revelado condicionado.
- Visión a través de objetos.
- Detección de entidades invisibles.
- Visión térmica.
- Visión basada en rastros.
- Visión condicionada a habilidades.
- Información mostrada únicamente en mapas o interfaces.

## 10.2. Ocultamiento e información incompleta

- Entidades ocultas.
- Identidades ocultas.
- Recursos desconocidos.
- Intenciones ocultas.
- Objetivos secretos.
- Mapas parcialmente conocidos.
- Reglas desconocidas.
- Información que se revela progresivamente.
- Informes imprecisos.
- Información deliberadamente falsa.
- Información disponible a otro jugador.
- Información que caduca.
- Información que depende del punto de vista.
- Información que requiere una herramienta específica.

## 10.3. Investigación y deducción

- Recoger pistas.
- Relacionar evidencias.
- Formular hipótesis.
- Comparar hipótesis.
- Interrogar.
- Reconstruir cronologías.
- Detectar contradicciones.
- Identificar patrones.
- Establecer relaciones causales.
- Inferir propiedades desconocidas.
- Confirmar una solución.
- Revisar una conclusión.
- Compartir una deducción.
- Resolver un problema con información distribuida.

## 10.4. Memoria

- Memoria del jugador.
- Memoria de entidades autónomas.
- Memoria de acontecimientos.
- Registro de pistas.
- Historial de decisiones.
- Memoria espacial.
- Registro de relaciones.
- Memoria de errores anteriores.
- Conocimiento persistente entre partidas.
- Conocimiento que cambia las opciones disponibles.
- Conocimiento que revela nuevas interpretaciones del mundo.

## 10.5. Sistemas de pistas y descubrimiento

- Pistas explícitas.
- Pistas ambientales.
- Pistas auditivas.
- Pistas visuales.
- Pistas contextuales.
- Pistas dependientes del orden.
- Pistas contradictorias.
- Pistas generadas proceduralmente.
- Ayudas graduadas.
- Sistemas de descubrimiento sin instrucciones directas.
- Recompensas por observación.
- Interpretación de mapas, símbolos o lenguajes ficticios.

---

# PARTE VII. RECURSOS, ECONOMÍA E INVENTARIOS

# 11. MECÁNICAS DE RECURSOS

## 11.1. Adquisición y generación

- Recoger recursos.
- Extraer.
- Cosechar.
- Derrotar entidades que producen recompensas.
- Obtener recursos por tiempo.
- Recibir recursos por objetivos.
- Producir recursos.
- Generar recursos automáticamente.
- Recuperar recursos del entorno.
- Intercambiar información por recursos.
- Convertir tiempo en recursos.
- Generar recursos bajo condiciones.
- Recuperar recursos a partir de residuos.
- Transformar objetos existentes.

## 11.2. Acumulación y almacenamiento

- Inventario.
- Capacidad limitada.
- Peso.
- Espacio de almacenamiento.
- Apilamiento.
- Contenedores.
- Almacenes compartidos.
- Almacenamiento remoto.
- Recursos persistentes.
- Recursos temporales.
- Recursos perecederos.
- Recursos que se deterioran.
- Recursos que producen otros recursos.

## 11.3. Consumo y gasto

- Munición.
- Energía.
- Salud.
- Resistencia.
- Dinero.
- Materiales.
- Puntos de acción.
- Tiempo.
- Reputación.
- Cargas limitadas.
- Recursos consumidos por mantenimiento.
- Recursos consumidos por operaciones automáticas.
- Recursos perdidos por daños.
- Recursos comprometidos en acciones futuras.

## 11.4. Transformación y fabricación

- Recetas.
- Combinación de objetos.
- Refinamiento.
- Descomposición.
- Fundición.
- Ensamblaje.
- Producción industrial.
- Fabricación bajo restricciones.
- Mejora de materiales.
- Conversión entre monedas.
- Conversión de recursos en información.
- Conversión de energía en movimiento.
- Reciclaje.
- Producción condicionada por calidad.
- Transformación de recursos mediante habilidades.

## 11.5. Comercio e intercambio

- Compra y venta.
- Intercambio directo.
- Mercados.
- Subastas.
- Negociación.
- Regateo.
- Precios dinámicos.
- Oferta y demanda.
- Deudas.
- Intereses.
- Impuestos.
- Contratos.
- Contratos con condiciones.
- Reparto de recursos.
- Comercio entre jugadores.
- Transferencia de recursos entre modos.

## 11.6. Riesgo económico

- Apostar recursos.
- Pérdida al morir.
- Costes de recuperación.
- Escasez.
- Recursos irreemplazables.
- Recursos compartidos.
- Competencia por recursos.
- Rendimientos decrecientes.
- Inflación.
- Devaluación.
- Recursos que se vuelven obsoletos.
- Inversión a largo plazo.
- Retorno variable.
- Costes de oportunidad.

## 11.7. Modelado económico

Para sistemas complejos, conviene representar los recursos como flujos:

- Fuentes.
- Almacenes.
- Consumos.
- Transformaciones.
- Intercambios.
- Distribución aleatoria.
- Transferencias condicionadas.
- Conexiones que modifican estados.
- Reglas de producción.
- Reglas de mantenimiento.

Machinations documenta estos patrones en un marco de modelado de sistemas. No implica que debamos adoptar esa herramienta: nos sirve como referencia conceptual para representar economías y comprobar el equilibrio de los flujos.

Referencia: https://machinations.io/docs/framework-basics

---

# PARTE VIII. PROGRESIÓN, OBJETIVOS Y RECOMPENSAS

# 12. MECÁNICAS DE PROGRESIÓN

## 12.1. Desarrollo del personaje

- Experiencia.
- Niveles.
- Atributos.
- Habilidades.
- Árboles de talentos.
- Clases.
- Especializaciones.
- Rasgos.
- Perks.
- Mutaciones.
- Capacidades adquiridas.
- Pérdida de capacidades.
- Habilidades temporales.
- Habilidades condicionadas.
- Combinación de habilidades.

## 12.2. Equipo y modificación de capacidades

- Armas.
- Armaduras.
- Herramientas.
- Accesorios.
- Mejoras.
- Modificadores.
- Equipo con propiedades aleatorias.
- Equipo que transforma habilidades.
- Equipo intercambiable entre personajes.
- Cargas de objetos.
- Desgaste.
- Reparación.
- Compatibilidad entre piezas.

## 12.3. Progresión basada en conocimiento

- Descubrimiento de reglas.
- Acceso a información.
- Aprendizaje de técnicas.
- Reconocimiento de patrones.
- Comprensión de mapas.
- Descubrimiento de secretos.
- Interpretación de acontecimientos.
- Aprendizaje de comandos.
- Comprensión de un sistema de programación.
- Conocimiento que habilita rutas o acciones.

## 12.4. Desbloqueos

- Nuevas áreas.
- Nuevas herramientas.
- Nuevos personajes.
- Nuevas acciones.
- Nuevos modos.
- Nuevas reglas.
- Nuevas perspectivas.
- Nuevos controles.
- Nuevas formas de interacción.
- Variantes de un sistema existente.

## 12.5. Progresión entre partidas

- Desbloqueos persistentes.
- Mejoras permanentes.
- Recursos que sobreviven al reinicio.
- Conocimiento que persiste.
- Metaprogresión.
- Prestigio.
- Reinicio voluntario.
- Reinicio condicionado.
- Beneficios por comenzar de nuevo.
- Sacrificio de progreso a cambio de nuevas posibilidades.

## 12.6. Objetivos y condiciones de victoria

- Llegar a una posición.
- Sobrevivir.
- Derrotar un objetivo.
- Defender una posición.
- Producir cierta cantidad.
- Alcanzar una puntuación.
- Descubrir información.
- Completar una secuencia.
- Reunir recursos.
- Controlar territorio.
- Mantener un estado durante un tiempo.
- Resolver un misterio.
- Construir una configuración válida.
- Cambiar las reglas para cumplir el objetivo.
- Alcanzar una meta compartida.
- Cumplir objetivos incompatibles con otros jugadores.
- Alcanzar varios objetivos simultáneos.

## 12.7. Recompensas

- Puntuación.
- Recursos.
- Experiencia.
- Objetos.
- Información.
- Habilidades.
- Acceso.
- Reputación.
- Ventajas estratégicas.
- Nuevas opciones narrativas.
- Cambios persistentes en el mundo.
- Reconocimiento social.
- Desbloqueos.
- Libertad para crear.

No todas las recompensas necesitan expresarse en números. Descubrir una regla o aprender una ruta también puede ampliar las posibilidades del jugador.

---

# PARTE IX. PUZLES Y LÓGICA

# 13. MECÁNICAS DE RESOLUCIÓN DE PROBLEMAS

## 13.1. Manipulación de objetos

- Empujar.
- Tirar.
- Levantar.
- Rotar.
- Apilar.
- Encajar.
- Lanzar.
- Transportar.
- Intercambiar.
- Conectar.
- Separar.
- Cambiar propiedades.
- Utilizar objetos como herramientas.
- Convertir objetos en otros.
- Utilizar un objeto para activar otro.

## 13.2. Puzles de restricciones

- Espacios limitados.
- Movimientos limitados.
- Orden obligatorio.
- Recursos limitados.
- Dependencias.
- Restricciones espaciales.
- Restricciones temporales.
- Restricciones de compatibilidad.
- Restricciones de información.
- Restricciones que pueden modificarse.

## 13.3. Puzles de lógica

- Reglas condicionales.
- Deducción.
- Identificación de patrones.
- Clasificación.
- Secuenciación.
- Correspondencias.
- Relaciones espaciales.
- Resolución de contradicciones.
- Interpretación de símbolos.
- Aprendizaje de reglas implícitas.

## 13.4. Puzles temporales

- Sincronización.
- Repetición de secuencias.
- Ventanas temporales.
- Grabación de acciones.
- Reproducción de acciones.
- Bucles.
- Acciones simultáneas.
- Planificación de órdenes.
- Manipulación del orden temporal.

## 13.5. Puzles de programación

- Programación por bloques.
- Secuencias de instrucciones.
- Condicionales.
- Bucles.
- Eventos.
- Circuitos lógicos.
- Automatización.
- Control de robots.
- Programación de agentes.
- Optimización de operaciones.
- Restricciones de memoria o tiempo.
- Depuración de errores.

---

# PARTE X. INTELIGENCIA ARTIFICIAL Y AGENTES AUTÓNOMOS

# 14. MECÁNICAS DE AGENTES

## 14.1. Percepción

- Detección visual.
- Detección auditiva.
- Detección de contacto.
- Identificación de amenazas.
- Percepción de objetivos.
- Percepción de recursos.
- Reconocimiento de patrones.
- Percepción parcial.
- Percepción con ruido.
- Percepción condicionada por estados.

## 14.2. Comportamiento y decisión

- Máquinas de estados.
- Árboles de comportamiento.
- Sistemas de prioridades.
- Reglas de reacción.
- Planificación.
- Selección de objetivos.
- Patrullaje.
- Persecución.
- Huida.
- Búsqueda.
- Defensa.
- Cooperación.
- Formación.
- Reacción a acontecimientos.
- Adaptación a cambios del entorno.

Los árboles de comportamiento son una técnica documentada para organizar decisiones de NPC; pueden representar desde conductas sencillas hasta secuencias complejas. No constituyen una mecánica jugable por sí mismos, sino una forma de implementar comportamiento.

Referencia: https://dev.epicgames.com/documentation/unreal-engine/behavior-trees-in-unreal-engine

## 14.3. Navegación autónoma

- Búsqueda de rutas.
- Evitación de obstáculos.
- Seguimiento de rutas.
- Navegación por cuadrículas.
- Navegación por grafos.
- Navegación por mallas.
- Navegación con múltiples agentes.
- Planificación por coste.
- Replanificación.
- Movimiento en formaciones.
- Navegación en entornos dinámicos.

## 14.4. Autonomía y comportamiento emergente

- Necesidades.
- Rutinas.
- Objetivos propios.
- Prioridades.
- Competencia por recursos.
- Cooperación.
- Conflictos.
- Memoria.
- Aprendizaje de patrones.
- Respuestas contextuales.
- Comportamientos colectivos.
- Interacciones entre agentes.
- Reacciones en cadena.
- Adaptación a condiciones cambiantes.

## 14.5. Sistemas colectivos

- Enjambres.
- Grupos.
- Formación militar.
- Colonias.
- Ecosistemas.
- Sociedades simuladas.
- Redes de agentes.
- Producción colectiva.
- Reparto de tareas.
- Emergencia de jerarquías.
- Competencia entre poblaciones.

## 14.6. Referencias de implementación

Dos ejemplos técnicos útiles para futuras inspecciones son:

- **BehaviorTree.CPP:** https://github.com/BehaviorTree/BehaviorTree.CPP
- **libtcod:** https://github.com/libtcod/libtcod

libtcod ofrece algoritmos y herramientas utilizados en juegos de tipo roguelike, incluyendo pathfinding y campo de visión. Es una referencia concreta para estudiar capacidades delimitadas, reutilizables y separables de un motor gráfico completo.

No elegiremos estas bibliotecas para el proyecto todavía. La tarea actual es identificar qué necesitamos, no fijar prematuramente la arquitectura.

---

# PARTE XI. INTERACCIÓN SOCIAL, DIÁLOGO Y COOPERACIÓN

# 15. MECÁNICAS SOCIALES

## 15.1. Diálogo y relaciones

- Elección de diálogo.
- Preguntas.
- Respuestas condicionadas.
- Persuasión.
- Intimidación.
- Engaño.
- Negociación.
- Intercambio de favores.
- Regalos.
- Reputación.
- Confianza.
- Relaciones cambiantes.
- Recuerdos sociales.
- Información que se desbloquea mediante relaciones.
- Conflictos de intereses.
- Acuerdos que pueden romperse.

## 15.2. Información social

- Roles secretos.
- Objetivos ocultos.
- Información privada.
- Información compartida.
- Información falsa.
- Comunicación limitada.
- Señales.
- Votaciones.
- Acusaciones.
- Defensa pública.
- Identificación de impostores.
- Confianza condicionada.
- Información que solo un participante puede ver.

## 15.3. Cooperación

- Roles complementarios.
- Habilidades exclusivas.
- Recursos compartidos.
- Objetivos compartidos.
- Acciones simultáneas.
- Acciones que requieren varios participantes.
- Transferencia de control.
- Control compartido.
- Comunicación de planes.
- División de tareas.
- Dependencia entre participantes.

## 15.4. Asimetría

- Distintos personajes.
- Distintas perspectivas.
- Distintos controles.
- Distintas reglas.
- Información diferente.
- Escalas distintas de intervención.
- Objetivos diferentes.
- Recursos diferentes.
- Capacidades incompatibles.
- Roles que se transforman.
- Participantes que controlan entidades y otros que controlan sistemas.

## 15.5. Competición indirecta

- Carrera económica.
- Control de territorio.
- Subasta.
- Negociación.
- Influencia.
- Manipulación del mercado.
- Acumulación de recursos.
- Bloqueo de rutas.
- Competencia por objetivos.
- Interferencia entre sistemas.
- Control de información.

---

# PARTE XII. NARRATIVA, INVESTIGACIÓN Y RECUERDO

# 16. MECÁNICAS NARRATIVAS

## 16.1. Decisiones narrativas

- Elecciones ramificadas.
- Decisiones irreversibles.
- Decisiones con consecuencias diferidas.
- Acciones con consecuencias narrativas.
- Información que altera la interpretación.
- Objetivos opcionales.
- Finales múltiples.
- Relaciones condicionadas a decisiones.
- Decisiones que cambian el mundo, no solo el diálogo.

## 16.2. Narración reactiva

- Diálogo condicionado al estado.
- Personajes que recuerdan acciones.
- Narradores reactivos.
- Reacciones a desobedecer instrucciones.
- Historias emergentes de simulaciones.
- Eventos narrativos generados por reglas.
- Información contextual de acontecimientos.
- Reconstrucción de secuencias.
- Consecuencias narrativas de la forma de jugar.

## 16.3. Investigación narrativa

- Recopilar documentos.
- Examinar objetos.
- Comparar testimonios.
- Reconstruir cronologías.
- Relacionar personajes.
- Identificar mentiras.
- Establecer causalidad.
- Descubrir secretos.
- Cambiar hipótesis.
- Vincular evidencias y objetivos.

## 16.4. Narrativa que altera las mecánicas

- Información que desbloquea acciones.
- Diálogos que modifican reglas sociales.
- Descubrimientos que alteran la navegación.
- Decisiones que cambian la percepción.
- Narrativa que modifica la economía.
- Acontecimientos que transforman la escala de control.
- Identidad del personaje que afecta las interacciones.
- Narradores que reaccionan a las reglas del juego.

La biblioteca debe registrar estas relaciones como combinaciones de mecánicas. La historia es el contenido; las reglas por las que la historia responde al jugador son parte del sistema de interacción.

---

# PARTE XIII. GENERACIÓN PROCEDURAL Y SISTEMAS ADAPTATIVOS

# 17. MECÁNICAS DE GENERACIÓN

## 17.1. Generación de espacio

- Niveles generados.
- Mazmorras generadas.
- Mapas estratégicos.
- Terreno.
- Ciudades.
- Redes de transporte.
- Estructuras.
- Rutas.
- Habitaciones.
- Espacios conectados.
- Obstáculos.
- Recursos distribuidos proceduralmente.

## 17.2. Generación de contenido jugable

- Objetos.
- Enemigos.
- Equipamiento.
- Encuentros.
- Misiones.
- Puzles.
- Recompensas.
- Combinaciones de habilidades.
- Eventos.
- Desafíos.
- Secuencias.
- Reglas.
- Configuraciones de mundo.

## 17.3. Generación de comportamiento

- Variación de patrones.
- Reglas seleccionadas por procedimiento.
- Misiones condicionadas.
- Comportamientos de agentes.
- Eventos emergentes.
- Reacciones a estados del mundo.
- Historias generadas por sistemas.
- Cambios de dificultad.
- Adaptación a decisiones anteriores.

## 17.4. Adaptación a la partida

- Ajuste de dificultad.
- Ajuste de recursos.
- Modificación de objetivos.
- Modificación de patrones de enemigos.
- Variación de recompensas.
- Creación de desafíos.
- Cambio de rutas.
- Cambio de reglas.
- Generación condicionada al estilo de juego.
- Selección adaptativa de mecánicas.

## 17.5. Limitaciones que deben investigarse

La generación procedural requiere mucho más que producir variaciones. Hay que determinar:

- Qué propiedades debe respetar el contenido.
- Cómo se asegura que resulte jugable.
- Cómo se evalúan la dificultad y la coherencia.
- Cómo se evita que el contenido se vuelva repetitivo.
- Cómo se conservan la legibilidad y el equilibrio.
- Cómo se prueban las combinaciones producidas.
- Qué coste computacional implica la generación.
- Qué ocurre cuando se modifica el contenido durante la partida.

Los estudios de generación procedural serán una fuente separada para distinguir técnicas verificadas, ejemplos de aplicación y propuestas todavía experimentales.

---

# PARTE XIV. CONSTRUCCIÓN, AUTOMATIZACIÓN Y PROGRAMACIÓN

# 18. MECÁNICAS DE CREACIÓN DE SISTEMAS

## 18.1. Construcción

- Colocar piezas.
- Conectar componentes.
- Apilar estructuras.
- Construir instalaciones.
- Diseñar vehículos.
- Modificar terreno.
- Crear caminos.
- Establecer redes.
- Configurar mecanismos.
- Construir refugios.
- Construir defensas.
- Editar niveles.
- Crear herramientas.
- Diseñar entornos funcionales.

## 18.2. Automatización

- Cintas transportadoras.
- Sistemas de producción.
- Rutas automáticas.
- Clasificación de recursos.
- Sensores.
- Activadores.
- Puertas lógicas.
- Redes eléctricas.
- Distribución de energía.
- Condiciones de producción.
- Sistemas de mantenimiento.
- Reparación automática.
- Agentes que ejecutan tareas.
- Procesos encadenados.
- Bucles de fabricación.

## 18.3. Programación dentro del juego

- Secuencias de instrucciones.
- Comandos.
- Condicionales.
- Bucles.
- Eventos.
- Scripts.
- Programación visual.
- Programación de robots.
- Programación de NPC.
- Reglas ejecutables.
- Circuitos lógicos.
- Interfaces de configuración.
- Programación de comportamiento.
- Programación de una estrategia.
- Modificación de reglas mediante código.

## 18.4. Herramientas de creación para jugadores

- Editor de niveles.
- Editor de mapas.
- Editor de pistas.
- Editor de entidades.
- Editor de reglas.
- Editor de escenarios.
- Herramientas para compartir creaciones.
- Herramientas para probar creaciones.
- Validación automática.
- Reglas personalizadas.
- Modificaciones de contenido.
- Creación de nuevos modos.
- Generación de campañas comunitarias.

## 18.5. Riesgos de diseño

Las herramientas de creación pueden ampliar enormemente el espacio de posibilidades, pero también añaden necesidades de validación, legibilidad, estabilidad, compatibilidad y control del contenido creado.

La herramienta de creación es un sistema. Las acciones posibles dentro del editor son mecánicas de esa herramienta. El contenido creado puede activar otras mecánicas durante la partida.

---

# PARTE XV. INTERFACES, FEEDBACK Y PERCEPCIÓN SENSORIAL

# 19. MECÁNICAS DE RETROALIMENTACIÓN

## 19.1. Indicadores visuales

- Barras de salud.
- Indicadores de recursos.
- Contadores.
- Marcadores de objetivos.
- Indicadores de alcance.
- Señales de peligro.
- Mapas.
- Rutas.
- Retículas.
- Elementos resaltados.
- Previsualización de consecuencias.
- Representación de zonas de efecto.
- Líneas de trayectoria.
- Indicadores de estado.
- Iconos de intención de NPC.

## 19.2. Feedback audiovisual

- Sonido de confirmación.
- Sonido de error.
- Sonido de proximidad.
- Audio espacial.
- Indicadores visuales sincronizados.
- Vibración.
- Efectos de cámara.
- Reacciones de animación.
- Cambios musicales.
- Señales ambientales.
- Feedback diferenciado por entidad o sistema.
- Confirmación de interacción.
- Señales que indican cambios de modo.

## 19.3. Feedback sistémico

- Puntuación.
- Multiplicadores.
- Historial de acciones.
- Estadísticas.
- Comparación de resultados.
- Registro de acontecimientos.
- Explicación de errores.
- Indicadores de causa y efecto.
- Previsualización de una orden.
- Evaluación del resultado.
- Reproducción de una secuencia.
- Herramientas de depuración.
- Identificación de estados incompatibles.

## 19.4. Interfaz como parte del mundo

- Terminales.
- Paneles de control.
- Mapas diegéticos.
- Instrumentos físicos.
- Dispositivos simulados.
- Consolas de programación.
- Interfaces de investigación.
- Sistemas de comunicación ficticios.
- Ordenadores dentro del mundo.
- Interfaces controladas por otro personaje.
- Interfaces que cambian según el modo.

## 19.5. Diseño de información

- Mostrar todo.
- Revelar progresivamente.
- Ocultar información.
- Mostrar consecuencias antes de actuar.
- Ocultar probabilidades.
- Explicar causas.
- Enseñar mediante el entorno.
- Permitir inspección.
- Comparar alternativas.
- Presentar información mediante sonidos.
- Presentar información mediante cambios del mundo.
- Separar información táctica y narrativa.

---

# PARTE XVI. RIESGO, FRACASO Y RECUPERACIÓN

# 20. MECÁNICAS DE FALLA Y RIESGO

## 20.1. Estados de fracaso

- Perder salud.
- Perder un objeto.
- Perder recursos.
- Perder territorio.
- Perder una unidad.
- Ser detectado.
- Fallar una misión.
- Agotar el tiempo.
- Incumplir una condición.
- Perder reputación.
- Provocar consecuencias persistentes.
- Activar una condición irreversible.

## 20.2. Recuperación

- Reintentar.
- Reiniciar una sección.
- Restaurar un punto de control.
- Recuperar objetos.
- Recuperar recursos.
- Revivir.
- Ser rescatado.
- Reconstruir capacidades.
- Reparar estructuras.
- Reorganizar el equipo.
- Recuperar información.
- Modificar una estrategia fallida.

## 20.3. Muerte y reinicio

- Muerte con reinicio inmediato.
- Muerte con pérdida parcial.
- Muerte permanente.
- Resurrección condicionada.
- Reencarnación.
- Sustitución de personaje.
- Reinicio de una run.
- Progreso persistente entre runs.
- Recuperación de un cadáver o inventario.
- Transformación de la muerte en recurso o información.

## 20.4. Riesgo-recompensa

- Apostar recursos por una ventaja.
- Explorar una ruta peligrosa.
- Mantener recursos para el futuro.
- Sacrificar seguridad por velocidad.
- Permanecer más tiempo para obtener recompensas.
- Extraer antes de que aumente el peligro.
- Arriesgar una ventaja acumulada.
- Exponerse para obtener información.
- Aceptar una penalización por una recompensa mayor.

## 20.5. Consecuencias irreversibles

- Decisiones que bloquean rutas.
- Recursos que no pueden recuperarse.
- Relaciones alteradas permanentemente.
- Entidades que pueden perderse.
- Cambios irreversibles del entorno.
- Reglas que quedan fijadas.
- Destrucción de oportunidades futuras.
- Decisiones que afectan a otras escalas de juego.

---

# PARTE XVII. TRANSFORMACIONES ENTRE MECÁNICAS Y PARADIGMAS

# 21. MECÁNICAS DE TRANSICIÓN

Esta familia es especialmente importante para nuestro proyecto. No debe entenderse como un género separado, sino como un conjunto de mecanismos capaces de cambiar la forma de jugar durante una misma experiencia.

## 21.1. Cambio de entidad controlada

- Cambiar de personaje.
- Cambiar de vehículo.
- Cambiar de unidad.
- Cambiar de grupo.
- Cambiar de objeto.
- Controlar una entidad autónoma.
- Cambiar la entidad protagonista.
- Alternar entre varias entidades.
- Transferir el control a otro jugador.
- Compartir el control.

## 21.2. Cambio de escala

- Personaje a escuadrón.
- Escuadrón a ejército.
- Vehículo a red de transporte.
- Edificio a ciudad.
- Ciudad a región.
- Individuo a sociedad.
- Organismo a ecosistema.
- Objeto a sistema.
- Sistema a conjunto de sistemas.

## 21.3. Cambio de perspectiva

- Primera persona a tercera persona.
- Tercera persona a mapa táctico.
- Cámara a vista cenital.
- Mundo físico a diagrama.
- Entorno a terminal.
- Personaje a visión remota.
- Vista global a vista microscópica.
- Cámara libre a cámara guiada.
- Cambio entre varias perspectivas simultáneas.

## 21.4. Cambio de modelo de control

- Control directo a órdenes indirectas.
- Mando a ratón y teclado.
- Movimiento físico a comandos.
- Selección de entidades a programación.
- Control individual a coordinación colectiva.
- Movimiento a dibujo.
- Entrada manual a secuencia automatizada.
- Acción directa a negociación.
- Control remoto a intervención local.

## 21.5. Cambio de estructura temporal

- Tiempo real a turnos.
- Tiempo real a pausa táctica.
- Pausa a ejecución automática.
- Acciones individuales a secuencias.
- Simulación continua a simulación por pasos.
- Tiempo real a bucle temporal.
- Tiempo normal a tiempo ralentizado.
- Avance local a planificación global.

## 21.6. Cambio de reglas

- Física convencional a física alterada.
- Movimiento directo a movimiento por órdenes.
- Combate a negociación.
- Simulación a puzle lógico.
- Reglas fijas a reglas editables.
- Mundo destructible a mundo construible.
- Recursos abundantes a recursos escasos.
- Objetivos convencionales a objetivos generados.
- Personajes controlables a agentes autónomos.

## 21.7. Tipos de transición

- **Permanente:** el sistema cambia y permanece modificado.
- **Temporal:** el sistema cambia durante un intervalo.
- **Condicional:** el cambio ocurre al cumplirse una regla.
- **Controlada por el jugador:** el jugador decide cuándo cambiar.
- **Automática:** el sistema decide el momento.
- **Progresiva:** los cambios se introducen gradualmente.
- **Abrupta:** el cambio ocurre de manera inmediata.
- **Simultánea:** coexisten varios paradigmas.
- **Reversible:** se puede retornar al paradigma anterior.
- **Irreversible:** el cambio cierra la posibilidad de volver.
- **Aleatoria:** el sistema selecciona entre variantes.
- **Adaptativa:** la transición responde al comportamiento de los jugadores.

## 21.8. Continuidad entre modos

Cuando cambia un paradigma, debemos determinar qué componentes permanecen activos y cuáles se reinician.

Posibles componentes persistentes:

- Posiciones.
- Salud.
- Recursos.
- Inventarios.
- Entidades.
- Territorio.
- Relaciones.
- Información descubierta.
- Reglas.
- Objetivos.
- Consecuencias narrativas.
- Estado de las máquinas.
- Comportamientos autónomos.
- Historial de acciones.

También puede ocurrir que el modo nuevo convierta los datos anteriores en conceptos diferentes. Por ejemplo, los recursos obtenidos en un combate podrían representar capacidad productiva dentro de una vista de gestión.

## 21.9. Transiciones de paradigma experimental

- Acción a estrategia.
- Estrategia a acción.
- Simulación a puzle.
- Puzle a construcción.
- Investigación a ejecución.
- Exploración a competición.
- Combate a negociación.
- Gestión a movimiento físico.
- Programación a control directo.
- Narrativa a manipulación de reglas.
- Control individual a control colectivo.
- Cámara tridimensional a representación abstracta.
- Mundo persistente a escenario procedural.
- Reglas establecidas a reglas modificables.

Estas combinaciones son hipótesis de diseño. El objetivo será investigar si generan experiencias interesantes, cuáles son sus requisitos y qué precedentes parciales existen.

---

# PARTE XVIII. COMBINACIÓN Y ANÁLISIS SISTEMÁTICO

# 22. RELACIONES ENTRE MECÁNICAS

La biblioteca no debe limitarse a describir piezas individualmente. También debe registrar cómo interactúan.

## 22.1. Dependencia

Una mecánica necesita otra para funcionar.

Ejemplo: un sistema de fabricación necesita materiales, recetas, condiciones de producción y almacenamiento.

## 22.2. Complementariedad

Dos mecánicas aportan capacidades diferentes que se potencian.

Ejemplo: la observación permite identificar un objetivo y la planificación permite coordinar una intervención.

## 22.3. Competencia

Dos mecanismos compiten por el mismo recurso, espacio, tiempo o capacidad.

Ejemplo: dos habilidades consumen energía de una reserva compartida.

## 22.4. Sustitución

Dos mecánicas permiten resolver el mismo problema mediante procedimientos diferentes.

Ejemplo: entrar en una instalación mediante sigilo, negociación o combate.

## 22.5. Condicionamiento

Una mecánica modifica las condiciones bajo las cuales funciona otra.

Ejemplo: una regla temporal altera la velocidad de los objetos y, por tanto, el funcionamiento de un puzle físico.

## 22.6. Transformación

Una mecánica modifica la representación, las reglas o el propósito de otra.

Ejemplo: convertir una orden estratégica en una acción que el jugador debe ejecutar en primera persona.

## 22.7. Conflicto

Dos mecánicas producen resultados incompatibles o requieren reglas de prioridad.

Ejemplo: un objeto debe ser simultáneamente empujable y completamente inmóvil bajo condiciones diferentes.

## 22.8. Emergencia

Las interacciones entre mecánicas producen comportamientos que no están definidos como una única acción independiente.

Ejemplo: los agentes, recursos, rutas y condiciones ambientales pueden generar una crisis económica o un conflicto territorial sin una secuencia de eventos completamente predeterminada.

## 22.9. Reutilización de estados

Dos modos pueden compartir datos aunque interpreten sus significados de manera diferente.

Ejemplo: la propiedad de una región puede convertirse en un modificador de las acciones disponibles cuando el jugador entra físicamente en ella.

---

# 23. MATRIZ PARA INVESTIGAR COMBINACIONES

Cada combinación propuesta deberá registrarse como una hipótesis verificable.

| Campo | Pregunta |
|---|---|
| Mecánica A | ¿Cuál es el sistema de origen? |
| Mecánica B | ¿Cuál es el sistema con el que se combina? |
| Relación | ¿Dependencia, complementariedad, sustitución, transformación o conflicto? |
| Estado compartido | ¿Qué datos deben persistir entre ambas? |
| Cambio de control | ¿Qué acciones puede ejecutar el jugador antes y después? |
| Cambio de reglas | ¿Cuáles se conservan y cuáles se modifican? |
| Feedback | ¿Cómo entiende el jugador lo que ha cambiado? |
| Precedentes | ¿Qué juegos o prototipos presentan algo comparable? |
| Riesgos | ¿Qué puede volverse confuso, injusto o técnicamente costoso? |
| Experimento mínimo | ¿Qué debe implementarse para probar la hipótesis? |
| Evaluación | ¿Qué observaciones permitirán decidir si vale la pena continuar? |

---

# 24. MÉTODO DE EXPERIMENTACIÓN

## 24.1. Prototipos mínimos

Cada hipótesis importante deberá probarse con la cantidad mínima de sistemas necesaria para observar su comportamiento.

El primer prototipo no necesita arte final, contenido extenso ni una campaña completa. Debe permitir verificar la interacción que estamos investigando.

Ejemplos:

- Un personaje y un sistema de órdenes para evaluar el cambio entre control directo e indirecto.
- Un conjunto de reglas modificables para comprobar cómo cambia el comportamiento de las entidades.
- Una economía mínima para estudiar la transferencia de recursos entre dos modos.
- Un escenario físico para comprobar la interacción entre movimiento, gravedad y construcción.
- Dos jugadores con información diferente para evaluar cooperación asimétrica.

## 24.2. Variables de evaluación

- Comprensión de las reglas.
- Claridad del feedback.
- Capacidad de anticipar consecuencias.
- Número de decisiones significativas.
- Variedad de soluciones.
- Estabilidad de las transiciones.
- Sensación de control.
- Necesidad de aprender nuevos procedimientos.
- Repetición de estrategias.
- Comportamientos emergentes.
- Coste técnico.
- Rendimiento medido.
- Dificultad de ampliar el sistema.
- Compatibilidad con otros paradigmas.

## 24.3. Separar hipótesis de resultados

Antes de probar un prototipo, se registrará qué esperamos que suceda.

Después, se documentará lo que realmente sucede.

Una combinación no se considerará exitosa simplemente porque su descripción resulte atractiva. Debe evaluarse en ejecución, identificando también los efectos secundarios, los problemas de comprensión y las condiciones bajo las cuales deja de funcionar.

---

# 25. REFERENCIAS Y RECURSOS DE INVESTIGACIÓN

Las siguientes fuentes fundamentan la clasificación inicial y servirán como referencias para futuras fichas.

## Fundamentos de diseño y análisis

**Sicart, Miguel. *Defining Game Mechanics*. Game Studies, 2008.**

https://gamestudies.org/0802/articles/sicart

Definición y análisis formal de mecánicas, agentes, acciones y estado del juego.

**Hunicke, Robin; LeBlanc, Marc; Zubek, Robert. *MDA: A Formal Approach to Game Design and Game Research*.**

https://www.cs.northwestern.edu/~hunicke/MDA.pdf

Relación entre mecánicas, dinámicas y experiencias.

**Zagal, José P. y colaboradores. *Towards an Ontological Language for Game Analysis*. DiGRA, 2005.**

https://dl.digra.org/index.php/dl/article/view/136

Marco para describir componentes estructurales y relaciones entre elementos de videojuegos.

**Björk, Staffan; Holopainen, Jussi. *Patterns in Game Design*.**

https://www.researchgate.net/publication/236157130_Patterns_in_Game_Design

Referencia para investigar patrones de interacción y sus relaciones con el diseño.

## Recursos, economías y generación

**Machinations — Framework Basics.**

https://machinations.io/docs/framework-basics

Modelado de recursos, flujos, transformaciones e interacciones entre estados.

**Hendrikx y colaboradores. *Procedural Content Generation for Games: A Survey*.**

https://doi.org/10.1145/2422956.2422957

Taxonomía y métodos para la generación procedural de contenido.

**Farrokhi Maleki y Zhao. *Procedural Content Generation in Games: A Survey with Insights on Emerging LLM Integration*.**

https://ojs.aaai.org/index.php/AIIDE/article/view/31877

Comparación de métodos de generación procedural, incluidos enfoques basados en búsqueda, aprendizaje automático y modelos de lenguaje.

## Documentación técnica y repositorios

**Godot Engine — Input handling.**

https://docs.godotengine.org/en/stable/tutorials/inputs/index.html

Entradas, eventos y dispositivos de control.

**Godot Engine — Physics.**

https://docs.godotengine.org/en/stable/tutorials/physics/physics_introduction.html

Detección de colisiones, respuesta física y objetos de colisión.

**Godot Engine — Navigation.**

https://docs.godotengine.org/en/stable/tutorials/navigation/

Navegación, rutas, agentes y obstáculos.

**Godot Engine — AnimationTree.**

https://docs.godotengine.org/en/stable/tutorials/animation/animation_tree.html

Mezcla de animaciones, transiciones y máquinas de estados de animación.

**Godot Engine — Audio.**

https://docs.godotengine.org/en/stable/tutorials/audio/index.html

Buses de audio, efectos, sincronización con música y captura de micrófono.

Estas fuentes se utilizan como ejemplos de subsistemas técnicos disponibles en una implementación real; no implican que Godot vaya a ser el motor elegido.

**BehaviorTree.CPP.**

https://github.com/BehaviorTree/BehaviorTree.CPP

Biblioteca abierta para estudiar implementaciones de árboles de comportamiento, ejecución de acciones, concurrencia y herramientas de observabilidad.

**libtcod.**

https://github.com/libtcod/libtcod

Biblioteca abierta para estudiar algoritmos de campo de visión, pathfinding y herramientas de desarrollo de roguelikes.

Los repositorios se deben inspeccionar en su código, documentación, pruebas, licencia y actividad antes de decidir si son reutilizables.

---

# 26. CONCLUSIÓN

Esta biblioteca proporciona una primera estructura para estudiar los componentes que hacen posibles distintas formas de jugar.

Su valor no reside en cerrar una lista definitiva de mecánicas. Reside en ofrecer un lenguaje común para describir acciones, reglas, recursos, estados, información, comportamientos autónomos y transformaciones entre sistemas.

A partir de esta base, cada nuevo juego estudiado podrá aportar entradas, variantes y relaciones adicionales.

La siguiente fase deberá profundizar en casos concretos: seleccionar videojuegos representativos, estudiar sus mecánicas en funcionamiento, contrastar sus reglas con documentación y código cuando exista, y registrar qué sistemas hacen falta para implementarlas.

Después se podrá construir una matriz de combinaciones que relacione las mecánicas documentadas, sus dependencias y los experimentos mínimos necesarios para explorar nuevas experiencias.

**Criterio rector del proyecto:** investigar las piezas con rigor, comprender cómo interactúan y experimentar con sus combinaciones antes de decidir qué videojuego construir.