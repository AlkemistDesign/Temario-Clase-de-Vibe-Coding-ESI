# MEMORY.md — Apuntes de Vibe Coding
Memoria del proyecto entre sesiones. Máximo ~50 líneas: resume o elimina lo que ya no aporte.

## Estado actual
- Repositorio configurado con estrategia multi-rama:
  - Rama `profesor`: Contiene el temario completo (Unidades 0, 1, 2, 3 y 4 completas).
  - Rama `main` (pública): Contiene únicamente `index.html` (Tareas 2 y 3 bloqueadas con candado), `0-introduccion.html`, `1-porfolio.html`, `4-otros-recursos.html` con sus 4 guías y assets.

## Decisiones (y por qué)
- `0-introduccion.html`: Eliminada la slide de transición intermedia (slide-8) para una navegación más fluida hacia Fundamentos de IA (0.2).
- Reestructuración de `2-dashboard.html`: Eliminada la slide redundante de configuración de opencode.json.
- Favicon SVG: Creado `assets/favicon.svg` y `favicon.svg` con círculo teal (`#2dd4bf`).
- Estrategia de despliegue progresivo: Temas 2 y 3 bloqueados en `index.html` y excluidos del árbol de `main` hasta ser impartidos. Enlace final de `1-porfolio.html` apunta a Recursos.

## Guía rápida de desbloqueo progresivo
1. **Desbloquear tema nuevo en clase (ej. Tema 2)**:
   `git checkout main` → `git checkout profesor -- 2-dashboard.html` → restaurar tarjeta en `index.html` → `git commit -m "feat: desbloquea Tema 2"` → `git push`
2. **Actualizar temario general**:
   Hacer cambios en rama `profesor` y mergear/copiar selectivamente a `main`.