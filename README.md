<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="theme-color" content="#f8f7f2">
  <title>AxieDeck — Plan your next move</title>
  <meta name="description" content="Build, refine, and share your Axie deck ideas with AxieDeck.">
  <style>
    :root {
      color-scheme: light;
      --ink: #20232c;
      --muted: #656a75;
      --paper: #f8f7f2;
      --white: #fffefa;
      --purple: #7657dc;
      --purple-dark: #5c40bd;
      --mint: #c9f0df;
      --line: #e8e5de;
      --shadow: 0 24px 70px rgba(37, 31, 65, .12);
    }

    * { box-sizing: border-box; }

    html { scroll-behavior: smooth; }

    body {
      margin: 0;
      background: var(--paper);
      color: var(--ink);
      font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      line-height: 1.55;
    }

    a { color: inherit; text-decoration: none; }

    .wrap {
      width: min(1120px, calc(100% - 40px));
      margin: 0 auto;
    }

    header {
      height: 82px;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    .brand {
      display: inline-flex;
      align-items: center;
      gap: 10px;
      font-size: 1.15rem;
      font-weight: 850;
      letter-spacing: -.04em;
    }

    .brand-mark {
      display: grid;
      width: 36px;
      height: 36px;
      place-items: center;
      border-radius: 12px;
      background: var(--purple);
      color: white;
      font-size: 1.1rem;
      transform: rotate(-5deg);
    }

    nav { display: flex; align-items: center; gap: 30px; }
    nav a { color: var(--muted); font-size: .92rem; font-weight: 650; }
    nav a:hover { color: var(--purple-dark); }

    .button {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 9px;
      min-height: 48px;
      padding: 0 20px;
      border: 0;
      border-radius: 14px;
      background: var(--purple);
      color: white;
      font: inherit;
      font-weight: 750;
      box-shadow: 0 8px 20px rgba(118, 87, 220, .22);
      transition: transform .18s ease, background .18s ease;
    }

    .button:hover { background: var(--purple-dark); transform: translateY(-2px); }
    .button.small { min-height: 42px; padding: 0 16px; font-size: .9rem; }
    .button.secondary { background: white; color: var(--ink); box-shadow: none; border: 1px solid var(--line); }
    .button.secondary:hover { background: #f1effa; }

    .hero {
      min-height: 620px;
      display: grid;
      grid-template-columns: 1.02fr .98fr;
      align-items: center;
      gap: 50px;
      padding: 45px 0 85px;
    }

    .eyebrow {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      margin-bottom: 20px;
      color: var(--purple-dark);
      font-size: .78rem;
      font-weight: 850;
      letter-spacing: .12em;
      text-transform: uppercase;
    }

    .eyebrow::before {
      content: "";
      width: 8px;
      height: 8px;
      border-radius: 50%;
      background: #65bd92;
      box-shadow: 0 0 0 5px rgba(101, 189, 146, .15);
    }

    h1 {
      max-width: 610px;
      margin: 0;
      font-size: clamp(3.2rem, 7vw, 5.7rem);
      line-height: .99;
      letter-spacing: -.075em;
    }

    h1 span { color: var(--purple); }

    .hero-copy {
      max-width: 490px;
      margin: 24px 0 30px;
      color: var(--muted);
      font-size: 1.12rem;
    }

    .actions { display: flex; flex-wrap: wrap; gap: 12px; }
    .note { margin-top: 18px; color: #858994; font-size: .83rem; }

    .showcase {
      position: relative;
      display: grid;
      min-height: 430px;
      place-items: center;
      isolation: isolate;
    }

    .blob {
      position: absolute;
      z-index: -1;
      width: min(390px, 85%);
      aspect-ratio: 1;
      border-radius: 43% 57% 59% 41% / 46% 41% 59% 54%;
      background: #e9e2ff;
      transform: rotate(-12deg);
    }

    .deck-window {
      width: min(390px, 100%);
      padding: 20px;
      border: 1px solid rgba(255,255,255,.9);
      border-radius: 24px;
      background: rgba(255, 254, 250, .88);
      box-shadow: var(--shadow);
      transform: rotate(2deg);
      backdrop-filter: blur(12px);
    }

    .window-top { display: flex; align-items: center; justify-content: space-between; margin-bottom: 18px; }
    .window-title { font-size: .87rem; font-weight: 800; }
    .dots { display: flex; gap: 5px; }
    .dots i { width: 7px; height: 7px; display: block; border-radius: 50%; background: #dedbe7; }

    .deck-label {
      display: inline-flex;
      align-items: center;
      gap: 7px;
      padding: 6px 10px;
      border-radius: 99px;
      background: #f0edff;
      color: var(--purple-dark);
      font-size: .72rem;
      font-weight: 800;
    }

    .cards { display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; margin: 15px 0; }

    .card {
      min-height: 148px;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      padding: 12px;
      border: 1px solid rgba(255,255,255,.8);
      border-radius: 17px;
      color: #302846;
      overflow: hidden;
      position: relative;
    }

    .card::after {
      content: "";
      position: absolute;
      width: 75px;
      height: 75px;
      right: -17px;
      bottom: 14px;
      border: 12px solid rgba(255,255,255,.35);
      border-radius: 50%;
    }

    .card:nth-child(1) { background: #ffe4ba; }
    .card:nth-child(2) { background: #c9efdf; }
    .card:nth-child(3) { background: #e1d8ff; }

    .card-icon { font-size: 1.65rem; }
    .card-name { font-size: .78rem; font-weight: 850; }
    .card-type { color: rgba(48,40,70,.7); font-size: .68rem; }

    .deck-stats {
      display: flex;
      justify-content: space-between;
      padding-top: 13px;
      border-top: 1px solid var(--line);
      color: var(--muted);
      font-size: .75rem;
    }
    .deck-stats strong { color: var(--ink); }

    .spark {
      position: absolute;
      color: #f0aa50;
      font-size: 2rem;
    }
    .spark.one { top: 44px; right: 12%; }
    .spark.two { bottom: 40px; left: 7%; color: var(--purple); font-size: 1.4rem; }

    section { padding: 88px 0; }
    .section-head { max-width: 620px; margin: 0 auto 42px; text-align: center; }
    .section-head h2 { margin: 0 0 12px; font-size: clamp(2rem, 4vw, 3rem); letter-spacing: -.055em; line-height: 1.1; }
    .section-head p { margin: 0; color: var(--muted); }

    .features { background: var(--white); border-top: 1px solid var(--line); border-bottom: 1px solid var(--line); }

    .feature-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 18px; }

    .feature {
      padding: 26px;
      border: 1px solid var(--line);
      border-radius: 20px;
      background: #fff;
    }

    .feature-icon {
      display: grid;
      width: 46px;
      height: 46px;
      place-items: center;
      margin-bottom: 18px;
      border-radius: 14px;
      background: #f0edff;
      font-size: 1.35rem;
    }

    .feature:nth-child(2) .feature-icon { background: #e7f7ef; }
    .feature:nth-child(3) .feature-icon { background: #fff1dc; }
    .feature h3 { margin: 0 0 8px; font-size: 1.05rem; }
    .feature p { margin: 0; color: var(--muted); font-size: .92rem; }

    .callout {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 25px;
      padding: 42px;
      border-radius: 28px;
      background: var(--ink);
      color: white;
    }

    .callout h2 { max-width: 540px; margin: 0; font-size: clamp(1.8rem, 4vw, 2.7rem); line-height: 1.1; letter-spacing: -.05em; }
    .callout p { margin: 12px 0 0; color: #c4c5ce; }
    .callout .button { flex-shrink: 0; background: var(--mint); color: #20362e; box-shadow: none; }
    .callout .button:hover { background: #a9e3c9; }

    footer {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 20px;
      padding: 28px 0;
      color: #858994;
      font-size: .8rem;
    }

    footer p { margin: 0; }

    @media (max-width: 760px) {
      .wrap { width: min(100% - 32px, 560px); }
      header { height: 72px; }
      nav { gap: 15px; }
      nav a:not(.button) { display: none; }
      .hero { grid-template-columns: 1fr; gap: 20px; padding: 55px 0 65px; }
      .showcase { min-height: 365px; }
      .deck-window { max-width: 360px; }
      .card { min-height: 125px; }
      section { padding: 66px 0; }
      .feature-grid { grid-template-columns: 1fr; }
      .callout { align-items: flex-start; flex-direction: column; padding: 30px; }
      footer { align-items: flex-start; flex-direction: column; }
    }

    @media (prefers-reduced-motion: reduce) {
      html { scroll-behavior: auto; }
      *, *::before, *::after { transition-duration: .01ms !important; }
    }
  </style>
</head>
<body>
  <header class="wrap">
    <a class="brand" href="#" aria-label="AxieDeck home">
      <span class="brand-mark" aria-hidden="true">✦</span>
      <span>AxieDeck</span>
    </a>
    <nav aria-label="Main navigation">
      <a href="#features">Features</a>
      <a href="#about">About</a>
      <a class="button small" href="#get-started">Get started <span aria-hidden="true">↗</span></a>
    </nav>
  </header>

  <main>
    <section class="wrap hero">
      <div>
        <div class="eyebrow">Your next great deck starts here</div>
        <h1>Think ahead.<br>Play <span>your way.</span></h1>
        <p class="hero-copy">
          AxieDeck is a home for your deck ideas. Organize strategies, try new combinations,
          and get ready for your next match.
        </p>
        <div class="actions">
          <a class="button" href="#get-started">Explore AxieDeck <span aria-hidden="true">→</span></a>
          <a class="button secondary" href="#features">See what you can do</a>
        </div>
        <p class="note">A fan-made companion for the Axie community.</p>
      </div>

      <div class="showcase" aria-label="Illustration of a sample deck">
        <div class="blob"></div>
        <span class="spark one" aria-hidden="true">✳</span>
        <span class="spark two" aria-hidden="true">✦</span>
        <div class="deck-window">
          <div class="window-top">
            <span class="window-title">A little deck in progress</span>
            <span class="dots" aria-hidden="true"><i></i><i></i><i></i></span>
          </div>
          <span class="deck-label">✦ &nbsp; DECK IDEA</span>
          <div class="cards">
            <div class="card">
              <span class="card-icon" aria-hidden="true">🌱</span>
              <span><span class="card-name">Grow</span><br><span class="card-type">Build your plan</span></span>
            </div>
            <div class="card">
              <span class="card-icon" aria-hidden="true">⚡</span>
              <span><span class="card-name">Adapt</span><br><span class="card-type">Try a new combo</span></span>
            </div>
            <div class="card">
              <span class="card-icon" aria-hidden="true">🛡️</span>
              <span><span class="card-name">Repeat</span><br><span class="card-type">Make it yours</span></span>
            </div>
          </div>
          <div class="deck-stats">
            <span><strong>Plan</strong> your next move</span>
            <span>Made for curious players ✨</span>
          </div>
        </div>
      </div>
    </section>

    <section class="features" id="features">
      <div class="wrap">
        <div class="section-head">
          <h2>Make room for better ideas.</h2>
          <p>Keep your strategy thinking together, from the first rough draft to the deck you’re excited to play.</p>
        </div>
        <div class="feature-grid">
          <article class="feature">
            <div class="feature-icon" aria-hidden="true">🧩</div>
            <h3>Build your combinations</h3>
            <p>Put ideas together and shape a deck that fits the way you like to play.</p>
          </article>
          <article class="feature">
            <div class="feature-icon" aria-hidden="true">🗂️</div>
            <h3>Keep ideas organized</h3>
            <p>Save your concepts in one tidy place so you can pick up where you left off.</p>
          </article>
          <article class="feature">
            <div class="feature-icon" aria-hidden="true">💬</div>
            <h3>Share with your crew</h3>
            <p>Bring your friends into the conversation and compare ideas together.</p>
          </article>
        </div>
      </div>
    </section>

    <section class="wrap" id="about">
      <div class="callout" id="get-started">
        <div>
          <h2>Ready to make your next move?</h2>
          <p>AxieDeck is built for players who love thinking one step ahead.</p>
        </div>
        <a class="button" href="mailto:hello@axiedeck.example">Say hello <span aria-hidden="true">→</span></a>
      </div>
    </section>
  </main>

  <footer class="wrap">
    <a class="brand" href="#"><span class="brand-mark" aria-hidden="true">✦</span><span>AxieDeck</span></a>
    <p>Fan-made and not affiliated with Sky Mavis or Axie Infinity.</p>
    <p>
      © <span id="year">2026</span> AxieDeck
      <a href="https://a-deck-0.flycricket.io/privacy.html">Privacy</a>
    </p>
  </footer>
</body>
</html>
