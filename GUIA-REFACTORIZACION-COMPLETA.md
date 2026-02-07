# GUÍA COMPLETA DE REFACTORIZACIÓN
## Aplicación del Design System Unificado

---

## 📋 CHECKLIST GENERAL PARA TODAS LAS PÁGINAS

### 1. NAVBAR (Idéntica en TODAS las páginas)

```html
<nav class="navbar navbar-expand-md navbar-light" style="background: rgba(255, 255, 255, 0.95); backdrop-filter: blur(10px); border-bottom: 1px solid #e2e8f0; position: fixed; top: 0; left: 0; right: 0; z-index: 1000; padding: 16px 0;">
    <div class="container">
        <a class="navbar-brand" href="index.html" style="font-weight: 700; font-size: 20px; color: #2d3748;">Martin Fernando Mora</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
            <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse justify-content-end" id="navbarNav">
            <ul class="navbar-nav align-items-center">
                <li class="nav-item"><a class="nav-link" href="career.html">Career</a></li>
                <li class="nav-item"><a class="nav-link" href="offerings.html">Offerings</a></li>
                <li class="nav-item"><a class="nav-link" href="case-studies.html">Case Studies</a></li>
                <li class="nav-item"><a class="nav-link" href="blog.html">Insights</a></li>
                <li class="nav-item">
                    <a href="#" onclick="openCalendly(); return false;" class="btn-primary ms-3" style="background: linear-gradient(135deg, #667eea, #764ba2); color: #fff; border-radius: 50px; padding: 12px 28px; font-weight: 600; text-decoration: none;">
                        Schedule a Strategy Call
                    </a>
                </li>
            </ul>
        </div>
    </div>
</nav>
```

**NOTAS CRÍTICAS:**
- Orden EXACTO: Career, Offerings, Case Studies, Insights
- "Blog" se renombra a "Insights"
- Eliminar "Engage" del navbar
- El CTA SIEMPRE dice "Schedule a Strategy Call"
- Clase activa (.active) solo en la página correspondiente

### 2. FOOTER (Idéntico en TODAS las páginas)

```html
<footer style="background: #f8f9fc; border-top: 1px solid #e2e8f0; padding: 48px 24px 32px; margin-top: 80px;">
    <div style="max-width: 1100px; margin: 0 auto; display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 24px;">
        <div style="color: #718096; font-size: 14px;">© 2026 Martin Fernando Mora</div>
        <div style="display: flex; gap: 16px;">
            <a href="https://www.linkedin.com/in/martinfmora/" target="_blank" style="color: #4a5568; font-size: 20px;">
                <i class="fab fa-linkedin"></i>
            </a>
            <a href="mailto:contact@martinfmora.com" style="color: #4a5568; font-size: 20px;">
                <i class="fas fa-envelope"></i>
            </a>
        </div>
    </div>
</footer>
```

**NOTAS CRÍTICAS:**
- SOLO LinkedIn y Email
- Eliminar GitHub y Medium (no refuerzan posicionamiento estratégico)
- Contact queda en footer, no en navbar

### 3. FLOATING CTA BUTTON (En TODAS las páginas)

Agregar antes de cerrar `</body>`:

```html
<!-- Calendly Widget -->
<link href="https://assets.calendly.com/assets/external/widget.css" rel="stylesheet">
<script src="https://assets.calendly.com/assets/external/widget.js" type="text/javascript"></script>
<script>
function openCalendly() {
    Calendly.initPopupWidget({ url: 'https://calendly.com/martin-f-mora/30-minute-meeting' });
    return false;
}
</script>

<!-- Floating Button -->
<div style="position: fixed; bottom: 32px; right: 32px; z-index: 999;">
    <a href="#" onclick="openCalendly(); return false;" style="background: linear-gradient(135deg, #667eea, #764ba2); color: #fff; padding: 14px 22px; border-radius: 50px; font-weight: 600; text-decoration: none; display: flex; align-items: center; gap: 10px; box-shadow: 0 8px 25px rgba(0,0,0,0.25);">
        <i class="fa-regular fa-calendar"></i> Schedule a Strategy Call
    </a>
</div>
```

---

## 📄 AJUSTES ESPECÍFICOS POR PÁGINA

### INDEX.HTML (Homepage)

**Cambios principales:**

1. **Hero Section** - ÚNICO lugar con gradient background
```css
.hero-section {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    padding: 120px 24px 80px;
    margin-top: 64px;
}
```

2. **Resto de secciones** - Fondo blanco o gris claro alterno
```css
.section {
    background: #ffffff; /* o #f8f9fc para alterno */
    padding: 80px 24px;
    max-width: 1100px;
    margin: 0 auto;
}
```

