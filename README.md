<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Bucket Things — Everything You Need</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&display=swap" rel="stylesheet">
<style>
  :root {
    --black: #080c0f;
    --black-2: #0e1419;
    --black-3: #161d24;
    --green: #1aff7a;
    --green-dim: #0fd660;
    --green-dark: #083d1a;
    --blue: #1a8fff;
    --blue-dim: #0d6fd6;
    --blue-dark: #041a3d;
    --white: #f0f4f8;
    --muted: #6b7f8f;
    --border: rgba(26,255,122,0.12);
    --glow-green: 0 0 40px rgba(26,255,122,0.18);
    --glow-blue: 0 0 40px rgba(26,143,255,0.18);
  }

  *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--black);
    color: var(--white);
    font-family: 'DM Sans', sans-serif;
    overflow-x: hidden;
    cursor: none;
  }

  /* ── CUSTOM CURSOR ── */
  .cursor {
    width: 10px; height: 10px;
    background: var(--green);
    border-radius: 50%;
    position: fixed; top: 0; left: 0;
    pointer-events: none; z-index: 9999;
    transform: translate(-50%, -50%);
    transition: transform .1s, width .25s, height .25s, background .25s;
  }
  .cursor-ring {
    width: 36px; height: 36px;
    border: 1.5px solid var(--green);
    border-radius: 50%;
    position: fixed; top: 0; left: 0;
    pointer-events: none; z-index: 9998;
    transform: translate(-50%, -50%);
    transition: transform .18s ease, width .25s, height .25s, border-color .25s;
    opacity: .6;
  }
  body:hover .cursor { opacity: 1; }

  /* ── NOISE OVERLAY ── */
  body::before {
    content: '';
    position: fixed; inset: 0; z-index: 1; pointer-events: none;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E");
    opacity: .4;
  }

  /* ── NAV ── */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 1.2rem 4rem;
    background: rgba(8,12,15,0.72);
    backdrop-filter: blur(20px);
    border-bottom: 1px solid var(--border);
    animation: fadeDown .8s ease both;
  }

  .logo {
    display: flex; align-items: center; gap: .75rem;
    text-decoration: none;
  }

  /* SVG Logo */
  .logo-icon {
    width: 44px; height: 44px;
    flex-shrink: 0;
  }

  .logo-text {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: 1.25rem;
    letter-spacing: -.02em;
    color: var(--white);
  }
  .logo-text span { color: var(--green); }

  .nav-links {
    display: flex; gap: 2.5rem; list-style: none;
  }
  .nav-links a {
    font-size: .875rem; font-weight: 400; letter-spacing: .04em;
    color: var(--muted); text-decoration: none;
    transition: color .25s;
    position: relative;
  }
  .nav-links a::after {
    content: ''; position: absolute; bottom: -4px; left: 0;
    width: 0; height: 1.5px; background: var(--green);
    transition: width .3s ease;
  }
  .nav-links a:hover { color: var(--white); }
  .nav-links a:hover::after { width: 100%; }

  .nav-cta {
    padding: .55rem 1.4rem;
    background: var(--green); color: var(--black);
    font-family: 'Syne', sans-serif; font-weight: 700;
    font-size: .82rem; letter-spacing: .06em; text-transform: uppercase;
    border: none; border-radius: 4px; cursor: none;
    transition: background .25s, transform .2s, box-shadow .25s;
  }
  .nav-cta:hover {
    background: var(--green-dim);
    transform: translateY(-1px);
    box-shadow: 0 8px 24px rgba(26,255,122,.28);
  }

  /* ── HERO ── */
  .hero {
    min-height: 100vh;
    display: flex; flex-direction: column;
    align-items: center; justify-content: center;
    padding: 8rem 4rem 4rem;
    position: relative; overflow: hidden;
    text-align: center;
  }

  /* Radial glow backgrounds */
  .hero::after {
    content: '';
    position: absolute;
    width: 700px; height: 700px;
    background: radial-gradient(circle, rgba(26,143,255,.1) 0%, transparent 70%);
    top: -100px; right: -150px; pointer-events: none;
    animation: pulse 6s ease-in-out infinite;
  }
  .glow-left {
    position: absolute;
    width: 500px; height: 500px;
    background: radial-gradient(circle, rgba(26,255,122,.08) 0%, transparent 70%);
    bottom: 0; left: -100px; pointer-events: none;
    animation: pulse 8s ease-in-out infinite reverse;
  }

  .hero-badge {
    display: inline-flex; align-items: center; gap: .5rem;
    background: rgba(26,255,122,.07);
    border: 1px solid rgba(26,255,122,.2);
    border-radius: 100px; padding: .35rem 1rem;
    font-size: .78rem; letter-spacing: .08em; text-transform: uppercase;
    color: var(--green); margin-bottom: 2rem;
    animation: fadeUp .8s .2s ease both;
  }
  .hero-badge::before {
    content: ''; width: 6px; height: 6px; border-radius: 50%;
    background: var(--green);
    animation: blink 2s infinite;
  }

  .hero h1 {
    font-family: 'Syne', sans-serif;
    font-size: clamp(3rem, 7vw, 6.5rem);
    font-weight: 800; line-height: .95;
    letter-spacing: -.04em;
    margin-bottom: 1.5rem;
    animation: fadeUp .8s .35s ease both;
  }
  .hero h1 em { font-style: normal; color: var(--green); }
  .hero h1 .blue-word { color: var(--blue); }

  .hero-sub {
    max-width: 520px;
    font-size: 1.05rem; font-weight: 300; line-height: 1.7;
    color: var(--muted); margin: 0 auto 2.5rem;
    animation: fadeUp .8s .5s ease both;
  }

  .hero-actions {
    display: flex; gap: 1rem; justify-content: center; flex-wrap: wrap;
    animation: fadeUp .8s .65s ease both;
    margin-bottom: 4rem;
  }

  .btn-primary {
    padding: .85rem 2.2rem;
    background: var(--green); color: var(--black);
    font-family: 'Syne', sans-serif; font-weight: 700;
    font-size: .9rem; letter-spacing: .04em;
    border: none; border-radius: 6px; cursor: none;
    transition: all .25s;
    display: flex; align-items: center; gap: .5rem;
  }
  .btn-primary:hover {
    background: var(--green-dim);
    transform: translateY(-2px);
    box-shadow: 0 16px 40px rgba(26,255,122,.3);
  }

  .btn-secondary {
    padding: .85rem 2.2rem;
    background: transparent; color: var(--white);
    font-family: 'Syne', sans-serif; font-weight: 600;
    font-size: .9rem; letter-spacing: .04em;
    border: 1px solid rgba(255,255,255,.15); border-radius: 6px; cursor: none;
    transition: all .25s;
  }
  .btn-secondary:hover {
    border-color: var(--blue);
    color: var(--blue);
    box-shadow: 0 0 20px rgba(26,143,255,.15);
  }

  /* Hero Stats */
  .hero-stats {
    display: flex; gap: 3rem; justify-content: center;
    animation: fadeUp .8s .8s ease both;
  }
  .stat { text-align: center; }
  .stat-num {
    font-family: 'Syne', sans-serif; font-weight: 800;
    font-size: 2rem; letter-spacing: -.04em;
    background: linear-gradient(135deg, var(--green), var(--blue));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
  }
  .stat-label { font-size: .78rem; color: var(--muted); letter-spacing: .06em; text-transform: uppercase; margin-top: .25rem; }

  /* Scroll indicator */
  .scroll-hint {
    position: absolute; bottom: 2.5rem; left: 50%; transform: translateX(-50%);
    display: flex; flex-direction: column; align-items: center; gap: .5rem;
    color: var(--muted); font-size: .72rem; letter-spacing: .1em; text-transform: uppercase;
    animation: fadeUp .8s 1s ease both;
  }
  .scroll-line {
    width: 1px; height: 48px;
    background: linear-gradient(to bottom, var(--green), transparent);
    animation: scrollLine 2s ease-in-out infinite;
  }

  /* ── MARQUEE ── */
  .marquee-wrap {
    overflow: hidden;
    border-top: 1px solid var(--border);
    border-bottom: 1px solid var(--border);
    padding: 1rem 0;
    background: var(--black-2);
  }
  .marquee-track {
    display: flex; width: max-content;
    animation: marquee 25s linear infinite;
    gap: 0;
  }
  .marquee-item {
    display: flex; align-items: center; gap: .75rem;
    padding: 0 2.5rem;
    font-family: 'Syne', sans-serif; font-size: .82rem;
    font-weight: 600; letter-spacing: .1em; text-transform: uppercase;
    color: var(--muted); white-space: nowrap;
  }
  .marquee-dot { width: 4px; height: 4px; border-radius: 50%; background: var(--green); }

  /* ── CATEGORIES ── */
  .section { padding: 6rem 4rem; position: relative; }
  .section-label {
    font-size: .75rem; letter-spacing: .16em; text-transform: uppercase;
    color: var(--green); margin-bottom: 1rem;
    display: flex; align-items: center; gap: .75rem;
  }
  .section-label::before {
    content: ''; width: 24px; height: 1px; background: var(--green);
  }
  .section-title {
    font-family: 'Syne', sans-serif; font-weight: 800;
    font-size: clamp(2rem, 4vw, 3.2rem); letter-spacing: -.03em;
    line-height: 1.1; margin-bottom: .75rem;
  }
  .section-sub {
    color: var(--muted); font-size: 1rem; font-weight: 300;
    max-width: 460px; line-height: 1.65; margin-bottom: 3.5rem;
  }

  .categories-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1.25rem;
  }

  .cat-card {
    background: var(--black-2);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 2rem;
    cursor: none;
    position: relative; overflow: hidden;
    transition: transform .35s cubic-bezier(.34,1.56,.64,1), border-color .3s, box-shadow .3s;
    group: true;
  }
  .cat-card::before {
    content: ''; position: absolute; inset: 0; border-radius: 16px;
    background: var(--cat-gradient);
    opacity: 0; transition: opacity .35s;
    z-index: 0;
  }
  .cat-card:hover { transform: translateY(-6px); }
  .cat-card:hover::before { opacity: 1; }
  .cat-card:hover { border-color: transparent; box-shadow: 0 20px 60px rgba(0,0,0,.4); }

  .cat-card--green { --cat-gradient: linear-gradient(135deg, rgba(26,255,122,.08), rgba(26,255,122,.02)); }
  .cat-card--green:hover { border-color: rgba(26,255,122,.25); box-shadow: 0 20px 60px rgba(26,255,122,.1); }
  .cat-card--blue { --cat-gradient: linear-gradient(135deg, rgba(26,143,255,.08), rgba(26,143,255,.02)); }
  .cat-card--blue:hover { border-color: rgba(26,143,255,.25); box-shadow: 0 20px 60px rgba(26,143,255,.1); }

  .cat-card > * { position: relative; z-index: 1; }

  .cat-emoji {
    font-size: 2.8rem; margin-bottom: 1.25rem;
    display: block;
    transition: transform .3s cubic-bezier(.34,1.56,.64,1);
  }
  .cat-card:hover .cat-emoji { transform: scale(1.15) rotate(-5deg); }

  .cat-name {
    font-family: 'Syne', sans-serif; font-weight: 700;
    font-size: 1.15rem; letter-spacing: -.01em;
    margin-bottom: .4rem;
  }
  .cat-desc { font-size: .85rem; color: var(--muted); line-height: 1.5; margin-bottom: 1.25rem; }

  .cat-link {
    display: inline-flex; align-items: center; gap: .4rem;
    font-size: .8rem; font-weight: 600; letter-spacing: .06em; text-transform: uppercase;
    color: var(--green); text-decoration: none;
    transition: gap .25s;
  }
  .cat-card--blue .cat-link { color: var(--blue); }
  .cat-link:hover { gap: .7rem; }

  .cat-count {
    position: absolute; top: 1.5rem; right: 1.5rem;
    font-size: .7rem; color: var(--muted); letter-spacing: .08em;
    z-index: 1;
  }

  /* ── FEATURED PRODUCTS ── */
  .products-section { background: var(--black-2); }

  .products-row {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 1rem;
  }

  .prod-card {
    background: var(--black-3);
    border: 1px solid rgba(255,255,255,.05);
    border-radius: 14px; overflow: hidden;
    cursor: none;
    transition: transform .3s cubic-bezier(.34,1.56,.64,1), border-color .3s, box-shadow .3s;
  }
  .prod-card:hover {
    transform: translateY(-5px);
    border-color: rgba(26,255,122,.2);
    box-shadow: 0 16px 48px rgba(26,255,122,.08);
  }

  .prod-img {
    width: 100%; height: 160px;
    display: flex; align-items: center; justify-content: center;
    font-size: 3.5rem;
    background: linear-gradient(135deg, rgba(26,255,122,.04), rgba(26,143,255,.04));
    border-bottom: 1px solid rgba(255,255,255,.04);
    transition: background .3s;
  }
  .prod-card:hover .prod-img {
    background: linear-gradient(135deg, rgba(26,255,122,.08), rgba(26,143,255,.08));
  }

  .prod-info { padding: 1.1rem; }
  .prod-tag {
    font-size: .68rem; letter-spacing: .1em; text-transform: uppercase;
    color: var(--blue); margin-bottom: .4rem;
  }
  .prod-name {
    font-family: 'Syne', sans-serif; font-weight: 700;
    font-size: 1rem; margin-bottom: .3rem;
  }
  .prod-price {
    font-size: .92rem; color: var(--green); font-weight: 500;
  }
  .prod-add {
    margin-top: .85rem; width: 100%;
    padding: .5rem;
    background: rgba(26,255,122,.08);
    border: 1px solid rgba(26,255,122,.15);
    border-radius: 6px;
    color: var(--green);
    font-family: 'Syne', sans-serif; font-weight: 600;
    font-size: .78rem; letter-spacing: .06em; text-transform: uppercase;
    cursor: none; transition: all .25s;
  }
  .prod-add:hover {
    background: var(--green); color: var(--black);
    box-shadow: 0 8px 20px rgba(26,255,122,.3);
  }

  /* ── WHY US ── */
  .features-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 1.5rem;
  }
  .feat {
    padding: 2rem;
    border: 1px solid var(--border);
    border-radius: 14px;
    background: var(--black-2);
    transition: transform .3s, border-color .3s;
  }
  .feat:hover {
    transform: translateY(-4px);
    border-color: rgba(26,143,255,.3);
  }
  .feat-icon {
    font-size: 2rem; margin-bottom: 1rem;
  }
  .feat-title {
    font-family: 'Syne', sans-serif; font-weight: 700;
    font-size: 1rem; margin-bottom: .5rem;
  }
  .feat-desc { font-size: .85rem; color: var(--muted); line-height: 1.6; }

  /* ── CTA BANNER ── */
  .cta-banner {
    margin: 0 4rem;
    border-radius: 20px; overflow: hidden;
    background: linear-gradient(135deg, var(--green-dark) 0%, var(--blue-dark) 50%, var(--black-3) 100%);
    border: 1px solid rgba(26,255,122,.15);
    padding: 4rem;
    display: flex; align-items: center; justify-content: space-between;
    gap: 2rem;
    position: relative; overflow: hidden;
  }
  .cta-banner::before {
    content: '';
    position: absolute; top: -80px; right: -80px;
    width: 300px; height: 300px;
    background: radial-gradient(circle, rgba(26,255,122,.15) 0%, transparent 65%);
    pointer-events: none;
  }
  .cta-title {
    font-family: 'Syne', sans-serif; font-weight: 800;
    font-size: clamp(1.8rem, 3vw, 2.8rem); letter-spacing: -.03em;
    line-height: 1.15; max-width: 500px;
  }
  .cta-title em { font-style: normal; color: var(--green); }
  .cta-sub { color: var(--muted); font-weight: 300; margin-top: .75rem; font-size: .95rem; }

  .cta-form {
    display: flex; gap: .75rem; flex-shrink: 0;
  }
  .cta-input {
    background: rgba(255,255,255,.06);
    border: 1px solid rgba(255,255,255,.12);
    border-radius: 6px; padding: .8rem 1.2rem;
    color: var(--white); font-family: 'DM Sans', sans-serif;
    font-size: .9rem; outline: none; width: 240px;
    transition: border-color .25s;
  }
  .cta-input:focus { border-color: var(--green); }
  .cta-input::placeholder { color: var(--muted); }

  /* ── FOOTER ── */
  footer {
    margin-top: 5rem;
    padding: 3rem 4rem;
    border-top: 1px solid var(--border);
    display: flex; align-items: center; justify-content: space-between;
  }
  .footer-copy { font-size: .8rem; color: var(--muted); }
  .footer-copy span { color: var(--green); }
  .footer-links { display: flex; gap: 2rem; }
  .footer-links a {
    font-size: .8rem; color: var(--muted); text-decoration: none;
    transition: color .2s;
  }
  .footer-links a:hover { color: var(--white); }

  /* ── ANIMATIONS ── */
  @keyframes fadeDown {
    from { opacity: 0; transform: translateY(-20px); }
    to { opacity: 1; transform: translateY(0); }
  }
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to { opacity: 1; transform: translateY(0); }
  }
  @keyframes pulse {
    0%, 100% { opacity: 1; transform: scale(1); }
    50% { opacity: .7; transform: scale(1.05); }
  }
  @keyframes blink {
    0%, 100% { opacity: 1; }
    50% { opacity: .3; }
  }
  @keyframes marquee {
    from { transform: translateX(0); }
    to { transform: translateX(-50%); }
  }
  @keyframes scrollLine {
    0% { transform: scaleY(0) translateY(-100%); opacity: 1; }
    100% { transform: scaleY(1) translateY(0); opacity: 0; }
  }

  /* Scroll reveal */
  .reveal {
    opacity: 0; transform: translateY(28px);
    transition: opacity .65s ease, transform .65s ease;
  }
  .reveal.visible { opacity: 1; transform: translateY(0); }

  /* Stagger children */
  .stagger > *:nth-child(1) { transition-delay: .05s; }
  .stagger > *:nth-child(2) { transition-delay: .12s; }
  .stagger > *:nth-child(3) { transition-delay: .19s; }
  .stagger > *:nth-child(4) { transition-delay: .26s; }
  .stagger > *:nth-child(5) { transition-delay: .33s; }
  .stagger > *:nth-child(6) { transition-delay: .4s; }
