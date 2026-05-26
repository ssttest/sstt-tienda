# SSTT — Visión "Amazon de la seguridad" · Roadmap

> Generado en sesión s74. Documento de referencia para futuras sesiones.

## Contexto

Single HTML file (~6.2 MB, 81,131 líneas) deployado en GitHub Pages
`ssttest.github.io/sstt-tienda/index.html`. Sin backend propio. Proxy AI
en Cloudflare Worker `sstt-proxy.ryanodina.workers.dev`.

## ✅ Lo que ya existe en el sitio

### Catálogo y producto
- 1,079 productos con datos técnicos; ~980 entradas SSTT_DATA enriquecidas
- FOV calculator con 406 cámaras; DORI, IR coverage, PoE budget, UPS, Bitrate
- 22 herramientas técnicas del Mesón Técnico
- Modal de producto con compatibilidades + fichas PDF
- Auditor de imágenes DMSS (modo voz)

### Comercial y operativo
- Carro con cálculo de tarifa por tier (Mayorista/Prime/Preferencial/General)
- Checkout funcional con WebPay + Khipu
- **Bsale ya emite factura electrónica automáticamente** (refs: 11 en código)
- 21k clientes en dataset (3 demos activos)
- e-RUT con validación, ahora con múltiples por cliente (lista en localStorage)
- Sistema de favoritos/wishlist completo
- Métodos de pago guardados por cliente
- Tickets, agencia, despacho, retiro, seguimiento

### IA y soporte
- 3 asesores IA (WhatsApp, Cotizador, Orb técnico)
- SSTT_KB con 629 entradas
- Modo voz STT/TTS

### Engagement
- Loyalty tiers (White/Silver/Gold/Black) con tarjeta física, flip 3D, QR
- Dashboard de cliente con cotizaciones/pedidos/tickets demo
- Visor de pedido → ciclo factura → e-RUT frente → verificación SII
- Selector de e-RUT cuando hay múltiples

### SEO + Marketing
- Open Graph, Twitter cards, structured data, meta description
- Google Analytics ya integrado

### Seguridad básica
- 2FA presente, CSP, sin `eval()`, login con try/catch

---

## ❌ Lo que falta para ser referencia mundial

### 1. Confianza y prueba social (CRÍTICO)
- **Sin sistema de reviews real** (solo menciones en texto)
- **Sin Q&A público en producto**
- **Sin badges** "compra verificada", "instalador certificado", "tester pro"
- **Sin media en reviews** — fotos/videos del cliente
- **Sin ranking de categoría** ("#1 más vendido en domos IP 4MP")

### 2. Seguridad real (CRÍTICO para sitio mundial)
- **244 usos de `innerHTML`** — superficie de XSS importante (DOMPurify pendiente)
- **Sin rate limiting visible en login** — brute-force posible
- **Sin CAPTCHA** en formularios públicos
- **CSP existe** pero validar que sea estricta (sin `unsafe-inline`)
- **Sin honeypot fields** en formularios
- **Sin Subresource Integrity** en scripts externos
- **localStorage tiene datos sensibles** — RUTs, e-RUT, pagos (cifrar o sessionStorage)
- **Sin política de cookies / banner GDPR**

### 3. Engagement / Loyalty avanzado
- Loyalty actual es **solo cosmético** — no hay acumulación real de puntos
- **Sin gamificación** (badges por hitos)
- **Sin referidos** (código único, ambos ganan)
- **Sin programa "Pro" / instaladores certificados** con marketplace
- **Sin newsletter** por categoría
- **Sin notificaciones push** (requiere PWA)

### 4. PWA y mobile real (CRÍTICO en 2026)
- **Sin manifest.json** → no se instala como app
- **Sin Service Worker** → no funciona offline, sin cache estratégico
- **Sin apple-touch-icon**
- **Sin theme-color**

### 5. Personalización inteligente
- **Sin "frecuentemente comprados juntos"**
- **Sin "los clientes que vieron X también vieron Y"**
- **Sin historial de navegación** persistente
- **Sin "continúa donde quedaste"** entre dispositivos
- **Sin búsqueda por imagen** (auditor existente está medio camino)

