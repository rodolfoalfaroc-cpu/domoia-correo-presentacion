# DOMO IA — Correo de presentación

Correo de presentación para envío masivo. Abre con un dato medido del piloto real,
presenta al plantel de agentes con sus fotos y lleva a agendar una reunión.

**→ [Ver el correo renderizado](https://rodolfoalfaroc-cpu.github.io/domoia-correo-presentacion/)**

---

## Archivos

| Archivo | Para qué |
|---|---|
| `index.html` | Vista previa con datos de ejemplo. Es lo que abre el link de arriba. |
| `email-template.html` | **Plantilla de producción.** Es la que se pega en la herramienta de envío. |
| `assets/domoia-logo.png` | Logo oficial, renderizado desde el SVG del sitio (480 × 80 px). |
| `assets/agentes/avatar-*.png` | Avatares circulares de los 7 agentes, listos para correo. |
| `assets/agentes/retrato-*.jpg` | Retratos originales descargados de domo-ia.com. |

Todas las imágenes ya están alojadas en este mismo repo y la plantilla las apunta con
URL absoluta, así que **el correo funciona sin configurar ningún CDN**.

---

## Asunto

**Recomendado:** `Tus clientes te escriben a las 22:47`

Alternativas para A/B testear:

- `¿A qué hora te escribió el último cliente?`
- `El 54% escribió fuera de horario`
- `406 conversaciones, 7 semanas, un dato incómodo`

**Preheader** (no dejarlo vacío):

> 406 conversaciones medidas en 7 semanas. El 54% llegó fuera de horario. Esto es lo que hicimos.

---

## Cifras usadas

Todas provienen del piloto real de 7 semanas (junio–julio 2026) y son verificables
en los informes publicados del caso.

| Cifra | Dónde aparece |
|---|---|
| 54% escribió fuera de horario hábil | Apertura + tira de cifras |
| 406 conversaciones atendidas | Apertura + bloque de Antonia |
| 76 horas recuperadas al equipo | Tira de cifras |
| 89% de interesados no calificaba | Bloque de prueba (hallazgo de Clara) |
| Costo por reunión: US$71 → US$8 | Bloque de prueba |
| Agendas por semana: 1,1 → 8,6 | Bloque de prueba |

**Nota:** el correo describe al cliente como "una corredora inmobiliaria de Santiago",
sin nombrarlo. Si hay autorización para nombrarlo, la prueba gana fuerza.

---

## Estructura

| Bloque | Agentes | Rol |
|---|---|---|
| 01 · Atrae | Sofía, Matías | Piezas, textos y gestión de campañas en Meta |
| 02 · Atiende | Antonia | WhatsApp 24/7, califica y agenda |
| 03 · Mide | Amanda, Lucas | Notas de reunión y evaluación con rúbrica |
| 04 · Aprende | Clara, Laura | Auditoría semanal y coaching del equipo humano |

Después del bloque 04 va una tarjeta de prueba en azul de marca que muestra la
auditoría de Clara en acción. Es el cierre del argumento: el sistema no solo trabaja,
corrige el rumbo.

El correo **no incluye video**. El P.D. ofrece el informe completo del piloto como
segunda salida para quien no quiere comprometer agenda todavía.

---

## Identidad de marca

Tokens tomados en vivo de `domo-ia.com`, no interpretados del logo.

| Token | Hex | Uso en el correo |
|---|---|---|
| `--bg` | `#F6F3EC` | Fondo general |
| `--surface` | `#FFFFFF` | Tarjeta principal y cabecera |
| `--surface2` | `#F0EBE0` | Fondo de los 4 bloques de agentes |
| `--text` | `#1C2340` | Texto principal y títulos |
| `--muted` | `#5D6478` | Texto secundario y pie |
| `--border` | `#E2DCCC` | Bordes y separadores |
| `--brand` | `#33508F` | Tarjeta de prueba, enlaces |
| `--brand2` | `#D98E3A` | Rótulos, botón CTA, anillo de los avatares |
| `--chip` | `#F3E8D2` | Tira de cifras de apertura |
| `--deep` | `#1B2340` | Bloque de video |

**Tipografía:** `Archivo` en títulos y cifras, `IBM Plex Sans` en texto corrido,
`IBM Plex Mono` en rótulos — la misma jerarquía del sitio. Se cargan por `@import`
para los clientes que lo permiten, con fallback a `Segoe UI / Helvetica / Arial`
en Gmail y Outlook, que no cargan fuentes web.

**Radios:** 14 px en tarjetas, 12 px en bloques, 10 px en elementos internos,
99 px en el botón. Iguales a `--radius-card`, `--radius-md`, `--radius-sm` y
`--radius-pill` del sitio.

**Logo:** renderizado desde el mismo SVG inline del header de domo-ia.com
(arco `#1C2340` + punto `#D98E3A`) con la tipografía Archivo a `wdth 125`,
que es como está definido en `.mark`.

---

## Compatibilidad

- Ancho 600 px, tablas y estilos inline.
- Botón con VML para que Outlook de escritorio lo muestre como píldora.
- Media query que apila avatares y columnas bajo 620 px.
- **Conviene pasarlo por Litmus o Email on Acid antes del primer envío masivo.**

---

## Antes de enviar

- [ ] Reemplazar `[URL_AGENDA]` y `[URL_BAJA]`.
- [ ] Reemplazar `{{nombre}}`, `{{empresa}}`, `{{remitente_nombre}}`, `{{remitente_cargo}}`, `{{remitente_telefono}}`, `{{direccion_empresa}}`.
- [ ] **Fallback de `{{nombre}}`:** si hay registros sin nombre, poner `Hola,` a secas.
- [ ] Tener listo el informe del piloto para mandarlo a quien responda al P.D.
- [ ] Pasar los enlaces por `domo-ia.com` en vez de mezclar dominios: protege la entregabilidad.
- [ ] Enlace de baja funcionando, obligatorio en envío masivo.
- [ ] Confirmar si se puede nombrar al cliente del piloto.