</style>
</head>
<body>

<!-- Cursor -->
<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- ── NAV ── -->
<nav>
  <a href="#" class="logo">
    <!-- Bucket Things SVG Logo -->
    <svg class="logo-icon" viewBox="0 0 44 44" fill="none" xmlns="http://www.w3.org/2000/svg">
      <defs>
        <linearGradient id="bucketGrad" x1="0" y1="0" x2="44" y2="44" gradientUnits="userSpaceOnUse">
          <stop offset="0%" stop-color="#1aff7a"/>
          <stop offset="100%" stop-color="#1a8fff"/>
        </linearGradient>
      </defs>
      <!-- Bucket body -->
      <path d="M10 18 L13 36 H31 L34 18 Z" stroke="url(#bucketGrad)" stroke-width="2" stroke-linejoin="round" fill="rgba(26,255,122,0.07)"/>
      <!-- Bucket top rim -->
      <rect x="8" y="14" width="28" height="5" rx="2.5" stroke="url(#bucketGrad)" stroke-width="2" fill="rgba(26,143,255,0.1)"/>
      <!-- Handle -->
      <path d="M16 14 C16 8 28 8 28 14" stroke="#1a8fff" stroke-width="2" stroke-linecap="round" fill="none"/>
      <!-- Little sparkle top -->
      <circle cx="22" cy="9" r="1.5" fill="#1aff7a" opacity="0.8"/>
      <!-- Dots pattern inside bucket -->
      <circle cx="18" cy="26" r="1.2" fill="url(#bucketGrad)" opacity="0.6"/>
      <circle cx="22" cy="29" r="1.2" fill="url(#bucketGrad)" opacity="0.6"/>
      <circle cx="26" cy="26" r="1.2" fill="url(#bucketGrad)" opacity="0.6"/>
    </svg>
    <span class="logo-text">Bucket <span>Things</span></span>
  </a>

  <ul class="nav-links">
    <li><a href="#categories">Categories</a></li>
    <li><a href="#products">Products</a></li>
    <li><a href="#features">Why Us</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>

  <button class="nav-cta">Shop Now →</button>
