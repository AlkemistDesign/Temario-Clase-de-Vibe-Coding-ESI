# DESIGN.md — Sistema de Diseño e Interfaz UI/UX

## 1. Filosofía Visual y Principios Clave
- **Minimalismo funcional y limpio:** Sin ornamentos innecesarios (sin barras de ventana falsas de macOS ni bordes duros).
- **Enfoque tipo "Presentación / Slide":** Experiencia de lectura lineal y espaciosa, con controles de avance superior e inferior para pasar de sección de forma natural.
- **Accesibilidad y Legibilidad (WCAG AA):** Ratios de contraste altos garantizados (mínimo 4.5:1 en texto normal, 3:1 en títulos y controles) tanto en modo claro como oscuro.
- **Microinteracciones discretas:** Sombras sutiles para profundidad y transiciones suaves (`duration-200 ease-in-out`).
- **Respeto a las preferencias del usuario:** Soporte para `@media (prefers-reduced-motion: reduce)`.

---

## 2. Sistema de Color (Inspirado en Material Design 3)
Estructura semántica basada en pares "color / on-color". 
Paleta fría dominante con **Turquesa Neón** como primario y **Naranja Vibrante** como contraste de acento.

### Tokens de Color Semánticos

| Token Semántico | Modo Claro | Modo Oscuro | Propósito |
| :--- | :--- | :--- | :--- |
| `surface` | `#F8FAFC` (Slate 50) | `#0F172A` (Slate 900) | Fondo general de la aplicación |
| `surface-container` | `#FFFFFF` (White) | `#1E293B` (Slate 800) | Fondo de tarjetas, bloques y modales |
| `surface-variant` | `#F1F5F9` (Slate 100) | `#334155` (Slate 700) | Fondos secundarios y áreas de código claro |
| `on-surface` | `#0F172A` (Slate 900) | `#F1F5F9` (Slate 100) | Texto principal y títulos |
| `on-surface-variant` | `#64748B` (Slate 500) | `#94A3B8` (Slate 400) | Texto secundario, subtítulos y leyendas |
| `primary` | `#0D9488` (Teal 600) | `#14B8A6` (Teal 500) | Enlaces, elementos activos, foco y marca |
| `primary-hover` | `#0F766E` (Teal 700) | `#2DD4BF` (Teal 400) | Estado hover e interactivo de primario |
| `on-primary` | `#FFFFFF` | `#042F2E` (Teal 950) | Texto e iconos sobre fondo primario |
| `accent` | `#C2410C` (Orange 700) | `#FB923C` (Orange 400) | Llamadas a la acción secundarias, alertas |
| `accent-hover` | `#9A3412` (Orange 800) | `#FDBA74` (Orange 300) | Hover sobre acento |
| `on-accent` | `#FFFFFF` | `#431407` (Orange 950) | Texto e iconos sobre acento |
| `border-subtle` | `rgba(226, 232, 240, 0.8)` | `rgba(51, 65, 85, 0.5)` | Separadores y bordes ultra-tenues |

### Tokens de Estado y Feedback

| Token | Modo Claro | Modo Oscuro | Uso |
| :--- | :--- | :--- | :--- |
| `success` / `on-success` | `#15803D` / `#FFFFFF` | `#4ADE80` / `#052E16` | Confirmación, copiado correcto, completado |
| `warning` / `on-warning` | `#B45309` / `#FFFFFF` | `#FBBF24` / `#451A03` | Advertencias, notas importantes |
| `error` / `on-error` | `#B91C1C` / `#FFFFFF` | `#F87171` / `#450A0A` | Errores críticos, fallos de validación |
| `info` / `on-info` | `#0369A1` / `#FFFFFF` | `#38BDF8` / `#082F49` | Consejos, notas informativas |

---

## 3. Tipografía y Jerarquía

- **Fuente General (Sans-serif):** Sistema moderno sans-serif (`Inter`, `system-ui`, `-apple-system`, `sans-serif`).
- **Fuente Monoespaciada (Prompts y código):** `JetBrains Mono`, `ui-monospace`, `SFMono-Regular`, `Consolas`, `monospace`.
- **Tamaño Base:** `16px` (`text-base`), interlineado holgado (`leading-relaxed` / `1.65`).

### Escala Tipográfica
- **H1 (Título de sección / slide):** `text-2xl` a `text-4xl` (`1.75rem` - `2.25rem`), `font-bold`, tracking ligeramente cerrado (`tracking-tight`).
- **H2 (Subsecciones):** `text-xl` a `text-2xl` (`1.25rem` - `1.5rem`), `font-semibold`.
- **H3 (Títulos de prompts / cajas):** `text-base` a `text-lg` (`1rem` - `1.125rem`), `font-medium`.
- **Párrafo / Lectura:** `text-base` (`1rem`), color `on-surface` con óptima legibilidad.
- **Code / Prompts:** `text-sm` (`0.875rem`), monoespaciado, interlineado `leading-6`.

