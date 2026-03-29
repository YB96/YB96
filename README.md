<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Yash Bhairao — Data Engineer</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Mono:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #050810;
    --surface: #0c1120;
    --surface2: #111827;
    --border: rgba(99,179,237,0.12);
    --accent: #38bdf8;
    --accent2: #818cf8;
    --accent3: #34d399;
    --text: #e2e8f0;
    --muted: #64748b;
    --glow: rgba(56,189,248,0.15);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Mono', monospace;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* Grid noise overlay */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(99,179,237,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(99,179,237,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  .container {
    max-width: 900px;
    margin: 0 auto;
    padding: 40px 24px 80px;
    position: relative;
    z-index: 1;
  }

  /* ── HERO ── */
  .hero {
    display: grid;
    grid-template-columns: auto 1fr;
    gap: 32px;
    align-items: center;
    padding: 48px 40px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 20px;
    margin-bottom: 32px;
    position: relative;
    overflow: hidden;
    animation: fadeUp 0.6s ease both;
  }

  .hero::after {
    content: '';
    position: absolute;
    top: -60px; right: -60px;
    width: 240px; height: 240px;
    background: radial-gradient(circle, rgba(56,189,248,0.12) 0%, transparent 70%);
    pointer-events: none;
  }

  .avatar-wrap {
    position: relative;
  }

  .avatar-ring {
    width: 100px; height: 100px;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    padding: 2px;
    animation: spin-slow 8s linear infinite;
  }

  .avatar-inner {
    width: 100%; height: 100%;
    border-radius: 50%;
    background: var(--surface);
    display: flex; align-items: center; justify-content: center;
    font-size: 36px;
  }

  .hero-text { }
  .hero-greeting {
    font-family: 'Syne', sans-serif;
    font-size: 13px;
    font-weight: 600;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 8px;
  }

  .hero-name {
    font-family: 'Syne', sans-serif;
    font-size: clamp(28px, 5vw, 42px);
    font-weight: 800;
    line-height: 1.1;
    background: linear-gradient(90deg, #e2e8f0 0%, var(--accent) 60%, var(--accent2) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin-bottom: 10px;
  }

  .hero-role {
    font-size: 14px;
    color: var(--muted);
    margin-bottom: 18px;
  }

  .hero-role span {
    color: var(--accent3);
    font-weight: 500;
  }

  .badge-row {
    display: flex; flex-wrap: wrap; gap: 8px;
  }

  .badge {
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    padding: 4px 12px;
    border-radius: 20px;
    border: 1px solid var(--border);
    color: var(--muted);
    background: var(--surface2);
    transition: all 0.2s;
    cursor: default;
  }

  .badge:hover {
    border-color: var(--accent);
    color: var(--accent);
    box-shadow: 0 0 12px var(--glow);
  }

  /* ── SECTION LABEL ── */
  .section-label {
    font-family: 'Syne', sans-serif;
    font-size: 11px;
    font-weight: 700;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 16px;
    display: flex; align-items: center; gap: 10px;
  }

  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, var(--border), transparent);
  }

  /* ── PROJECTS ── */
  .projects-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
    gap: 16px;
    margin-bottom: 32px;
  }

  .project-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 24px;
    cursor: pointer;
    transition: all 0.25s ease;
    text-decoration: none;
    color: inherit;
    display: block;
    position: relative;
    overflow: hidden;
    animation: fadeUp 0.6s ease both;
  }

  .project-card:hover {
    border-color: var(--accent);
    transform: translateY(-4px);
    box-shadow: 0 16px 40px rgba(0,0,0,0.4), 0 0 20px var(--glow);
  }

  .project-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--accent), var(--accent2));
    transform: scaleX(0);
    transform-origin: left;
    transition: transform 0.3s ease;
  }

  .project-card:hover::before { transform: scaleX(1); }

  .project-num {
    font-size: 11px;
    color: var(--accent);
    letter-spacing: 0.15em;
    margin-bottom: 10px;
  }

  .project-title {
    font-family: 'Syne', sans-serif;
    font-size: 15px;
    font-weight: 700;
    color: var(--text);
    margin-bottom: 8px;
    line-height: 1.3;
  }

  .project-desc {
    font-size: 12px;
    color: var(--muted);
    line-height: 1.6;
    margin-bottom: 16px;
  }

  .project-tags {
    display: flex; flex-wrap: wrap; gap: 6px;
  }

  .tag {
    font-size: 10px;
    padding: 3px 8px;
    border-radius: 4px;
    background: rgba(56,189,248,0.08);
    color: var(--accent);
    border: 1px solid rgba(56,189,248,0.15);
  }

  .project-arrow {
    position: absolute;
    top: 20px; right: 20px;
    font-size: 16px;
    color: var(--muted);
    transition: all 0.2s;
  }

  .project-card:hover .project-arrow {
    color: var(--accent);
    transform: translate(2px, -2px);
  }

  /* ── TOOLS ── */
  .tools-section {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 28px;
    margin-bottom: 32px;
    animation: fadeUp 0.6s 0.2s ease both;
  }

  .tools-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
  }

  .tool-group-title {
    font-size: 11px;
    color: var(--accent2);
    letter-spacing: 0.15em;
    text-transform: uppercase;
    margin-bottom: 10px;
  }

  .tool-pill-wrap { display: flex; flex-wrap: wrap; gap: 6px; }

  .tool-pill {
    font-size: 11px;
    padding: 5px 10px;
    border-radius: 6px;
    background: var(--surface2);
    border: 1px solid var(--border);
    color: var(--text);
    cursor: default;
    transition: all 0.2s;
  }

  .tool-pill:hover {
    background: rgba(129,140,248,0.1);
    border-color: var(--accent2);
    color: var(--accent2);
  }

  /* ── STATS ── */
  .stats-row {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 12px;
    margin-bottom: 32px;
    animation: fadeUp 0.6s 0.3s ease both;
  }

  .stat-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 20px 16px;
    text-align: center;
    transition: all 0.2s;
  }

  .stat-card:hover {
    border-color: var(--accent3);
    box-shadow: 0 0 20px rgba(52,211,153,0.1);
  }

  .stat-num {
    font-family: 'Syne', sans-serif;
    font-size: 26px;
    font-weight: 800;
    color: var(--accent3);
    line-height: 1;
    margin-bottom: 4px;
  }

  .stat-label {
    font-size: 10px;
    color: var(--muted);
    letter-spacing: 0.1em;
    text-transform: uppercase;
  }

  /* ── QUOTE ── */
  .quote-block {
    background: var(--surface);
    border: 1px solid var(--border);
    border-left: 3px solid var(--accent);
    border-radius: 0 12px 12px 0;
    padding: 24px 28px;
    margin-bottom: 32px;
    animation: fadeUp 0.6s 0.4s ease both;
  }

  .quote-text {
    font-family: 'Syne', sans-serif;
    font-size: 15px;
    font-style: italic;
    color: var(--text);
    line-height: 1.6;
    margin-bottom: 8px;
  }

  .quote-author {
    font-size: 12px;
    color: var(--accent);
  }

  /* ── FOOTER ── */
  .footer {
    text-align: center;
    padding-top: 24px;
    border-top: 1px solid var(--border);
    font-size: 12px;
    color: var(--muted);
    animation: fadeUp 0.6s 0.5s ease both;
  }

  .footer a { color: var(--accent); text-decoration: none; }
  .footer .star-cta {
    display: inline-flex; align-items: center; gap: 6px;
    margin-top: 12px;
    padding: 8px 20px;
    background: rgba(56,189,248,0.08);
    border: 1px solid rgba(56,189,248,0.2);
    border-radius: 20px;
    color: var(--accent);
    font-size: 12px;
    cursor: pointer;
    transition: all 0.2s;
    text-decoration: none;
  }

  .footer .star-cta:hover {
    background: rgba(56,189,248,0.15);
    box-shadow: 0 0 16px var(--glow);
  }

  /* ── ANIMATIONS ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  @keyframes spin-slow {
    from { transform: rotate(0deg); }
    to { transform: rotate(360deg); }
  }

  /* stagger cards */
  .project-card:nth-child(1) { animation-delay: 0.1s; }
  .project-card:nth-child(2) { animation-delay: 0.2s; }
  .project-card:nth-child(3) { animation-delay: 0.3s; }

  /* ── RESPONSIVE ── */
  @media (max-width: 640px) {
    .hero { grid-template-columns: 1fr; text-align: center; }
    .avatar-wrap { justify-self: center; }
    .badge-row { justify-content: center; }
    .tools-grid { grid-template-columns: 1fr; }
    .stats-row { grid-template-columns: repeat(2, 1fr); }
  }