</nav>

<!-- ── HERO ── -->
<section class="hero">
  <div class="glow-left"></div>

  <div class="hero-badge">🟢 Now Delivering in Your City</div>

  <h1>
    One <em>Bucket</em><br>
    <span class="blue-word">Everything</span> Inside
  </h1>

  <p class="hero-sub">
    Fresh fruits & veggies, your favourite snacks, chips & biscuits — plus daily home essentials and electronics. All in one place, at your door.
  </p>

  <div class="hero-actions">
    <button class="btn-primary">🛒 Start Shopping</button>
    <button class="btn-secondary">Browse Categories</button>
  </div>

  <div class="hero-stats">
    <div class="stat">
      <div class="stat-num">2,400+</div>
      <div class="stat-label">Products</div>
    </div>
    <div class="stat">
      <div class="stat-num">98%</div>
      <div class="stat-label">Satisfaction</div>
    </div>
    <div class="stat">
      <div class="stat-num">30 min</div>
      <div class="stat-label">Delivery</div>
    </div>
  </div>

  <div class="scroll-hint">
    <div class="scroll-line"></div>
    Scroll
  </div>
</section>

<!-- ── MARQUEE ── -->
<div class="marquee-wrap">
  <div class="marquee-track">
    <!-- Duplicated for seamless loop -->
    <div class="marquee-item"><span class="marquee-dot"></span>Fresh Fruits</div>
    <div class="marquee-item"><span class="marquee-dot"></span>Vegetables</div>
    <div class="marquee-item"><span class="marquee-dot"></span>Snacks & Chips</div>
    <div class="marquee-item"><span class="marquee-dot"></span>Biscuits & Cookies</div>
    <div class="marquee-item"><span class="marquee-dot"></span>Electronics</div>
    <div class="marquee-item"><span class="marquee-dot"></span>Kitchen Utensils</div>
    <div class="marquee-item"><span class="marquee-dot"></span>Daily Essentials</div>
    <div class="marquee-item"><span class="marquee-dot"></span>30 Min Delivery</div>
    <div class="marquee-item"><span class="marquee-dot"></span>Fresh Fruits</div>
    <div class="marquee-item"><span class="marquee-dot"></span>Vegetables</div>
    <div class="marquee-item"><span class="marquee-dot"></span>Snacks & Chips</div>
    <div class="marquee-item"><span class="marquee-dot"></span>Biscuits & Cookies</div>
    <div class="marquee-item"><span class="marquee-dot"></span>Electronics</div>
    <div class="marquee-item"><span class="marquee-dot"></span>Kitchen Utensils</div>
    <div class="marquee-item"><span class="marquee-dot"></span>Daily Essentials</div>
    <div class="marquee-item"><span class="marquee-dot"></span>30 Min Delivery</div>
  </div>
