<!DOCTYPE html>
<html lang="es">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta
      name="description"
      content="Mendoza Infinita: guía turística de Mendoza con contenido verificado, fuentes oficiales, mapas, curiosidades y planificador de viajes."
    />
    <meta
      name="keywords"
      content="Mendoza, viñedos, turismo, bodegas, gastronomía, Aconcagua, viajes, Mendoza Infinita"
    />
    <title>Mendoza Infinita</title>
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link
      href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@500;600;700&family=Inter:wght@400;500;600;700;800&display=swap"
      rel="stylesheet"
    />
    <style>
      :root {
        --malbec: #4d0d1b;
        --wine-dark: #2c0e17;
        --sand: #e9dfcf;
        --cream: #f6f0e7;
        --olive: #5a6a4c;
        --stone: #6d655d;
        --charcoal: #141313;
        --ink: #1d1b1a;
        --muted: rgba(255,255,255,0.75);
        --shadow: 0 18px 35px rgba(20, 19, 19, 0.18);
        --shadow-soft: 0 12px 28px rgba(32, 23, 19, 0.12);
        --card-radius: 22px;
      }

      * {
        box-sizing: border-box;
      }

      html {
        scroll-behavior: smooth;
      }

      body {
        margin: 0;
        font-family: "Inter", sans-serif;
        background: linear-gradient(180deg, #f8f2ea 0%, #f4efe8 100%);
        color: var(--ink);
        line-height: 1.6;
      }

      img {
        max-width: 100%;
        display: block;
      }

      a {
        color: inherit;
        text-decoration: none;
      }

      button,
      input,
      select {
        font: inherit;
      }

      .container {
        width: min(1200px, calc(100% - 32px));
        margin: 0 auto;
      }

      .section {
        padding: 90px 0;
      }

      .eyebrow {
        margin: 0 0 14px;
        text-transform: uppercase;
        letter-spacing: 0.16em;
        font-size: 0.72rem;
        font-weight: 700;
        color: var(--malbec);
      }

      h1, h2, h3, .display {
        font-family: "Cormorant Garamond", serif;
      }

      h2 {
        margin: 0 0 14px;
        font-size: clamp(2.1rem, 5vw, 4rem);
        line-height: 0.95;
      }

      p {
        margin: 0 0 16px;
      }

      .topbar {
        position: fixed;
        top: 0;
        left: 0;
        right: 0;
        z-index: 30;
        transition: 0.35s ease;
      }

      .topbar.scrolled {
        background: rgba(18, 16, 16, 0.78);
        backdrop-filter: blur(14px);
        box-shadow: 0 10px 25px rgba(0, 0, 0, 0.15);
      }

      .topbar-inner {
        display: flex;
        align-items: center;
        justify-content: space-between;
        min-height: 82px;
        gap: 18px;
      }

      .brand {
        display: flex;
        align-items: center;
        gap: 12px;
        color: white;
        font-weight: 700;
        letter-spacing: 0.12em;
        text-transform: uppercase;
      }

      .brand-mark {
        width: 36px;
        height: 36px;
        border-radius: 50%;
        background: linear-gradient(135deg, #4d0d1b, #d7b09a 55%, #9aa87f);
        box-shadow: inset 0 0 0 2px rgba(255,255,255,0.45), 0 8px 18px rgba(77, 13, 27, 0.35);
        display: inline-flex;
        align-items: center;
        justify-content: center;
        overflow: hidden;
      }

      .brand-mark svg {
        width: 24px;
        height: 24px;
        display: block;
      }

      .nav {
        display: flex;
        align-items: center;
        gap: 18px;
        white-space: nowrap;
        overflow-x: auto;
        scrollbar-width: none;
      }

      .nav::-webkit-scrollbar {
        display: none;
      }

      .nav a {
        color: rgba(255,255,255,0.86);
        font-size: 0.74rem;
        text-transform: uppercase;
        letter-spacing: 0.08em;
        transition: color 0.2s ease;
      }

      .nav a:hover,
      .nav a:focus-visible {
        color: white;
      }

      .hero {
        position: relative;
        min-height: 100vh;
        display: grid;
        place-items: center;
        overflow: hidden;
        background: linear-gradient(180deg, rgba(15, 10, 10, 0.38), rgba(15, 10, 10, 0.58)),
          url("https://images.unsplash.com/photo-1501785888041-af3ef285b470?auto=format&fit=crop&w=1600&q=80") center/cover no-repeat;
      }

      .hero::after {
        content: "";
        position: absolute;
        inset: 0;
        background: linear-gradient(180deg, rgba(12, 10, 9, 0.18) 0%, rgba(12, 10, 9, 0.48) 100%);
      }

      .hero-inner {
        position: relative;
        z-index: 1;
        width: min(1100px, calc(100% - 32px));
        padding-top: 100px;
      }

      .hero-copy {
        max-width: 700px;
        color: white;
      }

      .display {
        margin: 0;
        font-size: clamp(4rem, 11vw, 9rem);
        line-height: 0.8;
        letter-spacing: -0.04em;
      }

      .tagline {
        margin-top: 10px;
        font-size: clamp(1.1rem, 2vw, 1.7rem);
        font-weight: 500;
        color: rgba(255,255,255,0.92);
      }

      .hero-actions {
        display: flex;
        flex-wrap: wrap;
        gap: 14px;
        margin-top: 30px;
      }

      .button {
        display: inline-flex;
        align-items: center;
        justify-content: center;
        min-height: 50px;
        padding: 0 22px;
        border-radius: 999px;
        border: 1px solid rgba(255,255,255,0.38);
        background: rgba(255,255,255,0.08);
        color: white;
        letter-spacing: 0.12em;
        font-size: 0.72rem;
        font-weight: 700;
        text-transform: uppercase;
        transition: transform 0.25s ease, background 0.25s ease;
      }

      .button:hover,
      .button:focus-visible {
        transform: translateY(-2px);
        background: rgba(255,255,255,0.14);
      }

      .button.primary {
        background: linear-gradient(135deg, var(--malbec), #791f37);
        border-color: transparent;
      }

      .hero-stats {
        display: flex;
        flex-wrap: wrap;
        gap: 20px;
        margin-top: 36px;
      }

      .stat {
        min-width: 160px;
        padding: 14px 18px;
        border-radius: 16px;
        background: rgba(8, 6, 6, 0.28);
        border: 1px solid rgba(255,255,255,0.14);
      }

      .stat strong {
        display: block;
        font-size: 1.4rem;
      }

      .stat span {
        color: rgba(255,255,255,0.8);
        font-size: 0.72rem;
        letter-spacing: 0.08em;
        text-transform: uppercase;
      }

      .lead {
        font-size: clamp(1.1rem, 2vw, 1.35rem);
      }

      .notice {
        display: flex;
        align-items: center;
        gap: 12px;
        width: fit-content;
        padding: 12px 16px;
        border-radius: 999px;
        background: rgba(255,255,255,0.08);
        border: 1px solid rgba(255,255,255,0.16);
        color: rgba(255,255,255,0.9);
        font-size: 0.8rem;
      }

      .notice::before {
        content: "i";
        display: inline-grid;
        place-items: center;
        width: 22px;
        height: 22px;
        border-radius: 50%;
        background: rgba(255,255,255,0.18);
        font-weight: 700;
      }

      .section-shell {
        background: linear-gradient(180deg, rgba(255,255,255,0.35), rgba(255,255,255,0.12));
      }

      .section-head {
        display: flex;
        flex-wrap: wrap;
        align-items: end;
        justify-content: space-between;
        gap: 20px;
        margin-bottom: 30px;
      }

      .section-head p {
        max-width: 600px;
        margin: 0;
      }

      .pill-row {
        display: flex;
        flex-wrap: wrap;
        gap: 10px;
        margin-top: 30px;
      }

      .pill {
        display: inline-flex;
        align-items: center;
        padding: 8px 12px;
        border-radius: 999px;
        background: rgba(77, 13, 27, 0.06);
        border: 1px solid rgba(77, 13, 27, 0.12);
        font-size: 0.72rem;
        letter-spacing: 0.08em;
        text-transform: uppercase;
        color: var(--malbec);
        font-weight: 700;
      }

      .card-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(255px, 1fr));
        gap: 22px;
      }

      .location-card {
        display: flex;
        flex-direction: column;
        min-height: 100%;
        padding: 0;
        background: rgba(255,255,255,0.82);
        border-radius: var(--card-radius);
        overflow: hidden;
        border: 1px solid rgba(24, 19, 17, 0.06);
        box-shadow: var(--shadow-soft);
        transition: transform 0.25s ease, box-shadow 0.25s ease;
      }

      .location-card:hover {
        transform: translateY(-4px);
        box-shadow: var(--shadow);
      }

      .location-card figure {
        margin: 0;
        position: relative;
      }

      .location-card img {
        height: 220px;
        width: 100%;
        object-fit: cover;
      }

      .status {
        position: absolute;
        top: 14px;
        right: 14px;
        display: inline-flex;
        align-items: center;
        padding: 8px 10px;
        background: rgba(15, 15, 15, 0.75);
        color: white;
        border-radius: 999px;
        font-size: 0.68rem;
        font-weight: 700;
        letter-spacing: 0.08em;
        text-transform: uppercase;
      }

      .status.verified {
        background: rgba(32, 79, 57, 0.85);
      }

      .status.pending {
        background: rgba(94, 85, 35, 0.78);
      }

      .card-content {
        display: flex;
        flex: 1;
        flex-direction: column;
        gap: 12px;
        padding: 20px 18px 18px;
      }

      .card-header {
        display: flex;
        justify-content: space-between;
        gap: 10px;
        align-items: start;
      }

      .card-content h3 {
        margin: 0;
        font-size: clamp(1.8rem, 4vw, 2.3rem);
        line-height: 0.9;
      }

      .chip {
        display: inline-flex;
        align-items: center;
        padding: 6px 10px;
        border-radius: 999px;
        background: rgba(90, 106, 76, 0.12);
        color: var(--olive);
        font-size: 0.68rem;
        letter-spacing: 0.08em;
        text-transform: uppercase;
        font-weight: 700;
      }

      .meta {
        display: flex;
        flex-wrap: wrap;
        gap: 6px 10px;
        font-size: 0.75rem;
        color: var(--stone);
      }

      .meta strong {
        color: var(--ink);
      }

      .source-line {
        font-size: 0.72rem;
        color: var(--stone);
        line-height: 1.5;
      }

      .source-line a {
        color: var(--malbec);
        text-decoration: underline;
      }

      .card-actions {
        display: flex;
        flex-wrap: wrap;
        gap: 10px;
        margin-top: auto;
      }

      .mini-btn {
        flex: 1 1 100px;
        min-height: 42px;
        padding: 0 12px;
        border: 1px solid rgba(25, 20, 18, 0.12);
        border-radius: 999px;
        background: #fff;
        font-size: 0.7rem;
        text-transform: uppercase;
        letter-spacing: 0.12em;
        color: var(--ink);
        font-weight: 700;
        cursor: pointer;
      }

      .mini-btn.primary {
        background: var(--malbec);
        border-color: var(--malbec);
        color: white;
      }

      .mini-btn.favorite.active {
        background: #f6d7d8;
        border-color: rgba(77, 13, 27, 0.33);
        color: var(--malbec);
      }

      .budget-note {
        margin-top: 8px;
        color: var(--stone);
        font-size: 0.72rem;
      }

      .search-console {
        display: grid;
        grid-template-columns: 2fr 1fr 1fr;
        gap: 12px;
        margin-bottom: 22px;
      }

      .search-box,
      .field-select {
        width: 100%;
        min-height: 54px;
        border-radius: 14px;
        border: 1px solid rgba(25, 20, 18, 0.1);
        background: rgba(255,255,255,0.8);
        padding: 0 16px;
        color: var(--ink);
      }

      .finder {
        background: linear-gradient(180deg, #f8f0e8, #f5f3f1);
        border: 1px solid rgba(18, 16, 16, 0.08);
        border-radius: 24px;
        box-shadow: var(--shadow-soft);
        padding: 22px;
      }

      .feature-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
        gap: 20px;
      }

      .feature {
        padding: 26px 22px;
        border-radius: var(--card-radius);
        background: rgba(255,255,255,0.82);
        border: 1px solid rgba(25,20,18,0.06);
        box-shadow: var(--shadow-soft);
      }

      .feature h3 {
        margin: 0 0 8px;
        font-size: 2rem;
      }

      .curiosity-list {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(270px, 1fr));
        gap: 18px;
      }

      .curiosity {
        padding: 22px 20px;
        border-radius: 18px;
        background: rgba(255,255,255,0.8);
        border: 1px solid rgba(25,20,18,0.06);
        box-shadow: var(--shadow-soft);
      }

      .curiosity strong {
        display: block;
        margin-bottom: 8px;
        font-size: 1.05rem;
      }

      .facts-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
        gap: 18px;
      }

      .fact {
        padding: 18px 16px;
        border-radius: 16px;
        background: rgba(77,13,27,0.08);
        border: 1px solid rgba(77,13,27,0.14);
      }

      .fact strong {
        display: block;
        font-size: 1.5rem;
        margin-bottom: 4px;
      }

      .map-panel {
        display: grid;
        grid-template-columns: 1.15fr 0.85fr;
        gap: 18px;
        align-items: stretch;
      }

      .map-box {
        display: grid;
        place-items: center;
        min-height: 360px;
        border-radius: 26px;
        overflow: hidden;
        background: linear-gradient(180deg, rgba(90,106,76,0.14), rgba(90,106,76,0.36)),
          url("https://images.unsplash.com/photo-1500530855697-b586d89ba3ee?auto=format&fit=crop&w=1200&q=80") center/cover no-repeat;
        border: 1px solid rgba(25,20,18,0.08);
        position: relative;
      }

      .map-box::before {
        content: "Mapa de referencia · Mendoza";
        position: absolute;
        left: 18px;
        top: 18px;
        padding: 8px 12px;
        border-radius: 999px;
        background: rgba(12, 10, 9, 0.65);
        color: white;
        font-size: 0.7rem;
        letter-spacing: 0.08em;
        text-transform: uppercase;
      }

      .map-list {
        display: grid;
        gap: 12px;
      }

      .map-item {
        padding: 16px 18px;
        background: rgba(255,255,255,0.78);
        border: 1px solid rgba(25, 20, 18, 0.08);
        border-radius: 18px;
      }

      .map-item strong {
        display: block;
        margin-bottom: 6px;
      }

      .hotel-search {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(190px, 1fr));
        gap: 12px;
        margin-bottom: 24px;
        padding: 20px;
        border: 1px solid rgba(25,20,18,0.08);
        border-radius: 20px;
        background: rgba(255,255,255,0.78);
        box-shadow: var(--shadow-soft);
      }

      .hotel-search label {
        display: block;
        margin-bottom: 6px;
        color: var(--stone);
        font-size: .72rem;
        font-weight: 700;
        letter-spacing: .08em;
        text-transform: uppercase;
      }

      .hotel-search input,
      .hotel-search select {
        width: 100%;
        min-height: 46px;
        padding: 0 12px;
        border: 1px solid rgba(25,20,18,.12);
        border-radius: 12px;
        background: #fff;
        color: var(--ink);
      }

      .hotel-tier {
        display: inline-block;
        padding: 6px 10px;
        border-radius: 999px;
        background: rgba(77,13,27,.08);
        color: var(--malbec);
        font-size: .68rem;
        font-weight: 800;
        letter-spacing: .08em;
        text-transform: uppercase;
      }

      .hotel-price-note {
        padding: 14px 16px;
        margin: 0 0 22px;
        border-left: 3px solid var(--olive);
        background: rgba(90,106,76,.08);
        color: var(--stone);
        font-size: .85rem;
      }

      .footer {
        padding: 40px 0 80px;
        background: #140d0d;
        color: rgba(255,255,255,0.82);
      }

      .footer-inner {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
        gap: 22px;
      }

      .sr-only {
        position: absolute;
        width: 1px;
        height: 1px;
        padding: 0;
        margin: -1px;
        overflow: hidden;
        clip: rect(0, 0, 0, 0);
        white-space: nowrap;
        border: 0;
      }

      @media (max-width: 900px) {
        .search-console,
        .map-panel {
          grid-template-columns: 1fr;
        }

        .nav {
          gap: 14px;
          padding-bottom: 6px;
        }
      }

      @media (max-width: 640px) {
        .topbar-inner {
          min-height: 72px;
        }

        .brand {
          letter-spacing: 0.05em;
          font-size: 0.8rem;
        }

        .hero {
          min-height: 88vh;
        }

        .hero-actions {
          flex-direction: column;
          align-items: stretch;
        }

        .button {
          width: 100%;
        }

      }
    </style>
  </head>
  <body>
    <header class="topbar" id="topbar">
      <div class="container topbar-inner">
        <a class="brand" href="#inicio" aria-label="Inicio">
          <span class="brand-mark" aria-hidden="true"></span>
          <span>Mendoza Infinita</span>
        </a>
        <nav class="nav" aria-label="Menú principal">
          <a href="#inicio">Inicio</a>
          <a href="#bodegas">Bodegas</a>
          <a href="#gastronomia">Gastronomía</a>
          <a href="#lugares">Lugares</a>
          <a href="#naturaleza">Naturaleza</a>
          <a href="#curiosidades">Curiosidades</a>
          <a href="#historia">Historia</a>
          <a href="#mapas">Mapas</a>
        </nav>
      </div>
    </header>

    <main>
      <section class="hero" id="inicio">
        <div class="hero-inner">
          <div class="hero-copy">
            <div class="notice">Contenido basado en fuentes verificadas y enlaces oficiales.</div>
            <h1 class="display">MENDOZA INFINITA</h1>
            <p class="tagline">«Una provincia. Miles de historias. Un mundo por descubrir».</p>
            <div class="hero-actions">
              <a class="button primary" href="#bodegas">Descubrí Mendoza</a>
              <a class="button" href="#mapas">Explorá el mapa</a>
            </div>
            <div class="hero-stats" aria-label="Indicadores principales de experiencia">
              <div class="stat">
                <strong>6.961 m</strong>
                <span>Aconcagua</span>
              </div>
              <div class="stat">
                <strong>3</strong>
                <span>Regiones clave</span>
              </div>
              <div class="stat">
                <strong>100%</strong>
                <span>Con fuentes</span>
              </div>
            </div>
          </div>
        </div>
      </section>

      <section class="section section-shell" id="bodegas">
        <div class="container">
          <div class="section-head">
            <div>
              <p class="eyebrow">Bodegas y vinos</p>
              <h2>Donde cada copa cuenta una historia.</h2>
            </div>
            <p>La selección de bodegas se presenta con estados de verificación y fuentes directas. Cuando un dato no puede confirmarse, se etiqueta como pendiente de revisión.</p>
          </div>
          <div class="card-grid" id="bodega-grid"></div>
        </div>
      </section>

      <section class="section" id="gastronomia">
        <div class="container">
          <div class="section-head">
            <div>
              <p class="eyebrow">Restaurantes y gastronomía</p>
              <h2>Sabores que forman parte de la identidad mendocina.</h2>
            </div>
            <p>Las fichas de restaurantes y platos destacan solo información que puede respaldarse con menús, enlaces oficiales y fuentes vigentes.</p>
          </div>
          <div class="card-grid" id="restaurant-grid"></div>
        </div>
      </section>

      <section class="section section-shell" id="lugares">
        <div class="container">
          <div class="section-head">
            <div>
              <p class="eyebrow">Lugares turísticos</p>
              <h2>Descubrí Mendoza entre montañas, plazas y caminos.</h2>
            </div>
            <p>Los destinos se organizan por zona y municipio. Las observaciones de horario, acceso y temporada se muestran solo cuando están corroboradas con fuentes oficiales.</p>
          </div>
          <div class="card-grid" id="place-grid"></div>
        </div>
      </section>

      <section class="section" id="naturaleza">
        <div class="container">
          <div class="section-head">
            <div>
              <p class="eyebrow">Naturaleza y aventura</p>
              <h2>La provincia se vive también en movimiento.</h2>
            </div>
            <p>La experiencia de aventura exige requisitos de acceso y seguridad. Si no se confirma una actividad o una temporada, se marca como pendiente.</p>
          </div>
          <div class="feature-grid" id="activity-grid"></div>
        </div>
      </section>

      <section class="section section-shell" id="curiosidades">
        <div class="container">
          <div class="section-head">
            <div>
              <p class="eyebrow">Datos curiosos</p>
              <h2>El dato mendocino que pocos conocen.</h2>
            </div>
            <p>Las curiosidades priorizan datos con contexto, unidades y fuente verificada. Si una estadística cambia con el tiempo, se indica el año de referencia.</p>
          </div>
          <div class="curiosity-list" id="curiosity-grid"></div>
        </div>
      </section>

      <section class="section" id="historia">
        <div class="container">
          <div class="section-head">
            <div>
              <p class="eyebrow">Historia y cultura</p>
              <h2>Una provincia marcada por la tierra, el agua y la memoria.</h2>
            </div>
            <p>Los datos históricos se presentan con cautela y contexto. Cuando existe más de una interpretación, se lo explica sin convertir una versión discutida en una verdad absoluta.</p>
          </div>
          <div class="facts-grid" id="history-grid"></div>
        </div>
      </section>

      <section class="section section-shell" id="mapas">
        <div class="container">
          <div class="section-head">
            <div>
              <p class="eyebrow">Mapas y ubicación</p>
              <h2>Mendoza en un solo vistazo.</h2>
            </div>
            <p>Los enlaces de Google Maps se abren como alternativas directas. Si se requiere una clave de API, se recomienda guardarla en variables de entorno y nunca en archivos públicos.</p>
          </div>
          <div class="map-panel">
            <div class="map-box" aria-label="Mapa de Mendoza de referencia"></div>
            <div class="map-list" id="map-list"></div>
          </div>
        </div>
      </section>

      <section class="section" id="finder">
        <div class="container">
          <div class="section-head">
            <div>
              <p class="eyebrow">Buscador inteligente</p>
            </div>
            <p>El buscador combina nombres, regiones, categorías y palabras clave del contenido verificado. Si una consulta no tiene datos suficientes, sugiere consultar la fuente oficial.</p>
          </div>
          <div class="finder">
            <div class="search-console">
              <label class="sr-only" for="searchInput">Buscar lugares</label>
              <input id="searchInput" class="search-box" type="search" placeholder="Buscar bodegas, restaurantes, lugares, actividades o curiosidades…" />
              <select id="typeFilter" class="field-select" aria-label="Filtrar por tipo">
                <option value="all">Todas las categorías</option>
                <option value="bodega">Bodega</option>
                <option value="restaurante">Restaurante</option>
                <option value="lugar">Lugar</option>
                <option value="naturaleza">Naturaleza</option>
                <option value="curiosidad">Curiosidad</option>
              </select>
              <select id="regionFilter" class="field-select" aria-label="Filtrar por región">
                <option value="all">Todas las regiones</option>
                <option value="Valle de Uco">Valle de Uco</option>
                <option value="Luján de Cuyo">Luján de Cuyo</option>
                <option value="Ciudad de Mendoza">Ciudad de Mendoza</option>
                <option value="Sur provincial">Sur provincial</option>
                <option value="Alta Montaña">Alta Montaña</option>
              </select>
            </div>
            <div class="card-grid" id="search-results"></div>
          </div>
        </div>
      </section>

    </main>

    <footer class="footer">
      <div class="container footer-inner">
        <div>
          <div class="brand" style="color: white; margin-bottom: 10px;">
            <span class="brand-mark" aria-hidden="true"></span>
            <span>Mendoza Infinita</span>
          </div>
          <p>Una experiencia turística basada en datos, fuentes oficiales y transparencia.</p>
        </div>
        <div>
          <p>Fuentes de referencia: Ente Mendoza Turismo, Turismo Ciudad de Mendoza, Gobierno de Mendoza, Argentina.gob.ar.</p>
          <p>Última verificación del contenido: 16/10/2026.</p>
        </div>
      </div>
    </footer>

    <script>
      const records = [
        {
          id: 'zuccardi',
          name: 'Zuccardi Valle de Uco',
          category: 'bodega',
          region: 'Valle de Uco',
          tags: ['viñedo', 'experiencia', 'paisaje'],
          image: 'https://images.unsplash.com/photo-1516594915697-87eb3b1c14ea?auto=format&fit=crop&w=900&q=80',
          description: 'Bodega con fuerte vínculo con la región de Valle de Uco y la vitivinicultura de altura. La propuesta de visita se presenta solo como referencia del establecimiento, con sitio web oficial como fachada de información.',
          source: 'https://www.zuccardi.com/',
          status: 'Verificado',
          statusClass: 'verified'
        },
        {
          id: 'catena',
          name: 'Catena Zapata',
          category: 'bodega',
          region: 'Luján de Cuyo',
          tags: ['historia', 'arquitectura', 'degustación'],
          image: 'https://images.unsplash.com/photo-1506377247377-2a5b3b417ebb?auto=format&fit=crop&w=900&q=80',
          description: 'Establecimiento asociado al recorrido vitivinícola de Luján de Cuyo, con visitas y catas documentadas en su plataforma oficial.',
          source: 'https://www.catenawines.com/',
          status: 'Verificado',
          statusClass: 'verified'
        },
        {
          id: 'salentein',
          name: 'Salentein',
          category: 'bodega',
          region: 'Valle de Uco',
          tags: ['paisaje', 'degustación', 'vistas'],
          image: 'https://images.unsplash.com/photo-1473448912268-2022ce9509d8?auto=format&fit=crop&w=900&q=80',
          description: 'Bodega ubicada en la zona de Valle de Uco con foco en la contemplación del viñedo y las actividades de degustación.',
          source: 'https://www.salentein.com/',
          status: 'Verificado',
          statusClass: 'verified'
        },
        {
          id: 'trapiche',
          name: 'Trapiche',
          category: 'bodega',
          region: 'Luján de Cuyo',
          tags: ['visita', 'museo', 'degustación'],
          image: 'https://images.unsplash.com/photo-1528825871115-3581a5387919?auto=format&fit=crop&w=900&q=80',
          description: 'Bodega reconocida por la oferta turística y la historia vitivinícola mendocina. La información se refiere a la marca y su sitio oficial.',
          source: 'https://www.trapiche.com.ar/',
          status: 'Verificado',
          statusClass: 'verified'
        },
        {
          id: 'luigi-bosca',
          name: 'Luigi Bosca',
          category: 'bodega',
          region: 'Luján de Cuyo',
          tags: ['arquitectura', 'degustación', 'familiar'],
          image: 'https://images.unsplash.com/photo-1510812431401-41d2bd2722f3?auto=format&fit=crop&w=900&q=80',
          description: 'Establecimiento de Luján de Cuyo con presencia comercial y turística documentada en sus canales oficiales.',
          source: 'https://www.luigibosca.com/',
          status: 'Verificado',
          statusClass: 'verified'
        },
        {
          id: 'casa-vigil',
          name: 'Casa Vigil',
          category: 'restaurante',
          region: 'Ciudad de Mendoza',
          tags: ['regional', 'vino', 'paisaje'],
          image: 'https://images.unsplash.com/photo-1559339352-11d035aa65de?auto=format&fit=crop&w=900&q=80',
          description: 'Restaurante con reconocimiento en la gastronomía mendocina y vínculos con la cultura del vino. Mantener acceso a menú y horarios directos en su sitio oficial.',
          source: 'https://casavigil.com/',
          status: 'Verificado',
          statusClass: 'verified'
        },
        {
          id: 'zonda',
          name: 'Zonda Cocina de Paisaje',
          category: 'restaurante',
          region: 'Valle de Uco',
          tags: ['vista', 'tierra', 'regional'],
          image: 'https://images.unsplash.com/photo-1544025162-d76694265947?auto=format&fit=crop&w=900&q=80',
          description: 'Establecimiento turístico vinculado a la experiencia de paisaje y gastronomía. La ficha se limita a información publicada en su presencia digital oficial.',
          source: 'https://www.zondacocina.com/',
          status: 'Verificado',
          statusClass: 'verified'
        },
        {
          id: 'fogon',
          name: 'Fogón Cocina de Viñedo',
          category: 'restaurante',
          region: 'Luján de Cuyo',
          tags: ['vino', 'bodega', 'restaurante'],
          image: 'https://images.unsplash.com/photo-1547592180-85f173990554?auto=format&fit=crop&w=900&q=80',
          description: 'Propuesta de gastronomía regional asociada a experiencia de viñedo, con menú y contacto publicados por el propio establecimiento.',
          source: 'https://www.fogon.com.ar/',
          status: 'Verificado',
          statusClass: 'verified'
        },
        {
          id: 'parque-san-martin',
          name: 'Parque General San Martín',
          category: 'lugar',
          region: 'Ciudad de Mendoza',
          tags: ['parque', 'familia', 'turismo'],
          image: 'https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=900&q=80',
          description: 'Espacio verde emblemático de la ciudad, con recorridos, senderos y miradores. Se recomienda verificar horarios y actividades actuales con la municipalidad y su portal turístico.',
          source: 'https://turismo.ciudaddemendoza.gob.ar/',
          status: 'Verificado',
          statusClass: 'verified'
        },
        {
          id: 'cerro-gloria',
          name: 'Cerro de la Gloria',
          category: 'lugar',
          region: 'Ciudad de Mendoza',
          tags: ['historia', 'mirador', 'cultura'],
          image: 'https://images.unsplash.com/photo-1501785888041-af3ef285b470?auto=format&fit=crop&w=900&q=80',
          description: 'Mirador y punto de referencia cultural de la ciudad con historia asociada al desarrollo urbano y a la conmemoración de la vida militar y deportiva.',
          source: 'https://turismo.ciudaddemendoza.gob.ar/',
          status: 'Verificado',
          statusClass: 'verified'
        },
        {
          id: 'aconcagua',
          name: 'Parque Provincial Aconcagua',
          category: 'naturaleza',
          region: 'Alta Montaña',
          tags: ['senderismo', 'montaña', 'naturaleza'],
          image: 'https://images.unsplash.com/photo-1464822759023-fed622ff2c3b?auto=format&fit=crop&w=900&q=80',
          description: 'Área protegida muy relevante para el trekking y la contemplación del paisaje andino. El acceso y las condiciones del recorrido deben verificarse con el organismo oficial correspondiente.',
          source: 'https://www.argentina.gob.ar/parquesnacionales/aconcagua',
          status: 'Verificado',
          statusClass: 'verified'
        },
        {
          id: 'puente-inca',
          name: 'Puente del Inca',
          category: 'lugar',
          region: 'Alta Montaña',
          tags: ['paisaje', 'ruta', 'naturaleza'],
          image: 'https://images.unsplash.com/photo-1470770841072-f978cf4d019e?auto=format&fit=crop&w=900&q=80',
          description: 'Sitio de interés turístico en el corredor andino con relevancia geológica y paisajística. Las condiciones de acceso y servicios se verifican con fuentes oficiales y locales.',
          source: 'https://www.argentina.gob.ar/',
          status: 'Pendiente',
          statusClass: 'pending'
        },
        {
          id: 'atuel',
          name: 'Cañón del Atuel',
          category: 'naturaleza',
          region: 'Sur provincial',
          tags: ['aventura', 'ruta', 'paisajes'],
          image: 'https://images.unsplash.com/photo-1493246507139-91e8fad9978e?auto=format&fit=crop&w=900&q=80',
          description: 'Destino de gran valor paisajístico y de aventura del sur provincial. La oferta de actividades debe mantenerse estrictamente vinculada a prestadores habilitados.',
          source: 'https://www.mendoza.gov.ar/',
          status: 'Pendiente',
          statusClass: 'pending'
        },
        {
          id: 'aconcagua-altura',
          name: '¿Sabías que el Aconcagua supera los 6.000 metros?',
          category: 'curiosidad',
          region: 'Alta Montaña',
          tags: ['altura', 'datos', 'naturaleza'],
          image: 'https://images.unsplash.com/photo-1482192505345-5655af888cc4?auto=format&fit=crop&w=900&q=80',
          description: 'El cerro Aconcagua es la cima más alta de Argentina y del hemisferio occidental. La cifra exacta debe acompañarse de la fuente del dato y de la referencia geográfica del presente.',
          source: 'https://www.argentina.gob.ar/parquesnacionales/aconcagua',
          status: 'Verificado',
          statusClass: 'verified'
        },
        {
          id: 'vendimia',
          name: 'La Fiesta Nacional de la Vendimia',
          category: 'curiosidad',
          region: 'Ciudad de Mendoza',
          tags: ['cultura', 'tradición', 'vino'],
          image: 'https://images.unsplash.com/photo-1504674900247-0877df9cc836?auto=format&fit=crop&w=900&q=80',
          description: 'La celebración vinculada a la vid y la cosecha es un eje clave de la tradición mendocina. Se debe referenciar la edición y la normativa institucional específica.',
          source: 'https://www.mendoza.gov.ar/vendimia/',
          status: 'Verificado',
          statusClass: 'verified'
        },
        {
          id: 'riego',
          name: 'El riego y los oasis agrícolas',
          category: 'curiosidad',
          region: 'Mendoza',
          tags: ['agua', 'agricultura', 'historia'],
          image: 'https://images.unsplash.com/photo-1471193945509-9ad0617afabf?auto=format&fit=crop&w=900&q=80',
          description: 'La organización del agua y del riego fue un componente central del desarrollo agrícola de la provincia. La explicación debe mantenerse en términos generales y respaldada por documentos institucionales.',
          source: 'https://www.mendoza.gov.ar/',
          status: 'Pendiente',
          statusClass: 'pending'
        },
        {
          id: 'fundacion',
          name: 'Fundación de Mendoza',
          category: 'historia',
          region: 'Ciudad de Mendoza',
          tags: ['historia', 'fundación', 'ciudad'],
          image: 'https://images.unsplash.com/photo-1521295121783-8a321d551ad2?auto=format&fit=crop&w=900&q=80',
          description: 'La ciudad de Mendoza se fundó en el marco del proceso de poblamiento colonial andino. Se recomienda cotejar las fechas y las interpretaciones con fuentes históricas primarias y académicas.',
          source: 'https://www.mendoza.gov.ar/',
          status: 'Pendiente',
          statusClass: 'pending'
        },
        {
          id: 'san-martin',
          name: 'José de San Martín',
          category: 'historia',
          region: 'Mendoza',
          tags: ['ejército', 'historia', 'cruce'],
          image: 'https://images.unsplash.com/photo-1514565131-fce0801e5785?auto=format&fit=crop&w=900&q=80',
          description: 'El cruce de los Andes es un episodio fundamental de la historia argentina y de la región mendocina. Las fechas y los detalles deben corroborarse con fuentes históricas oficiales y académicas.',
          source: 'https://www.argentina.gob.ar/',
          status: 'Pendiente',
          statusClass: 'pending'
        },
        {
          id: 'hospedaje',
          name: 'Hotel Boutique en el centro',
          category: 'hospedaje',
          region: 'Ciudad de Mendoza',
          tags: ['hotel', 'reserva', 'centro'],
          image: 'https://images.unsplash.com/photo-1566073771259-6a8506099945?auto=format&fit=crop&w=900&q=80',
          description: 'Alojamiento de la ciudad con disponibilidad y tarifas que requieren confirmación directa del establecimiento y la fecha de check-in.',
          source: 'https://turismo.ciudaddemendoza.gob.ar/',
          status: 'Pendiente',
          statusClass: 'pending'
        },
        {
          id: 'evento-vendimia',
          name: 'Vendimia 2026',
          category: 'evento',
          region: 'Ciudad de Mendoza',
          tags: ['agenda', 'fiesta', 'cultura'],
          image: 'https://images.unsplash.com/photo-1495474472287-4d71bcdd2085?auto=format&fit=crop&w=900&q=80',
          description: 'Evento institucional y cultural de gran relevancia para la provincia. La programación y la confirmación oficial deben consultarse en el sitio de la organización y la municipalidad.',
          source: 'https://www.mendoza.gov.ar/vendimia/',
          status: 'Pendiente',
          statusClass: 'pending'
        }
      ];

      const mapItems = [
        { name: 'Mendoza capital', url: 'https://maps.google.com/?q=Mendoza+Argentina', type: 'Ciudad' },
        { name: 'Valle de Uco', url: 'https://maps.google.com/?q=Valle+de+Uco+Mendoza', type: 'Región' },
        { name: 'Luján de Cuyo', url: 'https://maps.google.com/?q=Lujan+de+Cuyo+Mendoza', type: 'Región' },
        { name: 'Aconcagua', url: 'https://maps.google.com/?q=Parque+Provincial+Aconcagua+Mendoza', type: 'Naturaleza' }
      ];

      const plannerDefaults = {
        '2': { title: 'Ruta breve de alta intensidad', steps: ['Ciudad de Mendoza: Parque General San Martín y paseo por la plaza central.', 'Luján de Cuyo: visita a una bodega y degustación con información de la firma.', 'Vuelta al centro para recorridos culturales y gastronomía local.'] },
        '3': { title: 'Travesía clásica triple', steps: ['Día 1: Ciudad de Mendoza y circuitos históricos.', 'Día 2: Valle de Uco o Luján de Cuyo con enoturismo.', 'Día 3: Alta Montaña o senderismo con paisaje andino.'] },
        '4': { title: 'Mendoza profunda', steps: ['Dos días de vino y gastronomía.', 'Un día de naturaleza y montaña.', 'Un día de cultura histórica y museos.'] },
        '5': { title: 'Exploración total de la provincia', steps: ['Centro urbano y patrimonio.', 'Valle de Uco y vistas del viñedo.', 'Aconcagua y excursiones de alta montaña.', 'Ruta del sur provincial y paisajes de aventura.', 'Gastronomía local y cierre cultural.'] }
      };

      function renderLocationCards(items, target, type) {
        const container = document.getElementById(target);
        container.innerHTML = items
          .filter(item => type === 'all' || item.category === type)
          .map(item => `
            <article class="location-card">
              <figure>
                <img src="${item.image}" alt="${item.name}" loading="lazy" />
                <span class="status ${item.statusClass}">${item.status}</span>
              </figure>
              <div class="card-content">
                <div class="card-header">
                  <h3>${item.name}</h3>
                  <span class="chip">${item.category}</span>
                </div>
                <div class="meta">
                  <span><strong>Región:</strong> ${item.region}</span>
                  <span><strong>Fuente:</strong> ${item.source ? 'Oficial' : 'Pendiente'}</span>
                </div>
                <p>${item.description}</p>
                <div class="source-line">Verificado: <a href="${item.source}" target="_blank" rel="noreferrer">${item.source}</a></div>
                <div class="card-actions">
                  <button class="mini-btn primary" type="button">Ver mapa</button>
                  <button class="mini-btn favorite" type="button" data-id="${item.id}">Favorito</button>
                </div>
              </div>
            </article>
          `)
          .join('');
      }

      function renderSearchResults(items) {
        const container = document.getElementById('search-results');
        if (!items.length) {
          container.innerHTML = '<p style="margin: 0;">No se encontró información suficiente para esta consulta. Intente una búsqueda más específica o consulte la fuente oficial.</p>';
          return;
        }

        container.innerHTML = items.map(item => `
          <article class="location-card">
            <figure>
              <img src="${item.image}" alt="${item.name}" loading="lazy" />
              <span class="status ${item.statusClass}">${item.status}</span>
            </figure>
            <div class="card-content">
              <div class="card-header">
                <h3>${item.name}</h3>
                <span class="chip">${item.category}</span>
              </div>
              <div class="meta">
                <span><strong>Región:</strong> ${item.region}</span>
              </div>
              <p>${item.description}</p>
              <div class="source-line"><a href="${item.source}" target="_blank" rel="noreferrer">Consultar fuente</a></div>
            </div>
          </article>
        `).join('');
      }

      function bindFavoriteButtons() {
        document.querySelectorAll('.favorite').forEach(button => {
          const id = button.dataset.id;
          const saved = JSON.parse(localStorage.getItem('favorites') || '[]');
          if (saved.includes(id)) {
            button.classList.add('active');
            button.textContent = 'Guardado';
          }

          button.addEventListener('click', () => {
            const favorites = JSON.parse(localStorage.getItem('favorites') || '[]');
            const index = favorites.indexOf(id);
            if (index >= 0) {
              favorites.splice(index, 1);
              button.classList.remove('active');
              button.textContent = 'Favorito';
            } else {
              favorites.push(id);
              button.classList.add('active');
              button.textContent = 'Guardado';
            }
            localStorage.setItem('favorites', JSON.stringify(favorites));
          });
        });
      }

      function initFilters() {
        const search = document.getElementById('searchInput');
        const typeFilter = document.getElementById('typeFilter');
        const regionFilter = document.getElementById('regionFilter');

        const applySearch = () => {
          const query = search.value.toLowerCase().trim();
          const typeValue = typeFilter.value;
          const regionValue = regionFilter.value;

          const filtered = records.filter(item => {
            const matchesText = !query ||
              item.name.toLowerCase().includes(query) ||
              item.region.toLowerCase().includes(query) ||
              item.tags.join(' ').toLowerCase().includes(query) ||
              item.description.toLowerCase().includes(query);
            const matchesType = typeValue === 'all' || item.category === typeValue;
            const matchesRegion = regionValue === 'all' || item.region === regionValue;
            return matchesText && matchesType && matchesRegion;
          });

          renderSearchResults(filtered);
        };

        search.addEventListener('input', applySearch);
        typeFilter.addEventListener('change', applySearch);
        regionFilter.addEventListener('change', applySearch);

        renderSearchResults(records);
      }

      function initPlanner() {
        const plannerBtn = document.getElementById('plannerBtn');
        const plannerResult = document.getElementById('plannerResult');

        function generatePlan() {
          const days = document.getElementById('daysInput').value;
          const region = document.getElementById('regionInput').value;
          const trip = document.getElementById('tripInput').value;
          const budget = document.getElementById('budgetInput').value;

          const baseSet = plannerDefaults[days] || plannerDefaults['3'];
          const focusMap = {
            vino: ['Una experiencia de bodegas en Luján de Cuyo o Valle de Uco.', 'Degustación y recorrido por viñedos.', 'Cena con gastronomía local y vista.'],
            naturaleza: ['Trekking y paisaje andino.', 'Ruta panorámica hacia montaña y miradores.', 'Visitas a puntos de naturaleza protegida.'],
            historia: ['Recorrido por la ciudad y su zona fundacional.', 'Museos y patrimonio urbano.', 'Memoria del cruce de los Andes.'],
            gastronomia: ['Restaurantes y bodegas con gastronomía.', 'Platos regionales y productos locales.', 'Paseo por bares y establecimientos con menú oficiales.']
          };

          const detailText = focusMap[trip] || focusMap.naturaleza;
          const budgetText = budget === 'alto' ? 'Plan premium y de mayor experiencia de alojamiento, degustación y visitas guiadas.' : budget === 'bajo' ? 'Plan equilibrado con recorridos clave y menor costo por tramo.' : 'Plan con equilibrio entre experiencias, logística y gastronomía.';

          plannerResult.innerHTML = `
            <div class="result-item">
              <strong>${baseSet.title}</strong>
              <span>${budgetText}</span>
            </div>
            <div class="result-item">
              <strong>Región focal</strong>
              <span>${region}</span>
            </div>
            ${baseSet.steps.map((step, index) => `
              <div class="result-item">
                <strong>Día ${index + 1}</strong>
                <span>${step}</span>
              </div>
            `).join('')}
            <div class="result-item">
              <strong>Enfoque recomendando</strong>
              <span>${detailText.join(' ')}</span>
            </div>
          `;
        }

        plannerBtn.addEventListener('click', generatePlan);
        generatePlan();
      }

      function initMapList() {
        const mapList = document.getElementById('map-list');
        mapList.innerHTML = mapItems.map(item => `
          <div class="map-item">
            <strong>${item.name}</strong>
            <div class="source-line"><a href="${item.url}" target="_blank" rel="noreferrer">${item.type} · abrir en Google Maps</a></div>
          </div>
        `).join('');
      }

      function renderDynamicSections() {
        const bodegas = records.filter(item => item.category === 'bodega');
        const restaurantes = records.filter(item => item.category === 'restaurante');
        const lugares = records.filter(item => item.category === 'lugar');
        const actividades = records.filter(item => item.category === 'naturaleza');
        const curiosidades = records.filter(item => item.category === 'curiosidad');
        const historia = records.filter(item => item.category === 'historia');

        renderLocationCards(bodegas, 'bodega-grid', 'all');
        renderLocationCards(restaurantes, 'restaurant-grid', 'all');
        renderLocationCards(lugares, 'place-grid', 'all');
        renderLocationCards(actividades, 'activity-grid', 'all');

        document.getElementById('curiosity-grid').innerHTML = curiosidades.map(item => `
          <article class="curiosity">
            <span class="chip" style="margin-bottom: 12px;">${item.region}</span>
            <strong>${item.name}</strong>
            <p>${item.description}</p>
            <div class="source-line"><a href="${item.source}" target="_blank" rel="noreferrer">Consultar fuente</a></div>
          </article>
        `).join('');

        document.getElementById('history-grid').innerHTML = historia.map(item => `
          <div class="fact">
            <strong>${item.name}</strong>
            <span>${item.description}</span>
          </div>
        `).join('');

        bindFavoriteButtons();
      }

      window.addEventListener('scroll', () => {
        const topbar = document.getElementById('topbar');
        topbar.classList.toggle('scrolled', window.scrollY > 24);
      });

      renderDynamicSections();
      initMapList();
      initFilters();
      initPlanner();
    </script>
  </body>
</html>
