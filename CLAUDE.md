# The Groomer's House — Contexto del proyecto

> Sistema de diseño completo (colores, tipografía, componentes, mobile): ver `BRANDING.md`

## Información del negocio

**Nombre:** The Groomer's House  
**Propietaria:** Silvia Acelas  
**Experiencia:** 8 años en grooming canino profesional  
**Dirección:** Cra. 38a # 204C-21, Floridablanca, Santander, Colombia  
**WhatsApp:** +57 320 402 2533  
**Instagram:** https://www.instagram.com/the_groomers_house  

## Qué es este proyecto

Landing page estática de una sola página (`index.html`) para una peluquería canina premium en Floridablanca, Santander. El objetivo principal es convertir visitantes en clientes vía WhatsApp. No hay framework — solo HTML, CSS y JS vanilla embebidos en un solo archivo.

## Objetivo de conversión

Todo el diseño apunta a un único CTA: abrir WhatsApp con mensaje prellenado.  
URL del CTA: `https://wa.me/573204022533?text=Hola%2C%20quiero%20agendar%20una%20cita%20para%20mi%20mascota`

## Servicios ofrecidos

1. **Baño y Cuidado** — baño con productos hipoalergénicos, limpieza de orejas, secado suave
2. **Corte y Estilizado** — cortes de autor adaptados a cada raza
3. **Cuidado del Pelaje** — tratamientos nutritivos, desenredo, cepillado profundo
4. **Secado Profesional** — equipos de bajo ruido y temperatura controlada
5. **Cuidado de Uñas** — corte y lima con herramientas esterilizadas

## Decisiones arquitectónicas

- **Todo en un solo `index.html`** — CSS y JS embebidos. No hay framework ni build step. Un solo request HTTP, fácil de desplegar en cualquier hosting estático. No separar en archivos a menos que el sitio crezca a múltiples páginas.

## Estructura de secciones

| Sección | ID | Descripción |
|---|---|---|
| Navbar | `#navbar` | Fijo, se oscurece al hacer scroll |
| Hero | `#hero` | Imagen estática de Martín (`hero1_MartinFix.png`), sin slider |
| Trust bar | — | Banda dorada con 4 credenciales (en móvil solo muestra 2) |
| Servicios | `#servicios` | Grid de 5 tarjetas con hover reveal + GIF animado en hover; descripción siempre visible en móvil |
| Antes/Después | `#antes-despues` | Slider interactivo drag/click; touch-action split: pan-y en wrapper, none en handle; hint animation al entrar al viewport |
| Sobre Silvia | `#silvia` | Foto + bio + certificaciones |
| Proceso | `#proceso` | 4 pasos numerados — oculto en móvil (`display: none`) |
| Testimonios | `#testimonios` | 3 reseñas placeholder |
| Galería | `#galeria` | Grid tipo revista con todas las fotos |
| Ubicación | `#ubicacion` | Google Maps embed + datos de contacto |
| CTA final | `#cta-final` | Botón WhatsApp grande con efecto shimmer; full-width en móvil |
| Footer | — | 3 columnas desktop; móvil: brand full-width + servicios/contacto en 2 columnas |
| WhatsApp flotante | — | Botón verde fijo esquina inferior derecha |

## Imágenes disponibles en /public

