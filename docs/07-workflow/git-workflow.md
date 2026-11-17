# Flujo de trabajo Git y GitHub

## Ramas
- `main`: versión estable; no trabajar directamente sobre ella.
- Rama por Issue o funcionalidad: `feature/<id>-descripcion`, `fix/<id>-descripcion`, `docs/<id>-descripcion`.
- No es obligatorio crear `develop`; usarlo solo si el equipo lo acuerda y puede mantenerlo.

## Flujo
1. Elegir una Issue asignada y comprobar dependencias.
2. Actualizar `main`.
3. Crear rama desde `main`.
4. Implementar solo el alcance de la Issue.
5. Ejecutar pruebas locales y revisar cambios.
6. Crear commits descriptivos.
7. Publicar la rama.
8. Abrir Pull Request y vincular Issue con `Closes #NUMERO`.
9. Solicitar revisión a otro integrante.
10. Corregir observaciones y ejecutar comprobaciones.
11. Integrar mediante PR.
12. Verificar `main` y cerrar Issue tras comprobar criterios.

## Convención de nombres
- `feature/TEC-009-movimiento-player`
- `fix/QA-008-colision-sala`
- `docs/RES-001-plantilla-investigacion`

## Commits
Usar mensajes breves y descriptivos:
- `feat: implementar movimiento en primera persona`
- `fix: corregir colision con muro`
- `docs: agregar fuentes de la coleccion`
- `test: cubrir apertura de fichas`

## Pull Request
Debe incluir:
- Issue relacionada.
- Resumen del cambio.
- Capturas o video cuando ayuden a revisar 3D/UI.
- Pruebas realizadas.
- Riesgos o limitaciones.
- Checklist de aceptación.

## Revisión
El revisor comprueba alcance, legibilidad, funcionamiento, errores de consola, assets y documentación afectada. No aprobar cambios que rompan el build o que incumplan criterios.
