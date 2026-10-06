## 1. Visión General del Proyecto
Sitio web estático, ultraligero y de carga inmediata para la asignatura/taller de **Vibe Coding**.
Su propósito es servir como portal de consulta lineal y por temas durante las clases: los alumnos acceden desde una página principal (Home Hub) a cada tema específico, leen el temario estructurado y copian los prompts de trabajo con un solo clic.

- **Tipo de web:** Estática multi-página (Vanilla HTML5 + Tailwind CSS + JavaScript puro).
  - `index.html`: Página principal / Hub de acceso al temario con tarjetas de cada tema y enlaces directos.
  - Páginas de tema individuales (ej. `0-introduccion.html`, `1-porfolio.html`, etc.): Contienen el desarrollo detallado del tema con navegación secuencial mediante botones de cambio de página (`[← Anterior]` / `[Siguiente →]`).
- **Entorno:** Se alojará directamente en un servidor web propio como archivos estáticos independientes (sin frameworks pesados, sin SSR, sin CMS, sin bundlers obligatorios).
- **Uso:** Solo lectura y consulta para los alumnos. Todo el contenido debe ser visible directamente en la web (sin descargas de archivos intermedias).

---

## 2. Stack Tecnológico y Reglas de Desarrollo
- **HTML5:** Semántico y estructurado (`<header>`, `<nav>`, `<main>`, `<article>`, `<section>`, `<footer>`).
- **CSS:** Tailwind CSS (vía CDN o CLI simple) complementado con CSS mínimo para casos puntuales.
- **JavaScript:** Vanilla JS sin dependencias ni frameworks.
  - Gestión de copia al portapapeles.
  - Conmutador de modo Claro / Oscuro sincronizado globalmente (con persistencia en `localStorage` y detección de `prefers-color-scheme`).
  - Navegación entre páginas por enlace y atajos de teclado (`←` y `→`).
- **Cero dependencias complejas:** No usar React, Vue, Svelte, ni bases de datos. Mantener la base de código comprensible, editable a mano y directa.

---

## 3. Estructura de Secciones y Contenido
El contenido es secuencial y lineal, organizado en las siguientes secciones principales:

0. Introducción
0.1. ¿Qué es el vibe coding?
0.2. Fundamentos de IA y agentes
1. Tarea 1 - Porfolio
1.1. Usar LLMs en un entorno de desarrollo integrado
1.2. Historial de versiones con Git y Github
2. Tarea 2 - Dashboard
2.1. Crear AGENTS.md, DESIGN.md y MEMORY.md
2.2. Workflows y skills
2.3. MCPs (Model Context Protocols)
3. Tarea 3 - App
3.1. Spec Driven Development
3.2. Crear agentes y subagentes
3.3. Conectar y usar una base de datos
4. Otros Recursos
4.1. Guía Antigravity
4.2. Guía Alkemist
4.3. Guía Olisto
4.4. Guía Prome

El contenido siempre debe ser el que te proporcionan, puedes cambiar la estructura para que quede mejor, pero no cambies el contenido ni añadas secciones nuevas.
Nota: Puede que más adelante se creen más apartados o subapartados. Así que ten en cuenta que los contenidos no son fijos y están sujetos a cambios.

---

## 4. Requisitos Clave de Componentes e Interacción

### Bloques de Prompts (Elemento Principal)
- **Diferenciación visual:** Deben destacar claramente del texto general mediante una tarjeta/bloque con estilo de terminal o editor de código.
- **Tipografía:** Fuente monoespaciada (`font-mono`, e.g., JetBrains Mono, Fira Code o monospace del sistema).
- **"Colorinchis" (Syntax Highlighting / Acentos de color):** Usar colores vibrantes (verde menta, violeta, cyan, naranja, amarillo) para resaltar variables, etiquetas, roles o instrucciones clave dentro de los prompts.
- **Botón "Copiar Prompt":**
  - Ubicado en la esquina superior derecha del bloque.
  - Copia al portapapeles con un solo clic usando `navigator.clipboard.writeText`.
  - Feedback visual inmediato (cambio de texto o icono a "¡Copiado!" durante 1.5–2 segundos).

### Modo Claro / Oscuro
- Toggle accesible en la cabecera.
- Alternar clase `dark` en el elemento `<html>`.
- Ambos temas deben garantizar alto contraste y legibilidad para proyectores de aula y pantallas individuales.

---

## 5. Diseño y Estética
- **Referencia obligatoria:** Consultar `DESIGN.md` para todas las decisiones tipográficas, paleta de colores, márgenes, sombras y detalles visuales específicos.
- **Criterio general:** Minimalista, espacioso, sin distracciones, enfocado en la legibilidad del texto y el protagonismo de los prompts.

---

## 6. Instrucciones para Agentes / Asistentes de IA
1. **Fidelidad absoluta al contenido (REGLA ESTRICTA):** NO cambiar, resumir, parafrasear, omitir ni inventar contenido bajo ningún concepto. El texto, explicaciones, prompts y avisos deben reproducirse con exactitud literal. Si se considera necesario algún cambio, se debe preguntar primero al usuario.
2. **Mantener todo el contenido en línea:** No generar enlaces a archivos descargables externos para el temario o los prompts; todo debe renderizarse directamente en el DOM.
3. **No añadir complejidad innecesaria:** Si se te pide añadir una funcionalidad, no propongas migrar a frameworks (React, Next.js, etc.) ni meter npm packages a menos que se solicite explícitamente.
4. **Estructura modular y limpia:** Si el HTML se divide en plantillas o se mantiene en un solo `index.html`, mantener el código bien indentado y comentado para facilitar el pegado manual de nuevos contenidos.

---

## 7. Memoria
- Al empezar, lee `MEMORY.md` para conocer el estado del proyecto y las decisiones tomadas.
- Al terminar una tarea, actualízalo: estado actual, decisiones importantes (con su porqué) y errores a evitar.
- Mantenlo breve (máximo ~50 líneas): resume o elimina lo que ya no aporte.
- Si algo se convierte en una regla permanente, propón moverlo a `AGENTS.md` en lugar de dejarlo en la memoria.
- No guardes nunca datos sensibles (claves, tokens, datos personales).