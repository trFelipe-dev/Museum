# Plan de pruebas y aceptación

## Tipos de prueba
1. Instalación y compilación.
2. Renderizado e inicialización.
3. Navegación y colisiones.
4. Interacción con placas y fichas.
5. Integridad de contenido y fuentes.
6. Controles táctiles y orientación.
7. NPCs y diálogos.
8. Audio, subtítulos y controles.
9. Rendimiento y memoria.
10. Compatibilidad y despliegue.

## Pruebas mínimas del recorrido
- Abrir la aplicación y completar la carga inicial.
- Iniciar en el vestíbulo.
- Llegar al núcleo y entrar en cada sala.
- Visitar las nueve exposiciones.
- Abrir y cerrar cada ficha.
- Verificar correspondencia entre placa, imagen y datos.
- Llegar al espacio de reflexión/salida.
- Confirmar que no se atraviesan paredes ni se queda bloqueado el jugador.

## Objetivos de rendimiento
El diseño técnico plantea aproximadamente 60 FPS en computadoras compatibles y 30 FPS estables en móviles de gama media. Son metas a validar, no garantías universales. Registrar dispositivo, navegador, perfil gráfico, escena y método de medición.

## Matriz de dispositivos
Pendiente de completar con los dispositivos reales disponibles. Registrar modelo, sistema operativo, navegador, resolución, orientación y resultado.

## Severidad de errores
- Bloqueante: impide iniciar, recorrer, consultar la colección o publicar.
- Alta: rompe una función central o afecta a varios dispositivos.
- Media: afecta una función secundaria con alternativa disponible.
- Baja: defecto visual o de contenido sin impedir la experiencia.

## Cierre de versión
No aprobar release con errores bloqueantes abiertos. Los errores altos deben corregirse o aceptarse explícitamente por el equipo con justificación y limitación documentada.
