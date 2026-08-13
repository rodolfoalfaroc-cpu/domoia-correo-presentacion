# DOMOIA — Correo de presentación

Correo de presentación para envío masivo. Presenta al equipo de agentes de DOMOIA
partiendo desde una problemática concreta (prospectos que escriben fuera de horario)
y lleva a agendar una reunión.

**→ [Ver el correo renderizado](https://rodolfoalfaroc-cpu.github.io/domoia-correo-presentacion/)**

---

## Archivos

| Archivo | Para qué |
|---|---|
| `index.html` | Vista previa con datos de ejemplo. Es lo que abre el link de arriba. |
| `email-template.html` | **Plantilla de producción.** Esta es la que se pega en la herramienta de envío. |
| `assets/domoia-logo-email.png` | Logo optimizado para correo, 440 × 89 px, fondo navy `#1c2340`. |

El logo ya está alojado y la plantilla lo apunta directo, así que funciona sin configurar nada:

```
https://rodolfoalfaroc-cpu.github.io/domoia-correo-presentacion/assets/domoia-logo-email.png
```

---

## Asunto

**Recomendado:** `¿A qué hora te escribió el último cliente?`

Alternativas para A/B testear:

- `El mensaje de las 22:47`
- `Lo que pasa con tus prospectos fuera de horario`
- `{{empresa}} y los mensajes sin responder`

**Preheader** (no dejarlo vacío):

> Un equipo de agentes que responde, califica y agenda mientras tú duermes. 90 segundos para verlo.

---

## Estructura

El correo recorre el ciclo completo del sistema. Cada bloque nombra a los agentes que participan.

| Bloque | Agentes | Rol |
|---|---|---|
| 01 · Atrae | Sofía, Matías | Contenido y campañas en Meta |
| 02 · Atiende | Antonia | WhatsApp 24/7, califica y agenda |
| 03 · Mide | Amanda, Lucas | Seguimiento de la conversión |
| 04 · Aprende | Clara, Laura | Auditoría y mejora continua |

El bloque 04 es el único sobre fondo navy: la jerarquía visual refuerza que el
aprendizaje continuo es el argumento diferenciador.

---

## Identidad de marca

Los tokens salen de la landing oficial, no de una interpretación del logo.

| Token | Hex | Uso |
|---|---|---|
| `navy` | `#1b2340` | Cabecera, bloque 04, títulos |
| `navy-3` | `#141b33` | Fondo del bloque de video |
| `gold` | `#d98e3a` | Botón CTA, filete, bordes de bloque |
| `gold-2` | `#e8a951` | Acentos sobre fondo oscuro |
| `amber-ink` | `#a06a1f` | Rótulos dorados sobre fondo claro |
| `cream` | `#f6f3ec` | Fondo general |
| `soft` | `#f0ebe0` | Fondo de bloques 01–03 |
| `ink` | `#1f283c` | Texto principal |
| `muted` | `#5d6478` | Texto secundario y pie |
| `line` | `#e2dccc` | Bordes y separadores |

**Tipografía:** `'Segoe UI', Helvetica, Arial`. Sin fuentes web — Outlook no las carga.

**Contraste:** el dorado de marca no es legible como texto pequeño sobre crema.
Los rótulos sobre fondo claro usan `#a06a1f` (amber-ink), que la landing ya define
para ese caso. Sobre navy sí va `#e8a951` pleno.

---

## Compatibilidad

- Ancho 600 px, maquetado con tablas y estilos inline.
- Botón con VML para que Outlook de escritorio lo renderice como píldora.
- Probado conceptualmente contra Gmail, Outlook y Apple Mail. **Conviene pasarlo por
  Litmus o Email on Acid antes del primer envío masivo.**

---

## Antes de enviar

- [ ] Reemplazar `[URL_AGENDA]`, `[URL_VIDEO]`, `[URL_MINIATURA]`, `[URL_BAJA]`.
- [ ] Reemplazar `{{nombre}}`, `{{empresa}}`, `{{remitente_nombre}}`, `{{remitente_cargo}}`, `{{remitente_telefono}}`, `{{direccion_empresa}}`.
- [ ] **Fallback de `{{nombre}}`:** si hay registros sin nombre, poner `Hola,` a secas. Un `Hola {{nombre}},` vacío mata la credibilidad del correo completo.
- [ ] La miniatura del video tiene que ser una imagen alojada (1000 px de ancho, se muestra a 500) con el play dibujado encima. Los videos incrustados no funcionan en ningún cliente de correo.
- [ ] Pasar los enlaces por `domo-ia.com` en vez de mezclar dominios (YouTube, Calendly): protege la entregabilidad.
- [ ] Enlace de baja funcionando, obligatorio en envío masivo.

## Pendiente de decisión

El correo **no incluye ninguna cifra**. La landing menciona el resultado del piloto
(costo por reunión agendada de US$71 a US$8 en 6 semanas). Si ese dato es publicable
en frío, la línea de cierre gana bastante — pero requiere confirmación antes de usarlo.