3. **Eliminar:**
- Múltiples fondos con glass/blur fuera del hero
- Tarjetas flotantes con gradientes
- Efectos visuales repetitivos

4. **CTA Hierarchy:**
- Primary CTA: "Schedule a Strategy Call" (navbar + floating + final section)
- Secondary CTAs: "View Case Studies", "See How I Work"
- Eliminar botones "Engage" o "Contact" duplicados

5. **Hero Copy** - Más autoridad, menos explicación:
```
ANTES: "I help organizations navigate the complexity of..."
DESPUÉS: "Strategic Product & Delivery Leadership for Regulated and Scaling Digital Businesses"
```

---

### OFFERINGS.HTML

**Cambios principales:**

1. **NO parece catálogo** - Evitar bullets tácticos como:
   - ❌ "Roadmap creation"
   - ❌ "Workshops"
   - ❌ "Assessments"

2. **SÍ suena estratégico:**
   - ✅ "Structural intervention"
   - ✅ "Governance model design"
   - ✅ "Regulatory alignment"
   - ✅ "Delivery transformation"

3. **Estructura por servicio:**
```
SERVICIO 1: Product Development & Innovation Strategy
  → No es "crear roadmaps"
  → Es "alinear producto con realidad de mercado y compliance"

SERVICIO 2: Organizational Excellence & Delivery Alignment
  → No es "implementar Agile"
  → Es "diseñar gobernanza cross-funcional"

SERVICIO 3: Strategic Advisory & Fractional Leadership
  → No es "consultoría"
  → Es "juicio senior embebido en ejecución"
```

4. **Conexiones explícitas:**
- Cerrar con: "These capabilities are illustrated in my Case Studies"
- Botón a Case Studies
- Referencia a Career: "This model emerges from..."

---

### CASE-STUDIES.HTML

**Cambios principales:**

1. **Estructura tipo memo ejecutivo** - NO storytelling decorativo

Cada caso debe seguir:
```
STRUCTURAL CHALLENGE
  → Problema específico (no "había que mejorar")
  
STRATEGIC REFRAMING
  → De X a Y
  → Cambio conceptual clave

PRODUCT & DELIVERY EXECUTION
  → Qué se hizo estructuralmente
  → No lista de features

OUTCOME
  → Impacto medible
  → Capacidades aplicadas
```

2. **Eliminar:**
- Narrativa tipo "once upon a time"
- Exceso de contexto decorativo
- Storytelling emocional

3. **Cierre obligatorio:**
```
"These cases illustrate the structural model behind my Offerings."
[Botón a Offerings]
```

---

### BLOG.HTML → INSIGHTS.HTML

**Cambios principales:**

1. **Renombrar archivo:** `blog.html` → `insights.html`

2. **Categorías estratégicas:**
```
ANTES:
- Tech
- Innovation
- General

DESPUÉS:
- Regulated Markets
- Product Governance
- Delivery Complexity
- Strategic Architecture
```

3. **Título página:**
```
ANTES: "Blog"
DESPUÉS: "Insights & Perspectives"

Subtítulo: "Thoughts on strategic product leadership, regulated market dynamics, and delivery governance"
```

4. **Cada artículo debe:**
- Reforzar tesis central
- Conectar con posicionamiento
- Evitar temas genéricos desconectados

---

### CONTACT.HTML

**Cambios principales:**

1. **CTA Hierarchy clara:**
```
PRIMARY ACTION:
  → Schedule a Strategy Call (botón destacado)
  
SECONDARY ACTION:
  → Strategic Brief (formulario)
```

2. **Eliminar:**
- Textos largos explicativos
- Múltiples opciones de contacto
- Redundancia con navbar

3. **Formulario simplificado:**
```
- Nombre
- Email
- Empresa
- Área de concern (dropdown)
- Descripción breve del constraint
```

4. **Tone:**
```
ANTES: "Get in touch to discuss your needs"
DESPUÉS: "Selective engagement for structural interventions"
```

---

## 🎨 SISTEMA DE COLORES - APLICACIÓN PRÁCTICA

### Variables CSS a usar en TODAS las páginas:

```css
:root {
  --primary-color: #667eea;
  --accent-dark: #2d3748;
  --text-body: #4a5568;
  --text-heading: #1a202c;
  --bg-primary: #ffffff;
  --bg-alternate: #f8f9fc;
  --border-light: #e2e8f0;
  --text-muted: #718096;
}
```

