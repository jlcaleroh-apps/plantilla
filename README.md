# Plantilla · apps de jlcaleroh-apps

Punto de partida para cada app nueva para niños con TDAH. Ya trae todo lo común funcionando:

- ¿Quién juega? con perfiles por niño
- Inicio con una sola meta, racha de días y una misión de ejemplo con final claro
- "¡Otra misión!" o "Terminar por ahora" (sin cuota diaria; límite opcional para el adulto)
- Ventana **?** de información con la estructura estándar y el contacto
- Panel del adulto con el gesto estándar (mantener presionado ⚙ 2 segundos)
- Español e inglés
- Componentes comunes: **`respaldo.js`** (respaldo del progreso), **`voz.js`** (prueba de voz) y **`adulto.js`** (gesto de 2 s para el panel del adulto)
- Funciona sin Internet e instalable en el iPad (`sw.js`, `manifest.webmanifest`, íconos)
- Pantalla siempre encendida mientras se juega

## Crear una app nueva
1. En GitHub, botón **Use this template → Create a new repository** (dentro de `jlcaleroh-apps`).
2. En `index.html`, cambiar los puntos marcados **① a ⑤** (nombre, colores, id de la app, información y mecánica del juego).
3. Cambiar `CACHE` en `sw.js`, el `manifest.webmanifest` y los íconos.
4. Activar GitHub Pages: **Settings → Pages → Branch: main / root**.
5. Revisar la lista de [ESTANDAR.md](ESTANDAR.md).

## Reglas
Todas las reglas comunes están en **[ESTANDAR.md](ESTANDAR.md)**: principios para TDAH, pantallas, almacenamiento, componentes, sin Internet, idioma, diseño y publicación.

## Contacto
jlcaleroh@gmail.com
