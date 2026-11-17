# Dependencias y secuencia de trabajo

## Cadena principal
1. PLN-001 a PLN-010: organización, alcance y gestión.
2. TEC-001 a TEC-011: base técnica.
3. PRO-001 y PRO-005 a PRO-012: prototipo vertical.
4. ARC-001 a ARC-010: arquitectura completa.
5. RES-001 a RES-016 en paralelo parcial; COL-001 a COL-006 después de estabilizar los componentes.
6. NPC-001 a NPC-009 y AUD/ACC según estabilidad de escena e interfaz.
7. QA-001 a QA-010.
8. DEP-001 a DEP-006.

## Dependencias críticas
- TEC-002 precede TEC-003 y TEC-004.
- TEC-003 precede TEC-007.
- TEC-006 precede TEC-009 y TEC-010.
- TEC-008, TEC-009 y TEC-010 preceden PRO-012.
- PRO-005, PRO-006, PRO-007, PRO-008 y PRO-009 preceden PRO-012.
- PRO-012 debe aprobarse antes de expandir masivamente arquitectura e integración.
- RES-001 precede RES-002 a RES-010.
- RES-002 a RES-010 preceden RES-011 y RES-015.
- RES-012 precede RES-013.
- RES-014 precede RES-015 y COL-004.
- ARC-001 precede ARC-002 a ARC-007.
- PRO-006 precede COL-002.
- PRO-007 y PRO-008 preceden COL-003 y COL-004.
- ARC-002 a ARC-009 y COL-001 a COL-004 preceden QA-003.
- PRO-003 y PRO-004 preceden QA-004.
- NPC-003 a NPC-009 y AUD/ACC preceden las pruebas completas correspondientes.
- QA-001 y QA-002 preceden la ejecución de pruebas.
- QA-003 a QA-009 preceden QA-010.
- DEP-001 y DEP-002 preceden DEP-004.

## Trabajo paralelizable
- Investigación RES-002 a RES-010 puede repartirse entre cuatro integrantes.
- Preparación de contenido e imágenes puede avanzar mientras se configura el entorno.
- Diseño de plano/identidad visual puede avanzar durante el prototipo técnico, pero no debe contradecir la prueba vertical.
- Documentación, revisión de fuentes y preparación de casos de prueba pueden avanzar en paralelo con implementación.
- Audio y subtítulos pueden prepararse mientras se construyen NPCs, pero integrarse después de estabilizar la interfaz.

## Regla para bloqueos
Si una dependencia no está lista, la Issue dependiente permanece en `Ready` o `Blocked` (si se añade ese estado) y se registra qué la bloquea. No comenzar trabajo que probablemente deba rehacerse por falta de una decisión crítica.
