**Para trabajar en un equipo de 4 personas sin dañar el proyecto funcional, cada integrante debe crear su propia rama personal para programar su tarea y luego unirla a la rama principal (main) cuando esté terminada. De esta forma, main siempre contiene una versión limpia y estable del museo 3D, mientras cada uno experimenta en su propio espacio aislado.**





###### **¿Qué son las ramas y cómo funcionan?**



Imagina que el proyecto es un árbol:

• Rama main (Principal): Es el tronco oficial del proyecto. Nadie debe escribir código directamente aquí. Solo recibe cambios que ya fueron probados y funcionan bien.

• Ramas de trabajo (Features): Son copias temporales del proyecto que cada persona crea para hacer una tarea específica (por ejemplo: rama-iluminacion, rama-personaje, rama-sala1). Si alguien comete un error en su rama, no afecta a los demás.





Flujo de trabajo con ramas en VS Code (Paso a paso)





###### ***Sigue este ciclo cada vez que tú o alguno de tus compañeros vaya a desarrollar una nueva función del proyecto:***





###### **1. Actualizar la rama principal antes de empezar**



• Asegúrate de estar en main: Mira la esquina inferior izquierda de VS Code. Debe decir main junto a un ícono de ramas. Si dice otro nombre, haz clic ahí y selecciona main.

• Descarga los últimos cambios: Ve al panel de Control de código fuente (Ctrl + Shift + G), haz clic en los tres puntos (...) arriba a la derecha y selecciona Extraer (Pull).





###### **2. Crear tu rama de trabajo**



• Abre el menú de ramas: Haz clic en el nombre main en la esquina inferior izquierda de VS Code.

• Crea una rama nueva: Selecciona + Crear nueva rama... (Create new branch...).

• Nómbrala claramente: Escribe un nombre corto sin espacios que describa lo que harás (ejemplo: escena-principal o luces-museo) y presiona Enter. Automáticamente cambiarás a esa rama.





###### **3. Programar y guardar tus avances (Commits)**



• Edita tu código: Crea o modifica los archivos de Three.js necesarios para tu tarea.

• Prepara los cambios: En Control de código fuente, pasa el mouse sobre Cambios (Changes) y haz clic en el símbolo +.

• Haz Commit: Escribe un mensaje descriptivo arriba (ejemplo: "Agregada luz ambiental y sombras") y haz clic en Confirmar (Commit).

• Sube tu rama a GitHub: Haz clic en el botón azul Publicar rama (Publish Branch). Tu rama quedará guardada en la nube como respaldo.





###### **4. Unir tu rama con el proyecto oficial (main)**



Cuando termines tu tarea y compruebes con npm run dev que no hay errores, es momento de compartir tu avance con los demás:

• 1. Vuelve a main: Haz clic en el nombre de tu rama en la esquina inferior izquierda de VS Code y selecciona main.

• 2. Descarga cambios recientes: Haz clic en los tres puntos (...) de Control de código fuente y selecciona Extraer (Pull), por si un compañero subió algo mientras trabajabas.

• 3. Fusiona tu rama (Merge): Haz clic en los tres puntos (...), ve a Rama (Branch) y selecciona Combinar rama (Merge Branch).

• 4. Elige tu rama: En la lista superior, selecciona el nombre de tu rama (ejemplo: luces-museo). VS Code traerá tu código hacia main.

• 5. Sube la actualización oficial: Haz clic en el botón azul Sincronizar cambios (Sync Changes). Ahora todo el equipo puede descargar tu trabajo.