---

## 4. Espaciado, Sombras y Bordes

### Espaciado (Sistema Base 4/8px)
- **Contenedores de contenido:** Máximo ancho centrado para lectura óptima (`max-w-4xl` o `max-w-5xl`).
- **Relleno interior de tarjetas:** `p-6` a `p-8` en escritorio, `p-4` a `p-5` en mobile.
- **Separación vertical entre bloques:** `gap-6` a `gap-8` (24px a 32px).

### Sombras y Bordes
- **Bordes:** Sin bordes duros. Únicamente bordes opcionales ultra-tenues (`border border-slate-200/60 dark:border-slate-800/60`).
- **Elevación y Profundidad:**
  - Nivel base (tarjetas/prompts): `shadow-sm` o `shadow-md`.
  - Nivel flotante (sidebar desplegado, modales, toasts): `shadow-xl` o `shadow-2xl`.
- **Radios de curvatura:** Esquinas suaves (`rounded-xl` para bloques y prompts, `rounded-2xl` para contenedores principales, `rounded-lg` para botones).

---

## 5. Anatomía de los Bloques de Prompt

Los prompts son el componente estrella. Se diseñan como contenedores diferenciados inspirados en el tema de editor **Tokyo Night** (o One Dark), garantizando lectura tanto en modo claro como oscuro.

```text
┌────────────────────────────────────────────────────────┐
│  [md/txt]                     [Ver más] [Copiar] 📋    │  <- Cabecera plana y limpia
├────────────────────────────────────────────────────────┤
│  Actúa como un experto en desarrollo...                │
│  Quiero que analices la siguiente función...           │  <- Max-height + scroll vertical
│  ...                                                   │
└────────────────────────────────────────────────────────┘
```

1. **Sin marcos de ventana:** Nada de botones semáforo de Mac ni pestañas falsas. Contenedor plano y minimalista.
2. **Botón Copiar:**
   - Ubicado arriba a la derecha en la cabecera.
   - **Copiar siempre copia el texto completo**, independientemente de si el bloque está colapsado o expandido.
   - Feedback: cambia temporalmente el icono a un check, el texto a *"¡Copiado!"* y el color a `success` / `primary`.
3. **Control de Longitud ("Ver más / Colapsar"):**
   - Si el prompt supera la altura límite (`max-h-64` o ~260px), se activa el botón *"Ver más / Expandir"* o *"Colapsar"*.
   - Mientras esté colapsado, cuenta con `overflow-y-auto` para scroll interno y un sutil degradado inferior indicador de contenido adicional.
4. **Syntax / Resaltado Semántico:**
   - **Modo Oscuro:** Fondo `#13141F` o `#1E293B`, variables/roles en turquesa `#2DD4BF`, parámetros en naranja `#FB923C`, strings en verde pastel `#9ECE6A`, comentarios en lavanda/gris azulado `#94A3B8`.
   - **Modo Claro:** Fondo `#F1F5F9` o `#1A1B26` (estilo editor oscuro consistente), contraste alto con turquesa `#0D9488`, acentos naranja `#C2410C` y texto de lectura `#1E293B`.

## 6. Arquitectura del Layout y Navegación

### 6.1. Barra Superior (Top Bar)
- Fija o sutilmente pegada arriba (`sticky top-0 z-40`).
- Muestra el acceso rápido al índice (`[← Índice]`), badge del tema, posición/apartado actual, botón de menú en móvil y selector de modo Claro/Oscuro.

### 6.2. Barra Inferior (Bottom Bar - Control de Pantallas/Slides)
- Fija abajo (`sticky bottom-0 z-30`).
- Control de avance lineal entre apartados de cada tema:
  - Botón `[← Anterior]` con título de la vista previa.
  - Indicador numérico de paso (ej. `Paso 1 / 9`).
  - Botón `[Siguiente →]` con título de la siguiente vista.
- Sincronización con atajos de teclado (`←` y `→`) y hash en URL (`#paso-N`).

### 6.3. Barra Lateral (Sidebar Plegable / Mini-Rail)
- **Comportamiento en Escritorio (Desktop `≥ 768px`):**
  - **Estado Plegado (Default):** Estrecha (`w-16`), fija a la izquierda (`fixed left-0 top-0 h-full z-30`). Muestra únicamente los iconos/números de cada apartado.
  - **Estado Desplegado (Hover/Focus):** Al pasar el ratón por encima, se expande suavemente a `w-64` / `w-72` (`transition-all duration-300 shadow-2xl`), revelando los títulos textuales completos de cada apartado para salto rápido.
  - **Área de Contenido:** Margen izquierdo compensado (`md:pl-20` / `md:ml-16`) para que el contenido nunca quede solapado por los iconos en reposo.
