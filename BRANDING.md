# The Groomer's House — Branding Guide

## Identidad de marca

**Posicionamiento:** Peluquería canina premium / lujo accesible  
**Tono:** Elegante, cálido, confiable — nunca genérico ni cursi  
**Personalidad:** Profesional con alma, experta pero cercana  
**Promesa:** Tu mascota merece verse — y sentirse — extraordinaria  

---

## Paleta de colores

### Colores principales

| Nombre | Variable CSS | Hex | Uso |
|---|---|---|---|
| Gold | `--gold` | `#C9A84C` | CTAs primarios, acentos, labels, líneas decorativas |
| Gold Light | `--gold-light` | `#E2C07A` | Texto italic en H1/H2, hover states suaves |
| Gold Dark | `--gold-dark` | `#9A7A30` | Bordes dorados, badge de fondo, logo border |
| Black | `--black` | `#0A0A0A` | Fondo base de la página |
| Black Soft | `--black-soft` | `#111111` | Fondos de secciones alternadas |
| Black Card | `--black-card` | `#161616` | Tarjetas, process steps |
| Black Border | `--black-border` | `#222222` | Bordes sutiles entre elementos |
| White | `--white` | `#FAFAFA` | Texto principal |
| White Muted | `--white-muted` | `#B8B8B8` | Texto secundario, descripciones, meta |

### Regla de uso de color

- **Negro** domina — es el lienzo
- **Dorado** es el acento — se usa con moderación para mantener el peso visual
- **Blanco** es el texto — nunca fondos blancos
- Nunca usar colores brillantes o saturados fuera de la paleta

---

## Tipografía

### Fuentes

| Familia | Variable CSS | Tipo | Fuente |
|---|---|---|---|
| Cormorant Garamond | `--serif` | Serif display | Google Fonts |
| Montserrat | `--sans` | Sans-serif UI | Google Fonts |

### Import

```css
@import url('https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=Montserrat:wght@300;400;500;600&display=swap');
```

### Jerarquía tipográfica

| Elemento | Fuente | Peso | Tamaño | Notas |
|---|---|---|---|---|
| H1 hero | Cormorant Garamond | 300 | `clamp(2.5rem, 7vw, 6rem)` | Italic en la parte gold |
| H2 secciones | Cormorant Garamond | 300 | `clamp(2rem, 5vw, 3.5rem)` | `line-height: 1.15` |
| Section labels | Montserrat | 600 | `11px` | `letter-spacing: 4px`, uppercase, color gold |
| Body | Montserrat | 300–400 | `0.95rem` | `line-height: 1.8–1.9` |
| Botones | Montserrat | 600 | `12–13px` | `letter-spacing: 2–3px`, uppercase |
| Números decorativos | Cormorant Garamond | 300 | `4rem` | Opacity baja (0.15), solo decorativos |

### Principios tipográficos

- Las H1/H2 siempre tienen al menos una palabra o frase en `<em>` con color `--gold-light`
- Los labels de sección van en Montserrat ALL CAPS con letter-spacing amplio y color dorado
- El body nunca supera `1.1rem` — la elegancia está en el espacio, no en el tamaño
- Las líneas doradas decorativas (`gold-line`) separan el label del título en cada sección

---

## Componentes UI

### Botón primario (WhatsApp CTA)

```css
background: var(--gold);
color: var(--black);
font-family: var(--sans);
font-size: 13px;
font-weight: 600;
letter-spacing: 2px;
text-transform: uppercase;
padding: 16px 36px;
transition: background 0.3s, transform 0.2s, box-shadow 0.3s;
/* hover: gold-light + translateY(-2px) + gold shadow */
```

### Botón secundario (outline)

```css
background: transparent;
color: var(--gold);
border: 1px solid var(--gold);
/* hover: fill gold, color black */
```

### Línea decorativa dorada

```css
width: 60px;
height: 1px;
background: linear-gradient(90deg, var(--gold), transparent);
margin: 24px 0;
```

### Tarjetas de servicio

- Fondo `--black-card`
- Imagen con `filter: brightness(0.7) saturate(0.8)` en reposo
- Hover: `brightness(0.5) saturate(0.6)` + `scale(1.07)` en imagen
- Descripción oculta que aparece con `max-height` transition en hover
- Gold bar inferior que se extiende de 0 a 40px en hover

---

## Estilo visual / Mood

### Filosofía de diseño

- **Dark luxury** — negro profundo como base, toques dorados como joyería
- **Natural contrast** — las fotos de perros con fondos verdes naturales contrastan con la UI oscura
- **Elegant restraint** — mucho espacio negativo, pocos elementos decorativos
- **Texture through photography** — la riqueza visual viene de las imágenes, no de gradientes complejos