</div>

<!-- ── CATEGORIES ── -->
<section class="section" id="categories">
  <div class="section-label reveal">Our Categories</div>
  <h2 class="section-title reveal">Everything in<br>One Bucket</h2>
  <p class="section-sub reveal">Six perfectly curated shelves — one seamless checkout.</p>

  <div class="categories-grid stagger">
    <div class="cat-card cat-card--green reveal">
      <span class="cat-count">142 items</span>
      <span class="cat-emoji">🍎</span>
      <div class="cat-name">Fresh Fruits</div>
      <div class="cat-desc">Mangoes, apples, bananas, berries & seasonal picks — sourced daily.</div>
      <a href="#" class="cat-link">Explore →</a>
    </div>
    <div class="cat-card cat-card--green reveal">
      <span class="cat-count">218 items</span>
      <span class="cat-emoji">🥦</span>
      <div class="cat-name">Vegetables</div>
      <div class="cat-desc">Farm-fresh greens, roots & herbs. Direct from local gardens.</div>
      <a href="#" class="cat-link">Explore →</a>
    </div>
    <div class="cat-card cat-card--blue reveal">
      <span class="cat-count">380 items</span>
      <span class="cat-emoji">🍟</span>
      <div class="cat-name">Snacks & Chips</div>
      <div class="cat-desc">Lays, Pringles, popcorn, nachos & flavoured crackers for every craving.</div>
      <a href="#" class="cat-link">Explore →</a>
    </div>
    <div class="cat-card cat-card--blue reveal">
      <span class="cat-count">260 items</span>
      <span class="cat-emoji">🍪</span>
      <div class="cat-name">Biscuits & Cookies</div>
      <div class="cat-desc">Oreos, Digestives, Bonn, Marie, and imported premium biscuits.</div>
      <a href="#" class="cat-link">Explore →</a>
    </div>
    <div class="cat-card cat-card--green reveal">
      <span class="cat-count">540 items</span>
      <span class="cat-emoji">🔌</span>
      <div class="cat-name">Electronics</div>
      <div class="cat-desc">Earbuds, chargers, smart bulbs, cables & everyday gadgets.</div>
      <a href="#" class="cat-link">Explore →</a>
    </div>
    <div class="cat-card cat-card--blue reveal">
      <span class="cat-count">870 items</span>
      <span class="cat-emoji">🧰</span>
      <div class="cat-name">Home & Utensils</div>
      <div class="cat-desc">Cookware, cleaning supplies, storage & everything for daily life.</div>
      <a href="#" class="cat-link">Explore →</a>
    </div>
  </div>