- **Comportamiento en Móvil (`< 768px`):**
  - Se oculta el riel fijo y se abre como cajón deslizante (*drawer*) desde la izquierda mediante el botón hamburguesa de la barra superior, con backdrop oscurecido y táctiles de 44px.

### 6.4. Modelo de Pantallas / Vistas Independientes
- Cada página de tema desglosa sus contenidos en vistas individuales (una sola en pantalla al mismo tiempo) para evitar scrolls infinitos.
- **Pantalla de Transición entre Subtemas:** Pantalla de hito al completar los apartados de un subtema (ej. de 0.1 a 0.2) con resumen y botón destacado `Continuar a 0.2 →`.
- **Pantalla de Fin de Tema:** Tarjeta destacada al culminar la unidad completa, con resumen global y llamada a la acción para volver al índice o continuar al siguiente tema.

---

## 7. Adaptabilidad y Reglas Mobile-First (`< 768px`)

En pantallas táctiles y móviles:
1. **Home Hub en Móvil:** Grid colapsa a una sola columna con tarjetas táctiles amplias y legibles.
2. **Sidebar Drawer / Overlay:** En páginas de tema, se despliega con botón hamburguesa y backdrop desenfocado.
3. **Dimensiones táctiles accesibles:** Todos los botones interactivos (flechas de slide, selector de tema, botones de acción) tienen un área táctil mínima de **44px x 44px**.
4. **Desplazamiento horizontal seguro:** Los bloques de código, tablas y conceptos cuentan con `overflow-x-auto` con `word-break: break-word` o saltos de línea suaves para evitar desbordar la pantalla del teléfono.

---

## 8. Botones de Enlace Externo e Interactivo (External Action Links)

Para recursos web externos, documentación oficial, repositorios y guías rápidas (cheat sheets), se debe utilizar un componente de enlace interactivo con estilo de botón reforzado para garantizar que el alumno identifique inmediatamente que es un enlace navegable hacia una página externa.

### 8.1. Principios de Diseño
- **Borde visible y distintivo:** El botón debe tener un borde exterior claro (`border-2 border-teal-600 dark:border-teal-400` para tema teal o `border-orange-500` para tema naranja) para diferenciarse de botones planos o texto común.
- **Icono de flecha direccional a la derecha:** Incluye un icono SVG de flecha apuntando a la derecha alineado al extremo derecho del botón.
- **Microinteracción hover:** Al pasar el cursor, la flecha se desplaza ligeramente a la derecha (`group-hover:translate-x-1 transition-transform`) y el fondo del botón adquiere un tono suave (`hover:bg-teal-50 dark:hover:bg-slate-800`).
- **Seguridad y apertura:** Siempre incluye `target="_blank"` y `rel="noopener noreferrer"`.

### 8.2. Plantilla Canónica (Banner + Botón con Borde y Flecha)

```html
<!-- Contenedor / Banner del recurso -->
<div class="bg-gradient-to-r from-teal-500/10 via-slate-100 dark:via-[#1a2333]/90 to-transparent rounded-2xl p-6 border border-teal-500/40 dark:border-teal-500/30 flex flex-col sm:flex-row items-start sm:items-center justify-between gap-4">
  <div class="space-y-1">
    <h3 class="font-bold text-slate-900 dark:text-white text-base">
      Título del Recurso o Guía
    </h3>
    <p class="text-xs sm:text-sm text-slate-600 dark:text-slate-300">
      Breve descripción explicativa del contenido que encontrará el alumno.
    </p>
  </div>

  <!-- Botón de enlace interactivo -->
  <a href="https://ejemplo.com/recurso" target="_blank" rel="noopener noreferrer"
    class="inline-flex items-center justify-between gap-3 px-5 py-3 rounded-xl bg-white dark:bg-slate-900 border-2 border-teal-600 hover:border-teal-500 dark:border-teal-400 hover:bg-teal-50 dark:hover:bg-slate-800 text-teal-700 dark:text-[#2dd4bf] font-bold text-xs sm:text-sm transition-all shadow-sm hover:shadow-md group shrink-0">
    <span>Texto de la Acción</span>
    <svg class="w-4 h-4 text-teal-600 dark:text-teal-400 group-hover:translate-x-1 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M14 5l7 7m0 0l-7 7m7-7H3"></path>
    </svg>
  </a>
</div>
```