### 6. Internacionalización y escala
- **Solo español**, **solo CLP**
- **Sin selector de país/región** con stock/precios por mercado
- **Sin geolocalización** para bodega más cercana

### 7. Comparador y discovery
- **Sin comparador lado a lado** de 2-4 productos
- **Sin filtros avanzados visuales** (sliders precio, marca, tecnología)
- **Sin "Ver alternativas"** desde producto sin stock
- **Sin búsqueda por atributos técnicos** (MP, lente, IP rating, IR)

### 8. Comunidad y B2B
- **Sin foro / comunidad** de instaladores y clientes
- **Sin marketplace de servicios**
- **Sin webinars / academia SSTT** con certificación
- **Sin RFQ para proyectos grandes** con SLA
- **Sin portal B2B con líneas de crédito visibles**

### 9. Integración Bsale más profunda
- Bsale emite factura (ya está) pero podríamos:
  - **Sincronizar stock real en vivo**
  - **Sincronizar precios** según política comercial Bsale
  - **Webhook → email automático** con tracking
  - **Reembolsos** desde panel del cliente

### 10. Confianza institucional
- **Sin sello "Distribuidor Oficial Dahua" verificable**
- **Sin "Sobre nosotros"** con historia, equipo, certificaciones
- **Sin garantías visibles** producto por producto
- **Sin política de devoluciones** clara
- **Sin sello SII / iniciación de actividades** visible

---

## 🎯 Roadmap priorizado — 3 ondas

### ONDA 1 — Más impacto, menos esfuerzo (1-2 sesiones)
Foco: confianza + engagement + PWA básico

1. **Sistema de reviews verificadas** con estrellas, foto del cliente, badge "compra verificada", helpful votes
2. **Q&A público por producto**
3. **PWA mínima viable** — manifest.json + service worker + cache catálogo + offline
4. **Comparador lado a lado** de hasta 4 productos
5. **Sistema de puntos real** — 1 punto/CLP$1.000, canjeable como descuento
6. **Banner de cookies / privacidad** (GDPR-ready)
7. **"Frecuentemente comprados juntos"** desde cart-history local

### ONDA 2 — Construir el moat (3-4 sesiones)
Foco: B2B serio + comunidad + seguridad real

8. **Programa Pro / Instaladores certificados** con marketplace
9. **Referidos** — código único, ambos ganan puntos
10. **Newsletter por categoría** con preferencias
11. **Sanitización XSS completa** — DOMPurify
12. **Honeypot + rate limiting** en formularios públicos
13. **Búsqueda avanzada con filtros visuales** mejorada
14. **Garantía visible** + política de devoluciones

### ONDA 3 — Internacionalización + escala (cuando haya backend real)
Foco: salir de Chile

15. **i18n EN/PT/ES** con `data-i18n` attributes
16. **Multi-moneda** con conversión en vivo
17. **Multi-país** con stock por bodega/región
18. **Webinars/Academia SSTT** con certificación
19. **Foro de la comunidad**
20. **Búsqueda por imagen**

---

## ⚠️ Limitación arquitectónica importante

Single HTML estático en GitHub Pages. Para ser "Amazon real":

- Reviews reales, puntos acumulables, referidos, foro, recomendaciones
  cross-cliente, multi-moneda con stock por país → **requieren backend con DB**
- Sin backend → todo "real" es simulado con `localStorage` por dispositivo

**Dos caminos:**

**A) Demo pulido** — todo simulado con localStorage + datos demo realistas
  · Útil para presentar a inversionistas/prospectos o como prototipo

**B) Migrar a arquitectura con backend** (Supabase / Firebase / Cloudflare
  Workers + D1) — permite "Amazon de la seguridad" real

**Recomendación:** Onda 1 con simulación localStorage ahora (rápido y
vistoso, da algo para presentar) + en paralelo planificar migración a
backend para Onda 2 cuando haya presupuesto/tiempo.