</section>

<!-- ── FEATURED PRODUCTS ── -->
<section class="section products-section" id="products">
  <div class="section-label reveal">Trending Now</div>
  <h2 class="section-title reveal">Picked For You</h2>
  <p class="section-sub reveal">Our top sellers this week.</p>

  <div class="products-row stagger">
    <div class="prod-card reveal">
      <div class="prod-img">🥭</div>
      <div class="prod-info">
        <div class="prod-tag">Fruits</div>
        <div class="prod-name">Sindhi Mangoes</div>
        <div class="prod-price">Rs. 320 / kg</div>
        <button class="prod-add">+ Add to Cart</button>
      </div>
    </div>
    <div class="prod-card reveal">
      <div class="prod-img">🍟</div>
      <div class="prod-info">
        <div class="prod-tag">Snacks</div>
        <div class="prod-name">Lays Classic Salt</div>
        <div class="prod-price">Rs. 60 / pack</div>
        <button class="prod-add">+ Add to Cart</button>
      </div>
    </div>
    <div class="prod-card reveal">
      <div class="prod-img">🎧</div>
      <div class="prod-info">
        <div class="prod-tag">Electronics</div>
        <div class="prod-name">TWS Earbuds Pro</div>
        <div class="prod-price">Rs. 1,499</div>
        <button class="prod-add">+ Add to Cart</button>
      </div>
    </div>
    <div class="prod-card reveal">
      <div class="prod-img">🍪</div>
      <div class="prod-info">
        <div class="prod-tag">Biscuits</div>
        <div class="prod-name">Oreo Double Stuff</div>
        <div class="prod-price">Rs. 120 / pack</div>
        <button class="prod-add">+ Add to Cart</button>
      </div>
    </div>
    <div class="prod-card reveal">
      <div class="prod-img">🥦</div>
      <div class="prod-info">
        <div class="prod-tag">Vegetables</div>
        <div class="prod-name">Organic Broccoli</div>
        <div class="prod-price">Rs. 180 / kg</div>
        <button class="prod-add">+ Add to Cart</button>
      </div>
    </div>
    <div class="prod-card reveal">
      <div class="prod-img">🫕</div>
      <div class="prod-info">
        <div class="prod-tag">Utensils</div>
        <div class="prod-name">Non-stick Pan Set</div>
        <div class="prod-price">Rs. 2,200</div>
        <button class="prod-add">+ Add to Cart</button>
      </div>
    </div>
    <div class="prod-card reveal">
      <div class="prod-img">🍋</div>
      <div class="prod-info">
        <div class="prod-tag">Fruits</div>
        <div class="prod-name">Fresh Lemons</div>
        <div class="prod-price">Rs. 80 / dozen</div>
        <button class="prod-add">+ Add to Cart</button>
      </div>
    </div>
    <div class="prod-card reveal">
      <div class="prod-img">💡</div>
      <div class="prod-info">
        <div class="prod-tag">Electronics</div>
        <div class="prod-name">Smart LED Bulb</div>
        <div class="prod-price">Rs. 450</div>
        <button class="prod-add">+ Add to Cart</button>
      </div>
    </div>
  </div>