### Google Maps dark mode

El embed de Google Maps no tiene dark mode nativo. Se logra con filtro CSS:

```css
/* Reposo — dark theme */
filter: invert(1) hue-rotate(180deg) brightness(0.85) saturate(0.9);

/* Hover — ligeramente más vivo */
filter: invert(1) hue-rotate(180deg) brightness(1) saturate(1.1);
```

`invert(1)` voltea los colores (fondo claro → oscuro), `hue-rotate(180deg)` corrige los tonos para que el verde de vegetación y el azul del agua no queden con colores extraños.

### Overlays en imágenes hero

```css
/* Overlay principal — preserva visibilidad del perro en zona media */
background: linear-gradient(to top,
  rgba(10,10,10,0.92) 0%,   /* texto encima oscuro */
  rgba(10,10,10,0.18) 45%,  /* zona de la imagen respira */
  rgba(10,10,10,0.08) 100%  /* top casi transparente */
);

/* Brillo de las imágenes hero */
filter: brightness(0.62);
```

### Animaciones

| Tipo | Duración | Easing | Uso |
|---|---|---|---|
| Fade up (hero) | `0.8s` | `ease` | Elementos del hero al cargar |
| Scroll reveal | `0.8s` | `ease` | Elementos al entrar al viewport (`threshold: 0.12`) |
| Slider hero | — | — | Eliminado — hero es imagen estática (mejor CWV y conversión) |
| Hover cards | `0.5–0.8s` | `cubic-bezier(0.25, 0.46, 0.45, 0.94)` | Imágenes de servicio y galería |
| WA float pulse | `3s` | `ease-in-out` | Botón flotante de WhatsApp |

### Principios de animación

- Siempre sutiles — nunca distractoras
- Solo `opacity` y `transform` para performance (GPU)
- Los hover deben sentirse lujosos, no rápidos — duración mínima 0.3s

---

## Espaciado

| Contexto | Valor |
|---|---|
| Padding de secciones grandes | `120px 0` |
| Padding sección CTA final | `160px 0` |
| Gap entre columnas principales | `80px` |
| Gap grids de tarjetas | `2px` (intencionalmente mínimo) |
| Padding interno de tarjetas | `32–48px` |

El `gap: 2px` entre tarjetas es una decisión de diseño intencional — crea líneas divisorias casi imperceptibles que estructuran sin dividir agresivamente.

---

## Mobile (max-width: 768px)

### Breakpoints

| Breakpoint | Uso |
|---|---|
| `768px` | Breakpoint principal — todos los cambios mobile van aquí |
| `480px` | Solo para servicios grid (1 columna forzada) |

### Reglas mobile específicas

- **Hero:** `100svh`, overlay más denso (`.97` abajo), `object-position: 58% 35% !important` (override inline style requiere `!important`)
- **Trust bar:** Muestra solo los 2 primeros ítems (`nth-child(3,4)` → `display: none`)
- **Servicios:** Descripción de tarjeta siempre visible en mobile (no se oculta en hover)
- **Proceso:** `display: none` — sección omitida en móvil
- **Footer:** `grid-template-columns: 1fr 1fr` + `footer-brand { grid-column: 1 / -1 }` — brand ocupa fila completa, columnas servicios/contacto lado a lado
- **CTAs:** `width: 100%; justify-content: center` — siempre full-width en mobile
- **Floating WA:** `bottom: 52px; right: 20px`

### Principios mobile

- Reducir spacing — no eliminar — mantener la jerarquía visual
- Los párrafos secundarios se pueden omitir; el copy esencial siempre presente
- Nada de hover en mobile — los estados hover se convierten en estado base

---

## Recursos de marca

| Recurso | Archivo |
|---|---|
| Logo | `public/logo.jpg` |
| WhatsApp | `+57 320 402 2533` |
| Instagram | `@the_groomers_house` |
| URL Instagram | `https://www.instagram.com/the_groomers_house` |

### Icono de WhatsApp

SVG inline — path estándar del logo de WhatsApp, fill con color del contexto (negro en botón dorado, blanco en botón verde flotante).

---

## Lo que NO hacer

- No usar fondos blancos o grises claros en ninguna sección
- No usar fuentes distintas a Cormorant Garamond y Montserrat
- No usar colores fuera de la paleta definida
- No usar bordes gruesos ni sombras de caja llamativas
- No usar animaciones rápidas o rebotes — nada de `bounce` o `elastic`
- No añadir iconos decorativos genéricos — solo íconos funcionales (WhatsApp, Instagram, ubicación)
- No usar emojis en el copy
- No centrar el texto de los párrafos (solo los títulos de sección y el CTA final van centrados)
