# Diseño técnico
## Museo virtual: La Evolución de la Computadora Personal (2005–2013)

**Archivo:** `docs/05-technical-design.md`  
**Estado:** Diseño técnico inicial aprobado  
**Versión:** 1.0

---

## 1. Introducción

Este documento establece la arquitectura técnica, las tecnologías, los requisitos funcionales y no funcionales, los criterios de rendimiento y el plan de implementación del proyecto **La Evolución de la Computadora Personal (2005–2013)**.

El proyecto consiste en desarrollar un museo virtual tridimensional accesible desde navegadores web, en el que los visitantes puedan recorrer diferentes espacios, observar exposiciones, consultar información histórica e interactuar con personajes virtuales.

La experiencia estará diseñada para computadoras, tabletas y dispositivos móviles, manteniendo una perspectiva en primera persona y adaptando los controles y la calidad gráfica a las capacidades de cada dispositivo.

## 2. Objetivos técnicos

- Desarrollar una experiencia 3D interactiva que funcione desde un navegador web.
- Permitir la navegación en primera persona mediante controles de escritorio y táctiles.
- Garantizar una experiencia adaptable a computadoras y dispositivos móviles de gama media.
- Implementar colisiones para evitar que el visitante atraviese paredes y elementos arquitectónicos.
- Incorporar exposiciones interactivas con información organizada en diferentes niveles.
- Implementar siete personajes virtuales (NPCs) con comportamientos autónomos.
- Optimizar los recursos gráficos y sonoros para mantener un rendimiento estable.
- Facilitar el mantenimiento y la ampliación del proyecto mediante una arquitectura modular.
- Publicar el museo como una aplicación web accesible mediante un enlace.

## 3. Plataformas y compatibilidad

### 3.1. Dispositivos objetivo

El museo estará disponible para:

- Computadoras de escritorio y portátiles.
- Tabletas.
- Teléfonos inteligentes de gama media de los últimos años y dispositivos superiores.

Los dispositivos de gama baja no constituyen el objetivo mínimo de compatibilidad de la primera versión.

### 3.2. Navegadores

Se buscará compatibilidad con versiones recientes de:

- Google Chrome.
- Microsoft Edge.
- Mozilla Firefox.
- Safari.

La compatibilidad deberá comprobarse mediante pruebas reales, especialmente en Safari para dispositivos Apple y navegadores móviles.

### 3.3. Orientación de dispositivos móviles

La experiencia móvil estará diseñada para orientación horizontal (landscape).

Cuando el visitante acceda desde un dispositivo en orientación vertical, se mostrará un aviso visual que recomendará girar el dispositivo.

No se bloqueará físicamente la orientación del dispositivo.

### 3.4. Comprobación inicial de compatibilidad

Antes de iniciar el recorrido, el sistema deberá comprobar:

- Disponibilidad de WebGL.
- Capacidad de inicialización del renderizador.
- Disponibilidad de los recursos esenciales.
- Tamaño y características básicas de la pantalla.
- Capacidad aproximada del dispositivo para seleccionar un perfil gráfico.

Si el navegador no puede ejecutar la experiencia, se mostrará un mensaje explicativo y no una pantalla vacía.

## 4. Tecnologías y herramientas

### 4.1. Tecnologías principales

| Tecnología | Función |
|---|---|
| Three.js | Motor de renderizado y gestión de escenas 3D |
| Vite | Entorno de desarrollo y compilación |
| JavaScript ES Modules | Lógica y organización del código |
| HTML5 | Estructura de la interfaz |
| CSS3 | Estilos y adaptación visual |
| Rapier 3D | Física, colisiones y controlador del visitante |
| JSON | Almacenamiento de información de exposiciones y diálogos |
| Git | Control de versiones |
| GitHub | Repositorio, documentación y seguimiento |

### 4.2. Herramientas complementarias

| Herramienta | Uso |
|---|---|
| Blender | Creación de arquitectura, marcos, placas y personajes 3D |
| GitHub Actions | Automatización de comprobaciones y publicación |
| Playwright | Pruebas automatizadas de navegador en etapas posteriores |

No todas las herramientas se incorporarán desde el primer momento. Se integrarán progresivamente según las necesidades de cada etapa.

### 4.3. Tecnologías descartadas inicialmente

Para mantener una arquitectura sencilla y reducir la curva de aprendizaje:

- No se utilizará React en la primera versión.
- No se implementará TypeScript inicialmente.
- No se incorporará un backend.
- No se utilizará una base de datos externa.
- No se implementará inteligencia artificial conversacional para los NPCs.