</section>

<!-- ── FEATURES ── -->
<section class="section" id="features">
  <div class="section-label reveal">Why Bucket Things</div>
  <h2 class="section-title reveal">Built Different</h2>
  <p class="section-sub reveal">We're not just another store. We're your daily companion.</p>

  <div class="features-grid stagger">
    <div class="feat reveal">
      <div class="feat-icon">⚡</div>
      <div class="feat-title">30-Min Express</div>
      <div class="feat-desc">Order placed, bucket packed, rider dispatched — all in under half an hour.</div>
    </div>
    <div class="feat reveal">
      <div class="feat-icon">🌿</div>
      <div class="feat-title">Farm Fresh</div>
      <div class="feat-desc">Fruits and vegetables sourced directly from verified local farms every morning.</div>
    </div>
    <div class="feat reveal">
      <div class="feat-icon">🔒</div>
      <div class="feat-title">Secure Payments</div>
      <div class="feat-desc">EasyPaisa, JazzCash, card payments — all protected with end-to-end encryption.</div>
    </div>
    <div class="feat reveal">
      <div class="feat-icon">🔄</div>
      <div class="feat-title">Easy Returns</div>
      <div class="feat-desc">Not happy? Instant returns and refunds within 24 hours, no questions asked.</div>
    </div>
  </div>
