# Fases de desarrollo

## Fase 1 — Organización y planificación
**Objetivo:** preparar equipo, alcance, documentación y gestión.  
**Incluye:** revisión documental, alcance, requisitos, responsabilidades, GitHub, flujo Git, riesgos y calendario.  
**Salida:** equipo conoce qué debe construir, cómo colaborar y cómo se aceptará el trabajo.

## Fase 2 — Investigación y preparación de recursos
**Objetivo:** obtener contenido verificable y recursos adecuados.  
**Incluye:** investigación de nueve equipos, fuentes, imágenes, fichas, licencias/uso, convenciones y organización de assets.  
**Salida:** contenido revisado y recursos con procedencia documentada.

## Fase 3 — Configuración y prototipo técnico
**Objetivo:** tener una aplicación 3D modular y ejecutable.  
**Incluye:** Vite, Three.js, JavaScript ES Modules, Rapier 3D, estructura, escena, cámara, ciclo de renderizado, movimiento desktop y colisiones.  
**Salida:** visitante puede desplazarse en un espacio de prueba en computadora.

## Fase 4 — Prototipo museográfico y multiplataforma
**Objetivo:** validar una experiencia completa pequeña.  
**Incluye:** controles táctiles, una sala piloto, una exposición, marco, placa, ficha de tres niveles, interacción y un NPC de prueba.  
**Salida:** una sección representativa funciona de principio a fin; se valida en escritorio y móvil objetivo.

## Fase 5 — Construcción arquitectónica
**Objetivo:** crear el recorrido espacial completo.  
**Incluye:** vestíbulo, núcleo, tres salas, espacio de reflexión/salida, circulación, señalización, materiales, iluminación y colisiones.  
**Salida:** recorrido completo, comprensible y sin bloqueos.

## Fase 6 — Integración de la colección
**Objetivo:** incorporar las nueve computadoras.  
**Incluye:** datos JSON, imágenes, marcos, placas, fichas, referencias y control de calidad del contenido.  
**Salida:** las nueve piezas se pueden consultar y la información tiene fuentes.

## Fase 7 — NPCs e interacciones
**Objetivo:** poblar el museo con siete visitantes autónomos.  
**Incluye:** dos entusiastas, tres visitantes casuales, dos historiadores; rutas, puntos de interés, estados WALKING, OBSERVING, READING, TALKING, REACTING e IDLE.  
**Salida:** personajes realizan los comportamientos esenciales sin bloquear el recorrido.

## Fase 8 — Ambientación sonora y accesibilidad
**Objetivo:** completar ambiente y alternativas de acceso a la información.  
**Incluye:** ambiente sonoro, pasos, efectos, conversaciones cuando proceda, subtítulos, volumen/silencio, contraste y legibilidad.  
**Salida:** sonido controlable y contenido importante disponible también en texto.

## Fase 9 — Integración, optimización y pruebas
**Objetivo:** estabilizar y validar la aplicación completa.  
**Incluye:** integración, perfiles Alto/Equilibrado/Rendimiento, optimización, carga progresiva, pruebas funcionales, rendimiento, compatibilidad y correcciones.  
**Salida:** versión candidata que cumple los criterios acordados en los dispositivos de prueba.

## Fase 10 — Publicación y entrega
**Objetivo:** publicar y entregar el museo.  
**Incluye:** build de producción, Vite base path, GitHub Actions, GitHub Pages, smoke test, documentación y presentación.  
**Salida:** enlace público verificado y repositorio actualizado.

## Regla de solapamiento
Las fases no son necesariamente secuenciales al 100 %. Investigación (Fase 2), documentación y preparación de assets pueden avanzar mientras se desarrolla el prototipo técnico. La expansión de arquitectura y colección debe respetar las dependencias del prototipo.
