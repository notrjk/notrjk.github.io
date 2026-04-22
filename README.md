<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Marketing Dashboard — Sede Orizaba</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,600;0,9..40,700;1,9..40,300&family=DM+Serif+Display:ital@0;1&display=swap');

  :root {
    --gold: #ce9b3c;
    --gold-light: #e8b85a;
    --gold-dim: #a07828;
    --black: #0a0a0a;
    --dark: #111111;
    --card: #181818;
    --card2: #1e1e1e;
    --border: #2a2a2a;
    --text: #e8e8e8;
    --muted: #888;
    --ig: #e1306c;
    --fb: #1877f2;
    --tk: #ff0050;
    --green: #4caf82;
  }

  * { margin:0; padding:0; box-sizing:border-box; }

  body {
    background: var(--black);
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    min-height: 100vh;
  }

  /* HEADER */
  header {
    background: var(--dark);
    border-bottom: 1px solid var(--border);
    padding: 18px 40px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    position: sticky;
    top: 0;
    z-index: 100;
  }

  .logo-area {
    display: flex;
    align-items: center;
    gap: 14px;
  }

  .logo-icon {
    width: 38px;
    height: 38px;
    background: var(--gold);
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 700;
    color: #000;
    font-size: 14px;
    letter-spacing: -0.5px;
  }

  .logo-text {
    font-family: 'DM Serif Display', serif;
    font-size: 20px;
    color: #fff;
    letter-spacing: 0.5px;
  }

  .logo-text span { color: var(--gold); }

  .header-tag {
    background: rgba(206,155,60,0.12);
    color: var(--gold);
    border: 1px solid rgba(206,155,60,0.3);
    border-radius: 20px;
    padding: 4px 14px;
    font-size: 12px;
    font-weight: 600;
    letter-spacing: 0.5px;
    text-transform: uppercase;
  }

  /* NAV TABS */
  .nav-tabs {
    display: flex;
    gap: 4px;
    padding: 20px 40px 0;
    border-bottom: 1px solid var(--border);
    overflow-x: auto;
  }

  .tab {
    padding: 10px 22px;
    border-radius: 8px 8px 0 0;
    font-size: 13px;
    font-weight: 600;
    cursor: pointer;
    color: var(--muted);
    border: 1px solid transparent;
    border-bottom: none;
    transition: all 0.2s;
    white-space: nowrap;
  }

  .tab:hover { color: var(--text); }

  .tab.active {
    color: var(--gold);
    background: var(--card);
    border-color: var(--border);
    border-bottom-color: var(--card);
    margin-bottom: -1px;
    z-index: 1;
  }

  /* SECTIONS */
  .section { display: none; padding: 36px 40px 60px; }
  .section.active { display: block; }

  /* SECTION HEADER */
  .section-title {
    font-family: 'DM Serif Display', serif;
    font-size: 28px;
    color: #fff;
    margin-bottom: 6px;
  }

  .section-sub {
    color: var(--muted);
    font-size: 14px;
    margin-bottom: 32px;
    line-height: 1.6;
  }

  /* CARDS GRID */
  .grid-2 { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; margin-bottom: 28px; }
  .grid-3 { display: grid; grid-template-columns: repeat(3, 1fr); gap: 20px; margin-bottom: 28px; }
  .grid-4 { display: grid; grid-template-columns: repeat(4, 1fr); gap: 16px; margin-bottom: 28px; }

  .card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 24px;
  }

  .card-label {
    font-size: 11px;
    font-weight: 700;
    letter-spacing: 1px;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 10px;
  }

  .card-value {
    font-family: 'DM Serif Display', serif;
    font-size: 36px;
    color: #fff;
    line-height: 1;
    margin-bottom: 6px;
  }

  .card-desc {
    font-size: 13px;
    color: var(--muted);
    line-height: 1.5;
  }

  .card-desc b { color: var(--text); }

  /* PLATFORM BADGE */
  .plat-badge {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 3px 10px 3px 7px;
    border-radius: 20px;
    font-size: 11px;
    font-weight: 700;
    letter-spacing: 0.5px;
    text-transform: uppercase;
    margin-bottom: 12px;
  }

  .plat-badge.ig { background: rgba(225,48,108,0.12); color: var(--ig); border: 1px solid rgba(225,48,108,0.25); }
  .plat-badge.fb { background: rgba(24,119,242,0.12); color: var(--fb); border: 1px solid rgba(24,119,242,0.25); }
  .plat-badge.tk { background: rgba(255,0,80,0.1); color: var(--tk); border: 1px solid rgba(255,0,80,0.2); }
  .plat-badge.all { background: rgba(206,155,60,0.12); color: var(--gold); border: 1px solid rgba(206,155,60,0.25); }
  .plat-badge .dot { width:6px; height:6px; border-radius:50%; background:currentColor; }

  /* PILLAR CARDS */
  .pillar-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 22px;
    border-top: 3px solid var(--gold);
    transition: border-color 0.2s, transform 0.2s;
    cursor: default;
  }

  .pillar-card:hover {
    transform: translateY(-2px);
    border-color: var(--gold-light);
    box-shadow: 0 8px 32px rgba(0,0,0,0.4);
  }

  .pillar-num {
    font-family: 'DM Serif Display', serif;
    font-size: 42px;
    color: rgba(206,155,60,0.2);
    line-height: 1;
    margin-bottom: 4px;
  }

  .pillar-title {
    font-weight: 700;
    font-size: 15px;
    color: #fff;
    margin-bottom: 8px;
  }

  .pillar-examples {
    list-style: none;
    margin-top: 12px;
  }

  .pillar-examples li {
    font-size: 12.5px;
    color: var(--muted);
    padding: 5px 0;
    border-bottom: 1px solid rgba(255,255,255,0.05);
    display: flex;
    align-items: flex-start;
    gap: 8px;
    line-height: 1.4;
  }

  .pillar-examples li::before {
    content: '→';
    color: var(--gold);
    flex-shrink: 0;
    margin-top: 1px;
  }

  /* CALENDAR */
  .cal-week {
    display: grid;
    grid-template-columns: 80px repeat(7, 1fr);
    gap: 1px;
    background: var(--border);
    border-radius: 10px;
    overflow: hidden;
    margin-bottom: 20px;
  }

  .cal-cell {
    background: var(--card);
    padding: 10px 12px;
    font-size: 12px;
  }

  .cal-head {
    background: var(--card2);
    font-size: 11px;
    font-weight: 700;
    letter-spacing: 0.5px;
    text-transform: uppercase;
    color: var(--muted);
  }

  .cal-row-label {
    background: var(--card2);
    font-size: 11px;
    font-weight: 600;
    color: var(--muted);
    display: flex;
    align-items: center;
    padding-left: 12px;
  }

  .post-chip {
    display: inline-block;
    padding: 3px 8px;
    border-radius: 5px;
    font-size: 10.5px;
    font-weight: 600;
    margin: 2px 0;
    line-height: 1.4;
  }

  .post-chip.ig { background: rgba(225,48,108,0.15); color: #ff6b9d; }
  .post-chip.fb { background: rgba(24,119,242,0.15); color: #6baef4; }
  .post-chip.tk { background: rgba(255,0,80,0.12); color: #ff6699; }
  .post-chip.rest { background: rgba(255,255,255,0.05); color: var(--muted); font-style: italic; }

  /* CONTENT TEMPLATE */
  .template-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 14px;
    overflow: hidden;
    transition: transform 0.2s, box-shadow 0.2s;
  }

  .template-card:hover {
    transform: translateY(-3px);
    box-shadow: 0 10px 40px rgba(0,0,0,0.5);
  }

  .template-header {
    padding: 20px 22px 16px;
    border-bottom: 1px solid var(--border);
    display: flex;
    align-items: flex-start;
    justify-content: space-between;
    gap: 12px;
  }

  .template-name {
    font-weight: 700;
    font-size: 14px;
    color: #fff;
    margin-bottom: 4px;
  }

  .template-body { padding: 18px 22px; }

  .copy-block {
    background: var(--black);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 14px 16px;
    font-size: 12.5px;
    color: var(--text);
    line-height: 1.7;
    font-family: 'DM Sans', sans-serif;
    position: relative;
    margin-bottom: 12px;
    cursor: text;
    user-select: text;
  }

  .copy-block .var {
    background: rgba(206,155,60,0.2);
    color: var(--gold);
    border-radius: 3px;
    padding: 1px 5px;
    font-weight: 600;
    font-size: 11px;
    font-family: monospace;
  }

  .tags-row {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
    margin-top: 10px;
  }

  .tag {
    font-size: 11px;
    color: var(--muted);
    background: rgba(255,255,255,0.04);
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 2px 8px;
  }

  .format-pills {
    display: flex;
    gap: 5px;
    flex-wrap: wrap;
    margin-top: 10px;
  }

  .format-pill {
    font-size: 10px;
    font-weight: 700;
    letter-spacing: 0.5px;
    padding: 2px 8px;
    border-radius: 4px;
    background: rgba(255,255,255,0.06);
    color: var(--muted);
    text-transform: uppercase;
  }

  /* TOOLS */
  .tool-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 20px;
    display: flex;
    gap: 16px;
    align-items: flex-start;
  }

  .tool-icon {
    width: 44px;
    height: 44px;
    border-radius: 10px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 22px;
    flex-shrink: 0;
  }

  .tool-name { font-weight: 700; font-size: 14px; color: #fff; margin-bottom: 4px; }
  .tool-purpose { font-size: 12.5px; color: var(--muted); line-height: 1.5; margin-bottom: 10px; }

  .use-list { list-style: none; }
  .use-list li {
    font-size: 12px;
    color: var(--text);
    padding: 3px 0;
    display: flex;
    gap: 8px;
  }
  .use-list li::before { content: '✓'; color: var(--green); font-weight: 700; }

  /* CHECKLIST */
  .checklist { list-style: none; }
  .checklist li {
    padding: 10px 0;
    border-bottom: 1px solid rgba(255,255,255,0.05);
    display: flex;
    gap: 12px;
    align-items: flex-start;
    font-size: 13.5px;
    line-height: 1.5;
  }

  .check-box {
    width: 18px;
    height: 18px;
    border: 2px solid var(--border);
    border-radius: 4px;
    flex-shrink: 0;
    margin-top: 2px;
    cursor: pointer;
    transition: all 0.15s;
  }

  .checklist li.done .check-box {
    background: var(--gold);
    border-color: var(--gold);
    position: relative;
  }

  .checklist li.done .check-box::after {
    content: '✓';
    color: #000;
    font-size: 11px;
    font-weight: 900;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }

  .checklist li.done .check-label { text-decoration: line-through; color: var(--muted); }

  /* SECTION SUBTITLE */
  .s-sub {
    font-size: 12px;
    font-weight: 700;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 14px;
    margin-top: 30px;
  }

  /* HIGHLIGHT BOX */
  .highlight-box {
    background: rgba(206,155,60,0.07);
    border: 1px solid rgba(206,155,60,0.2);
    border-left: 3px solid var(--gold);
    border-radius: 8px;
    padding: 14px 18px;
    font-size: 13px;
    color: var(--text);
    line-height: 1.6;
    margin-bottom: 20px;
  }

  .highlight-box b { color: var(--gold); }

  /* RESPONSIVE */
  @media (max-width: 900px) {
    header { padding: 14px 20px; }
    .nav-tabs { padding: 16px 20px 0; }
    .section { padding: 24px 20px 60px; }
    .grid-2, .grid-3, .grid-4 { grid-template-columns: 1fr; }
  }

  /* DIVIDER */
  .divider {
    border: none;
    border-top: 1px solid var(--border);
    margin: 28px 0;
  }

  /* FREQ CHART */
  .freq-bar-wrap { display: flex; flex-direction: column; gap: 10px; }
  .freq-bar-row { display: flex; align-items: center; gap: 12px; }
  .freq-bar-label { width: 90px; font-size: 12px; color: var(--muted); text-align: right; flex-shrink: 0; }
  .freq-bar-bg { flex: 1; background: var(--card2); border-radius: 4px; height: 8px; overflow: hidden; }
  .freq-bar-fill { height: 100%; border-radius: 4px; background: var(--gold); }
  .freq-bar-val { width: 40px; font-size: 12px; color: var(--text); font-weight: 600; }
</style>
</head>
<body>

<header>
  <div class="logo-area">
    <div class="logo-icon">SO</div>
    <div class="logo-text">Sede <span>Orizaba</span></div>
  </div>
  <div class="header-tag">📱 Marketing Social</div>
</header>

<div class="nav-tabs">
  <div class="tab active" onclick="switchTab('plan')">📋 Plan de Trabajo</div>
  <div class="tab" onclick="switchTab('pilares')">🏛️ Pilares de Contenido</div>
  <div class="tab" onclick="switchTab('plantillas')">✍️ Plantillas</div>
  <div class="tab" onclick="switchTab('calendario')">📅 Calendario</div>
  <div class="tab" onclick="switchTab('herramientas')">🛠️ Herramientas</div>
  <div class="tab" onclick="switchTab('checklist')">✅ Checklist Semanal</div>
</div>

<!-- ===================== PLAN ===================== -->
<div id="tab-plan" class="section active">
  <div class="section-title">Plan de Trabajo</div>
  <p class="section-sub">Tu guía completa para gestionar el marketing de Sede Orizaba con 2–3 publicaciones semanales, sin complicaciones.</p>

  <div class="highlight-box">
    <b>🎯 Regla de oro:</b> Con 2–3 posts/semana, cada publicación debe cumplir UNO de estos objetivos: <b>Atraer</b> nuevos prospectos, <b>Convencer</b> a indecisos, o <b>Fidelizar</b> a estudiantes actuales. Nunca publiques sin tener claro cuál es.
  </div>

  <div class="s-sub">Panorama Semanal</div>
  <div class="grid-4">
    <div class="card">
      <div class="card-label">Publicaciones / semana</div>
      <div class="card-value">2–3</div>
      <div class="card-desc">Mínimo <b>2</b> para mantener presencia. <b>3</b> en temporadas de admisión.</div>
    </div>
    <div class="card">
      <div class="card-label">Plataformas activas</div>
      <div class="card-value">3</div>
      <div class="card-desc"><b>Instagram</b> (imagen), <b>Facebook</b> (alcance y padres), <b>TikTok</b> (viralidad).</div>
    </div>
    <div class="card">
      <div class="card-label">Tiempo por publicación</div>
      <div class="card-value">~45m</div>
      <div class="card-desc">Con plantillas y textos listos: <b>diseño 20 min, copy 10 min, publicar 15 min</b>.</div>
    </div>
    <div class="card">
      <div class="card-label">Reutilización</div>
      <div class="card-value">×3</div>
      <div class="card-desc">Cada contenido se adapta para las <b>3 plataformas</b> sin crear desde cero.</div>
    </div>
  </div>

  <div class="s-sub">Flujo de Trabajo (por publicación)</div>
  <div class="grid-3">
    <div class="card">
      <div class="card-label">Paso 1 — Lunes</div>
      <div class="pillar-title" style="color:var(--gold);font-size:16px;">🧠 Planea</div>
      <ul class="pillar-examples">
        <li>Elige el pilar de contenido de la semana</li>
        <li>Selecciona el tema concreto (usa la tabla de temas)</li>
        <li>Define qué plataformas usarás</li>
        <li>¿Hay evento, fecha especial o carrera a destacar?</li>
      </ul>
    </div>
    <div class="card">
      <div class="card-label">Paso 2 — Martes/Miércoles</div>
      <div class="pillar-title" style="color:var(--gold);font-size:16px;">🎨 Diseña</div>
      <ul class="pillar-examples">
        <li>Abre Canva con tu plantilla de esa categoría</li>
        <li>Cambia texto, colores y foto según el tema</li>
        <li>Exporta en 3 formatos: 1:1 (IG feed), 9:16 (Stories/Reels), 16:9 (FB)</li>
        <li>Genera el copy con la plantilla de texto</li>
      </ul>
    </div>
    <div class="card">
      <div class="card-label">Paso 3 — Jueves/Viernes</div>
      <div class="pillar-title" style="color:var(--gold);font-size:16px;">🚀 Publica</div>
      <ul class="pillar-examples">
        <li>Programa con Meta Business Suite (IG + FB)</li>
        <li>Sube el Reel/TikTok con el audio de tendencia</li>
        <li>Responde comentarios las primeras 2 horas</li>
        <li>Guarda en tu carpeta de "contenido reutilizable"</li>
      </ul>
    </div>
  </div>

  <div class="s-sub">Distribución de Plataformas</div>
  <div class="card" style="max-width:500px;">
    <div class="freq-bar-wrap">
      <div class="freq-bar-row">
        <div class="freq-bar-label" style="color:#ff6b9d;">Instagram</div>
        <div class="freq-bar-bg"><div class="freq-bar-fill" style="width:100%;background:#e1306c;"></div></div>
        <div class="freq-bar-val">Feed + Story + Reel</div>
      </div>
      <div class="freq-bar-row">
        <div class="freq-bar-label" style="color:#6baef4;">Facebook</div>
        <div class="freq-bar-bg"><div class="freq-bar-fill" style="width:80%;background:#1877f2;"></div></div>
        <div class="freq-bar-val">Post + Reels</div>
      </div>
      <div class="freq-bar-row">
        <div class="freq-bar-label" style="color:#ff6699;">TikTok</div>
        <div class="freq-bar-bg"><div class="freq-bar-fill" style="width:65%;background:#ff0050;"></div></div>
        <div class="freq-bar-val">1–2/semana</div>
      </div>
    </div>
    <div class="card-desc" style="margin-top:16px;">
      <b>IG y FB</b> comparten el mismo contenido (Meta Business Suite lo publica en ambos). <b>TikTok</b> requiere video vertical corto, mínimo 1 vez por semana.
    </div>
  </div>
</div>

<!-- ===================== PILARES ===================== -->
<div id="tab-pilares" class="section">
  <div class="section-title">Pilares de Contenido</div>
  <p class="section-sub">5 pilares que cubren todo el funnel: desde captar atención hasta convertir a alumno inscrito. Rota entre ellos cada semana.</p>

  <div class="highlight-box">
    <b>💡 Cómo usar los pilares:</b> Asigna un pilar a cada post de la semana. Si publicas 3 veces, combina por ejemplo: <b>Inspiración + Oferta Educativa + Vida Universitaria</b>. El pilar que menos uses es el que más falta.
  </div>

  <div class="grid-3">
    <div class="pillar-card">
      <div class="pillar-num">01</div>
      <div class="pillar-title">🎓 Oferta Educativa</div>
      <div class="card-desc">Muestra carreras, maestrías y bachillerato. El contenido más importante: convierte prospectos.</div>
      <ul class="pillar-examples">
        <li>¿Qué hace un Licenciado en Derecho? (día a día)</li>
        <li>Plan de estudios de Mercadotecnia en 60 segundos</li>
        <li>Diferencia entre LAE y Administración</li>
        <li>"¿Cuánto gana un psicólogo en México?" + nuestra oferta</li>
        <li>Maestría en Terapia Familiar: ¿para quién es?</li>
        <li>Contaduría Pública: salidas profesionales</li>
      </ul>
    </div>
    <div class="pillar-card">
      <div class="pillar-num">02</div>
      <div class="pillar-title">✨ Inspiración y Motivación</div>
      <div class="card-desc">Engancha emocionalmente. Ideal para historias, reels y TikTok. Alto alcance orgánico.</div>
      <ul class="pillar-examples">
        <li>"Ser universitario en Orizaba sí es posible"</li>
        <li>Frases de egresados exitosos locales</li>
        <li>Historia de superación de un alumno (con permiso)</li>
        <li>"El mejor momento para estudiar fue ayer, el segundo mejor es hoy"</li>
        <li>Transformación: antes y después de graduarse</li>
        <li>Fechas importantes: Día del Maestro, Día del Estudiante</li>
      </ul>
    </div>
    <div class="pillar-card">
      <div class="pillar-num">03</div>
      <div class="pillar-title">🏛️ Vida Universitaria</div>
      <div class="card-desc">Humaniza la institución. Genera comunidad y orgullo de pertenencia entre alumnos activos.</div>
      <ul class="pillar-examples">
        <li>Fotos de instalaciones y aulas</li>
        <li>Detrás de cámaras: un día en la sede</li>
        <li>Eventos: ceremonias, talleres, graduaciones</li>
        <li>Presentación del equipo docente</li>
        <li>Estudiantes en proyecto final o prácticas</li>
        <li>LIAH (mascota) en situaciones cotidianas</li>
      </ul>
    </div>
    <div class="pillar-card">
      <div class="pillar-num">04</div>
      <div class="pillar-title">📣 Captación y Admisiones</div>
      <div class="card-desc">Publicaciones de conversión directa. Usar en temporada de inscripciones con mayor frecuencia.</div>
      <ul class="pillar-examples">
        <li>"¿Ya sabes qué vas a estudiar?" + link de info</li>
        <li>Cuenta regresiva: cierre de inscripciones</li>
        <li>Descuentos de pronto pago o becas disponibles</li>
        <li>Requisitos para inscribirse (simple y visual)</li>
        <li>"Agenda tu visita a la sede" con dirección</li>
        <li>Testimoniales de alumnos en video (30 segundos)</li>
      </ul>
    </div>
    <div class="pillar-card">
      <div class="pillar-num">05</div>
      <div class="pillar-title">💡 Contenido de Valor</div>
      <div class="card-desc">Posiciona a la institución como experta. Atrae a padres y prospectos que investigan antes de decidir.</div>
      <ul class="pillar-examples">
        <li>Tips de estudio y organización universitaria</li>
        <li>"Las 5 carreras con más demanda en Veracruz 2025"</li>
        <li>Diferencia entre universidad pública y privada</li>
        <li>Cómo financiar tu carrera (becas, planes de pago)</li>
        <li>¿Qué hago si no sé qué estudiar? Test vocacional</li>
        <li>Consejos para la primera semana de universidad</li>
      </ul>
    </div>
    <div class="card" style="border-top:3px solid #444;">
      <div class="card-label">📌 Regla de Rotación</div>
      <div style="margin-top:8px;">
        <div style="display:flex;gap:8px;flex-wrap:wrap;">
          <div style="background:rgba(206,155,60,0.1);border:1px solid rgba(206,155,60,0.3);border-radius:6px;padding:8px 12px;font-size:12px;">
            <div style="color:var(--gold);font-weight:700;margin-bottom:2px;">Semana A</div>
            <div style="color:var(--muted);">Oferta Educativa<br>+ Vida Universitaria<br>+ Inspiración</div>
          </div>
          <div style="background:rgba(206,155,60,0.1);border:1px solid rgba(206,155,60,0.3);border-radius:6px;padding:8px 12px;font-size:12px;">
            <div style="color:var(--gold);font-weight:700;margin-bottom:2px;">Semana B</div>
            <div style="color:var(--muted);">Captación<br>+ Contenido de Valor<br>+ Inspiración</div>
          </div>
          <div style="background:rgba(206,155,60,0.1);border:1px solid rgba(206,155,60,0.3);border-radius:6px;padding:8px 12px;font-size:12px;">
            <div style="color:var(--gold);font-weight:700;margin-bottom:2px;">Semana C</div>
            <div style="color:var(--muted);">Oferta Educativa<br>+ Captación<br>+ Vida Universitaria</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- ===================== PLANTILLAS ===================== -->
<div id="tab-plantillas" class="section">
  <div class="section-title">Plantillas de Copy</div>
  <p class="section-sub">Textos listos para copiar. Solo reemplaza los valores en <span style="background:rgba(206,155,60,0.2);color:var(--gold);border-radius:3px;padding:1px 5px;font-size:12px;font-family:monospace;">[ corchetes ]</span> y adapta el tono según la plataforma.</p>

  <div class="s-sub">📸 Presentación de Carrera</div>
  <div class="grid-2">
    <div class="template-card">
      <div class="template-header">
        <div>
          <div class="template-name">🎓 "¿Qué es [CARRERA]?"</div>
          <div class="card-desc" style="font-size:12px;">Ideal para: feed IG, FB post</div>
        </div>
        <div class="plat-badge ig"><span class="dot"></span>IG</div>
      </div>
      <div class="template-body">
        <div class="copy-block">
¿Sabes qué hace un <span class="var">[LICENCIADO/A EN CARRERA]</span>? 🎓

En <span class="var">[CARRERA]</span> aprenderás a <span class="var">[habilidad 1]</span>, <span class="var">[habilidad 2]</span> y <span class="var">[habilidad 3]</span>.

✅ Duración: <span class="var">[X]</span> años
✅ Modalidad: <span class="var">[escolarizada/semiescolarizada]</span>
✅ Ubicación: Sede Orizaba

¿Te llama la atención? 📲 Escríbenos al DM o al <span class="var">[teléfono]</span> para más información.

#SedeOrizaba #<span class="var">[Carrera]</span> #Orizaba #Universidad #<span class="var">[ciudad]</span>
        </div>
        <div class="tags-row">
          <span class="tag">feed cuadrado 1:1</span>
          <span class="tag">foto de estudiante o instalaciones</span>
          <span class="tag">color de la carrera</span>
        </div>
      </div>
    </div>

    <div class="template-card">
      <div class="template-header">
        <div>
          <div class="template-name">📱 Reel/TikTok "¿Te identificas?"</div>
          <div class="card-desc" style="font-size:12px;">Ideal para: Reels IG, TikTok</div>
        </div>
        <div style="display:flex;gap:4px;">
          <div class="plat-badge ig"><span class="dot"></span>IG</div>
          <div class="plat-badge tk"><span class="dot"></span>TK</div>
        </div>
      </div>
      <div class="template-body">
        <div class="copy-block">
Si siempre te has preguntado <span class="var">[curiosidad de la carrera]</span>... 🤔

Esta carrera es para ti 👇

📌 <span class="var">[CARRERA]</span> en Sede Orizaba
🗓 Inscripciones abiertas
📲 Info en el link del bio

¿Cuál es tu carrera favorita? Comenta abajo 👇
        </div>
        <div class="copy-block" style="font-size:11px;color:var(--muted);margin-top:0;">
          <b style="color:var(--gold);">Guión del video (30 seg):</b><br>
          0:00 Hook: pregunta o dato sorpresa<br>
          0:05 Problema que resuelve la carrera<br>
          0:15 Beneficios / lo que aprenderás<br>
          0:25 CTA: "Escríbenos o visítanos"
        </div>
      </div>
    </div>
  </div>

  <div class="s-sub">🗣️ Testimoniales</div>
  <div class="grid-2">
    <div class="template-card">
      <div class="template-header">
        <div>
          <div class="template-name">💬 Historia de Alumno</div>
          <div class="card-desc" style="font-size:12px;">El contenido que más convierte</div>
        </div>
        <div class="plat-badge all"><span class="dot"></span>Todas</div>
      </div>
      <div class="template-body">
        <div class="copy-block">
"<span class="var">[Frase poderosa del alumno, máx 2 líneas]</span>" 💛

<span class="var">[Nombre]</span> — <span class="var">[Carrera]</span>, <span class="var">[semestre/generación]</span>

Historias como la de <span class="var">[nombre]</span> nos recuerdan por qué hacemos lo que hacemos. 🙌

¿Tú quieres ser parte de nuestra comunidad? 
📲 Contáctanos: <span class="var">[teléfono/link]</span>

#SedeOrizaba #Testimonial #Orgullosos<span class="var">[NombreSede]</span>
        </div>
        <div class="tags-row">
          <span class="tag">foto del alumno (con permiso)</span>
          <span class="tag">fondo con colores institucionales</span>
        </div>
      </div>
    </div>

    <div class="template-card">
      <div class="template-header">
        <div>
          <div class="template-name">📣 Captación Directa</div>
          <div class="card-desc" style="font-size:12px;">Para épocas de inscripción</div>
        </div>
        <div style="display:flex;gap:4px;">
          <div class="plat-badge ig"><span class="dot"></span>IG</div>
          <div class="plat-badge fb"><span class="dot"></span>FB</div>
        </div>
      </div>
      <div class="template-body">
        <div class="copy-block">
⏳ ¡Las inscripciones cierran pronto!

Si estás pensando en estudiar <span class="var">[CARRERA]</span>, este es el momento. 

✨ Aquí encuentras:
→ Horarios accesibles
→ Instalaciones modernas
→ Docentes con experiencia real
→ Una comunidad que te apoya

📍 Estamos en <span class="var">[dirección Orizaba]</span>
📲 Escríbenos al: <span class="var">[teléfono]</span>
🌐 <span class="var">[sitio web o link.bio]</span>

¡Tu futuro empieza aquí! 🎓
        </div>
      </div>
    </div>
  </div>

  <div class="s-sub">💡 Contenido de Valor (Educativo)</div>
  <div class="grid-2">
    <div class="template-card">
      <div class="template-header">
        <div>
          <div class="template-name">📊 Carrusel "X cosas que no sabías"</div>
          <div class="card-desc" style="font-size:12px;">Muy alto alcance en IG</div>
        </div>
        <div class="plat-badge ig"><span class="dot"></span>IG</div>
      </div>
      <div class="template-body">
        <div class="copy-block">
<b>Caption (antes del carrusel):</b>

¿Estás eligiendo tu carrera? Antes de decidir, lee esto 👆 (desliza)

<b>Slide 1 (portada):</b> "<span class="var">[X]</span> cosas que nadie te dice de <span class="var">[carrera]</span>"

<b>Slides 2–5:</b> Una dato/tip por slide
- <span class="var">[Dato 1]</span>
- <span class="var">[Dato 2]</span>
- <span class="var">[Dato 3]</span>
- <span class="var">[Dato 4]</span>

<b>Slide final:</b> "¿Quieres saber más? Contáctanos" + logo

¿Te sorprendió alguno? Comenta cuál 👇
        </div>
        <div class="format-pills">
          <span class="format-pill">5–7 slides</span>
          <span class="format-pill">texto grande</span>
          <span class="format-pill">1 dato por slide</span>
        </div>
      </div>
    </div>

    <div class="template-card">
      <div class="template-header">
        <div>
          <div class="template-name">🎯 TikTok "POV: estudias en Sede Orizaba"</div>
          <div class="card-desc" style="font-size:12px;">Formato nativo TikTok, muy orgánico</div>
        </div>
        <div class="plat-badge tk"><span class="dot"></span>TK</div>
      </div>
      <div class="template-body">
        <div class="copy-block">
<b>Texto en pantalla (subtítulos):</b>

POV: decides estudiar <span class="var">[carrera]</span> en Sede Orizaba

*imagen de llegada a la sede*
→ "Llegas con nervios"

*imagen de compañeros*  
→ "Sales con amigos de por vida"

*imagen de graduación*
→ "Y un título que vale"

<b>Caption:</b>
¿Qué POV quieres que hagamos? 👇
#SedeOrizaba #<span class="var">[carrera]</span>TikTok #Universidad #Orizaba
        </div>
        <div class="copy-block" style="font-size:11px;color:var(--muted);">
          <b style="color:var(--gold);">Audio sugerido:</b> Usa audios trending de TikTok Mexico. Revisa la sección "Audios en tendencia" en TikTok Creator Center cada semana.
        </div>
      </div>
    </div>
  </div>

  <div class="s-sub">📅 Fechas Especiales (Rejurgitar)</div>
  <div class="card">
    <div class="card-desc" style="font-size:13px;line-height:2;">
      Crea estas publicaciones una vez y <b style="color:var(--gold);">reutilízalas cada año</b> cambiando solo el año. Guárdalas en una carpeta "Contenido Evergreen":
      <br><br>
      🎓 <b>Día del Maestro</b> (15 mayo) — Homenaje a docentes con fotos<br>
      📚 <b>Inicio de ciclo escolar</b> — Bienvenida con foto grupal<br>
      🌟 <b>Día del Estudiante</b> (23 mayo) — Frase + foto de alumnos<br>
      🎉 <b>Graduaciones</b> — Serie de fotos por generación<br>
      🔔 <b>Apertura de inscripciones</b> — Countdown + CTA<br>
      🏖️ <b>Vacaciones</b> — "Nos vemos en Agosto" + info de clases<br>
      🎄 <b>Navidad / Año Nuevo</b> — Felicitación institucional con logo
    </div>
  </div>
</div>

<!-- ===================== CALENDARIO ===================== -->
<div id="tab-calendario" class="section">
  <div class="section-title">Calendario de Contenido</div>
  <p class="section-sub">Ejemplo de distribución mensual. Usa esto como base y ajusta según eventos de la universidad.</p>

  <div class="highlight-box">
    <b>📌 Cómo leer el calendario:</b> Cada semana tiene 2–3 posts distribuidos estratégicamente. Miércoles y viernes son los mejores días para publicar (mayor engagement). El lunes se reserva para captación en temporada de admisiones.
  </div>

  <div class="s-sub">Semana Tipo — Mes de Captación</div>
  <div class="cal-week">
    <div class="cal-cell cal-head cal-row-label"></div>
    <div class="cal-cell cal-head" style="text-align:center;">Lun</div>
    <div class="cal-cell cal-head" style="text-align:center;">Mar</div>
    <div class="cal-cell cal-head" style="text-align:center;">Mié</div>
    <div class="cal-cell cal-head" style="text-align:center;">Jue</div>
    <div class="cal-cell cal-head" style="text-align:center;">Vie</div>
    <div class="cal-cell cal-head" style="text-align:center;">Sáb</div>
    <div class="cal-cell cal-head" style="text-align:center;">Dom</div>

    <div class="cal-cell cal-row-label">Instagram</div>
    <div class="cal-cell"></div>
    <div class="cal-cell"></div>
    <div class="cal-cell"><span class="post-chip ig">📸 Carrera: Derecho</span></div>
    <div class="cal-cell"></div>
    <div class="cal-cell"><span class="post-chip ig">💬 Testimonial alumno</span></div>
    <div class="cal-cell"></div>
    <div class="cal-cell"></div>

    <div class="cal-cell cal-row-label">Facebook</div>
    <div class="cal-cell"></div>
    <div class="cal-cell"></div>
    <div class="cal-cell"><span class="post-chip fb">📢 Carrera: Derecho</span></div>
    <div class="cal-cell"></div>
    <div class="cal-cell"><span class="post-chip fb">💬 Testimonial</span></div>
    <div class="cal-cell"></div>
    <div class="cal-cell"></div>

    <div class="cal-cell cal-row-label">TikTok</div>
    <div class="cal-cell"></div>
    <div class="cal-cell"></div>
    <div class="cal-cell"></div>
    <div class="cal-cell"><span class="post-chip tk">🎬 Reel: "POV Derecho"</span></div>
    <div class="cal-cell"></div>
    <div class="cal-cell"></div>
    <div class="cal-cell"></div>

    <div class="cal-cell cal-row-label">Stories</div>
    <div class="cal-cell"><span class="post-chip ig" style="font-size:9px;">📊 Poll: ¿qué carrera?</span></div>
    <div class="cal-cell"></div>
    <div class="cal-cell"><span class="post-chip ig" style="font-size:9px;">🔁 Reshare post</span></div>
    <div class="cal-cell"></div>
    <div class="cal-cell"><span class="post-chip ig" style="font-size:9px;">📍 "Visítanos hoy"</span></div>
    <div class="cal-cell"></div>
    <div class="cal-cell"></div>
  </div>

  <div class="s-sub">Semana Tipo — Mes Normal</div>
  <div class="cal-week">
    <div class="cal-cell cal-head cal-row-label"></div>
    <div class="cal-cell cal-head" style="text-align:center;">Lun</div>
    <div class="cal-cell cal-head" style="text-align:center;">Mar</div>
    <div class="cal-cell cal-head" style="text-align:center;">Mié</div>
    <div class="cal-cell cal-head" style="text-align:center;">Jue</div>
    <div class="cal-cell cal-head" style="text-align:center;">Vie</div>
    <div class="cal-cell cal-head" style="text-align:center;">Sáb</div>
    <div class="cal-cell cal-head" style="text-align:center;">Dom</div>

    <div class="cal-cell cal-row-label">IG + FB</div>
    <div class="cal-cell"></div>
    <div class="cal-cell"></div>
    <div class="cal-cell"><span class="post-chip ig">💡 Tip de estudio</span></div>
    <div class="cal-cell"></div>
    <div class="cal-cell"><span class="post-chip ig">🏛️ Vida universitaria</span></div>
    <div class="cal-cell"></div>
    <div class="cal-cell"></div>

    <div class="cal-cell cal-row-label">TikTok</div>
    <div class="cal-cell"></div>
    <div class="cal-cell"><span class="post-chip tk">🎬 "¿Cuál carrera eres?"</span></div>
    <div class="cal-cell"></div>
    <div class="cal-cell"></div>
    <div class="cal-cell"></div>
    <div class="cal-cell"></div>
    <div class="cal-cell"></div>

    <div class="cal-cell cal-row-label">Stories</div>
    <div class="cal-cell"></div>
    <div class="cal-cell"><span class="post-chip ig" style="font-size:9px;">🗳️ "¿Sabías que...?"</span></div>
    <div class="cal-cell"><span class="post-chip ig" style="font-size:9px;">🔁 Reshare</span></div>
    <div class="cal-cell"></div>
    <div class="cal-cell"><span class="post-chip ig" style="font-size:9px;">😄 Meme universitario</span></div>
    <div class="cal-cell"></div>
    <div class="cal-cell"></div>
  </div>

  <div class="s-sub">Carreras a Rotar (cíclicamente)</div>
  <div class="grid-4">
    <div class="card" style="padding:16px;">
      <div class="card-label">Licenciaturas</div>
      <ul class="pillar-examples">
        <li>Derecho</li>
        <li>Mercadotecnia</li>
        <li>LAE (Administración)</li>
        <li>Psicología</li>
        <li>Contaduría Pública</li>
        <li>Ciencias de la Educación</li>
        <li>Empresas Turísticas</li>
      </ul>
    </div>
    <div class="card" style="padding:16px;">
      <div class="card-label">Maestrías</div>
      <ul class="pillar-examples">
        <li>Administración</li>
        <li>Terapia Familiar</li>
        <li>Derecho Penal</li>
        <li>Ciencias de la Educación</li>
      </ul>
    </div>
    <div class="card" style="padding:16px;">
      <div class="card-label">Bachillerato</div>
      <ul class="pillar-examples">
        <li>Bachillerato (8 meses)</li>
        <li>Ideal para adultos</li>
        <li>Horario flexible</li>
      </ul>
    </div>
    <div class="card" style="padding:16px;">
      <div class="card-label">Frecuencia sugerida</div>
      <ul class="pillar-examples">
        <li>1 carrera nueva por semana</li>
        <li>Repite cada ~2 meses</li>
        <li>Más frecuencia en admisiones</li>
      </ul>
    </div>
  </div>
</div>

<!-- ===================== HERRAMIENTAS ===================== -->
<div id="tab-herramientas" class="section">
  <div class="section-title">Herramientas Recomendadas</div>
  <p class="section-sub">Stack completo para crear contenido profesional rápido, sin necesitar un diseñador. Todas tienen versión gratuita suficiente para comenzar.</p>

  <div class="s-sub">🎨 Diseño</div>
  <div class="grid-2">
    <div class="tool-card">
      <div class="tool-icon" style="background:#7c3aed22;font-size:26px;">🎨</div>
      <div>
        <div class="tool-name">Canva — Principal</div>
        <div class="tool-purpose">Tu herramienta central. Crea una cuenta con el correo de la institución y guarda TODAS tus plantillas ahí.</div>
        <ul class="use-list">
          <li>Crea plantillas para cada tipo de post</li>
          <li>Usa los colores: blanco (#FFFFFF) y dorado (#CE9B3C)</li>
          <li>Sube la tipografía Geist desde la carpeta que tienes</li>
          <li>Sube el logo SVG de la sede</li>
          <li>Exporta en múltiples tamaños de una vez (Pro)</li>
        </ul>
      </div>
    </div>
    <div class="tool-card">
      <div class="tool-icon" style="background:#06b6d422;">📱</div>
      <div>
        <div class="tool-name">CapCut — Videos</div>
        <div class="tool-purpose">Para editar Reels y TikToks rápidamente. Tiene templates de tendencia y subtítulos automáticos.</div>
        <ul class="use-list">
          <li>Templates de TikTok ya con transiciones</li>
          <li>Subtítulos automáticos en español</li>
          <li>Elimina silencios con un clic</li>
          <li>Usa audios trending del catálogo</li>
        </ul>
      </div>
    </div>
  </div>

  <div class="s-sub">📅 Programación y Gestión</div>
  <div class="grid-2">
    <div class="tool-card">
      <div class="tool-icon" style="background:#1877f222;font-size:24px;">📘</div>
      <div>
        <div class="tool-name">Meta Business Suite — Gratis</div>
        <div class="tool-purpose">Programa posts en Instagram Y Facebook al mismo tiempo. Gratuito y oficial de Meta.</div>
        <ul class="use-list">
          <li>Publica en IG y FB desde un solo lugar</li>
          <li>Programa con días/horas de anticipación</li>
          <li>Ve métricas básicas de cada post</li>
          <li>Gestiona mensajes de ambas plataformas</li>
        </ul>
      </div>
    </div>
    <div class="tool-card">
      <div class="tool-icon" style="background:#10b98122;font-size:24px;">📊</div>
      <div>
        <div class="tool-name">Notion o Google Sheets — Banco de Contenido</div>
        <div class="tool-purpose">Lleva un registro de TODO el contenido publicado. Esto es lo que te permite rejurgitar sin repetirte.</div>
        <ul class="use-list">
          <li>Columnas: Fecha, Plataforma, Pilar, Carrera, Tipo</li>
          <li>Guarda el link del post publicado</li>
          <li>Nota cuáles tuvieron mejor desempeño</li>
          <li>Identifica qué contenido puedes reutilizar en 3 meses</li>
        </ul>
      </div>
    </div>
  </div>

  <div class="s-sub">🤖 IA para Agilizar</div>
  <div class="grid-3">
    <div class="tool-card" style="display:block;padding:20px;">
      <div style="display:flex;gap:12px;align-items:center;margin-bottom:12px;">
        <div class="tool-icon" style="background:#10a37f22;font-size:22px;width:36px;height:36px;">🧠</div>
        <div class="tool-name">Claude / ChatGPT</div>
      </div>
      <div class="tool-purpose">Para generar variaciones de copy, hashtags y guiones de video en segundos.</div>
      <ul class="use-list">
        <li>Genera 5 versiones del mismo caption</li>
        <li>Escribe guiones de TikTok de 30 seg</li>
        <li>Sugiere ideas para la semana</li>
      </ul>
    </div>
    <div class="tool-card" style="display:block;padding:20px;">
      <div style="display:flex;gap:12px;align-items:center;margin-bottom:12px;">
        <div class="tool-icon" style="background:#ff6b9d22;font-size:22px;width:36px;height:36px;">🖼️</div>
        <div class="tool-name">Adobe Firefly / Canva AI</div>
      </div>
      <div class="tool-purpose">Genera imágenes complementarias cuando no tienes fotos de la sede disponibles.</div>
      <ul class="use-list">
        <li>Fondos abstractos con colores institucionales</li>
        <li>Texturas y elementos decorativos</li>
        <li>Nunca para reemplazar fotos reales</li>
      </ul>
    </div>
    <div class="tool-card" style="display:block;padding:20px;">
      <div style="display:flex;gap:12px;align-items:center;margin-bottom:12px;">
        <div class="tool-icon" style="background:#f59e0b22;font-size:22px;width:36px;height:36px;">📈</div>
        <div class="tool-name">TikTok Creative Center</div>
      </div>
      <div class="tool-purpose">Descubre audios y hashtags en tendencia en México cada semana. Gratis.</div>
      <ul class="use-list">
        <li>Top audios México esta semana</li>
        <li>Hashtags por industria (educación)</li>
        <li>Revísalo cada lunes al planear</li>
      </ul>
    </div>
  </div>

  <div class="s-sub">📸 Banco de Fotos / Assets</div>
  <div class="highlight-box">
    <b>Prioridad #1:</b> Toma fotos reales de la sede, alumnos y docentes. Ese contenido auténtico genera 3–5x más engagement que imágenes de stock.<br><br>
    <b>Para complementar usa:</b> Unsplash (gratis, sin atribución), Pexels (gratis), o Freepik (versión gratuita). Busca: "university students mexico", "classroom modern", "graduation".<br><br>
    <b>Ya tienes:</b> Flyers oficiales de cada carrera en JPG, logo SVG, mascota LIAH en PNG, imágenes de misión-visión. <b>Úsalos todos en Canva.</b>
  </div>
</div>

<!-- ===================== CHECKLIST ===================== -->
<div id="tab-checklist" class="section">
  <div class="section-title">Checklist Semanal</div>
  <p class="section-sub">Tu rutina de marketing semana a semana. Haz click en cada tarea para marcarla como completada.</p>

  <div class="grid-2">
    <div class="card">
      <div class="s-sub" style="margin-top:0;">📋 Lunes — Planeación</div>
      <ul class="checklist" id="cl-lunes">
        <li onclick="toggleCheck(this)"><div class="check-box"></div><span class="check-label">Revisar TikTok Creative Center: audios y tendencias de la semana</span></li>
        <li onclick="toggleCheck(this)"><div class="check-box"></div><span class="check-label">Definir los 2–3 temas de la semana (pilar + carrera)</span></li>
        <li onclick="toggleCheck(this)"><div class="check-box"></div><span class="check-label">Revisar si hay fecha especial esta semana</span></li>
        <li onclick="toggleCheck(this)"><div class="check-box"></div><span class="check-label">Abrir banco de contenido y verificar qué no se ha publicado</span></li>
        <li onclick="toggleCheck(this)"><div class="check-box"></div><span class="check-label">Escribir el borrador de copy para cada post</span></li>
      </ul>
    </div>

    <div class="card">
      <div class="s-sub" style="margin-top:0;">🎨 Martes/Miércoles — Diseño</div>
      <ul class="checklist" id="cl-diseno">
        <li onclick="toggleCheck(this)"><div class="check-box"></div><span class="check-label">Abrir plantilla en Canva correspondiente al tipo de post</span></li>
        <li onclick="toggleCheck(this)"><div class="check-box"></div><span class="check-label">Actualizar texto, imagen y colores de la plantilla</span></li>
        <li onclick="toggleCheck(this)"><div class="check-box"></div><span class="check-label">Exportar en formato 1:1 (feed), 9:16 (stories/reel) y 16:9 (FB)</span></li>
        <li onclick="toggleCheck(this)"><div class="check-box"></div><span class="check-label">Grabar o editar video en CapCut si es Reel/TikTok</span></li>
        <li onclick="toggleCheck(this)"><div class="check-box"></div><span class="check-label">Revisar que aparezca el logo y branding correcto</span></li>
      </ul>
    </div>

    <div class="card">
      <div class="s-sub" style="margin-top:0;">🚀 Jueves/Viernes — Publicación</div>
      <ul class="checklist" id="cl-pub">
        <li onclick="toggleCheck(this)"><div class="check-box"></div><span class="check-label">Programar IG + FB en Meta Business Suite</span></li>
        <li onclick="toggleCheck(this)"><div class="check-box"></div><span class="check-label">Subir TikTok con audio de tendencia + hashtags</span></li>
        <li onclick="toggleCheck(this)"><div class="check-box"></div><span class="check-label">Crear story de IG para dar visibilidad al post</span></li>
        <li onclick="toggleCheck(this)"><div class="check-box"></div><span class="check-label">Responder todos los comentarios y DMs pendientes</span></li>
        <li onclick="toggleCheck(this)"><div class="check-box"></div><span class="check-label">Registrar el post en el banco de contenido (Notion/Sheets)</span></li>
      </ul>
    </div>

    <div class="card">
      <div class="s-sub" style="margin-top:0;">📊 Domingo — Revisión</div>
      <ul class="checklist" id="cl-rev">
        <li onclick="toggleCheck(this)"><div class="check-box"></div><span class="check-label">Revisar métricas de la semana (alcance, likes, guardados)</span></li>
        <li onclick="toggleCheck(this)"><div class="check-box"></div><span class="check-label">Identificar el post con mejor desempeño y anotar por qué</span></li>
        <li onclick="toggleCheck(this)"><div class="check-box"></div><span class="check-label">¿Llegaron mensajes de prospectos? Registrarlos</span></li>
        <li onclick="toggleCheck(this)"><div class="check-box"></div><span class="check-label">Tomar 3–5 fotos en la sede para el banco de imágenes</span></li>
        <li onclick="toggleCheck(this)"><div class="check-box"></div><span class="check-label">Planear qué carrera o tema corresponde la próxima semana</span></li>
      </ul>
    </div>
  </div>

  <div class="s-sub">⚡ Tips de Rejurgitación de Contenido</div>
  <div class="grid-3">
    <div class="card">
      <div class="card-label">♻️ Repurpose cada post</div>
      <ul class="pillar-examples">
        <li>Un carrusel de IG → haz el mismo contenido como Reel</li>
        <li>Un video largo → corta 3 clips de 15 segundos</li>
        <li>Una frase de un testimonial → haz un gráfico independiente</li>
        <li>Un post exitoso → publícalo de nuevo en 3 meses</li>
      </ul>
    </div>
    <div class="card">
      <div class="card-label">🔄 Adaptar por plataforma</div>
      <ul class="pillar-examples">
        <li>IG feed: imagen cuadrada, copy mediano, hashtags al final</li>
        <li>FB: mismo contenido, añade dirección y teléfono</li>
        <li>TikTok: solo video vertical, texto corto, audio trending</li>
        <li>Stories: recorta el post principal, añade "swipe up" o link</li>
      </ul>
    </div>
    <div class="card">
      <div class="card-label">📦 Organiza tu banco</div>
      <ul class="pillar-examples">
        <li>Carpeta: Plantillas Canva (no borrar)</li>
        <li>Carpeta: Publicados IG/FB</li>
        <li>Carpeta: Publicados TikTok</li>
        <li>Carpeta: Por publicar / En revisión</li>
        <li>Carpeta: Evergreen (para repetir)</li>
      </ul>
    </div>
  </div>
</div>

<script>
function switchTab(name) {
  document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
  document.querySelectorAll('.section').forEach(s => s.classList.remove('active'));
  document.querySelector(`[onclick="switchTab('${name}')"]`).classList.add('active');
  document.getElementById(`tab-${name}`).classList.add('active');
  window.scrollTo({ top: 0, behavior: 'smooth' });
}

function toggleCheck(li) {
  li.classList.toggle('done');
}
</script>
</body>
</html>