</section>

<!-- ── CTA BANNER ── -->
<div class="cta-banner reveal" id="contact">
  <div>
    <h2 class="cta-title">Get <em>10% off</em> your first order today</h2>
    <p class="cta-sub">Enter your email and we'll drop the discount right in your inbox.</p>
  </div>
  <form class="cta-form" onsubmit="return false">
    <input class="cta-input" type="email" placeholder="your@email.com">
    <button class="btn-primary">Claim Offer</button>
  </form>
</div>

<!-- ── FOOTER ── -->
<footer>
  <div class="footer-copy">© 2025 <span>Bucket Things</span> — All rights reserved.</div>
  <div class="footer-links">
    <a href="#">Privacy</a>
    <a href="#">Terms</a>
    <a href="#">Support</a>
    <a href="#">Instagram</a>
  </div>
</footer>

<script>
  // Cursor
  const cursor = document.getElementById('cursor');
  const ring   = document.getElementById('cursorRing');
  let mx = 0, my = 0;
  document.addEventListener('mousemove', e => {
    mx = e.clientX; my = e.clientY;
    cursor.style.left = mx + 'px';
    cursor.style.top  = my + 'px';
    setTimeout(() => {
      ring.style.left = mx + 'px';
      ring.style.top  = my + 'px';
    }, 80);
  });
  document.querySelectorAll('button, a, .cat-card, .prod-card').forEach(el => {
    el.addEventListener('mouseenter', () => {
      cursor.style.transform = 'translate(-50%,-50%) scale(2)';
      cursor.style.background = '#1a8fff';
      ring.style.borderColor = '#1a8fff';
    });
    el.addEventListener('mouseleave', () => {
      cursor.style.transform = 'translate(-50%,-50%) scale(1)';
      cursor.style.background = 'var(--green)';
      ring.style.borderColor = 'var(--green)';
    });
  });

  // Scroll reveal
  const observer = new IntersectionObserver(entries => {
    entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
  }, { threshold: .12 });
  document.querySelectorAll('.reveal').forEach(el => observer.observe(el));
</script>
</body>
</html>
