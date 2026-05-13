# Trainingym · Navegación App

Mockup interactivo navegable de la app móvil Trainingym, montado como una single-page web. Reproduce los flujos principales de la app (Hoy tienes / Mi centro / Mi perfil / Más) sobre un iPhone 16 Pro y permite recorrer cada sub-flujo con clicks reales sobre las pantallas reales de la app.

**Demo en vivo**: [añadir URL de GitHub Pages cuando se publique]

---

## Cómo abrirlo

- Local: doble click sobre `index.html`. No requiere servidor.
- Online (GitHub Pages): apunta al repo y la URL servirá automáticamente `index.html`.

## Atajos de teclado

- **Ctrl+B** (o **Cmd+B** en Mac): plegar / desplegar la sidebar.
- **Esc**: salir del flujo actual y volver al tab de origen.

---

## URLs únicas (deep linking)

Cada vista navegable tiene su propia URL con hash, así que se puede compartir, recargar o usar el back/forward del navegador.

| Vista | URL |
| --- | --- |
| Hoy tienes | `index.html#hoy` |
| Mi centro | `index.html#centro` |
| Mi perfil | `index.html#perfil` |
| Más | `index.html#mas` |
| Asistente virtual, paso 3 (desde Hoy) | `index.html#hoy/asistente/3` |
| Cartera, paso 3 (desde Mi perfil) | `index.html#perfil/cartera/3` |
| Cartera, paso 3 (desde Más) | `index.html#mas/cartera/3` |
| Tienda, paso 4 (desde Centro) | `index.html#centro/tienda/4` |

El primer segmento (`hoy`, `centro`, `perfil`, `mas`) indica el tab de origen, y la flecha back del flujo regresa a ese tab.

---

## Estructura del proyecto

```
navegacion-app/
├── index.html              ← single-page con todo el código y el routing
├── README.md
├── .gitignore
├── stitched/               ← imágenes de la app (capturas y mockups)
│   ├── hoy.jpg, centro.jpg, perfil.jpg, mas.jpg
│   ├── agenda/, asistente/, entrenamiento/, dieta/, rewards/, pesaje/
│   ├── tienda/, notificaciones/, gymder/, cartera/, qr-acceso/, dietas/
│   └── composicion/
└── _fuentes/               ← material origen (NO se sube a git)
    ├── screenshots/        ← capturas crudas
    ├── backups/            ← .bak originales
    ├── debug/              ← previews intermedios
    ├── stitched-archive/   ← stitched no usados en la web
    └── fonts/              ← fuentes locales para PIL
```

## Menús y flujos implementados

- **1 · Hoy tienes** (con 7 sub-flujos: 1.1 Asistente virtual, 1.2 Agenda, 1.3 Entrenamiento Buscar, 1.4 Entrenamiento Crear, 1.5 Pesaje básculas, 1.6 Dieta, 1.7 Rewards)
- **2 · Mi centro** (con 7 tiles activos: Tienda, Notificaciones, Gymder®, Reserva de Actividades, Asígnate un Entrenamiento, Nutrición, Rewards)
- **3 · Mi perfil** (con 4 sub-flujos: 3.1 Cartera, 3.2 QR acceso, 3.3 Pesaje básculas, 3.4 Dietas personalizadas)
- **4 · Más** (con 6 sub-flujos espejo de los anteriores)

Cada item de la sidebar resalta en rojo cuando estás en la página correspondiente del flujo, la sidebar auto-expande sus padres y hace scroll para mostrarlo, y la URL del navegador se actualiza con la vista activa.

## Tipografía

Toda la UI usa **Poppins** (Google Fonts). Las capturas de la app real conservan su tipografía original baked-in.

## Tecnologías

- HTML/CSS/JS puros (sin frameworks).
- Hash routing en vanilla JS con `history.pushState` y listeners de `popstate` / `hashchange`.
- PIL (Python) para procesar capturas y mockups generados.
- qrcode lib para el QR de acceso de ejemplo.

---

## Publicar en GitHub Pages

1. Crea un repo nuevo en GitHub.
2. Sube todo el contenido de `navegacion-app/` (excluyendo `_fuentes/` y `_debug/` — están en `.gitignore`).
3. Settings → Pages → Source: `Deploy from a branch` → `main` / `(root)`.
4. Espera unos minutos. Tu web estará en `https://<usuario>.github.io/<repo>/`.

`index.html` es la entrada principal, así que la URL pública apuntará a la app sin sufijo. Las URLs con hash (`...#perfil/cartera/3`) funcionan tal cual en GitHub Pages, no requieren configuración adicional.
