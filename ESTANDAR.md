# Estándar de las apps de jlcaleroh-apps

Reglas comunes para todas las apps (Trazos de Arquitecto, Números, Mi Rutina, Robot Sílabo y las que vengan). Cada app nueva parte de esta plantilla y revisa esta lista antes de publicarse.

Contacto: jlcaleroh@gmail.com

---

## 1. Principios para TDAH (lo que más pesa)
Basados en el documento de investigación "Juegos en iPad para que niños con TDAH aprendan a leer en español".

- [ ] **Respuesta en menos de 1 segundo** tras cada toque: sonido + animación.
- [ ] **Elogio específico por voz** ("¡Leíste ma!", "¡Encontraste el siete!"), no solo "¡bien!".
- [ ] **Sin castigo por error:** nada de vidas perdidas ni sonidos negativos. Se intenta otra vez. Tras 2 errores, una pista visual.
- [ ] **Una meta por pantalla.** Sin menús ni distractores visibles durante el juego.
- [ ] **Audio en todo:** cada instrucción, letra, número o palabra se puede escuchar. Botón para repetir.
- [ ] **Final claro de cada misión**, con celebración. **Sin cuota diaria fija** (aprovechar el hiperfoco): al terminar, "¡Otra misión!" o "Terminar por ahora". Límite diario solo como opción del adulto, apagado por defecto.
- [ ] **Premios por sesión, no por acierto.** Sin tiendas, monedas, anuncios ni rankings contra otros niños.
- [ ] **Práctica espaciada:** lo fallado vuelve en la misma sesión y en días siguientes.
- [ ] **Adulto incluido:** un modo "juntos" cuando tenga sentido, y siempre un modo en que el niño juegue solo.
- [ ] **Movimiento reducido** respetado (`prefers-reduced-motion`).

## 2. Pantallas y estructura
- [ ] **¿Quién juega?** al abrir si hay más de un perfil.
- [ ] **Inicio:** una sola acción grande para jugar. Racha visible si existe.
- [ ] **Juego → Fin:** celebración, racha si es de 2 días o más, "¡Otra misión!" / "Terminar por ahora".
- [ ] **Botón ?** de información, siempre accesible, con esta estructura y en este orden:
  1. Qué es
  2. Cómo se juega
  3. Principios para TDAH
  4. Para el adulto
  5. Sin Internet (instalar)
  6. Contacto: jlcaleroh@gmail.com
- [ ] **Panel del adulto** con el **gesto estándar: mantener presionado ⚙ 2 segundos** (anillo que se llena). PIN solo como opción extra.
- [ ] El panel incluye: progreso, jugadores (agregar, cambiar nombre, borrar con confirmación), idioma, límite diario opcional, **Prueba de voz**, **Respaldo** y contacto.

## 3. Perfiles, racha y progreso
- [ ] **Un perfil por niño**, con progreso separado.
- [ ] **Racha de días:** sube un día por día con al menos una misión; si se corta, vuelve a 1 **sin regaño**. Se guarda la mejor racha para el adulto.
- [ ] Confirmaciones dentro de la página (no `alert()` ni `confirm()`).

## 4. Almacenamiento (importante)
- Todas las apps viven en `jlcaleroh-apps.github.io` y **comparten localStorage**.
- [ ] **Todas las claves empiezan con el id de la app y dos puntos:** `silabas:…`, `numeros:…`. Nunca claves genéricas como `perfiles`.
- [ ] El respaldo declara exactamente esas claves (`clave: k => k.startsWith(APP + ':')`).
- Pendiente conocido: Números usa claves sin prefijo (`perfiles`, `nivel_…`); migrarlas con cuidado algún día.

## 5. Componentes comunes (mismo archivo en todas las apps)
Copiar **sin cambios**. Si se mejora uno, se copia igual a todos los repos.

| Archivo | Qué hace | Dónde se monta |
|---|---|---|
| `respaldo.js` | Guardar y restaurar el progreso de todos los niños en un archivo; fecha del último respaldo y aviso a las 2 semanas; pide al navegador no borrar los datos. | Panel del adulto |
| `voz.js` | Elegir la voz por idioma, velocidad y ejemplos para comprobar la pronunciación. | Panel del adulto |

El habla de la app usa siempre la voz elegida: `Voz.elegida(lang)` y `Voz.velocidad(lang)`.

## 6. Sin Internet e instalación
- [ ] `sw.js`: página con red primero (espera máxima 4 s) y copia guardada si no hay Internet; íconos, fuentes y componentes desde la copia.
- [ ] `CACHE` con el id de la app y versión (`numeros-v3`). **Subir la versión** cuando cambien archivos que no sean la página.
- [ ] Todo archivo nuevo se agrega a la lista `CORE` de `sw.js`.
- [ ] `manifest.webmanifest` con nombre, nombre corto, colores e íconos (192, 512, 512 maskable) + `apple-touch-icon`.
- [ ] Pantalla siempre encendida mientras se juega (Wake Lock).

## 7. Idioma
- [ ] Español por defecto. Inglés opcional, con textos en un diccionario por idioma; **nunca mezclar idiomas** en la voz ni en la pantalla.
- [ ] Una app que enseña a leer en español puede quedarse solo en español en el juego.

## 8. Diseño
- [ ] Botones grandes para dedos de 5 años, buen contraste, letra clara (Andika para letras de lectura).
- [ ] Funciona en iPad horizontal y vertical, y en teléfono, sin desplazamiento lateral.
- [ ] Márgenes que respetan la zona segura del iPad (`env(safe-area-inset-*)`).

## 9. Publicar
1. Crear el repo en `jlcaleroh-apps` con **"Use this template"** desde `plantilla`.
2. Cambiar los puntos marcados ① a ⑤ en `index.html`, el `CACHE` de `sw.js`, `manifest.webmanifest` e íconos.
3. Activar GitHub Pages: **Settings → Pages → Branch: main / root**.
4. Abrir `https://jlcaleroh-apps.github.io/<repo>/` en Safari e instalar con **Compartir → Agregar a pantalla de inicio**.
5. Revisar esta lista completa.
