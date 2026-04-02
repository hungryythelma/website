# website
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8"/>
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Hungry Thelma</title>

  <link href="https://db.onlinewebfonts.com/c/07cb29fdcb073fff840edc6de2067b50?family=Amsterdam+Four_ttf" rel="stylesheet">
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;1,300;1,400&family=DM+Sans:opsz,wght@9..40,300;9..40,400;9..40,500&display=swap" rel="stylesheet">

  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --white:    #ffffff;
      --bg:       #f8f7f5;
      --bg2:      #f2f1ee;
      --accent:   #fffee6;
      --accent-b: #ede9b0;
      --ink:      #1a1a18;
      --dark:     #2c2c28;
      --mid:      #6a6a5e;
      --muted:    #9c9c8c;
      --border:   #e6e5e0;
      --serif:    'Cormorant Garamond', Georgia, serif;
      --sans:     'DM Sans', sans-serif;
      --display:  'Amsterdam Four_ttf', cursive;
    }

    html { scroll-behavior: smooth; }

    body {
      background: var(--white);
      color: var(--ink);
      font-family: var(--sans);
      font-weight: 300;
      line-height: 1.75;
      overflow-x: hidden;
    }

    img { display: block; width: 100%; height: 100%; object-fit: cover; }

    /* ─── NAV ─── */
    nav {
      position: fixed; top: 0; left: 0; right: 0; z-index: 200;
      display: flex; justify-content: space-between; align-items: center;
      padding: 1.1rem 6vw;
      background: rgba(255,255,255,0.96);
      backdrop-filter: blur(20px);
      border-bottom: 1px solid var(--border);
    }

    .nav-logo {
      font-family: var(--display);
      font-size: 2.3rem;
      color: var(--ink);
      text-decoration: none;
      line-height: 1;
      font-weight: 100;
      letter-spacing: 0.01em;
    }

    .nav-links { display: flex; gap: 2.2rem; list-style: none; align-items: center; }
    .nav-links a {
      text-decoration: none; color: var(--muted);
      font-size: 0.71rem; letter-spacing: 0.14em;
      text-transform: uppercase; font-weight: 400;
      transition: color 0.2s;
    }
    .nav-links a:hover { color: var(--ink); }

    .nav-pill {
      background: var(--ink) !important;
      color: var(--white) !important;
      padding: 0.52rem 1.35rem;
      border-radius: 100px;
      font-weight: 500 !important;
      letter-spacing: 0.1em !important;
      transition: opacity 0.2s !important;
    }
    .nav-pill:hover { opacity: 0.72 !important; }

    .nav-toggle {
      display: none; flex-direction: column; gap: 5px;
      cursor: pointer; background: none; border: none; padding: 4px;
    }
    .nav-toggle span { display: block; width: 22px; height: 1px; background: var(--ink); }

    /* ─── BUTTONS ─── */
    .btn {
      display: inline-block; text-decoration: none;
      font-family: var(--sans); font-size: 0.7rem;
      letter-spacing: 0.14em; text-transform: uppercase; font-weight: 500;
      padding: 0.9rem 2rem; border-radius: 100px;
      transition: all 0.22s; cursor: pointer; border: none; text-align: center;
    }
    .btn-dark    { background: var(--ink); color: var(--white); }
    .btn-dark:hover { opacity: 0.78; transform: translateY(-1px); }
    .btn-ghost   { background: transparent; color: var(--ink); border: 1px solid var(--border); }
    .btn-ghost:hover { border-color: var(--ink); }
    .btn-outline { background: transparent; color: var(--ink); border: 1px solid rgba(26,26,24,0.18); }
    .btn-outline:hover { background: var(--bg2); }

    /* ─── HERO ─── */
    #hero {
      min-height: 100svh;
      display: grid; grid-template-columns: 1fr 1fr;
      align-items: center; padding: 7rem 6vw 4rem; gap: 4rem;
      background: var(--white); position: relative; overflow: hidden;
    }
    #hero::after {
      content: ''; position: absolute;
      width: 500px; height: 500px; border-radius: 50%;
      background: var(--bg); top: -160px; right: -140px;
      z-index: 0; pointer-events: none;
    }

    .hero-left { position: relative; z-index: 1; }

    .hero-eyebrow {
      display: inline-flex; align-items: center; gap: 0.7rem;
      font-size: 0.63rem; letter-spacing: 0.24em;
      text-transform: uppercase; color: var(--muted); font-weight: 400;
      margin-bottom: 1.5rem;
      animation: fadeUp 0.7s ease both;
    }
    .hero-eyebrow span { display: block; width: 20px; height: 1px; background: var(--border); }

    h1.site-name {
      font-family: var(--display);
      font-size: clamp(5rem, 9.5vw, 10.5rem);
      color: var(--ink); line-height: 0.92; font-weight: 100;
      animation: fadeUp 0.7s 0.1s ease both;
    }

    .hero-tags {
      display: flex; gap: 0.55rem; flex-wrap: wrap;
      margin: 1.9rem 0;
      animation: fadeUp 0.7s 0.2s ease both;
    }
    .htag {
      font-size: 0.63rem; letter-spacing: 0.12em; text-transform: uppercase;
      font-weight: 500; padding: 0.38rem 0.95rem; border-radius: 100px;
      background: var(--bg); color: var(--dark); border: 1px solid var(--border);
    }

    .hero-tagline {
      font-family: var(--serif); font-style: italic;
      font-size: 1.08rem; color: var(--mid); max-width: 370px; line-height: 1.9;
      animation: fadeUp 0.7s 0.3s ease both;
    }

    .hero-ctas {
      display: flex; gap: 0.9rem; flex-wrap: wrap;
      margin-top: 2.5rem;
      animation: fadeUp 0.7s 0.4s ease both;
    }

    /* ─── HERO IMAGES ─── */
    .hero-right { position: relative; z-index: 1; height: 560px; animation: fadeUp 0.8s 0.15s ease both; }

    .hi-main {
      position: absolute; top: 0; right: 0; width: 72%; height: 75%;
      border-radius: 42% 58% 52% 48% / 46% 44% 56% 54%;
      overflow: hidden; box-shadow: 0 20px 55px rgba(0,0,0,0.08);
    }
    .hi-sm1 {
      position: absolute; bottom: 3%; left: 0; width: 46%; height: 50%;
      border-radius: 54% 46% 44% 56% / 54% 52% 48% 46%;
      overflow: hidden; box-shadow: 0 14px 38px rgba(0,0,0,0.07);
    }
    .hi-sm2 {
      position: absolute; top: 46%; right: 4%; width: 30%; height: 34%;
      border-radius: 50%; overflow: hidden;
      box-shadow: 0 10px 28px rgba(0,0,0,0.07);
      border: 5px solid var(--white);
    }

    /* Accent yellow — small floating badge only */
    .hero-float {
      position: absolute; bottom: 9%; right: -1%;
      background: var(--accent); border: 1px solid var(--accent-b);
      border-radius: 14px; padding: 0.85rem 1.15rem;
      display: flex; align-items: center; gap: 0.65rem;
      box-shadow: 0 6px 20px rgba(0,0,0,0.06);
      animation: float 3.5s ease-in-out infinite;
    }
    .hero-float-icon { font-size: 1.3rem; }
    .hero-float-text { font-size: 0.68rem; font-weight: 500; color: var(--dark); line-height: 1.35; }
    .hero-float-text small { display: block; font-weight: 300; color: var(--mid); }

    /* ─── SECTION COMMONS ─── */
    section { padding: 6.5rem 6vw; }

    .sec-eyebrow {
      font-size: 0.62rem; letter-spacing: 0.26em;
      text-transform: uppercase; color: var(--muted);
      font-weight: 500; margin-bottom: 0.65rem;
    }
    .sec-title {
      font-family: var(--serif);
      font-size: clamp(2rem, 3.5vw, 2.8rem);
      font-weight: 300; line-height: 1.2; color: var(--ink);
      margin-bottom: 0.8rem;
    }
    .sec-title em { font-style: italic; font-weight: 400; }
    .sec-sub { font-size: 0.89rem; color: var(--mid); line-height: 1.9; max-width: 460px; }

    .rule { width: 36px; height: 1px; background: var(--border); margin: 1.2rem 0 2rem; }

    /* ─── ABOUT ─── */
    #about {
      background: var(--bg);
      display: grid; grid-template-columns: 1fr 1fr;
      gap: 6rem; align-items: center;
    }

    .about-mosaic {
      display: grid;
      grid-template-columns: 1fr 1fr;
      grid-template-rows: 230px 230px;
      gap: 10px;
    }
    .ab-photo { border-radius: 16px; overflow: hidden; box-shadow: 0 4px 18px rgba(0,0,0,0.06); }
    .ab-photo:nth-child(1) { grid-row: 1 / 3; border-radius: 22px; }
    .ab-photo:nth-child(2) { border-radius: 16px 22px 16px 16px; }
    .ab-photo:nth-child(3) { border-radius: 16px 16px 22px 16px; }

    .about-text p { font-size: 0.9rem; color: var(--mid); line-height: 1.95; margin-bottom: 1rem; }

    .about-chips { display: flex; flex-wrap: wrap; gap: 0.5rem; margin: 1.6rem 0 2rem; }
    .chip {
      font-size: 0.64rem; font-weight: 500; letter-spacing: 0.07em;
      padding: 0.36rem 0.9rem; border-radius: 100px;
      background: var(--white); color: var(--dark); border: 1px solid var(--border);
    }

    /* ─── BLOG ─── */
    #blog { background: var(--white); }

    .blog-top {
      display: flex; justify-content: space-between;
      align-items: flex-end; margin-bottom: 2.8rem; flex-wrap: wrap; gap: 1rem;
    }

    .blog-grid { display: grid; grid-template-columns: repeat(3,1fr); gap: 1.5rem; }

    .p-card {
      background: var(--white); border-radius: 18px; overflow: hidden;
      border: 1px solid var(--border);
      transition: transform 0.3s, box-shadow 0.3s, border-color 0.3s;
      cursor: pointer;
    }
    .p-card:hover { transform: translateY(-4px); box-shadow: 0 12px 36px rgba(0,0,0,0.07); border-color: #d4d3cc; }

    .p-thumb { height: 210px; overflow: hidden; position: relative; }
    .p-thumb img { transition: transform 0.5s; }
    .p-card:hover .p-thumb img { transform: scale(1.04); }

    .p-cat {
      position: absolute; top: 12px; left: 12px;
      font-size: 0.58rem; font-weight: 600; letter-spacing: 0.12em;
      text-transform: uppercase; padding: 0.28rem 0.78rem; border-radius: 100px;
    }
    /* neutral — white pill */
    .p-cat-neutral {
      background: rgba(255,255,255,0.9); color: var(--dark);
      border: 1px solid rgba(230,229,224,0.8);
    }
    /* accent — #fffee6 pill for Featured, Mom Life, Wellness */
    .p-cat-accent {
      background: var(--accent); color: var(--dark);
      border: 1px solid var(--accent-b);
    }

    .p-body { padding: 1.3rem 1.4rem 1.65rem; }
    .p-title {
      font-family: var(--serif); font-size: 1.06rem;
      font-weight: 400; color: var(--ink); line-height: 1.4; margin-bottom: 0.5rem;
    }
    .p-excerpt { font-size: 0.8rem; color: var(--mid); line-height: 1.75; }
    .p-meta {
      display: flex; gap: 0.5rem; font-size: 0.66rem; color: var(--muted);
      margin-top: 1rem; padding-top: 0.85rem; border-top: 1px solid var(--border);
    }
    .p-meta span::after { content: '·'; margin-left: 0.5rem; }
    .p-meta span:last-child::after { content: ''; }

    .p-card.feat { grid-column: 1 / -1; display: grid; grid-template-columns: 1.1fr 1fr; }
    .p-card.feat .p-thumb { height: 100%; min-height: 270px; }
    .p-card.feat .p-body { padding: 2.2rem 2.6rem; display: flex; flex-direction: column; justify-content: center; }
    .p-card.feat .p-title { font-size: 1.55rem; }

    /* ─── RESOURCES ─── */
    #resources { background: var(--bg); }

    .res-header { margin-bottom: 3.2rem; }

    .res-grid { display: grid; grid-template-columns: repeat(3,1fr); gap: 1.5rem; }

    .r-card {
      background: var(--white); border-radius: 20px; overflow: hidden;
      border: 1px solid var(--border);
      transition: transform 0.3s, box-shadow 0.3s, border-color 0.3s;
    }
    .r-card:hover { transform: translateY(-5px); box-shadow: 0 16px 45px rgba(0,0,0,0.07); border-color: #d4d3cc; }

    .r-img { height: 190px; overflow: hidden; position: relative; }
    .r-img img { transition: transform 0.5s; }
    .r-card:hover .r-img img { transform: scale(1.04); }

    .r-badge {
      position: absolute; top: 12px; right: 12px;
      font-size: 0.57rem; font-weight: 600; letter-spacing: 0.1em;
      text-transform: uppercase; padding: 0.28rem 0.82rem; border-radius: 100px;
    }
    /* accent yellow on sale badge */
    .rb-sale     { background: var(--accent); color: var(--dark); border: 1px solid var(--accent-b); }
    .rb-free     { background: #e6f3ec; color: #2e7a50; }
    .rb-waitlist { background: var(--bg2); color: var(--mid); border: 1px solid var(--border); }

    .r-body { padding: 1.5rem 1.65rem 1.85rem; }
    .r-icon { font-size: 1.7rem; margin-bottom: 0.7rem; }
    .r-title {
      font-family: var(--serif); font-size: 1.08rem; font-weight: 400;
      color: var(--ink); margin-bottom: 0.5rem; line-height: 1.35;
    }
    .r-desc { font-size: 0.79rem; color: var(--mid); line-height: 1.8; margin-bottom: 1.3rem; }
    .r-price { display: flex; align-items: baseline; gap: 0.5rem; margin-bottom: 1.15rem; }
    .rp-main { font-family: var(--serif); font-size: 1.45rem; font-weight: 400; color: var(--ink); }
    .rp-old  { font-size: 0.8rem; color: var(--muted); text-decoration: line-through; }
    .rp-free { font-family: var(--serif); font-size: 1.3rem; color: #2e7a50; }
    .rp-soon { font-family: var(--serif); font-size: 1.3rem; color: var(--mid); }

    .r-form { display: flex; flex-direction: column; gap: 0.55rem; }
    .r-form input {
      width: 100%; padding: 0.7rem 0.95rem;
      border-radius: 10px; border: 1px solid var(--border);
      background: var(--bg); font-family: var(--sans); font-size: 0.81rem;
      color: var(--ink); outline: none; transition: border-color 0.2s;
    }
    .r-form input:focus { border-color: #a0a096; background: var(--white); }
    .r-form input::placeholder { color: var(--muted); }

    /* ─── CONTACT ─── */
    #contact {
      background: var(--white);
      display: grid; grid-template-columns: 1fr 1fr;
      gap: 6rem; align-items: start;
    }

    .contact-info p { font-size: 0.89rem; color: var(--mid); line-height: 1.95; margin-bottom: 2rem; }

    .c-links { display: flex; flex-direction: column; gap: 0.8rem; }
    .c-link {
      display: flex; align-items: center; gap: 0.8rem;
      text-decoration: none; color: var(--mid); font-size: 0.83rem; transition: color 0.2s;
    }
    .c-link:hover { color: var(--ink); }
    .c-icon {
      width: 38px; height: 38px; border-radius: 10px;
      background: var(--bg); border: 1px solid var(--border);
      display: flex; align-items: center; justify-content: center;
      font-size: 0.9rem; flex-shrink: 0;
    }

    .contact-form { display: flex; flex-direction: column; gap: 1rem; }
    .f-row { display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; }
    .f-group { display: flex; flex-direction: column; gap: 0.4rem; }
    .f-group label {
      font-size: 0.63rem; letter-spacing: 0.16em;
      text-transform: uppercase; font-weight: 500; color: var(--muted);
    }
    .f-group input,
    .f-group textarea,
    .f-group select {
      background: var(--bg); border: 1px solid var(--border);
      border-radius: 12px; padding: 0.8rem 1rem;
      color: var(--ink); font-family: var(--sans); font-size: 0.86rem; font-weight: 300;
      outline: none; transition: border-color 0.2s; width: 100%; resize: vertical;
    }
    .f-group input:focus,
    .f-group textarea:focus,
    .f-group select:focus { border-color: #a0a096; background: var(--white); }
    .f-group textarea { min-height: 115px; }
    .f-group input::placeholder,
    .f-group textarea::placeholder { color: var(--muted); }

    /* ─── FOOTER ─── */
    footer {
      background: var(--ink);
      padding: 1.8rem 6vw;
      display: flex; justify-content: space-between;
      align-items: center; flex-wrap: wrap; gap: 1rem;
    }
    footer p { font-size: 0.72rem; color: rgba(255,255,255,0.3); }
    .footer-links { display: flex; gap: 1.6rem; }
    .footer-links a {
      color: rgba(255,255,255,0.3); text-decoration: none;
      font-size: 0.7rem; letter-spacing: 0.1em; text-transform: uppercase;
      transition: color 0.2s;
    }
    .footer-links a:hover { color: rgba(255,255,255,0.7); }

    /* ─── ANIMATIONS ─── */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(18px); }
      to   { opacity: 1; transform: none; }
    }
    @keyframes float {
      0%,100% { transform: translateY(0); }
      50%      { transform: translateY(-9px); }
    }

    .reveal { opacity: 0; transform: translateY(22px); transition: opacity 0.65s ease, transform 0.65s ease; }
    .reveal.visible { opacity: 1; transform: none; }
    .rd1 { transition-delay: 0.1s; }
    .rd2 { transition-delay: 0.2s; }

    /* ─── RESPONSIVE ─── */
    @media (max-width: 960px) {
      #hero    { grid-template-columns: 1fr; padding-top: 6.5rem; }
      .hero-right { height: 360px; }
      #about   { grid-template-columns: 1fr; gap: 3rem; }
      .blog-grid  { grid-template-columns: 1fr 1fr; }
      .p-card.feat { grid-template-columns: 1fr; }
      .p-card.feat .p-thumb { min-height: 220px; }
      .res-grid   { grid-template-columns: 1fr 1fr; }
      #contact    { grid-template-columns: 1fr; gap: 3rem; }
    }

    @media (max-width: 640px) {
      nav { padding: 1rem 5vw; }
      .nav-links { display: none; }
      .nav-links.open {
        display: flex; flex-direction: column;
        position: fixed; inset: 0;
        background: rgba(255,255,255,0.98);
        align-items: center; justify-content: center;
        gap: 2.2rem; z-index: 250;
      }
      .nav-links.open a { font-size: 1rem; color: var(--ink); }
      .nav-toggle { display: flex; z-index: 300; position: relative; }
      section { padding: 4.5rem 5vw; }
      h1.site-name { font-size: 4.8rem; }
      .hero-right { height: 300px; }
      .blog-grid  { grid-template-columns: 1fr; }
      .res-grid   { grid-template-columns: 1fr; }
      .f-row      { grid-template-columns: 1fr; }
      .about-mosaic { display: none; }
      footer { flex-direction: column; text-align: center; }
    }
  </style>
</head>
<body>

<!-- ── NAV ── -->
<nav>
  <a href="#hero" class="nav-logo">Hungry Thelma</a>
  <ul class="nav-links" id="navLinks">
    <li><a href="#about">About</a></li>
    <li><a href="#blog">Blog</a></li>
    <li><a href="#resources">Resources</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#resources" class="nav-pill">Shop Now</a></li>
  </ul>
  <button class="nav-toggle" id="navToggle" aria-label="Menu">
    <span></span><span></span><span></span>
  </button>
</nav>

<!-- ── HERO ── -->
<section id="hero">
  <div class="hero-left">
    <div class="hero-eyebrow">
      <span></span>Food · Self Care · Mom Life<span></span>
    </div>
    <h1 class="site-name">Hungry<br>Thelma</h1>
    <div class="hero-tags">
      <span class="htag">🍽 Food</span>
      <span class="htag">🌸 Self Care</span>
      <span class="htag">💛 Mom Life</span>
    </div>
    <p class="hero-tagline">Real recipes, honest moments, and a whole lot of love — from my kitchen and my heart, to yours.</p>
    <div class="hero-ctas">
      <a href="#blog" class="btn btn-dark">Read the Blog</a>
      <a href="#resources" class="btn btn-ghost">Shop Resources</a>
    </div>
  </div>

  <div class="hero-right">
    <div class="hi-main">
      <img src="https://images.unsplash.com/photo-1565299543923-37dd37887442?w=800&q=80" alt="Parfait dessert"/>
    </div>
    <div class="hi-sm1">
      <img src="https://images.unsplash.com/photo-1490645935967-10de6ba17061?w=600&q=80" alt="Meal prep"/>
    </div>
    <div class="hi-sm2">
      <img src="https://images.unsplash.com/photo-1511690743698-d9d85f2fbf38?w=400&q=80" alt="Breakfast bowl"/>
    </div>
    <div class="hero-float">
      <span class="hero-float-icon">🍓</span>
      <div class="hero-float-text">
        Parfait Masterclass
        <small>Waitlist open now</small>
      </div>
    </div>
  </div>
</section>

<!-- ── ABOUT ── -->
<section id="about">
  <div class="about-mosaic reveal">
    <div class="ab-photo">
      <img src="https://images.unsplash.com/photo-1556909114-f6e7ad7d3136?w=600&q=80" alt="Cooking at home"/>
    </div>
    <div class="ab-photo">
      <img src="https://images.unsplash.com/photo-1484723091739-30a097e8f929?w=500&q=80" alt="Breakfast flatlay"/>
    </div>
    <div class="ab-photo">
      <img src="https://images.unsplash.com/photo-1467453678174-768ec283a940?w=500&q=80" alt="Morning routine"/>
    </div>
  </div>

  <div class="about-text reveal rd1">
    <p class="sec-eyebrow">About Me</p>
    <h2 class="sec-title">Hi, I'm <em>Thelma</em></h2>
    <div class="rule"></div>

    <p>I'm a mum, a home cook, and a digital creator who found her voice in the kitchen — and decided to share it. What started as feeding my family became something much bigger: a space where real women come for honest recipes, gentle reminders to take care of themselves, and a little warmth on the hard days.</p>
    <p>Here at Hungry Thelma, food is never just food. It's how I show love, how I unwind, and how I make ordinary days feel a little more special. I create nourishing, accessible recipes that don't require fancy ingredients or hours of your time — because most days, neither do I.</p>
    <p>Beyond the kitchen, I talk about the things every mum quietly carries: the guilt, the joy, the self care we keep putting off, and the small rituals that bring us back to ourselves. This is a judgment-free table, and there is always room for you.</p>

    <div class="about-chips">
      <span class="chip">🌻 Home Cook</span>
      <span class="chip">🥗 Meal Prep Lover</span>
      <span class="chip">💛 Mama First</span>
      <span class="chip">✨ Parfait Queen</span>
      <span class="chip">🌿 Wellness Creator</span>
      <span class="chip">🌸 Self Care Advocate</span>
    </div>

    <a href="#contact" class="btn btn-dark">Say Hello</a>
  </div>
</section>

<!-- ── BLOG ── -->
<section id="blog">
  <div class="blog-top reveal">
    <div>
      <p class="sec-eyebrow">From the Blog</p>
      <h2 class="sec-title">Stories & <em>Recipes</em></h2>
    </div>
    <a href="#" class="btn btn-ghost">View All →</a>
  </div>

  <div class="blog-grid">

    <article class="p-card feat reveal">
      <div class="p-thumb">
        <img src="https://images.unsplash.com/photo-1488477181946-6428a0291777?w=900&q=80" alt="Parfait"/>
        <span class="p-cat p-cat-accent">⭐ Featured</span>
      </div>
      <div class="p-body">
        <h3 class="p-title">The Only Parfait Recipe You'll Ever Need — Layers of Joy in a Glass</h3>
        <p class="p-excerpt">Creamy yoghurt, fresh berries, crunchy granola, and a drizzle of honey. Ten minutes, total luxury. My kids request this every single morning and I am not complaining.</p>
        <div class="p-meta">
          <span>March 2025</span>
          <span>6 min read</span>
          <span>Recipe + Video</span>
        </div>
      </div>
    </article>

    <article class="p-card reveal">
      <div class="p-thumb">
        <img src="https://images.unsplash.com/photo-1512621776951-a57141f2eefd?w=600&q=80" alt="Salad bowl"/>
        <span class="p-cat p-cat-neutral">🥗 Food</span>
      </div>
      <div class="p-body">
        <h3 class="p-title">My 5-Day Meal Prep Routine That Saves My Sanity</h3>
        <p class="p-excerpt">Sunday prep sessions that make the whole week feel manageable — bowls, sauces, snacks ready to go.</p>
        <div class="p-meta"><span>Feb 2025</span><span>8 min read</span></div>
      </div>
    </article>

    <article class="p-card reveal rd1">
      <div class="p-thumb">
        <img src="https://images.unsplash.com/photo-1515003197210-e0cd71810b5f?w=600&q=80" alt="Morning routine"/>
        <span class="p-cat p-cat-neutral">🌸 Self Care</span>
      </div>
      <div class="p-body">
        <h3 class="p-title">5 AM Mornings Changed My Life — My Actual Routine</h3>
        <p class="p-excerpt">Not a Pinterest morning — a real one. Tea, journaling, gentle movement, and quiet before the chaos begins.</p>
        <div class="p-meta"><span>Feb 2025</span><span>5 min read</span></div>
      </div>
    </article>

    <article class="p-card reveal rd2">
      <div class="p-thumb">
        <img src="https://images.unsplash.com/photo-1464349095431-e9a21285b5f3?w=600&q=80" alt="Birthday cake"/>
        <span class="p-cat p-cat-neutral">🎂 Baking</span>
      </div>
      <div class="p-body">
        <h3 class="p-title">My Daughter's Birthday Cake Request Every Single Year</h3>
        <p class="p-excerpt">Soft vanilla layers, pastel buttercream, and enough sprinkles to make any child weep happy tears.</p>
        <div class="p-meta"><span>Jan 2025</span><span>6 min read</span></div>
      </div>
    </article>

    <article class="p-card reveal">
      <div class="p-thumb">
        <img src="https://images.unsplash.com/photo-1540189549336-e6e99c3679fe?w=600&q=80" alt="Nourish bowl"/>
        <span class="p-cat p-cat-accent">💛 Mom Life</span>
      </div>
      <div class="p-body">
        <h3 class="p-title">The Night I Burned Dinner and What It Taught Me About Grace</h3>
        <p class="p-excerpt">Sometimes the kitchen wins. A story about laughing instead of crying, and ordering pizza without guilt.</p>
        <div class="p-meta"><span>Dec 2024</span><span>4 min read</span></div>
      </div>
    </article>

    <article class="p-card reveal rd1">
      <div class="p-thumb">
        <img src="https://images.unsplash.com/photo-1461023058943-07fcbe16d735?w=600&q=80" alt="Coffee morning"/>
        <span class="p-cat p-cat-accent">🌿 Wellness</span>
      </div>
      <div class="p-body">
        <h3 class="p-title">How I Started Eating Better Without Giving Up Joy</h3>
        <p class="p-excerpt">No restriction. No guilt. Small, delicious swaps that made our whole family feel genuinely nourished.</p>
        <div class="p-meta"><span>Nov 2024</span><span>7 min read</span></div>
      </div>
    </article>

  </div>
</section>

<!-- ── RESOURCES ── -->
<section id="resources">
  <div class="res-header reveal">
    <p class="sec-eyebrow">Resources</p>
    <h2 class="sec-title">Plans, Guides & <em>Freebies</em></h2>
    <p class="sec-sub">Everything I've put together to help you eat well, feel good, and enjoy the process.</p>
  </div>

  <div class="res-grid">

    <div class="r-card reveal">
      <div class="r-img">
        <img src="https://images.unsplash.com/photo-1547592180-85f173990554?w=700&q=80" alt="Meal plan"/>
        <span class="r-badge rb-sale">On Sale</span>
      </div>
      <div class="r-body">
        <div class="r-icon">📋</div>
        <h3 class="r-title">4-Week Nourish Meal Plan</h3>
        <p class="r-desc">28 days of balanced, family-friendly meals — with a full shopping list, prep guide, and my personal notes. Instant digital download.</p>
        <div class="r-price">
          <span class="rp-main">₦4,500</span>
          <span class="rp-old">₦7,000</span>
        </div>
        <a href="#" class="btn btn-dark" style="display:block;" onclick="return handlePurchase(event)">Buy Now — Instant Download</a>
      </div>
    </div>

    <div class="r-card reveal rd1">
      <div class="r-img">
        <img src="https://images.unsplash.com/photo-1565958011703-44f9829ba187?w=700&q=80" alt="Free recipes"/>
        <span class="r-badge rb-free">Free Download</span>
      </div>
      <div class="r-body">
        <div class="r-icon">📥</div>
        <h3 class="r-title">7 Quick Recipes — Free PDF</h3>
        <p class="r-desc">Seven of my most-loved weeknight recipes, all under 30 minutes. Drop your email and I'll send it straight to your inbox.</p>
        <div class="r-price"><span class="rp-free">Free</span></div>
        <form class="r-form" onsubmit="handleFreebie(event)">
          <input type="email" placeholder="Your email address…" required/>
          <button type="submit" class="btn btn-ghost" style="width:100%;">Send It to Me →</button>
        </form>
      </div>
    </div>

    <div class="r-card reveal rd2">
      <div class="r-img">
        <img src="https://images.unsplash.com/photo-1488477181946-6428a0291777?w=700&q=80" alt="Parfait masterclass"/>
        <span class="r-badge rb-waitlist">Waitlist Open</span>
      </div>
      <div class="r-body">
        <div class="r-icon">🍓</div>
        <h3 class="r-title">Parfait Masterclass — Join the Waitlist</h3>
        <p class="r-desc">My first online class — all about parfaits! Beautiful layering, flavour combos, and presentation tips. Be first to know when it launches.</p>
        <div class="r-price"><span class="rp-soon">Coming Soon</span></div>
        <form class="r-form" onsubmit="handleWaitlist(event)">
          <input type="text" placeholder="Your name…" required/>
          <input type="email" placeholder="Your email…" required/>
          <button type="submit" class="btn btn-outline" style="width:100%;">Join the Waitlist →</button>
        </form>
      </div>
    </div>

  </div>
</section>

<!-- ── CONTACT ── -->
<section id="contact">
  <div class="contact-info reveal">
    <p class="sec-eyebrow">Get in Touch</p>
    <h2 class="sec-title">Let's <em>Connect</em></h2>
    <div class="rule"></div>
    <p>Whether it's a collaboration, a recipe question, or just wanting to say hello — my inbox is always open. I read every message personally and love hearing from you.</p>

    <div class="c-links">
      <a href="mailto:hungryythelma@gmail.com" class="c-link">
        <span class="c-icon">✉️</span>hungryythelma@gmail.com
      </a>
      <a href="https://www.instagram.com/thehungrythelma/" target="_blank" class="c-link">
        <span class="c-icon">📸</span>@thehungrythelma · Instagram
      </a>
      <a href="https://www.tiktok.com/@hungrythelma" target="_blank" class="c-link">
        <span class="c-icon">🎵</span>@hungrythelma · TikTok
      </a>
      <a href="https://www.youtube.com/@Hungrythelma" target="_blank" class="c-link">
        <span class="c-icon">▶️</span>Hungry Thelma · YouTube
      </a>
    </div>
  </div>

  <div class="reveal rd1">
    <form class="contact-form" onsubmit="handleContact(event)">
      <div class="f-row">
        <div class="f-group">
          <label for="cname">Name</label>
          <input type="text" id="cname" placeholder="Your name" required>
        </div>
        <div class="f-group">
          <label for="cemail">Email</label>
          <input type="email" id="cemail" placeholder="you@email.com" required>
        </div>
      </div>
      <div class="f-group">
        <label for="ctopic">Topic</label>
        <select id="ctopic">
          <option value="">What's this about?</option>
          <option>Brand collaboration</option>
          <option>Recipe question</option>
          <option>Parfait Masterclass</option>
          <option>Meal plan support</option>
          <option>Just saying hi 👋</option>
        </select>
      </div>
      <div class="f-group">
        <label for="cmsg">Message</label>
        <textarea id="cmsg" placeholder="Tell me everything…" required></textarea>
      </div>
      <button type="submit" class="btn btn-dark" id="contactBtn" style="align-self:flex-start;">Send Message</button>
    </form>
  </div>
</section>

<!-- ── FOOTER ── -->
<footer>
  <p>© 2025 Hungry Thelma · All rights reserved</p>
  <div class="footer-links">
    <a href="#about">About</a>
    <a href="#blog">Blog</a>
    <a href="#resources">Resources</a>
    <a href="#contact">Contact</a>
  </div>
</footer>

<script>
  const toggle = document.getElementById('navToggle');
  const links  = document.getElementById('navLinks');
  toggle.addEventListener('click', () => links.classList.toggle('open'));
  links.querySelectorAll('a').forEach(a => a.addEventListener('click', () => links.classList.remove('open')));

  const obs = new IntersectionObserver(entries => {
    entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('visible'); obs.unobserve(e.target); } });
  }, { threshold: 0.08 });
  document.querySelectorAll('.reveal').forEach(el => obs.observe(el));

  function feedback(btn, msg) {
    const orig = btn.textContent;
    btn.textContent = msg; btn.disabled = true;
    setTimeout(() => { btn.textContent = orig; btn.disabled = false; }, 3000);
  }
  function handleFreebie(e)  { e.preventDefault(); feedback(e.target.querySelector('button'), '✓ Check your inbox!'); e.target.reset(); }
  function handleWaitlist(e) { e.preventDefault(); feedback(e.target.querySelector('button'), "✓ You're on the list!"); e.target.reset(); }
  function handleContact(e)  { e.preventDefault(); feedback(document.getElementById('contactBtn'), '✓ Message sent!'); e.target.reset(); }
  function handlePurchase(e) { e.preventDefault(); alert('Link this to your payment page — Paystack, Selar, or Gumroad.'); }
</script>

</body>
</html>