</style>
</head>
<body>
<div class="container">

  <!-- HERO -->
  <div class="hero">
    <div class="avatar-wrap">
      <div class="avatar-ring">
        <div class="avatar-inner">👨‍💻</div>
      </div>
    </div>
    <div class="hero-text">
      <div class="hero-greeting">// hello world</div>
      <div class="hero-name">Yash Bhairao</div>
      <div class="hero-role">Data Engineer · <span>Building pipelines that move the world</span></div>
      <div class="badge-row">
        <span class="badge">🔧 Data Pipelines</span>
        <span class="badge">📊 EDA</span>
        <span class="badge">🤖 ML</span>
        <span class="badge">🌐 Web Scraping</span>
        <span class="badge">Open to Collaborate</span>
      </div>
    </div>
  </div>

  <!-- STATS -->
  <div class="stats-row">
    <div class="stat-card"><div class="stat-num">3</div><div class="stat-label">Projects</div></div>
    <div class="stat-card"><div class="stat-num">5+</div><div class="stat-label">Languages</div></div>
    <div class="stat-card"><div class="stat-num">10+</div><div class="stat-label">Libraries</div></div>
    <div class="stat-card"><div class="stat-num">∞</div><div class="stat-label">Curiosity</div></div>
  </div>

  <!-- PROJECTS -->
  <div class="section-label">Featured Projects</div>
  <div class="projects-grid">

    <a class="project-card" href="https://github.com/YB96/data-analysis" target="_blank">
      <div class="project-arrow">↗</div>
      <div class="project-num">// project 01</div>
      <div class="project-title">Brazilian E-Commerce EDA</div>
      <div class="project-desc">Deep-dive into Olist's dataset to surface actionable insights on sales, delivery, and customer behavior.</div>
      <div class="project-tags">
        <span class="tag">Python</span><span class="tag">Pandas</span><span class="tag">Plotly</span><span class="tag">EDA</span>
      </div>
    </a>

    <a class="project-card" href="https://jovian.ai/yashchamp96/course-project-on-breast-cancer" target="_blank">
      <div class="project-arrow">↗</div>
      <div class="project-num">// project 02</div>
      <div class="project-title">Breast Cancer Classification</div>
      <div class="project-desc">Identifying malignant vs benign samples via statistical analysis and ML models on clinical data.</div>
      <div class="project-tags">
        <span class="tag">Scikit-learn</span><span class="tag">Seaborn</span><span class="tag">ML</span>
      </div>
    </a>

    <a class="project-card" href="https://jovian.ai/yashchamp96/project-web-scraping" target="_blank">
      <div class="project-arrow">↗</div>
      <div class="project-num">// project 03</div>
      <div class="project-title">Flipkart Scraper</div>
      <div class="project-desc">Automated scraper that monitors iPhone listings on Flipkart and aggregates pricing data in real time.</div>
      <div class="project-tags">
        <span class="tag">BeautifulSoup</span><span class="tag">Requests</span><span class="tag">Automation</span>
      </div>
    </a>

  </div>

  <!-- TOOLS -->
  <div class="section-label">Tech Stack</div>
  <div class="tools-section">
    <div class="tools-grid">
      <div>
        <div class="tool-group-title">Languages</div>
        <div class="tool-pill-wrap">
          <span class="tool-pill">Python</span>
          <span class="tool-pill">R</span>
          <span class="tool-pill">SQL</span>
        </div>
      </div>
      <div>
        <div class="tool-group-title">Libraries</div>
        <div class="tool-pill-wrap">
          <span class="tool-pill">Pandas</span>
          <span class="tool-pill">NumPy</span>
          <span class="tool-pill">Scikit-learn</span>
          <span class="tool-pill">TensorFlow</span>
        </div>
      </div>
      <div>
        <div class="tool-group-title">Visualization</div>
        <div class="tool-pill-wrap">
          <span class="tool-pill">Matplotlib</span>
          <span class="tool-pill">Seaborn</span>
          <span class="tool-pill">Plotly</span>
          <span class="tool-pill">Tableau</span>
          <span class="tool-pill">Power BI</span>
        </div>
      </div>
    </div>
  </div>

  <!-- QUOTE -->
  <div class="quote-block">
    <div class="quote-text">"Data holds the key to unlocking knowledge. Let's explore its secrets together."</div>
    <div class="quote-author">— Yash Prakash Bhairao</div>
  </div>

  <!-- FOOTER -->
  <div class="footer">
    <div>Licensed under <a href="#">MIT License</a> · Free to use &amp; adapt</div>
    <a class="star-cta" href="https://github.com/YB96" target="_blank">⭐ Star the repository if you find this helpful</a>
  </div>

</div>
</body>
</html>