Estas tecnologías podrán evaluarse en futuras versiones si aparecen necesidades concretas que justifiquen su incorporación.

## 5. Arquitectura general del sistema

El proyecto utilizará una arquitectura modular basada en JavaScript ES Modules.

Cada módulo tendrá responsabilidades específicas y se comunicará con los demás mediante interfaces definidas.

### 5.1. Organización de carpetas

```text
museo-computadoras/
├── README.md
├── package.json
├── package-lock.json
├── index.html
├── vite.config.js
│
├── docs/
│
├── public/
│   └── assets/
│       ├── images/
│       ├── models/
│       ├── textures/
│       ├── audio/
│       └── fonts/
│
├── src/
│   ├── main.js
│   │
│   ├── core/
│   ├── museum/
│   ├── player/
│   ├── exhibits/
│   ├── npcs/
│   ├── systems/
│   ├── ui/
│   ├── data/
│   └── styles/
│
└── .github/
    ├── ISSUE_TEMPLATE/
    └── workflows/
```

### 5.2. Responsabilidades de los módulos

| Módulo | Responsabilidad |
|---|---|
| `core` | Inicialización del proyecto, escena, cámara y renderizador |
| `museum` | Arquitectura, vestíbulo, núcleo central y salas |
| `player` | Movimiento, cámara, controles y colisiones del visitante |
| `exhibits` | Exposiciones, retratos, marcos, placas y fichas |
| `npcs` | Personajes, animaciones, rutas y comportamientos |
| `systems` | Audio, carga de recursos, rendimiento e interacciones generales |
| `ui` | Menús, ventanas, avisos, controles táctiles y diálogos |
| `data` | Datos JSON de las computadoras y conversaciones |
| `styles` | Estilos de la interfaz |

La estructura podrá ampliarse conforme aparezcan nuevas necesidades, evitando crear módulos innecesarios antes de tiempo.

## 6. Renderizado y escenas 3D

### 6.1. Motor gráfico

Se utilizará Three.js con `WebGLRenderer` como sistema principal de renderizado.

La elección de WebGL prioriza la compatibilidad con los navegadores y dispositivos objetivo.

### 6.2. Escenas

El entorno se organizará alrededor de los espacios principales:

1. Vestíbulo de entrada.
2. Núcleo central con instalación cronológica.
3. Sala I: La computadora se redefine (2005–2007).
4. Sala II: La movilidad se transforma (2008–2010).
5. Sala III: Identidad, diseño y nuevas plataformas (2011–2013).
6. Espacio de reflexión y salida.

Las salas y sus recursos se organizarán de forma modular para facilitar su construcción y carga.

### 6.3. Iluminación

Se utilizará una combinación de:

- Iluminación ambiental controlada.
- Luces focales sobre las exposiciones.
- Sombras selectivas.
- Iluminación precalculada (baking) cuando resulte conveniente.

La iluminación deberá conservar la estética museográfica minimalista, evitando efectos gráficos innecesariamente costosos.

## 7. Navegación y controles del visitante

### 7.1. Perspectiva

La navegación será en primera persona estricta tanto en computadoras como en dispositivos móviles.

El visitante observará el entorno desde la perspectiva del personaje y no podrá cambiar a una cámara en tercera persona.

### 7.2. Controles de computadora

| Acción | Control |
|---|---|
| Avanzar | W |
| Retroceder | S |
| Desplazarse a la izquierda | A |
| Desplazarse a la derecha | D |
| Mirar alrededor | Ratón |
| Interactuar | E o clic |
| Cerrar ficha o diálogo | Escape |
| Liberar el ratón | Escape |

Se utilizará Pointer Lock API cuando esté disponible y permitido por el navegador.

Como alternativa se permitirá controlar la cámara mediante arrastre del ratón.

### 7.3. Controles móviles

| Acción | Control |
|---|---|
| Desplazamiento | Joystick virtual izquierdo |
| Mirar alrededor | Deslizar el dedo en la zona derecha |
| Interactuar | Botón contextual |
| Cerrar ficha o diálogo | Botón de cierre |

Los controles táctiles deberán ser suficientemente grandes, visibles y estar separados para evitar interacciones accidentales.

### 7.4. Sistema de movimiento

El visitante contará con:

- Movimiento en primera persona.
- Rotación horizontal y vertical de cámara.
- Detección de colisiones.
- Restricciones para evitar atravesar paredes y objetos sólidos.
- Velocidad de movimiento controlada.
- Comportamiento consistente entre escritorio y dispositivos táctiles.

Se utilizará Rapier 3D para gestionar la física necesaria y un controlador cinemático para el movimiento del personaje.

El movimiento no deberá depender de la frecuencia de fotogramas.