| Archivo | Uso |
|---|---|
| `logo.jpg` | Logo en navbar y footer |
| `hero1_MartinFix.png` | Hero estático principal (Golden Retriever "Martín") — versión outpainted por Gemini, cara completa visible con letrero al fondo |
| `hero2_Kira.jpg` | Slide 2 del hero (perro pequeño "Kira") — posición `center 65%`, bien encuadrado |
| `hero3_Luca.jpg` | Slide 3 del hero (Collie "Luca") — posición `55% 30%` |
| `antes.png` | Imagen "Antes" del slider de comparación |
| `despues.png` | Imagen "Después" del slider de comparación |
| `servicio-bano-cuidado.png` | Tarjeta servicio Baño y Cuidado (imagen estática en reposo) |
| `servicio-bano-cuidado.gif` | GIF animado hover — Baño y Cuidado (480×600, ~1.1 MB) |
| `servicio-corte-estilizado.png` | Tarjeta servicio Corte y Estilizado (imagen estática en reposo) |
| `servicio-corte-estilizado.gif` | GIF animado hover — Corte y Estilizado (480×600, ~1.1 MB) |
| `servicio-cuidado-pelaje.png` | Tarjeta servicio Cuidado del Pelaje (imagen estática en reposo) |
| `servicio-cuidado-pelaje.gif` | GIF animado hover — Cuidado del Pelaje (480×600, ~1.1 MB) |
| `servicio-secado-profesional.png` | Tarjeta servicio Secado Profesional (imagen estática en reposo) |
| `servicio-secado-profesional.gif` | GIF animado hover — Secado Profesional (480×600, ~1.1 MB) |
| `servicio-cuidado-unas.png` | Tarjeta servicio Cuidado de Uñas (imagen estática en reposo) |
| `servicio-cuidado-unas.gif` | GIF animado hover — Cuidado de Uñas (480×600, ~1.1 MB) |
| `silvia-estilista.jpg.jpg` | Foto de Silvia (nota: nombre con doble extensión) |
| `fachada.jpg` | Fachada del local — usada como imagen grande en galería |
| `letrero_entrada.jpg` | Letrero de entrada — usada en galería |

## Decisiones de diseño móvil

- Hamburger toggle (3 líneas): abre y cierra el menú en el mismo botón — sin botón X
- Hero: `100svh`, `object-position: 58% 35% !important` en móvil con `!important` para override del inline style
- Before/After slider: `syncBeforeWidth()` JS fija `beforeImg.style.width = slider.offsetWidth + 'px'` en load y resize
- Footer móvil: `grid-template-columns: 1fr 1fr` + `footer-brand { grid-column: 1 / -1 }`
- Sección proceso: `display: none` en móvil

## Pendientes conocidos
- Los testimonios son placeholders realistas — reemplazar con reseñas reales cuando estén disponibles
- Las certificaciones de Silvia en la sección "About" son genéricas — confirmar con la propietaria cuáles son reales
- Horario de atención sin confirmar con Silvia (actualmente: Lun–Sáb 8am–6pm, Dom con cita)

## SEO

- **H1 único:** "Peluquería canina en Floridablanca"
- **Keywords primarias:** peluquería canina Floridablanca, grooming canino Bucaramanga, estética canina Santander
- **Meta title:** "Peluquería Canina en Floridablanca | The Groomer's House"
- **Meta description:** incluye Floridablanca, Santander, Bucaramanga, grooming canino
- Estructura H1 → H2 → H3 correcta en toda la página
- Google Maps embed con `title` y `referrerpolicy`

## Google Maps embed

URL actual (mapa normal, no Street View):
```html
<iframe src="https://maps.google.com/maps?q=7.060762,-73.080845&z=17&hl=es&output=embed" ...></iframe>
```
Dark mode via CSS: `filter: invert(1) hue-rotate(180deg) brightness(0.85) saturate(0.9)`

## Horario de atención (placeholder)

- Lunes a Sábado: 8:00 am – 6:00 pm
- Domingos: con cita previa

*Confirmar horario real con Silvia.*

## Tecnología

- HTML5 semántico
- CSS3 puro (variables, grid, flexbox, animaciones, IntersectionObserver)
- JS vanilla (before/after drag, scroll reveal, navbar scroll, mobile menu toggle, GIF hover swap + preload, before/after hint animation)
- Fuentes: Google Fonts (Cormorant Garamond + Montserrat)
- Sin dependencias externas, sin frameworks, sin build step
- Un solo archivo `index.html` — listo para servir en cualquier hosting estático (GitHub Pages, Netlify, etc.)
