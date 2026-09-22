# Cal Turisme — proyecto Astro

Estructura inicial del sitio, sin branding definitivo todavía. Todo lo
visual (colores, tipografías) está centralizado para poder cambiarlo
fácilmente cuando tengáis el branding.

## Qué hay montado

- **Home** (`src/pages/index.astro`): cabecera + bloque de presentación +
  listado de alojamientos en formato tarjeta (como Airbnb: al hacer clic
  en la tarjeta, te lleva a la web externa del alojamiento, en este caso
  `masdelmoli.lodgify.com`).
- **Qui som** (`src/pages/qui-som/index.astro`): página "quiénes somos"
  con las dos líneas del proyecto.
- Diseño editorial con paleta tierra/verde pino/teula (no es definitivo:
  ver más abajo cómo cambiarlo).

## Cómo añadir un nuevo alojamiento

No hace falta tocar ningún componente. Edita el archivo
`src/data/allotjaments.json` y añade un bloque como este:

```json
{
  "name": "Nombre del alojamiento",
  "description": "Una frase corta que lo describa.",
  "url": "https://su-web-externa.com/",
  "image": ""
}
```

Si dejas `"image": ""`, se muestra un panel ilustrativo provisional
(el motivo de turons/colinas). Cuando tengáis fotos reales, poned la
ruta de la imagen ahí (por ejemplo `/img/mas-del-moli.jpg`, guardando
el archivo dentro de `public/img/`).

## Cómo cambiar colores y tipografías cuando llegue el branding

Todo vive en `src/styles/global.css`, dentro de `:root`. Cambia los
valores hexadecimales de `--color-*` y los nombres de fuente en
`--font-display` / `--font-body` (y actualiza el enlace de Google
Fonts en `src/layouts/BaseLayout.astro` si cambiáis de tipografía).

## Cómo poner el logo definitivo

De momento el nombre "Cal Turisme" se muestra como texto (wordmark) en
`src/components/Header.astro` y `Footer.astro`. Cuando tengáis un logo,
sustituid el texto por una etiqueta `<img>` apuntando a
`public/logo.svg` (o el formato que sea).

## Desarrollo local

```bash
npm install
npm run dev
```

## Desplegar en Cloudflare Pages

1. Sube este proyecto a un repositorio de GitHub.
2. En Cloudflare Pages, "Create a project" → conecta el repositorio.
3. Build command: `npm run build` — Build output directory: `dist`.
4. Cada `push` a la rama principal desplegará automáticamente.
5. Obtendréis una URL tipo `cal-turisme.pages.dev` de forma gratuita.
   El día que compréis el dominio, se añade desde
   Pages → tu proyecto → Custom domains, sin tener que migrar nada.

## Pendiente / a decidir

- Textos reales de cada alojamiento (ahora hay un texto genérico
  provisional en `allotjaments.json`).
- Fotografías reales (ahora hay un placeholder ilustrado).
- Eslogan definitivo en catalán para la home (ahora está
  "On cal fer turisme? A Cal Turisme." — cámbialo en
  `src/pages/index.astro` si preferís la otra opción o una nueva).
- Branding: logo, colores y tipografías definitivos.