## 8. Sistema de exposiciones e interacciones

### 8.1. Presentación de las computadoras

Las nueve computadoras se presentarán mediante imágenes planas integradas en marcos tridimensionales.

No se desarrollarán modelos 3D completos de cada computadora para la primera versión.

Los marcos, placas y elementos arquitectónicos sí serán objetos tridimensionales.

### 8.2. Interacción con las exposiciones

El visitante podrá acercarse a una exposición y activar su ficha informativa mediante el botón correspondiente.

Se utilizará Raycaster de Three.js para detectar la selección de placas y elementos interactivos.

### 8.3. Estructura de las fichas

Cada exposición tendrá tres niveles de información:

1. **Identificación:** nombre del equipo, fabricante y año.
2. **Especificaciones técnicas:** características principales verificadas.
3. **Contexto histórico:** importancia del equipo, tendencias de la época y relación con la evolución de la computadora personal.

La información se almacenará en archivos JSON para facilitar su edición y ampliación.

Los datos técnicos deberán verificarse mediante fuentes documentales confiables antes de incorporarse a la versión definitiva.

## 9. Sistema de NPCs

### 9.1. Cantidad

Se implementarán siete NPCs:

- Dos entusiastas de tecnología.
- Tres visitantes casuales.
- Dos historiadores tecnológicos.

Los siete personajes deberán estar presentes tanto en computadoras como en dispositivos móviles.

### 9.2. Comportamiento

Los personajes tendrán comportamientos autónomos y podrán:

- Caminar hacia exposiciones.
- Detenerse y observar.
- Leer placas.
- Conversar entre ellos.
- Reaccionar ante la proximidad del visitante.
- Reanudar su recorrido.

### 9.3. Arquitectura de comportamiento

Se utilizará un sistema de máquinas de estados finitos (Finite State Machine).

Los estados iniciales serán:

- `WALKING`
- `OBSERVING`
- `READING`
- `TALKING`
- `REACTING`
- `IDLE`

El desplazamiento se realizará mediante rutas y puntos de interés definidos en el escenario.

Se evitará implementar simulaciones complejas o sistemas de inteligencia artificial que no sean necesarios para la experiencia.

### 9.4. Optimización

Los siete NPCs estarán presentes en móviles, pero se podrán aplicar optimizaciones como:

- Reducción de la frecuencia de actualización de personajes alejados.
- Menor complejidad de sombras.
- Simplificación de materiales.
- Reducción de detalles geométricos.
- Actualización de animaciones según la distancia a la cámara.

El objetivo es conservar la sensación de un museo activo sin comprometer el rendimiento.

## 10. Rendimiento y optimización gráfica

### 10.1. Objetivos

Se establecen los siguientes objetivos iniciales:

| Dispositivo | Objetivo |
|---|---|
| Computadoras compatibles | Aproximadamente 60 FPS |
| Móviles de gama media compatibles | Aproximadamente 30 FPS estables |

Estos valores son metas de desarrollo que deberán comprobarse mediante pruebas reales.

### 10.2. Perfiles gráficos

El sistema tendrá tres perfiles:

**Alto**
- Mayor calidad de sombras.
- Mayor resolución de renderizado.
- Mayor calidad de efectos gráficos.

**Equilibrado**
- Calidad visual y rendimiento balanceados.
- Configuración predeterminada.
- Sombras y efectos selectivos.

**Rendimiento**
- Resolución interna reducida.
- Sombras simplificadas.
- Menor complejidad de efectos.
- Reducción de cálculos gráficos secundarios.

El perfil se seleccionará inicialmente según la capacidad estimada del dispositivo, pero el visitante podrá modificarlo manualmente.

### 10.3. Técnicas de optimización

- Controlar el pixel ratio del renderizador.
- Limitar la resolución interna cuando sea necesario.
- Reutilizar geometrías y materiales.
- Evitar luces y sombras innecesarias.
- Optimizar texturas.
- Utilizar niveles de detalle cuando aporten beneficios.
- Reducir cálculos de animación para elementos lejanos.
- Evitar cargas simultáneas de grandes cantidades de recursos.

## 11. Gestión y carga de recursos

### 11.1. Formatos

| Recurso | Formato |
|---|---|
| Modelos 3D | GLB |
| Imágenes | WebP |
| Texturas | WebP inicialmente |
| Audio | OGG o MP3 |
| Información | JSON |
| Fuentes | Formatos compatibles con navegadores |

Se evaluarán formatos de texturas comprimidas para GPU si las pruebas de rendimiento lo justifican.

### 11.2. Carga progresiva

El museo utilizará una estrategia de carga progresiva:

