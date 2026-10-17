<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="theme-color" content="#25191b">
  <meta name="description" content="Mendoza Infinita: una guía visual para inspirarte y descubrir Mendoza, Argentina.">
  <title>Mendoza Infinita — Un mundo por descubrir</title>
  <link rel="preconnect" href="https://images.unsplash.com">
  <style>
    :root {
      --ink: #25191b;
      --wine: #713744;
      --wine-dark: #382029;
      --cream: #f7f2ea;
      --paper: #fffdf9;
      --gold: #d8b780;
      --muted: #746963;
      --line: rgba(37, 25, 27, .14);
      --serif: Georgia, "Times New Roman", serif;
      --sans: "Aptos", "Segoe UI", sans-serif;
    }

    * { box-sizing: border-box; }
    html { scroll-behavior: smooth; scroll-padding-top: 78px; }
    body { margin: 0; color: var(--ink); background: var(--cream); font-family: var(--sans); }
    body.locked { overflow: hidden; }
    a { color: inherit; }
    button, input, select { font: inherit; }
    a:focus-visible, button:focus-visible, input:focus-visible, select:focus-visible {
      outline: 3px solid #d8a852; outline-offset: 3px;
    }

    .skip {
      position: fixed; z-index: 100; top: 10px; left: 10px; padding: 10px;
      background: white; transform: translateY(-150%);
    }
    .skip:focus { transform: translateY(0); }

    .header {
      position: sticky; z-index: 20; top: 0; color: white;
      background: rgba(37, 25, 27, .96); backdrop-filter: blur(12px);
      border-bottom: 1px solid rgba(255,255,255,.12);
    }
    .nav {
      max-width: 1400px; min-height: 76px; margin: auto; padding: 0 5vw;
      display: flex; align-items: center; gap: 24px;
    }
    .brand { display: flex; align-items: center; gap: 10px; text-decoration: none; }
    .brand svg { width: 43px; height: 43px; }
    .brand b { display: block; font-size: 10px; letter-spacing: .19em; }
    .brand small { display: block; margin-top: 4px; color: #dfcdb5; font: italic 10px var(--serif); }
    .links { display: flex; align-items: center; gap: 18px; margin-left: auto; }
    .links a { color: #f2e9df; font-size: 10px; text-decoration: none; letter-spacing: .06em; }
    .links a:hover { color: var(--gold); }
    .round, .menu {
      position: relative; width: 42px; height: 42px; display: inline-grid; place-items: center;
      border: 1px solid rgba(255,255,255,.34); border-radius: 50%; background: transparent;
      color: white; cursor: pointer;
    }
    .menu { display: none; border-radius: 0; }
    .count {
      position: absolute; top: -4px; right: -5px; min-width: 18px; height: 18px;
      padding: 0 4px; border-radius: 20px; background: var(--gold); color: var(--ink);
      font-size: 10px; font-weight: bold; line-height: 18px;
    }

    .hero {
      min-height: min(790px, calc(100svh - 76px)); position: relative; display: grid;
      align-items: center; overflow: hidden; isolation: isolate; color: white;
      background: #59434a;
    }
    .hero::after {
      content: ""; position: absolute; z-index: -1; inset: 0;
      background: linear-gradient(90deg, rgba(22,15,17,.78), rgba(22,15,17,.12)),
        linear-gradient(0deg, rgba(22,15,17,.46), transparent 55%);
    }
    .hero img { position: absolute; z-index: -2; inset: 0; width: 100%; height: 100%;
      object-fit: cover; object-position: 50% 52%; }
    .hero-content { width: min(1350px, 100%); margin: auto; padding: 90px 8vw 115px; }
    .eyebrow, .kicker { color: var(--wine); font-size: 10px; letter-spacing: .2em; text-transform: uppercase; }
    .hero .eyebrow { color: #f2e4d0; }
    .hero h1 {
      margin: 27px 0 18px; font: 400 clamp(66px, 10vw, 140px)/.84 var(--serif);
      letter-spacing: -.06em;
    }
    .hero h1 em { color: #e2c18c; }
    .hero p { max-width: 460px; color: #f0e6dc; font-size: 16px; line-height: 1.8; }
    .button {
      display: inline-flex; min-height: 47px; justify-content: center; align-items: center;
      gap: 9px; margin: 10px 8px 0 0; padding: 0 18px; border: 1px solid transparent;
      text-decoration: none; text-transform: uppercase; letter-spacing: .09em;
      font-size: 10px; font-weight: bold; cursor: pointer; transition: transform .2s;
    }
    .button:hover { transform: translateY(-2px); }
    .gold { color: var(--ink); background: var(--gold); }
    .ghost { color: white; border-color: rgba(255,255,255,.65); }
    .hero-caption { position: absolute; right: 5vw; bottom: 22px; font-size: 9px; color: #eee1d6; }

    .section { padding: 90px max(6vw, calc((100vw - 1220px)/2)); }
    .section h2 { margin: 12px 0; font: 400 clamp(40px, 5.5vw, 68px)/.98 var(--serif); letter-spacing: -.045em; }
    .section-head { max-width: 700px; margin-bottom: 34px; }
    .section-head p { max-width: 620px; color: var(--muted); font-size: 14px; line-height: 1.8; }
    .intro { display: grid; grid-template-columns: 1fr .8fr; gap: 8vw; align-items: end; }
    .intro .section-head { margin: 0; }
    .quote { border-left: 1px solid var(--gold); padding-left: 23px; font: 21px/1.5 var(--serif); }
    .quote small { display: block; margin-top: 12px; color: var(--muted); font: 10px var(--sans); }

    .ribbon {
      padding: 26px max(6vw, calc((100vw - 1220px)/2)); display: flex;
      justify-content: space-between; align-items: center; gap: 20px;
      background: var(--wine-dark); color: white;
    }
    .ribbon p { margin: 0; font: 23px var(--serif); }
    .ribbon a { color: var(--gold); font-size: 10px; letter-spacing: .1em; text-transform: uppercase; }

    .gallery { background: #ece2d6; }
    .mosaic { display: grid; grid-template-columns: 1.2fr .8fr 1fr; grid-template-rows: 230px 220px; gap: 10px; }
    .tile { position: relative; min-width: 0; overflow: hidden; }
    .tile:first-child { grid-row: span 2; }
    .tile:last-child { grid-column: span 2; }
    .tile img { width: 100%; height: 100%; object-fit: cover; transition: transform .5s; }
    .tile:hover img { transform: scale(1.05); }
    .tile::after { content: ""; position: absolute; inset: 40% 0 0; background: linear-gradient(transparent, rgba(20,14,15,.72)); }
    .tile figcaption { position: absolute; z-index: 1; left: 16px; bottom: 15px; color: white; font: 20px var(--serif); }
    .tile figcaption small { display: block; margin-top: 5px; font: 9px var(--sans); letter-spacing: .12em; text-transform: uppercase; }

    .directory { background: var(--paper); }
    .filters {
      display: grid; grid-template-columns: 1.5fr .8fr .8fr auto; gap: 10px;
      padding: 15px; margin-bottom: 16px; background: var(--cream); border: 1px solid var(--line);
    }
    .field label { display: block; margin-bottom: 7px; color: var(--muted);
      font-size: 9px; font-weight: bold; letter-spacing: .1em; text-transform: uppercase; }
    .field input, .field select {
      width: 100%; min-height: 42px; padding: 0 10px; border: 1px solid var(--line);
      border-radius: 0; background: white; color: var(--ink);
    }
    .filter-action { display: flex; align-items: end; }
    .outline {
      min-height: 42px; padding: 0 13px; border: 1px solid var(--wine);
      background: transparent; color: var(--wine); cursor: pointer;
      font-size: 10px; font-weight: bold; text-transform: uppercase;
    }
    .result { min-height: 24px; color: var(--muted); font-size: 12px; }
    .cards { display: grid; grid-template-columns: repeat(3, minmax(0,1fr)); gap: 20px; }
    .card { overflow: hidden; background: white; border: 1px solid var(--line); transition: transform .2s, box-shadow .2s; }
    .card:hover { transform: translateY(-4px); box-shadow: 0 18px 45px #33231f1a; }
    .card-image { position: relative; height: 210px; overflow: hidden; background: linear-gradient(140deg,#bc9a76,#41343b); }
    .card-image img { width: 100%; height: 100%; object-fit: cover; transition: transform .45s; }
    .card:hover .card-image img { transform: scale(1.04); }
    .image-label {
      position: absolute; left: 12px; bottom: 12px; padding: 6px 8px;
      color: white; background: #21191ab3; font-size: 8px; letter-spacing: .1em; text-transform: uppercase;
    }
    .card-copy { padding: 18px; }
    .meta { display: flex; justify-content: space-between; gap: 8px; color: var(--wine);
      font-size: 9px; font-weight: bold; letter-spacing: .08em; text-transform: uppercase; }
    .card h3 { margin: 12px 0 8px; font: 25px/1.1 var(--serif); }
    .card p { min-height: 61px; margin: 0; color: var(--muted); font-size: 12px; line-height: 1.7; }
    .card-actions { display: flex; align-items: center; justify-content: space-between; gap: 8px;
      margin-top: 15px; padding-top: 12px; border-top: 1px solid var(--line); }
    .map-link, .save { color: var(--wine); font-size: 10px; font-weight: bold; text-decoration: none; }
    .save { padding: 7px 0 7px 7px; border: 0; background: transparent; cursor: pointer; }
    .save[aria-pressed="true"] { color: #a12c49; }
    .empty { grid-column: 1/-1; padding: 40px; border: 1px dashed var(--line); color: var(--muted); text-align: center; }

    .wide-photo { position: relative; min-height: 430px; overflow: hidden; color: white; }
    .wide-photo img { position: absolute; inset: 0; height: 100%; object-fit: cover; }
    .wide-photo::after { content: ""; position: absolute; inset: 0; background: linear-gradient(90deg,#1c1415c7,transparent); }
    .wide-copy { position: absolute; z-index: 1; top: 50%; left: 8vw; width: min(550px,80%); transform: translateY(-50%); }
    .wide-copy .kicker { color: var(--gold); }
    .wide-copy p { line-height: 1.7; }

    .food { background: #e9dfd2; }
    .food-grid { display: grid; grid-template-columns: repeat(4,1fr); gap: 1px; background: var(--line); border: 1px solid var(--line); }
    .food-card { padding: 22px; background: #f7f2ea; }
    .food-card small { color: var(--wine); font-size: 9px; letter-spacing: .12em; text-transform: uppercase; }
    .food-card h3 { font: 23px var(--serif); }
    .food-card p { color: var(--muted); font-size: 12px; line-height: 1.7; }

    .map-section { color: white; background: var(--ink); }
    .map-section .kicker { color: var(--gold); }
    .map-section p { color: #d2c5b9; line-height: 1.7; }
    .map-links { display: grid; }
    .map-links a { padding: 14px 0; border-bottom: 1px solid #ffffff30; color: #efd8b4; text-decoration: none; font-size: 12px; }
    .map-links a:hover { color: white; }
    .footer { display: flex; justify-content: space-between; gap: 20px; padding: 25px 6vw; background: #191214; color: #ddd0c4; font-size: 10px; }
    .footer p { margin: 0; }
    .footer a { color: var(--gold); }

    .backdrop { position: fixed; z-index: 39; inset: 0; visibility: hidden; opacity: 0; background: #120d0db3; transition: .2s; }
    .backdrop.open { visibility: visible; opacity: 1; }
    .drawer {
      position: fixed; z-index: 40; inset: 0 0 0 auto; width: min(430px,100%); padding: 23px;
      overflow-y: auto; background: var(--paper); transform: translateX(102%); transition: transform .25s;
    }
    .drawer.open { transform: translateX(0); }
    .drawer-head { display: flex; justify-content: space-between; align-items: center; border-bottom: 1px solid var(--line); }
    .drawer-head h2 { font: 32px var(--serif); }
    .close { width: 40px; height: 40px; border: 1px solid var(--line); background: transparent; cursor: pointer; font-size: 21px; }
    .note { color: var(--muted); font-size: 11px; line-height: 1.6; }
    .favorite { display: flex; justify-content: space-between; gap: 10px; padding: 14px 0; border-bottom: 1px solid var(--line); }
    .favorite strong { display: block; font: 19px var(--serif); }
    .favorite small { display: block; margin-top: 5px; color: var(--muted); }
    .favorite a { display: inline-block; margin-top: 8px; color: var(--wine); font-size: 10px; }
    .favorite button { align-self: start; border: 0; background: transparent; color: var(--wine); cursor: pointer; }
    .toast {
      position: fixed; z-index: 60; left: 50%; bottom: 22px; padding: 12px 17px;
      transform: translate(-50%,20px); opacity: 0; pointer-events: none;
      color: white; background: var(--ink); font-size: 12px; transition: .2s;
    }
    .toast.show { transform: translate(-50%,0); opacity: 1; }

    @media(max-width:1050px) {
      .links { gap: 11px; }
      .links a { font-size: 9px; }
      .cards { grid-template-columns: repeat(2,minmax(0,1fr)); }
    }
    @media(max-width:780px) {
      .nav { min-height: 66px; padding: 0 18px; }
      .menu { display: inline-grid; }
      .links { position: absolute; top: 66px; left: 0; right: 0; display: none; padding: 10px 20px 18px; background: #25191b; }
      .links.open { display: grid; }
      .links a { padding: 11px 0; border-bottom: 1px solid #ffffff1b; font-size: 12px; }
      .hero { min-height: min(730px,calc(100svh - 66px)); }
      .hero-content { padding: 80px 7vw 100px; }
      .section { padding: 70px 7vw; }
      .intro { grid-template-columns: 1fr; gap: 27px; }
      .filters { grid-template-columns: 1fr 1fr; }
      .field:first-child { grid-column: 1/-1; }
      .food-grid { grid-template-columns: repeat(2,1fr); }
    }
    @media(max-width:540px) {
      .brand svg { width: 37px; height: 37px; }
      .brand b { font-size: 9px; }
      .hero h1 { font-size: clamp(60px,17vw,85px); }
      .section { padding: 60px 6vw; }
      .section h2 { font-size: 44px; }
      .mosaic { grid-template-columns: 1fr 1fr; grid-template-rows: 240px 165px 165px; gap: 8px; }
      .tile:first-child { grid-column: span 2; grid-row: auto; }
      .tile:last-child { grid-column: span 2; }
      .filters { grid-template-columns: 1fr; }
      .field:first-child { grid-column: auto; }
      .cards, .food-grid { grid-template-columns: 1fr; }
      .card p { min-height: 0; }
      .ribbon, .footer { align-items: flex-start; flex-direction: column; }
      .drawer { padding: 19px; }
    }
    @media(prefers-reduced-motion:reduce) {
      *,*::before,*::after { scroll-behavior: auto !important; animation-duration: .01ms !important; transition-duration: .01ms !important; }
    }
  </style>
</head>
<body>
  <a class="skip" href="#contenido">Saltar al contenido</a>

  <header class="header">
    <div class="nav">
      <button class="menu" id="menuToggle" aria-label="Abrir menú" aria-expanded="false" aria-controls="navLinks">☰</button>
      <a class="brand" href="#inicio" aria-label="Mendoza Infinita, ir al inicio">
        <svg viewBox="0 0 64 64" aria-hidden="true">
          <circle cx="32" cy="32" r="30" fill="none" stroke="#d8b780" stroke-width="1.5"/>
          <path d="m12 42 16-25 7 11 6-8 12 22H12Z" fill="none" stroke="#fffaf2" stroke-width="2" stroke-linejoin="round"/>
          <path d="m20 42 7-11 6 9 6-9 7 11M21 49l6-4 6 4 6-4 6 4" fill="none" stroke="#d8b780" stroke-width="2" stroke-linecap="round"/>
        </svg>
        <span><b>MENDOZA INFINITA</b><small>Un mundo por descubrir</small></span>
      </a>
      <nav class="links" id="navLinks" aria-label="Navegación principal">
        <a href="#inicio">Inicio</a><a href="#galeria">Galería</a><a href="#explorar">Explorar</a>
        <a href="#bodegas">Bodegas</a><a href="#gastronomia">Sabores</a><a href="#mapa">Mapa</a>
      </nav>
      <button class="round" id="openFavorites" aria-label="Abrir favoritos" title="Favoritos">
        ♡<span class="count" id="favoriteCount">0</span>
      </button>
    </div>
  </header>

  <main id="contenido">
    <section class="hero" id="inicio">
      <img src="https://images.unsplash.com/photo-1470252649378-9c29740c9fa8?auto=format&fit=crop&w=2200&q=88"
           alt="Paisaje de montaña bajo la luz dorada del atardecer" fetchpriority="high">
      <div class="hero-content">
        <span class="eyebrow">Argentina · Andes · Tierra del sol</span>
        <h1>Mendoza<br><em>Infinita.</em></h1>
        <p>Una provincia. Miles de historias. Un mundo por descubrir.<br>De la cordillera a los viñedos, cada camino es una invitación.</p>
        <a class="button gold" href="#explorar">Empezar a explorar ↗</a>
        <a class="button ghost" href="#galeria">Dejarse inspirar ↓</a>
      </div>
      <span class="hero-caption">Fotografía ilustrativa · Unsplash</span>
    </section>

    <section class="section">
      <div class="intro">
        <div class="section-head"><span class="kicker">Mucho más que un destino</span>
          <h2>Un paisaje que<br>se queda con vos.</h2>
          <p>Montaña, agua, oasis, ciudad y el ritual de compartir una mesa. Elegí tu propio ritmo y empezá a imaginar el viaje.</p>
        </div>
        <div class="quote">“La montaña marca el horizonte. El agua, la vida. Y el vino, una forma de contar esta tierra.”
          <small>Una mirada editorial sobre Mendoza</small>
        </div>
      </div>
    </section>

    <div class="ribbon"><p>La próxima historia puede empezar en cualquier dirección.</p><a href="#explorar">Encontrá tu próximo lugar ↗</a></div>

    <section class="section gallery" id="galeria">
      <div class="section-head"><span class="kicker">Postales para soñar</span>
        <h2>Mendoza, en imágenes.</h2>
        <p>Una colección visual para entrar en clima. Las fotos son ilustrativas y no necesariamente muestran los destinos mencionados.</p>
      </div>
      <div class="mosaic">
        <figure class="tile"><img loading="lazy" src="https://images.unsplash.com/photo-1500530855697-b586d89ba3ee?auto=format&fit=crop&w=1000&q=85" alt="Amplio paisaje natural de montaña"><figcaption>Aventura en la montaña<small>Paisajes de altura</small></figcaption></figure>
        <figure class="tile"><img loading="lazy" src="https://images.unsplash.com/photo-1510812431401-41d2bd2722f3?auto=format&fit=crop&w=800&q=85" alt="Copas de vino servidas en una mesa"><figcaption>El ritual del vino<small>Una mesa, muchas historias</small></figcaption></figure>
        <figure class="tile"><img loading="lazy" src="https://images.unsplash.com/photo-1414235077428-338989a2e8c0?auto=format&fit=crop&w=800&q=85" alt="Plato presentado en un restaurante"><figcaption>Sabores para compartir<small>Un viaje de los sentidos</small></figcaption></figure>
        <figure class="tile"><img loading="lazy" src="https://images.unsplash.com/photo-1504279577054-acfeccf8fc52?auto=format&fit=crop&w=1300&q=85" alt="Hileras de viñas sobre un paisaje ondulado"><figcaption>Entre hileras de viñas<small>Cultura vitivinícola</small></figcaption></figure>
      </div>
    </section>

    <section class="section directory" id="explorar">
      <div class="section-head"><span class="kicker">Tu guía de viaje</span>
        <h2>Lugares con<br>alma propia.</h2>
        <p>Buscá por nombre, categoría o zona. Los enlaces de mapa realizan una búsqueda por nombre; verificá el resultado antes de viajar.</p>
      </div>
      <form class="filters" id="filters" role="search">
        <div class="field"><label for="search">Buscar un lugar</label><input id="search" type="search" placeholder="Ej. Aconcagua, bodega, ciudad"></div>
        <div class="field"><label for="category">Categoría</label>
          <select id="category">
            <option value="">Todas</option><option>Bodega</option><option>Gastronomía</option>
            <option>Hotel</option><option>Naturaleza</option><option>Cultura</option><option>Actividad</option>
          </select>
        </div>
        <div class="field"><label for="region">Zona</label><select id="region"><option value="">Todas las zonas</option></select></div>
        <div class="filter-action"><button class="outline" id="clearFilters" type="button">Limpiar</button></div>
      </form>
      <p class="result" id="resultCount" aria-live="polite"></p>
      <div class="cards" id="placeCards"></div>
    </section>

    <section class="wide-photo">
      <img loading="lazy" src="https://images.unsplash.com/photo-1464822759023-fed622ff2c3b?auto=format&fit=crop&w=1900&q=88" alt="Cumbres imponentes de una cordillera">
      <div class="wide-copy"><span class="kicker">Un horizonte que no se termina</span>
        <h2>La cordillera<br>te está esperando.</h2>
        <p>Respirá profundo. Mirá hacia arriba. La montaña siempre tiene algo más para mostrar.</p>
        <a class="button gold" href="#mapa">Explorar destinos ↗</a>
      </div>
    </section>

    <section class="section directory" id="bodegas">
      <div class="section-head"><span class="kicker">Cultura vitivinícola</span>
        <h2>De la viña<br>a la copa.</h2>
        <p>Conocé algunos nombres y empezá a explorar. Confirmá visitas, horarios y experiencias directamente con cada establecimiento.</p>
      </div>
      <div class="cards" id="wineryCards"></div>
    </section>

    <section class="section food" id="gastronomia">
      <div class="section-head"><span class="kicker">A la mesa</span>
        <h2>Sabores de una<br>tierra generosa.</h2>
        <p>Recetas argentinas, productos de estación y la cultura de compartir.</p>
      </div>
      <div class="food-grid">
        <article class="food-card"><small>Para compartir</small><h3>Empanadas</h3><p>Clásico argentino de masa rellena, horneada o frita. Las recetas varían según cada tradición.</p></article>
        <article class="food-card"><small>Mesa mendocina</small><h3>Tortitas</h3><p>Panificados cotidianos de panadería, presentes en desayunos y meriendas cuyanas.</p></article>
        <article class="food-card"><small>Fuego y reunión</small><h3>Asado</h3><p>Una forma argentina de reunirse alrededor del fuego, compartir y disfrutar la sobremesa.</p></article>
        <article class="food-card"><small>Estación y origen</small><h3>Productos locales</h3><p>Frutas, verduras, aceite de oliva y propuestas que expresan la identidad de la región.</p></article>
      </div>
    </section>

    <section class="section" id="hoteles">
      <div class="section-head"><span class="kicker">Quedarse un poco más</span>
        <h2>Un refugio<br>entre recorridos.</h2>
        <p>Referencias para iniciar la búsqueda. Tarifas, disponibilidad y servicios deben consultarse directamente con cada alojamiento.</p>
      </div>
      <div class="cards" id="hotelCards"></div>
    </section>

    <section class="section map-section" id="mapa">
      <div class="section-head"><span class="kicker">Orientate y seguí</span>
        <h2>Mendoza,<br>en el mapa.</h2>
        <p>Los siguientes enlaces abren búsquedas en Google Maps. Comprobá el destino, la ruta, los accesos y las condiciones antes de salir.</p>
      </div>
      <div class="map-links">
        <a href="https://www.google.com/maps/search/?api=1&query=Mendoza+Capital+Argentina" target="_blank" rel="noopener noreferrer">Explorar la ciudad de Mendoza ↗</a>
        <a href="https://www.google.com/maps/search/?api=1&query=Valle+de+Uco+Mendoza+Argentina" target="_blank" rel="noopener noreferrer">Explorar Valle de Uco ↗</a>
        <a href="https://www.google.com/maps/search/?api=1&query=Parque+Provincial+Aconcagua+Mendoza" target="_blank" rel="noopener noreferrer">Explorar alta montaña ↗</a>
        <a href="https://www.google.com/maps/search/?api=1&query=Maipu+Mendoza+Argentina" target="_blank" rel="noopener noreferrer">Explorar Maipú ↗</a>
      </div>
      <p>Las imágenes son ilustrativas. Esta guía no consulta en tiempo real horarios, tarifas ni accesos.</p>
    </section>
  </main>

  <footer class="footer"><p><strong>MENDOZA INFINITA</strong> · Una provincia. Miles de historias. Un mundo por descubrir.</p><p><a href="#inicio">Volver al inicio ↑</a></p></footer>

  <div class="backdrop" id="backdrop"></div>
  <aside class="drawer" id="drawer" role="dialog" aria-modal="true" aria-labelledby="drawerTitle" aria-hidden="true">
    <div class="drawer-head"><h2 id="drawerTitle">Tus favoritos</h2><button class="close" id="closeDrawer" aria-label="Cerrar favoritos">×</button></div>
    <p class="note">Se guardan en este navegador y no se sincronizan entre dispositivos.</p>
    <div id="favoriteList"></div>
    <p class="note" id="storageStatus"></p>
    <button class="outline" id="clearFavorites">Quitar todos</button>
  </aside>
  <div class="toast" id="toast" role="status" aria-live="polite"></div>

  <script>
    "use strict";

    const places = [
      {id:"aconcagua",name:"Parque Provincial Aconcagua",category:"Naturaleza",region:"Las Heras · Alta montaña",kind:"Naturaleza",photo:"photo-1464822759023-fed622ff2c3b",alt:"Cumbres de una cordillera",description:"Paisajes de alta montaña en torno al cerro Aconcagua. Consultá permisos y condiciones oficiales.",query:"Parque Provincial Aconcagua Mendoza Argentina",tags:"montaña senderismo naturaleza"},
      {id:"potrerillos",name:"Embalse de Potrerillos",category:"Naturaleza",region:"Luján de Cuyo",kind:"Naturaleza",photo:"photo-1500530855697-b586d89ba3ee",alt:"Paisaje de valle y montañas",description:"Un paisaje de agua y montaña al oeste de la ciudad. Revisá las condiciones locales antes de ir.",query:"Embalse Potrerillos Mendoza Argentina",tags:"montaña agua naturaleza"},
      {id:"puente-inca",name:"Puente del Inca",category:"Naturaleza",region:"Las Heras · Alta montaña",kind:"Naturaleza",photo:"photo-1470252649378-9c29740c9fa8",alt:"Paisaje natural iluminado al atardecer",description:"Sitio natural emblemático de la ruta de alta montaña. Verificá estado de caminos y condiciones.",query:"Puente del Inca Mendoza Argentina",tags:"montaña naturaleza historia"},
      {id:"parque-san-martin",name:"Parque General San Martín",category:"Naturaleza",region:"Ciudad de Mendoza",kind:"Naturaleza",photo:"photo-1441974231531-c6227db76b6e",alt:"Sendero rodeado de árboles",description:"Un amplio espacio verde urbano para recorrer y disfrutar del arbolado de la ciudad.",query:"Parque General San Martín Mendoza Argentina",tags:"ciudad parque paseo"},
      {id:"cerro-gloria",name:"Cerro de la Gloria",category:"Cultura",region:"Ciudad de Mendoza",kind:"Historia y cultura",photo:"photo-1464822759023-fed622ff2c3b",alt:"Montañas bajo el cielo abierto",description:"Monumento y mirador en el Parque General San Martín, dedicado al Ejército de los Andes.",query:"Cerro de la Gloria Mendoza Argentina",tags:"historia cultura monumento"},
      {id:"catena",name:"Bodega Catena Zapata",category:"Bodega",region:"Luján de Cuyo",kind:"Bodega",photo:"photo-1504279577054-acfeccf8fc52",alt:"Hileras de viñedos verdes",description:"Bodega mendocina conocida por su arquitectura. Confirmá visitas y experiencias directamente.",query:"Bodega Catena Zapata Mendoza Argentina",tags:"vino viñedos visita"},
      {id:"trapiche",name:"Bodega Trapiche",category:"Bodega",region:"Maipú",kind:"Bodega",photo:"photo-1510812431401-41d2bd2722f3",alt:"Copas de vino sobre una mesa",description:"Referencia vitivinícola de Maipú. La oferta de visitas puede variar: consultá sus canales oficiales.",query:"Bodega Trapiche Maipu Mendoza Argentina",tags:"vino viñedos degustación"},
      {id:"casa-vigil",name:"Casa Vigil",category:"Gastronomía",region:"Maipú",kind:"Gastronomía",photo:"photo-1414235077428-338989a2e8c0",alt:"Plato servido en una mesa de restaurante",description:"Propuesta gastronómica en Maipú. Consultá menú, horarios y reservas con el establecimiento.",query:"Casa Vigil Chachingo Mendoza Argentina",tags:"comida restaurante vino"},
      {id:"hyatt",name:"Park Hyatt Mendoza",category:"Hotel",region:"Ciudad de Mendoza",kind:"Hotel",photo:"photo-1566073771259-6a8506099945",alt:"Hotel con piscina y jardines",description:"Hotel céntrico frente a Plaza Independencia. Tarifas y disponibilidad dependen de las fechas.",query:"Park Hyatt Mendoza Argentina",tags:"hotel alojamiento ciudad"},
      {id:"diplomatic",name:"Diplomatic Hotel",category:"Hotel",region:"Ciudad de Mendoza",kind:"Hotel",photo:"photo-1542314831-068cd1dbfeeb",alt:"Hotel con iluminación cálida",description:"Alojamiento en la ciudad. Consultá directamente servicios, disponibilidad y tarifas actuales.",query:"Diplomatic Hotel Mendoza Argentina",tags:"hotel alojamiento ciudad"},
      {id:"valle-uco",name:"Paisajes del Valle de Uco",category:"Actividad",region:"Valle de Uco",kind:"Actividad",photo:"photo-1504279577054-acfeccf8fc52",alt:"Viñedos extendidos en un valle",description:"Región de paisajes andinos y vitivinícolas. Planificá traslados y visitas con cada proveedor.",query:"Valle de Uco Mendoza Argentina",tags:"actividad naturaleza vino excursión"}
    ];

    const KEY = "mendoza-infinita-favoritos-v1";
    const $ = id => document.getElementById(id);
    let favorites = new Set();
    let storageAvailable = true;
    let toastTimer;

    function escapeHtml(text) {
      return String(text).replace(/[&<>"']/g, char =>
        ({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"}[char]));
    }
    function imageUrl(photo) {
      return `https://images.unsplash.com/${encodeURIComponent(photo)}?auto=format&fit=crop&w=850&q=82`;
    }
    function mapUrl(place) {
      return "https://www.google.com/maps/search/?api=1&query=" + encodeURIComponent(place.query);
    }
    function toast(message) {
      $("toast").textContent = message;
      $("toast").classList.add("show");
      clearTimeout(toastTimer);
      toastTimer = setTimeout(() => $("toast").classList.remove("show"), 3200);
    }
    function loadFavorites() {
      try {
        const raw = localStorage.getItem(KEY);
        if (!raw) return new Set();
        const value = JSON.parse(raw);
        if (!Array.isArray(value) || value.some(id =>
          typeof id !== "string" || !places.some(place => place.id === id))) {
          throw new Error("Formato inválido de favoritos");
        }
        return new Set(value);
      } catch (error) {
        storageAvailable = false;
        toast("No se pudieron leer los favoritos guardados en este navegador.");
        return new Set();
      }
    }
    function saveFavorites() {
      try {
        localStorage.setItem(KEY, JSON.stringify([...favorites]));
        storageAvailable = true;
      } catch (error) {
        storageAvailable = false;
        toast("No se pudieron guardar los favoritos. Revisá el almacenamiento del navegador.");
      }
    }
    function card(place) {
      const saved = favorites.has(place.id);
      return `<article class="card">
        <div class="card-image">
          <img loading="lazy" src="${imageUrl(place.photo)}" alt="${escapeHtml(place.alt)}">
          <span class="image-label">Imagen ilustrativa</span>
        </div>
        <div class="card-copy">
          <div class="meta"><span>${escapeHtml(place.kind)}</span><span>${escapeHtml(place.region)}</span></div>
          <h3>${escapeHtml(place.name)}</h3>
          <p>${escapeHtml(place.description)}</p>
          <div class="card-actions">
            <a class="map-link" href="${mapUrl(place)}" target="_blank" rel="noopener noreferrer">⌖ Buscar en Maps ↗</a>
            <button class="save" type="button" data-save="${escapeHtml(place.id)}" aria-pressed="${saved}">
              ${saved ? "♥ Guardado" : "♡ Guardar"}
            </button>
          </div>
        </div>
      </article>`;
    }
    function renderCards(element, list) {
      element.innerHTML = list.length ? list.map(card).join("") :
        '<div class="empty">No encontramos resultados. Probá otra búsqueda o limpiá los filtros.</div>';
      element.querySelectorAll("img").forEach(img => img.addEventListener("error", () => {
        img.alt = "Imagen no disponible";
        img.remove();
      }, {once:true}));
    }
    function filteredPlaces() {
      const term = $("search").value.trim().toLocaleLowerCase("es");
      const category = $("category").value;
      const region = $("region").value;
      return places.filter(place => {
        const searchable = `${place.name} ${place.category} ${place.region} ${place.description} ${place.tags}`.toLocaleLowerCase("es");
        return (!term || searchable.includes(term)) &&
          (!category || category === place.category) &&
          (!region || region === place.region);
      });
    }
    function renderFavorites() {
      const list = places.filter(place => favorites.has(place.id));
      $("favoriteCount").textContent = String(favorites.size);
      $("favoriteList").innerHTML = list.length ? list.map(place => `
        <article class="favorite">
          <div><strong>${escapeHtml(place.name)}</strong>
          <small>${escapeHtml(place.kind)} · ${escapeHtml(place.region)}</small>
          <a href="${mapUrl(place)}" target="_blank" rel="noopener noreferrer">Buscar en Maps ↗</a></div>
          <button type="button" data-remove="${escapeHtml(place.id)}" aria-label="Quitar ${escapeHtml(place.name)}">Quitar</button>
        </article>`).join("") : '<p class="note">Todavía no guardaste lugares. Explorá y armá tu lista.</p>';
      $("storageStatus").textContent = storageAvailable ? "Favoritos guardados en este navegador." : "Almacenamiento no disponible.";
      $("clearFavorites").disabled = list.length === 0;
    }
    function renderAll() {
      renderCards($("placeCards"), filteredPlaces());
      $("resultCount").textContent = `${filteredPlaces().length} lugares encontrados`;
      renderCards($("wineryCards"), places.filter(place => place.category === "Bodega"));
      renderCards($("hotelCards"), places.filter(place => place.category === "Hotel"));
      renderFavorites();
    }
    function toggleFavorite(id) {
      if (!places.some(place => place.id === id)) return;
      if (favorites.has(id)) {
        favorites.delete(id);
        toast("Lugar quitado de favoritos.");
      } else {
        favorites.add(id);
        toast("Lugar guardado en favoritos.");
      }
      saveFavorites();
      renderAll();
    }
    function openDrawer() {
      $("drawer").classList.add("open");
      $("backdrop").classList.add("open");
      $("drawer").setAttribute("aria-hidden", "false");
      document.body.classList.add("locked");
      $("closeDrawer").focus();
    }
    function closeDrawer() {
      $("drawer").classList.remove("open");
      $("backdrop").classList.remove("open");
      $("drawer").setAttribute("aria-hidden", "true");
      document.body.classList.remove("locked");
      $("openFavorites").focus();
    }

    [...new Set(places.map(place => place.region))]
      .sort((a,b) => a.localeCompare(b, "es"))
      .forEach(region => {
        const option = document.createElement("option");
        option.value = region;
        option.textContent = region;
        $("region").append(option);
      });

    favorites = loadFavorites();
    renderAll();

    $("filters").addEventListener("submit", event => event.preventDefault());
    $("search").addEventListener("input", () => {
      renderCards($("placeCards"), filteredPlaces());
      $("resultCount").textContent = `${filteredPlaces().length} lugares encontrados`;
    });
    $("category").addEventListener("change", () => {
      renderCards($("placeCards"), filteredPlaces());
      $("resultCount").textContent = `${filteredPlaces().length} lugares encontrados`;
    });
    $("region").addEventListener("change", () => {
      renderCards($("placeCards"), filteredPlaces());
      $("resultCount").textContent = `${filteredPlaces().length} lugares encontrados`;
    });
    $("clearFilters").addEventListener("click", () => {
      $("search").value = "";
      $("category").value = "";
      $("region").value = "";
      renderAll();
      $("search").focus();
    });
    document.addEventListener("click", event => {
      const save = event.target.closest("[data-save]");
      const remove = event.target.closest("[data-remove]");
      if (save) toggleFavorite(save.dataset.save);
      if (remove) toggleFavorite(remove.dataset.remove);
    });
    $("openFavorites").addEventListener("click", openDrawer);
    $("closeDrawer").addEventListener("click", closeDrawer);
    $("backdrop").addEventListener("click", closeDrawer);
    document.addEventListener("keydown", event => {
      if (event.key === "Escape" && $("drawer").classList.contains("open")) closeDrawer();
    });
    $("clearFavorites").addEventListener("click", () => {
      if (favorites.size && confirm("¿Quitar todos los lugares guardados?")) {
        favorites.clear();
        saveFavorites();
        renderAll();
        toast("Se quitaron todos los favoritos.");
      }
    });
    $("menuToggle").addEventListener("click", () => {
      const nav = $("navLinks");
      const open = nav.classList.toggle("open");
      $("menuToggle").setAttribute("aria-expanded", String(open));
      $("menuToggle").setAttribute("aria-label", open ? "Cerrar menú" : "Abrir menú");
      $("menuToggle").textContent = open ? "×" : "☰";
    });
    $("navLinks").addEventListener("click", event => {
      if (event.target.closest("a")) {
        $("navLinks").classList.remove("open");
        $("menuToggle").setAttribute("aria-expanded", "false");
        $("menuToggle").setAttribute("aria-label", "Abrir menú");
        $("menuToggle").textContent = "☰";
      }
    });
  </script>
</body>
</html>
