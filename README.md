# Ionex AI — Landing

Landing de una sola página para Ionex AI (servicios de IA/automatización propios del usuario). Contenido y código escritos a mano — no hay web previa que "cazar" (no aplicó la skill `cazador-de-webs`/Kimi K3), así que Claude armó todo directo.

## Historial de diseño (2026-08-11)
1. **v1 — túnel 3D** (`motion-kit` de `Downloads\kit-cazador-webs\`): pensado para fotos reales que se ocultan unas a otras. Con contenido de solo texto varios shots quedaban visibles a la vez y las letras se superponían (bug real). Descartado.
2. **v2 — scroll simple con motion-kit:** secciones apiladas con `mk-reveal`/`mk-split`. Funcional pero el usuario quería más nivel de producción.
3. **v3 (actual) — estructura propia inspirada en [krea.uy](https://krea.uy)**, agencia real de Uruguay que el usuario señaló como referencia de calidad. Se tomó la **estructura y patrones técnicos** (nav que aparece al hacer scroll, preloader con efecto de tipeo, ticker/marquee, grilla de servicios partida en 2, sección "por qué elegirnos" con tarjetas, contacto con 3 tarjetas, footer con columnas, grupo de botones flotantes sutiles con tooltip) — **no** su contenido ni su color de marca (rojo). Todo el código de `site.css`/`index.html` es propio, reescrito desde cero con la paleta y el copy de Ionex. Ya no depende de `motion-kit` (se eliminó `assets/css/motion.css` y `assets/js/motion.js`, sin uso).

## Estructura
```
ionex/
├── index.html          ← toda la landing (1 sola página)
├── assets/
│   ├── css/site.css    ← toda la hoja de estilos (navy #0B1220 + blanco, tipografía Outfit/Inter vía Google Fonts)
│   └── img/            ← vacío, para logo/fotos cuando existan
```

## Posicionamiento (reescrito 2026-08-11 — cambio importante, no repetir el error anterior)
La landing NO vende "un agente de WhatsApp para clínicas". Vende **auditoría/diagnóstico primero**: el Hero abre con "Antes de proponerte nada, te mostramos dónde estás perdiendo tiempo y plata" — automatización e IA aparecen como la solución que puede salir de esa auditoría, no como el producto de entrada. El copy es genérico (cualquier negocio), con **una sola mención explícita a clínicas**: el bloque "Ejemplo real: en una clínica" dentro de la sección "Así funciona el agente" — ahí sí se detalla el caso concreto, en el resto de la página no se nombra el nicho.

## Secciones (de arriba a abajo, reestructurado 2026-08-12 — ver "Consolidación de Servicios" abajo)
Preloader (tipea "IONEX") → Nav fija (centrada de verdad con position:absolute, no con flex space-between) → Hero (diagnóstico/auditoría-led, una sola frase: "Soluciones tecnológicas para tu negocio, aplicando IA donde realmente suma.") → Ticker → **Servicios: UNA sola sección, 4 puntos numerados** (01 Automatización de procesos, 02 Chatbots y Agentes, 03 Diseño Web, 04 Sistema de Atención 24 Horas — este último trae TODO el detalle: 7 pasos, ejemplo de clínica, y el proceso de instalación de 4 pasos que antes era su propia sección "Cómo trabajamos") → Antes / Después (2 columnas) → Ventajas (3 tarjetas: $0, 1:1, UY) → Confianza y transparencia (3 filas) → FAQ (acordeón nativo + schema FAQPage) → Contacto (3 tarjetas, sin mostrar el teléfono) → Footer → Grupo flotante.

### Consolidación de Servicios (2026-08-12)
El usuario señaló `krea.uy` como referencia pero además pidió corregir algo puntual: la landing tenía el contenido de servicios **disperso** (2 tiles arriba + una sección aparte "Así funciona el agente" + otra sección aparte "Catálogo ampliado"). Se fusionó todo en una sola sección `#servicios` con 4 bloques numerados — el 04 concentra lo que antes eran 2 secciones separadas (el deep-dive del agente + el proceso "Cómo trabajamos"). Se sacó también: la tarjeta "99% Arquitectura confiable" y la fila "Sin doble reserva" (el usuario los consideró ruido), la palabra "WhatsApp" de la fila "Todo a tu nombre", y el número de teléfono visible en la tarjeta de contacto.

**Detalle de timing de recordatorios:** decisión explícita del usuario, **24 horas y 3 horas antes** (no 48h/24h que es lo que usa el resto del catálogo técnico en otras memorias) — aplica en 4 lugares del texto: tile de servicios, catálogo, paso 5 del deep-dive del agente, y el ejemplo de la clínica. Si se retoca la landing, mantener consistencia entre los 4.

**Fuente del contenido ampliado:** el usuario pidió revisar todo lo estudiado en `project_recursos_tecnicos` (catálogo La Tribu Divisual) para que la landing no fuera solo el reciclado de los 3 posts de IG. Catálogo y confianza salen de ahí — pero **a propósito no se prometen** el agente de voz (sin estudiar aún), el RAG de e-commerce (tiene una vulnerabilidad de SQL libre sin corregir en el template original), WordPress (el usuario lo descartó explícitamente en esta pasada) ni nada de contenido/video viral (tono no encaja con el perfil profesional de Ionex).

Sin sección de casos/clientes todavía (decisión explícita: sumar el caso SANEX recién cuando esa web esté terminada y en vivo). Sin formularios — contacto solo por WhatsApp, Instagram y mail. Sin calculadora interactiva (el usuario la descartó, se quedó solo con las preguntas como texto dentro del deep-dive/contraste).

## Datos de contacto usados
- WhatsApp: `59897535033` (confirmado por el usuario, formato internacional UY sin el 0)
- Instagram: `@ionex.ai`
- Mail: `contacto@ionex.ai`

## SEO (aplicado 2026-08-12 con la skill `seo-optimizer` de `web-clientes-template`)
La skill está pensada para el template de 4 páginas — se adaptó a mano para 1 sola página. Aplicado: `meta robots`/`author`, Twitter Card, `og:site_name`, Schema.org `ProfessionalService` ampliado (email, `addressCountry: UY`, sin teléfono ni `priceRange` a propósito — el usuario no quiere el número visible ni precios públicos en ningún lado, ni siquiera en datos invisibles), `sitemap.xml` y `robots.txt` en la raíz. **Marcado `<!-- REVISAR -->` en el `<head>`:** falta `og:image` (1200x630) — no hay ninguna foto/imagen real todavía.

## Pendiente antes de publicar
- [ ] Logo real (hoy es wordmark de texto "IONEX" — coincide con la foto de perfil de IG; si aparece un archivo de logo, meterlo en `assets/img/`)
- [ ] Imagen para `og:image` (1200x630) — cómo se ve el link al compartirlo en WhatsApp/redes, hoy no hay ninguna
- [ ] Confirmar que `contacto@ionex.ai` existe y recibe mail (si no, crear el alias o cambiar a otro real) — **ojo:** el sitio web quedó en `ionex.agency` (2026-08-12 — `.ai`, `.com`, `ionexai.com`, `ionex.uy`, y como 15 variantes más estaban todas ocupadas por especuladores de dominios, confirmado con WHOIS real; `.agency` encaja bien igual porque literalmente es una agencia), queda un mail `@ionex.ai` con web en `.agency` — decidir si conviene unificar el mail más adelante
- [x] Conectar dominio real → comprado en Hostinger: **`ionex.agency`** ($3.99 primer año, renueva a $35.99/año el 2027-08-12). `index.html`, `sitemap.xml` y `robots.txt` ya actualizados a `https://ionex.agency/`. Falta: conectar el DNS en Vercel (Settings → Domains → Añadir existente) y copiar los registros en el panel DNS de Hostinger
- [ ] Publicar vía GitHub + Vercel (mismo patrón que el resto de los proyectos, ver memoria `project_vps_hosting_webs`) — el usuario lo está haciendo él mismo, tiene los pasos
- [ ] Una vez con dominio conectado: dar de alta el sitio en Google Search Console (requiere la cuenta de Google del usuario, no lo puede hacer Claude)
- [ ] Una vez en vivo: tomar el screenshot real para el 3er post de Instagram (pieza de prueba, no prompt de IA)

## Cómo previsualizar
Abrir `index.html` directo en el navegador (todo es CSS/JS vanilla, sin build ni servidor) o con Live Server si se prefiere auto-reload.