1. Cargar la interfaz y los recursos esenciales.
2. Inicializar el entorno básico.
3. Cargar el vestíbulo y el núcleo central.
4. Preparar la sala próxima al visitante.
5. Cargar progresivamente los recursos de las demás salas.
6. Liberar recursos que ya no sean necesarios, evitando eliminar elementos que todavía estén en uso.

La experiencia deberá informar visualmente cuando se encuentre cargando recursos importantes.

### 11.3. Gestión de modelos

Se utilizará `GLTFLoader` para cargar modelos GLB.

Las animaciones de los personajes se gestionarán mediante `AnimationMixer` de Three.js.

## 12. Audio y ambiente

El museo contará con:

- Ambiente sonoro espacializado.
- Sonido de pasos con reverberación leve.
- Murmullos y conversaciones discretas.
- Efectos breves al interactuar con exposiciones.
- Sonidos ambientales asociados a los espacios.

Se utilizarán las herramientas de audio de Three.js, incluyendo `PositionalAudio` cuando corresponda.

La reproducción de audio se activará después de una interacción del visitante, respetando las restricciones de reproducción automática de los navegadores.

La interfaz incluirá controles para regular el volumen y silenciar el audio.

La información importante siempre estará disponible mediante texto.

## 13. Interfaz y experiencia de usuario

La interfaz será minimalista y coherente con la identidad visual del museo.

Incluirá:

- Pantalla inicial.
- Comprobación de compatibilidad.
- Aviso de orientación móvil.
- Indicaciones de controles.
- Indicadores de interacción.
- Fichas informativas.
- Ventanas de diálogo.
- Controles de audio.
- Menú de pausa o configuración.

La interfaz deberá adaptarse a diferentes tamaños de pantalla sin cubrir innecesariamente el espacio visual de la exposición.

## 14. Almacenamiento y privacidad

La primera versión no requerirá:

- Registro de usuarios.
- Cuentas.
- Contraseñas.
- Base de datos externa.
- Servidor propio.

La información de las exposiciones y diálogos se almacenará en archivos JSON.

Opcionalmente se podrán guardar preferencias locales, como el volumen o el perfil gráfico.

No se incorporarán herramientas de analítica ni seguimiento de visitantes en la primera versión.

## 15. Pruebas y control de calidad

### 15.1. Pruebas funcionales

Se comprobará:

- Inicialización correcta del museo.
- Movimiento del visitante.
- Rotación de cámara.
- Colisiones.
- Controles táctiles.
- Interacción con placas.
- Apertura y cierre de fichas.
- Conversaciones con NPCs.
- Comportamiento autónomo de personajes.
- Reproducción y control de audio.
- Carga de modelos e imágenes.

### 15.2. Pruebas de rendimiento

Se medirán:

- FPS.
- Tiempo de carga inicial.
- Tiempo de carga de las salas.
- Uso de memoria.
- Comportamiento con los siete NPCs activos.
- Estabilidad durante recorridos prolongados.

### 15.3. Pruebas de compatibilidad

Se probará el museo en:

- Computadoras de escritorio.
- Portátiles.
- Teléfonos Android de gama media.
- Dispositivos Apple compatibles.
- Diferentes tamaños y resoluciones de pantalla.

Las pruebas automatizadas de navegador podrán incorporarse mediante Playwright en etapas posteriores.

## 16. Publicación y despliegue

El museo se publicará inicialmente mediante GitHub Pages.

Se utilizará Vite para generar la versión de producción.

El flujo de publicación será:

1. Desarrollo y pruebas locales.
2. Integración de cambios en la rama principal.
3. Compilación del proyecto.
4. Comprobación de errores de compilación.
5. Publicación automática mediante GitHub Actions.
6. Verificación de la versión publicada.

El proyecto deberá configurarse correctamente para la ruta de GitHub Pages mediante la propiedad `base` de Vite cuando corresponda.

El museo deberá ejecutarse desde HTTP o HTTPS y no depender de abrir directamente el archivo `index.html` desde el sistema de archivos.

## 17. Plan de implementación

El desarrollo se dividirá en ocho hitos.

### Hito 1. Preparación y prototipo técnico

- Configuración de Vite y Three.js.
- Estructura inicial del proyecto.
- Inicialización de escena y cámara.
- Movimiento en primera persona.
- Prueba de colisiones.

**Resultado esperado:** un visitante puede desplazarse por un espacio 3D en computadora.

### Hito 2. Prototipo multiplataforma

- Joystick virtual.
- Control táctil de cámara.
- Botones de interacción.
- Aviso de orientación.
- Pruebas en móviles de gama media.

