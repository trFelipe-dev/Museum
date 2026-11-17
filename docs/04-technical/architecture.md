# Arquitectura del sistema

## Enfoque
Arquitectura modular basada en JavaScript ES Modules, con Three.js para renderizado, Vite para desarrollo/compilación y Rapier 3D para física y colisiones.

## Módulos previstos
| Módulo | Responsabilidad |
|---|---|
| `core` | Inicialización, escena, cámara y renderizador |
| `museum` | Arquitectura y espacios del museo |
| `player` | Movimiento, cámara, controles y colisiones |
| `exhibits` | Exposiciones, marcos, placas y fichas |
| `npcs` | Personajes, rutas, animaciones y estados |
| `systems` | Audio, carga de recursos, rendimiento e interacciones generales |
| `ui` | Menús, ventanas, avisos y controles |
| `data` | Datos JSON de exposiciones y diálogos |
| `styles` | Estilos de interfaz |

## Estructura de código prevista
La estructura detallada de `src/` está definida en `technical-design.md`. No crear módulos adicionales hasta que exista una responsabilidad concreta que lo justifique.

## Principios
- Mantener responsabilidades separadas.
- Evitar dependencias innecesarias.
- Cargar recursos progresivamente.
- Documentar decisiones técnicas relevantes.
- Integrar cambios mediante Pull Requests.
