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

## Estructura del proyecto

```
navegacion-app/
├── index.html              ← entrada (redirige a app.html)
├── app.html                ← single-page con todo el código
├── stitched/               ← imágenes de la app (capturas y mockups)
│   ├── hoy.jpg, centro.jpg, perfil.jpg, mas.jpg
│   ├── agenda/, asistente/, entrenamiento/, dieta/, rewards/, pesaje/
│   ├── tienda/, notificaciones/, gymder/, cartera/, qr-acceso/, dietas/
│   └── composicion/
└── _fuentes/               ← material origen (NO se sube a git)
    ├── screenshots/        ← capturas crudas
    ├── backups/            ← .bak originales
    ├── debug/              ← previews intermedios
    └── fonts/              ← fuentes locales para PIL
```

## Menús y flujos implementados

- **1 · Hoy tienes** (con 7 sub-flujos: 1.1 Asistente virtual, 1.2 Agenda, 1.3 Entrenamiento Buscar, 1.4 Entrenamiento Crear, 1.5 Pesaje básculas, 1.6 Dieta, 1.7 Rewards)
- **2 · Mi centro** (con 7 tiles activos: Tienda, Notificaciones, Gymder®, Reserva de Actividades, Asígnate un Entrenamiento, Nutrición, Rewards)
- **3 · Mi perfil** (con 4 sub-flujos: 3.1 Cartera, 3.2 QR acceso, 3.3 Pesaje básculas, 3.4 Dietas personalizadas)
- **4 · Más** (con 6 sub-flujos espejo de los anteriores)

Cada item de la sidebar resalta en rojo cuando estás en la página correspondiente del flujo, y la sidebar auto-expande sus padres y hace scroll para mostrarlo.

## Tipografía

Toda la UI usa **Poppins** (Google Fonts). Las capturas de la app real conservan su tipografía original baked-in.

## Tecnologías

- HTML/CSS/JS puros (sin frameworks).
- PIL (Python) para procesar capturas y mockups generados.
- qrcode lib para el QR de acceso de ejemplo.

---

## Publicar en GitHub Pages

1. Crea un repo nuevo en GitHub.
2. Sube todo el contenido de `navegacion-app/` (excluyendo `_fuentes/` y `_debug/` — están en .gitignore).
3. Settings → Pages → Source: `Deploy from a branch` → `main` / `(root)`.
4. Espera unos minutos. Tu web estará en `https://<usuario>.github.io/<repo>/`.

`index.html` redirige automáticamente a `app.html`, así que la URL pública apuntará a la app sin sufijo.