**Resultado esperado:** el mismo espacio funciona en computadora y móvil.

### Hito 3. Prototipo museográfico

- Una sala de prueba.
- Una computadora de la colección.
- Retrato enmarcado.
- Placa interactiva.
- Ficha de tres niveles.
- Un NPC funcional.

**Resultado esperado:** una experiencia representativa del museo final.

### Hito 4. Construcción arquitectónica

- Vestíbulo.
- Núcleo central.
- Tres salas.
- Espacio de reflexión y salida.
- Materiales e iluminación.
- Señalización.

**Resultado esperado:** recorrido completo y navegable.

### Hito 5. Integración de la colección

- Incorporación de las nueve computadoras.
- Imágenes y marcos.
- Placas informativas.
- Fichas técnicas.
- Contexto histórico.
- Verificación de fuentes.

**Resultado esperado:** colección completa y consultable.

### Hito 6. NPCs y ambiente

- Incorporación de los siete personajes.
- Rutas y estados de comportamiento.
- Conversaciones e interacciones.
- Audio ambiental.
- Efectos sonoros.

**Resultado esperado:** museo habitado y con ambiente sonoro.

### Hito 7. Optimización y pruebas

- Perfiles gráficos.
- Optimización de modelos y texturas.
- Carga progresiva.
- Pruebas en dispositivos reales.
- Corrección de errores.
- Verificación de objetivos de rendimiento.

**Resultado esperado:** versión candidata a publicación.

### Hito 8. Publicación

- Configuración de GitHub Actions.
- Compilación de producción.
- Configuración de GitHub Pages.
- Pruebas de la versión publicada.
- Documentación de acceso.

**Resultado esperado:** museo disponible mediante un enlace web público.

## 18. Criterios de aceptación

El proyecto se considerará técnicamente funcional cuando cumpla los siguientes criterios:

| Área | Criterio |
|---|---|
| Navegación | El visitante puede completar el recorrido sin atravesar paredes ni quedar atrapado |
| Computadora | Los controles de teclado y ratón funcionan correctamente |
| Móvil | El recorrido puede realizarse con controles táctiles |
| Orientación | Se muestra el aviso cuando el dispositivo está en vertical |
| Cámara | Se mantiene la primera persona en todas las plataformas |
| Exposiciones | Las nueve computadoras tienen imagen e información consultable |
| Información | Las especificaciones y datos históricos tienen fuentes verificables |
| NPCs | Los siete personajes están presentes y ejecutan comportamientos autónomos |
| Interacciones | Las placas y conversaciones responden correctamente |
| Audio | Se puede activar, regular y silenciar |
| Rendimiento | Se alcanzan los objetivos establecidos en los dispositivos de prueba acordados |
| Compatibilidad | La experiencia funciona en los navegadores objetivo |
| Publicación | El museo se puede abrir mediante un enlace web público |

## 19. Decisiones técnicas consolidadas

Las siguientes decisiones constituyen la base técnica aprobada para la primera versión:

| Aspecto | Decisión |
|---|---|
| Plataforma | Aplicación web 3D |
| Dispositivos | Computadoras, tabletas y móviles |
| Móvil mínimo | Gama media |
| Orientación móvil | Horizontal |
| Perspectiva | Primera persona estricta |
| NPCs en móviles | Los siete personajes |
| Motor 3D | Three.js |
| Renderizado | WebGL |
| Entorno de desarrollo | Vite |
| Lenguaje | JavaScript ES Modules |
| Física | Rapier 3D |
| Modelos | GLB |
| Imágenes | WebP |
| Datos | JSON |
| Interfaz | HTML y CSS |
| Backend | No requerido inicialmente |
| Base de datos | No requerida inicialmente |
| Publicación | GitHub Pages |
| Calidad gráfica | Adaptable según capacidad |
| Objetivo de rendimiento | 60 FPS en computadoras compatibles y 30 FPS en móviles compatibles |

## 20. Aspectos pendientes de validación

Aunque la arquitectura inicial está definida, algunos parámetros deberán confirmarse mediante el prototipo:

- Dispositivos móviles concretos que se utilizarán como referencia.
- Resoluciones internas óptimas para cada perfil gráfico.
- Calidad y resolución máxima de texturas.
- Cantidad y complejidad de luces por sala.
- Presupuesto de memoria.
- Tiempos aceptables de carga inicial y de cada sala.
- Complejidad final de los modelos y animaciones de NPCs.
- Rendimiento real con todos los recursos activos.

Estos aspectos no impiden comenzar el desarrollo. Se documentarán y ajustarán durante las pruebas.

---

**Fin del documento.**