### Regla de oro:
- Gradient SOLO en hero de homepage
- Todo lo demás: blanco (#ffffff) o gris claro (#f8f9fc)
- NO usar glass/blur fuera del navbar

---

## 🔘 SISTEMA DE BOTONES - APLICACIÓN ESTRICTA

### Primary Button (SOLO para "Schedule a Strategy Call")

```html
<a href="#" onclick="openCalendly(); return false;" class="btn-primary">
    Schedule a Strategy Call
</a>

<!-- CSS -->
.btn-primary {
    background: linear-gradient(135deg, #667eea, #764ba2);
    color: #ffffff;
    border: none;
    border-radius: 50px;
    padding: 14px 32px;
    font-size: 16px;
    font-weight: 600;
    text-decoration: none;
    display: inline-block;
    transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.btn-primary:hover {
    transform: translateY(-2px);
    box-shadow: 0 6px 20px rgba(102, 126, 234, 0.4);
}
```

### Secondary Button

```html
<a href="case-studies.html" class="btn-secondary">
    View Case Studies
</a>

<!-- CSS -->
.btn-secondary {
    background: #ffffff;
    color: #667eea;
    border: 2px solid #667eea;
    border-radius: 50px;
    padding: 12px 28px;
    font-size: 16px;
    font-weight: 600;
    text-decoration: none;
    display: inline-block;
    transition: all 0.2s ease;
}

.btn-secondary:hover {
    background: #667eea;
    color: #ffffff;
}
```

**NUNCA mezclar 3+ acciones primarias en una página.**

---

## 📏 SISTEMA DE ESPACIADO - ESTÁNDAR

### Sections
```css
.section {
    padding: 80px 24px;  /* Desktop */
    max-width: 1100px;
    margin: 0 auto;
}

@media (max-width: 768px) {
    .section {
        padding: 50px 20px;  /* Mobile */
    }
}
```

### Headings
```css
h2 {
    font-size: 36px;
    margin-bottom: 32px;  /* SIEMPRE 32px */
}
```

### Paragraphs
```css
p {
    line-height: 1.7-1.8;  /* NUNCA menos de 1.7 */
}
```

---

## 🧭 ARQUITECTURA DE CONVERSIÓN - FLUJO MENTAL

### Homepage → Offerings → Case Studies → Career → Contact

**Cada página debe responder UNA pregunta:**

| Página | Pregunta | Respuesta |
|--------|----------|-----------|
| Homepage | ¿Es relevante para mi problema? | Sí - posicionamiento claro |
| Offerings | ¿Cómo trabaja? | Modelo de intervención estructural |
| Case Studies | ¿Tiene evidencia? | Casos con impacto medible |
| Career | ¿Tiene seniority? | Trayectoria de responsabilidad estructural |
| Contact | ¿Cómo empezamos? | Strategy Call primario |

**Cada página debe tener:**
1. Un mensaje claro (no 3 mensajes)
2. Un CTA principal
3. Conexión explícita con siguiente paso

---

## ✅ CHECKLIST FINAL ANTES DE PUBLICAR

### Por página:
- [ ] Navbar idéntica (orden: Career, Offerings, Case Studies, Insights, CTA)
- [ ] Footer idéntico (solo LinkedIn + Email)
- [ ] Floating button con "Schedule a Strategy Call"
- [ ] NO gradient fuera del hero (excepto homepage)
- [ ] Fondo blanco o #f8f9fc
- [ ] Espaciado 80px desktop / 50px mobile
- [ ] H2 con margin-bottom 32px
- [ ] Line-height 1.7-1.8 en párrafos
- [ ] Max-width 1100px en sections
- [ ] Primary button SOLO dice "Schedule a Strategy Call"
- [ ] NO más de 2 CTAs principales por página

### Global:
- [ ] Tesis central presente: "Strategic clarity without execution discipline is noise. Execution without structural clarity is fragility."
- [ ] Conexiones explícitas entre páginas
- [ ] Tone: autoridad, no explicación
- [ ] Sin efectos visuales innecesarios
- [ ] Coherencia tipográfica total

---

## 🎯 TESIS CENTRAL A REFORZAR EN TODO EL SITIO

**Core Message:**
"Strategic clarity without execution discipline is noise.
Execution without structural clarity is fragility.
I operate in that intersection."

**Dónde debe aparecer:**
- Homepage: Hero subtitle o section post-hero
- Offerings: Intro o cierre
- Case Studies: Unifying thesis section
- Career: Executive framing
- Contact: No necesario (ya está contextualizado)

---

## 📊 NIVEL ACTUAL VS OBJETIVO

**Hoy: 8.0/10**
- Posicionamiento conceptual claro
- Contenido estratégico fuerte
- Inconsistencia visual
- Jerarquía de conversión difusa

**Con refactorización: 9.5/10**
- Coherencia estructural total
- Sobriedad visual profesional
- Jerarquía de conversión clara
- Autoridad reforzada

**La diferencia está en los detalles sistemáticos.**

---

