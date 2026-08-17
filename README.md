# HW04 — UX + Tailwind CSS

**Week 4 · DSAW · Universidad de La Sabana**

## LINK DE DESPLIEGUE
https://dsaw-2026-2.github.io/hw04-ux-tailwind-css-acaycedo24/

## Objective

Create complete wireframes for your project in Figma and rebuild the landing page with Tailwind CSS, including a working dark mode toggle.

## Deliverables

### `index.html`

Rebuild your landing page using **Tailwind CSS** (via CDN or Vite):
- Use utility classes for **all** styling — no separate custom CSS file
- Responsive using Tailwind's prefixes: `sm:`, `md:`, `lg:` — no manual media queries
- Implement a **working dark mode toggle** using Tailwind's `dark:` variant:
  - There must be a visible button that switches between light and dark mode
  - The switch must affect background colors, text, and at least one component

### `figma-link.txt`

URL to your Figma file containing wireframes for **all main screens** of the project:
- At least 3 distinct screens
- Each screen must show at least 3 states: empty, with data, and error/validation

## Layer 2

The dark mode toggle must persist across page reloads using `localStorage`.

## AI Log (`AI-LOG.md`)

- Did you use AI to generate Tailwind classes? Did you also use it for the wireframes?
- What did you learn about Tailwind that you wouldn't have learned if AI had done everything?

## Deployment

GitHub Pages. If you use Vite, configure the `base` option in `vite.config.js`.

## Autograding

The pipeline will check:
- ✅ `index.html` and `figma-link.txt` are present
- ✅ HTMLHint passes with no errors
- ✅ GitHub Pages responds with HTTP 200
- ✅ Tailwind used correctly, dark mode works, wireframes complete (reviewed by Claude)

> **Submission rule:** If it is not deployed and public, it cannot be graded.

 ## Registro de uso de IA

**Prompt utilizado:** le pedí a Claude que reconstruyera el `index.html`
de HW03 usando solo clases de utilidad de Tailwind (vía CDN), con una
paleta de colores personalizada igual a la identidad visual real del
equipo (los mismos colores sacados de las capturas del Figma de
Catalina), y un botón de modo oscuro que guardara la preferencia en
`localStorage`.

**Qué se mantuvo de la propuesta de la IA:** la configuración de
colores en `tailwind.config` se mantuvo casi igual, porque ya coincidía
con la paleta que el equipo había definido antes a partir del Figma
real, no de una paleta genérica sin contexto del proyecto.

**Cómo funciona el modo oscuro persistente:** un script en el `<head>`,
antes de que cargue Tailwind, revisa `localStorage.getItem('theme')` y
agrega la clase `dark` al `<html>` si corresponde — así se evita el
parpadeo al recargar. El botón solo alterna esa clase y guarda la
elección.

**Errores reales y cómo los resolví:**
1. La página daba 404 porque no había activado GitHub Pages en este
   repo nuevo — no se hereda de tareas anteriores.
2. Después de activarlo, seguía en 404 aunque Actions mostraba el
   despliegue exitoso. La causa real fue el archivo llamado
   `Index.html` en vez de `index.html`: como macOS no distingue
   mayúsculas de minúsculas, un simple renombrado en VS Code no bastaba
   — Git no registraba el cambio. Lo resolví renombrando en dos pasos
   (`git mv Index.html temp.html`, commit; `git mv temp.html
   index.html`, commit) para forzar a Git a grabar el nombre correcto.

**Diferencia entre el syllabus general y el rubric.json real:** el
syllabus general sugería "todas las pantallas" en Figma; el rubric.json
real solo exige mínimo 3 pantallas distintas con un elemento mostrando
3 estados (vacío, lleno, error). A la fecha de esta entrega el Figma
tiene 2 de 3 — quedó documentado en el README en vez de ocultarlo.
