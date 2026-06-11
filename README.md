<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Gowtham MG — Portfolio README</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&family=JetBrains+Mono:wght@300;400;700&family=Syne:wght@700;800&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #06070f;
    --surface: rgba(255,255,255,0.04);
    --border: rgba(255,255,255,0.08);
    --violet: #7c3aed;
    --violet-glow: rgba(124,58,237,0.4);
    --cyan: #22d3ee;
    --cyan-glow: rgba(34,211,238,0.3);
    --pink: #f472b6;
    --white: #f0f4ff;
    --muted: #6b7280;
    --card-bg: rgba(255,255,255,0.03);
    --r: 16px;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--white);
    font-family: 'Space Grotesk', sans-serif;
    line-height: 1.6;
    overflow-x: hidden;
  }

  /* ── CANVAS ── */
  #starfield {
    position: fixed; inset: 0;
    pointer-events: none;
    z-index: 0;
  }

  /* ── LAYOUT ── */
  .wrap { max-width: 860px; margin: 0 auto; padding: 0 24px; position: relative; z-index: 1; }

  section { padding: 80px 0; }

  /* ── HERO ── */
  #hero {
    min-height: 100vh;
    display: flex; align-items: center;
    padding-top: 40px;
  }

  .hero-inner { width: 100%; }

  .hero-eyebrow {
    font-family: 'JetBrains Mono', monospace;
    font-size: 13px;
    color: var(--cyan);
    letter-spacing: 0.2em;
    text-transform: uppercase;
    opacity: 0;
    animation: fadeUp 0.6s 0.2s forwards;
    display: flex; align-items: center; gap: 10px;
  }
  .hero-eyebrow::before {
    content: '';
    display: inline-block;
    width: 32px; height: 1px;
    background: var(--cyan);
  }

  .hero-name {
    font-family: 'Syne', sans-serif;
    font-size: clamp(52px, 10vw, 110px);
    font-weight: 800;
    line-height: 0.95;
    letter-spacing: -0.03em;
    margin-top: 16px;
    opacity: 0;
    animation: fadeUp 0.7s 0.4s forwards;
  }

  .hero-name span {
    background: linear-gradient(135deg, var(--violet) 0%, var(--cyan) 60%, var(--pink) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero-roles {
    margin-top: 24px;
    display: flex; flex-wrap: wrap; gap: 10px;
    opacity: 0;
    animation: fadeUp 0.7s 0.6s forwards;
  }

  .role-chip {
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    padding: 5px 14px;
    border-radius: 100px;
    border: 1px solid var(--border);
    background: var(--surface);
    color: var(--muted);
    transition: all 0.3s;
  }
  .role-chip:hover {
    border-color: var(--violet);
    color: var(--white);
    background: var(--violet-glow);
  }

  .hero-bio {
    max-width: 540px;
    margin-top: 28px;
    font-size: 16px;
    color: #94a3b8;
    opacity: 0;
    animation: fadeUp 0.7s 0.8s forwards;
  }

  .hero-cta {
    margin-top: 36px;
    display: flex; flex-wrap: wrap; gap: 14px;
    opacity: 0;
    animation: fadeUp 0.7s 1s forwards;
  }

  .btn {
    display: inline-flex; align-items: center; gap: 8px;
    padding: 11px 24px;
    border-radius: 100px;
    font-size: 14px; font-weight: 600;
    text-decoration: none;
    transition: all 0.3s;
    cursor: pointer;
    border: none;
  }
  .btn-primary {
    background: linear-gradient(135deg, var(--violet), var(--cyan));
    color: #fff;
    box-shadow: 0 0 30px var(--violet-glow);
  }
  .btn-primary:hover { box-shadow: 0 0 50px var(--violet-glow); transform: translateY(-2px); }

  .btn-ghost {
    background: transparent;
    border: 1px solid var(--border);
    color: var(--white);
  }
  .btn-ghost:hover { border-color: var(--cyan); color: var(--cyan); }

  .hero-scroll-hint {
    margin-top: 64px;
    display: flex; align-items: center; gap: 12px;
    font-size: 12px;
    color: var(--muted);
    font-family: 'JetBrains Mono', monospace;
    opacity: 0;
    animation: fadeUp 0.6s 1.4s forwards;
  }
  .scroll-line {
    width: 40px; height: 1px;
    background: linear-gradient(90deg, var(--violet), transparent);
  }

  /* ── SECTION HEADERS ── */
  .sec-label {
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    color: var(--cyan);
    letter-spacing: 0.25em;
    text-transform: uppercase;
    display: flex; align-items: center; gap: 12px;
    margin-bottom: 12px;
  }
  .sec-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, var(--border), transparent);
  }

  .sec-title {
    font-family: 'Syne', sans-serif;
    font-size: clamp(28px, 5vw, 44px);
    font-weight: 800;
    line-height: 1.1;
    margin-bottom: 48px;
  }
  .sec-title em { font-style: normal; color: var(--violet); }

  /* ── EXPERIENCE ── */
  .timeline { position: relative; padding-left: 32px; }
  .timeline::before {
    content: '';
    position: absolute; left: 6px; top: 8px; bottom: 8px;
    width: 1px;
    background: linear-gradient(to bottom, var(--violet), var(--cyan), transparent);
  }

  .exp-item {
    position: relative;
    margin-bottom: 48px;
    opacity: 0;
    transform: translateX(-20px);
    transition: all 0.6s ease;
  }
  .exp-item.visible { opacity: 1; transform: translateX(0); }

  .exp-dot {
    position: absolute;
    left: -34px; top: 6px;
    width: 14px; height: 14px;
    border-radius: 50%;
    background: var(--violet);
    box-shadow: 0 0 16px var(--violet-glow);
    border: 2px solid var(--bg);
  }

  .exp-card {
    background: var(--card-bg);
    border: 1px solid var(--border);
    border-radius: var(--r);
    padding: 24px 28px;
    transition: border-color 0.3s, box-shadow 0.3s;
  }
  .exp-card:hover {
    border-color: var(--violet);
    box-shadow: 0 0 40px rgba(124,58,237,0.12);
  }

  .exp-header {
    display: flex; justify-content: space-between; align-items: flex-start;
    flex-wrap: wrap; gap: 8px;
    margin-bottom: 12px;
  }

  .exp-title {
    font-size: 17px; font-weight: 700;
    color: var(--white);
  }
  .exp-company {
    font-size: 13px;
    color: var(--cyan);
    font-family: 'JetBrains Mono', monospace;
    margin-top: 3px;
  }
  .exp-period {
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    color: var(--muted);
    white-space: nowrap;
    padding: 3px 10px;
    background: var(--surface);
    border-radius: 100px;
    border: 1px solid var(--border);
  }

  .exp-bullets {
    list-style: none;
    margin-top: 12px;
    display: flex; flex-direction: column; gap: 8px;
  }
  .exp-bullets li {
    font-size: 14px;
    color: #94a3b8;
    padding-left: 18px;
    position: relative;
  }
  .exp-bullets li::before {
    content: '▸';
    position: absolute; left: 0;
    color: var(--violet);
    font-size: 11px; top: 2px;
  }
  .exp-bullets li strong { color: var(--white); }

  /* ── SKILLS ── */
  .terminal {
    background: #0d0f1a;
    border: 1px solid var(--border);
    border-radius: var(--r);
    overflow: hidden;
    font-family: 'JetBrains Mono', monospace;
  }
  .terminal-bar {
    background: rgba(255,255,255,0.05);
    padding: 12px 18px;
    display: flex; align-items: center; gap: 8px;
    border-bottom: 1px solid var(--border);
  }
  .dot-r { width: 12px; height: 12px; border-radius: 50%; background: #ff5f57; }
  .dot-y { width: 12px; height: 12px; border-radius: 50%; background: #febc2e; }
  .dot-g { width: 12px; height: 12px; border-radius: 50%; background: #28c840; }
  .terminal-title { font-size: 12px; color: var(--muted); margin-left: auto; margin-right: auto; }

  .terminal-body { padding: 24px; }

  .skill-group { margin-bottom: 24px; }
  .skill-group-label {
    font-size: 11px;
    color: var(--cyan);
    letter-spacing: 0.15em;
    text-transform: uppercase;
    margin-bottom: 12px;
  }
  .skill-group-label::before { content: '$ '; color: var(--pink); }

  .skill-tags { display: flex; flex-wrap: wrap; gap: 8px; }

  .skill-tag {
    font-size: 12px;
    padding: 4px 12px;
    border-radius: 6px;
    background: var(--surface);
    border: 1px solid var(--border);
    color: #cbd5e1;
    transition: all 0.25s;
    cursor: default;
  }
  .skill-tag:hover {
    background: var(--violet-glow);
    border-color: var(--violet);
    color: var(--white);
    transform: translateY(-2px);
  }

  /* ── PROJECTS ── */
  .projects-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(340px, 1fr));
    gap: 20px;
  }

  .proj-card {
    background: var(--card-bg);
    border: 1px solid var(--border);
    border-radius: var(--r);
    padding: 28px;
    transition: all 0.35s;
    position: relative;
    overflow: hidden;
    opacity: 0;
    transform: translateY(24px);
  }
  .proj-card.visible { opacity: 1; transform: translateY(0); }
  .proj-card::before {
    content: '';
    position: absolute; inset: 0;
    background: radial-gradient(circle at top left, var(--violet-glow), transparent 60%);
    opacity: 0;
    transition: opacity 0.3s;
  }
  .proj-card:hover { border-color: var(--violet); box-shadow: 0 8px 40px rgba(124,58,237,0.18); }
  .proj-card:hover::before { opacity: 1; }

  .proj-number {
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    color: var(--violet);
    letter-spacing: 0.1em;
    margin-bottom: 12px;
  }

  .proj-title { font-size: 18px; font-weight: 700; margin-bottom: 10px; }

  .proj-desc { font-size: 14px; color: #94a3b8; margin-bottom: 18px; line-height: 1.6; }

  .proj-stack {
    display: flex; flex-wrap: wrap; gap: 6px;
    margin-bottom: 20px;
  }
  .stack-tag {
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    padding: 3px 8px;
    border-radius: 4px;
    background: rgba(34,211,238,0.08);
    color: var(--cyan);
    border: 1px solid rgba(34,211,238,0.15);
  }

  .proj-links { display: flex; gap: 12px; }
  .proj-link {
    font-size: 13px; font-weight: 600;
    color: var(--violet);
    text-decoration: none;
    display: flex; align-items: center; gap: 6px;
    transition: color 0.2s;
  }
  .proj-link:hover { color: var(--cyan); }

  /* ── CERTIFICATIONS ── */
  .certs-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 16px;
  }
  .cert-card {
    background: var(--card-bg);
    border: 1px solid var(--border);
    border-radius: var(--r);
    padding: 20px;
    text-align: center;
    transition: all 0.3s;
    opacity: 0;
    transform: scale(0.95);
  }
  .cert-card.visible { opacity: 1; transform: scale(1); }
  .cert-card:hover { border-color: var(--cyan); box-shadow: 0 0 30px var(--cyan-glow); }
  .cert-icon { font-size: 28px; margin-bottom: 10px; }
  .cert-name { font-size: 14px; font-weight: 600; margin-bottom: 4px; }
  .cert-issuer { font-size: 12px; color: var(--muted); font-family: 'JetBrains Mono', monospace; }

  /* ── EDUCATION ── */
  .edu-cards { display: flex; flex-direction: column; gap: 16px; }
  .edu-card {
    background: var(--card-bg);
    border: 1px solid var(--border);
    border-radius: var(--r);
    padding: 22px 28px;
    display: flex; justify-content: space-between; align-items: center;
    flex-wrap: wrap; gap: 12px;
    transition: border-color 0.3s;
    opacity: 0;
    transform: translateX(20px);
  }
  .edu-card.visible { opacity: 1; transform: translateX(0); }
  .edu-card:hover { border-color: var(--violet); }

  .edu-degree { font-size: 16px; font-weight: 700; }
  .edu-college { font-size: 13px; color: var(--cyan); margin-top: 3px; font-family: 'JetBrains Mono', monospace; }
  .edu-year { font-size: 12px; color: var(--muted); }
  .edu-gpa {
    font-family: 'Syne', sans-serif;
    font-size: 22px; font-weight: 800;
    color: var(--violet);
  }
  .edu-gpa span { font-size: 12px; font-family: 'JetBrains Mono', monospace; color: var(--muted); display: block; text-align: right; }

  /* ── CONTACT ── */
  #contact { text-align: center; }
  .contact-subtext { color: #94a3b8; max-width: 480px; margin: 0 auto 36px; }
  .contact-links { display: flex; justify-content: center; flex-wrap: wrap; gap: 16px; }
  .contact-link {
    display: flex; align-items: center; gap: 10px;
    padding: 13px 24px;
    border-radius: 100px;
    border: 1px solid var(--border);
    background: var(--surface);
    color: var(--white);
    text-decoration: none;
    font-size: 14px; font-weight: 500;
    transition: all 0.3s;
  }
  .contact-link:hover { border-color: var(--violet); background: var(--violet-glow); transform: translateY(-3px); }

  /* ── FOOTER ── */
  footer {
    border-top: 1px solid var(--border);
    padding: 32px 24px;
    text-align: center;
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    color: var(--muted);
  }
  .footer-gradient {
    background: linear-gradient(90deg, var(--violet), var(--cyan));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    font-weight: 700;
  }

  /* ── DIVIDER ── */
  .glow-divider {
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--violet), var(--cyan), transparent);
    margin: 0;
    opacity: 0.4;
  }

  /* ── GLOW ORB ── */
  .orb {
    position: fixed;
    border-radius: 50%;
    filter: blur(120px);
    pointer-events: none;
    z-index: 0;
    animation: orbFloat 8s ease-in-out infinite alternate;
  }
  .orb-1 { width: 500px; height: 500px; background: rgba(124,58,237,0.12); top: -100px; right: -150px; }
  .orb-2 { width: 400px; height: 400px; background: rgba(34,211,238,0.08); bottom: 10%; left: -100px; animation-delay: -4s; }

  @keyframes orbFloat {
    from { transform: translateY(0px) scale(1); }
    to   { transform: translateY(30px) scale(1.05); }
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  /* ── CURSOR GLOW ── */
  .cursor-glow {
    position: fixed;
    width: 300px; height: 300px;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(124,58,237,0.08) 0%, transparent 70%);
    pointer-events: none;
    transform: translate(-50%, -50%);
    transition: transform 0.1s linear;
    z-index: 0;
  }

  @media (max-width: 600px) {
    .projects-grid { grid-template-columns: 1fr; }
    .exp-header { flex-direction: column; }
    .hero-cta { flex-direction: column; }
  }
</style>
</head>
<body>

<canvas id="starfield"></canvas>
<div class="orb orb-1"></div>
<div class="orb orb-2"></div>
<div class="cursor-glow" id="cursorGlow"></div>

<!-- ═══ HERO ═══ -->
<section id="hero">
<div class="wrap">
<div class="hero-inner">
  <div class="hero-eyebrow">Available for opportunities</div>
  <h1 class="hero-name"><span>Gowtham</span><br>MG</h1>
  <div class="hero-roles">
    <span class="role-chip">Machine Learning Engineer</span>
    <span class="role-chip">Cybersecurity Analyst</span>
    <span class="role-chip">MLOps</span>
    <span class="role-chip">Assistant Professor</span>
    <span class="role-chip">AWS · Docker · K8s</span>
  </div>
  <p class="hero-bio">I build end-to-end AI systems — from feature engineering to Kubernetes deployments — and I'm equally drawn to cybersecurity, threat detection, and incident response.</p>
  <div class="hero-cta">
    <a class="btn btn-primary" href="mailto:mggowtham347@gmail.com">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="m2 7 10 6 10-6"/></svg>
      Get in touch
    </a>
    <a class="btn btn-ghost" href="https://github.com/GOWTHAMMG347" target="_blank">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0 0 24 12c0-6.63-5.37-12-12-12z"/></svg>
      GitHub
    </a>
    <a class="btn btn-ghost" href="https://linkedin.com/in/gowtham-m-g-7266aa325" target="_blank">
      <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6zM2 9h4v12H2z"/><circle cx="4" cy="4" r="2"/></svg>
      LinkedIn
    </a>
  </div>
  <div class="hero-scroll-hint">
    <div class="scroll-line"></div>
    scroll to explore
  </div>
</div>
</div>
</section>

<div class="glow-divider"></div>

<!-- ═══ EXPERIENCE ═══ -->
<section id="experience">
<div class="wrap">
  <div class="sec-label">Career</div>
  <h2 class="sec-title">Professional <em>Experience</em></h2>
  <div class="timeline">

    <div class="exp-item">
      <div class="exp-dot"></div>
      <div class="exp-card">
        <div class="exp-header">
          <div>
            <div class="exp-title">Assistant Professor</div>
            <div class="exp-company">ATME College of Engineering · Mysore</div>
          </div>
          <div class="exp-period">2025 – Present</div>
        </div>
        <ul class="exp-bullets">
          <li>Teaching <strong>100+ students</strong> per semester across CS subjects</li>
          <li>Concurrently deepening expertise in <strong>security monitoring</strong>, threat detection &amp; incident response</li>
          <li>Balancing classroom delivery with hands-on lab research under real production pressure</li>
        </ul>
      </div>
    </div>

    <div class="exp-item">
      <div class="exp-dot" style="background:var(--cyan);box-shadow:0 0 16px var(--cyan-glow);"></div>
      <div class="exp-card">
        <div class="exp-header">
          <div>
            <div class="exp-title">Machine Learning Engineer Intern</div>
            <div class="exp-company">Technocolabs Software Inc.</div>
          </div>
          <div class="exp-period">Apr – Jun 2025</div>
        </div>
        <ul class="exp-bullets">
          <li>Trained Linear Regression, Random Forest, XGBoost pipelines achieving <strong>85%+ accuracy</strong></li>
          <li>Shipped production <strong>Flask</strong> apps deployed via <strong>Docker + Kubernetes on AWS</strong></li>
          <li>Reduced deployment time by <strong>≈40%</strong> through container orchestration &amp; CI/CD automation</li>
        </ul>
      </div>
    </div>

    <div class="exp-item">
      <div class="exp-dot" style="background:var(--pink);box-shadow:0 0 16px rgba(244,114,182,0.4);"></div>
      <div class="exp-card">
        <div class="exp-header">
          <div>
            <div class="exp-title">Data Science Intern</div>
            <div class="exp-company">EISystems Technologies</div>
          </div>
          <div class="exp-period">Jun – Aug 2025</div>
        </div>
        <ul class="exp-bullets">
          <li>Deployed transfer-learning <strong>real-time object detection</strong> model (~75% accuracy)</li>
          <li>Deployed on <strong>AWS EC2</strong> with Docker + Kubernetes for live inference</li>
          <li>Built a minimal <strong>Flask UI</strong> for real-time monitoring and result visualization</li>
        </ul>
      </div>
    </div>

  </div>
</div>
</section>

<div class="glow-divider"></div>

<!-- ═══ SKILLS ═══ -->
<section id="skills">
<div class="wrap">
  <div class="sec-label">Expertise</div>
  <h2 class="sec-title">Skills &amp; <em>Tech Stack</em></h2>
  <div class="terminal">
    <div class="terminal-bar">
      <div class="dot-r"></div><div class="dot-y"></div><div class="dot-g"></div>
      <div class="terminal-title">skills.sh — gowtham@portfolio</div>
    </div>
    <div class="terminal-body">

      <div class="skill-group">
        <div class="skill-group-label">siem-and-network</div>
        <div class="skill-tags">
          <span class="skill-tag">Splunk</span><span class="skill-tag">Wireshark</span><span class="skill-tag">Nmap</span>
          <span class="skill-tag">TCP/IP</span><span class="skill-tag">DNS · DHCP</span><span class="skill-tag">VPN · VLANs</span>
          <span class="skill-tag">IDS/IPS</span><span class="skill-tag">Firewall</span><span class="skill-tag">OSI Model</span>
        </div>
      </div>

      <div class="skill-group">
        <div class="skill-group-label">offensive-and-vuln</div>
        <div class="skill-tags">
          <span class="skill-tag">Burp Suite</span><span class="skill-tag">Kali Linux</span><span class="skill-tag">Metasploit</span>
          <span class="skill-tag">OWASP ZAP</span><span class="skill-tag">Nessus</span><span class="skill-tag">CVE Analysis</span>
          <span class="skill-tag">MITRE ATT&CK</span><span class="skill-tag">Threat Intel</span>
        </div>
      </div>

      <div class="skill-group">
        <div class="skill-group-label">machine-learning</div>
        <div class="skill-tags">
          <span class="skill-tag">Regression</span><span class="skill-tag">Classification</span><span class="skill-tag">XGBoost</span>
          <span class="skill-tag">Ensemble Learning</span><span class="skill-tag">Anomaly Detection</span>
          <span class="skill-tag">Time Series</span><span class="skill-tag">RAG</span><span class="skill-tag">LLM</span>
        </div>
      </div>

      <div class="skill-group">
        <div class="skill-group-label">deep-learning</div>
        <div class="skill-tags">
          <span class="skill-tag">CNN</span><span class="skill-tag">LSTM</span><span class="skill-tag">GAN</span>
          <span class="skill-tag">Transformers</span><span class="skill-tag">ResNet</span><span class="skill-tag">Auto Encoders</span>
          <span class="skill-tag">YOLO</span><span class="skill-tag">Hugging Face</span>
        </div>
      </div>

      <div class="skill-group">
        <div class="skill-group-label">mlops-and-cloud</div>
        <div class="skill-tags">
          <span class="skill-tag">AWS EC2/S3/IAM</span><span class="skill-tag">Docker</span><span class="skill-tag">Kubernetes</span>
          <span class="skill-tag">Jenkins</span><span class="skill-tag">Flask</span><span class="skill-tag">CI/CD</span>
          <span class="skill-tag">Azure AD</span><span class="skill-tag">PowerShell</span><span class="skill-tag">Bash</span>
        </div>
      </div>

      <div class="skill-group">
        <div class="skill-group-label">languages-and-libs</div>
        <div class="skill-tags">
          <span class="skill-tag">Python</span><span class="skill-tag">Java</span><span class="skill-tag">SQL</span>
          <span class="skill-tag">Scikit-learn</span><span class="skill-tag">PyTorch</span><span class="skill-tag">Keras</span>
          <span class="skill-tag">NLTK</span><span class="skill-tag">SpaCy</span><span class="skill-tag">OpenCV</span>
        </div>
      </div>

    </div>
  </div>
</div>
</section>

<div class="glow-divider"></div>

<!-- ═══ PROJECTS ═══ -->
<section id="projects">
<div class="wrap">
  <div class="sec-label">Work</div>
  <h2 class="sec-title">Featured <em>Projects</em></h2>
  <div class="projects-grid">

    <div class="proj-card">
      <div class="proj-number">01 / PROJECT</div>
      <h3 class="proj-title">Generative AI for Ethical Hacking</h3>
      <p class="proj-desc">AI-powered penetration testing toolkit integrating Nmap, SQLMap, and Gemini API to automate reconnaissance, vulnerability detection, exploit suggestions, and generate automated PDF security audit reports.</p>
      <div class="proj-stack">
        <span class="stack-tag">Gemini API</span><span class="stack-tag">Nmap</span><span class="stack-tag">SQLMap</span><span class="stack-tag">Python</span>
      </div>
      <div class="proj-links">
        <a class="proj-link" href="https://github.com/GOWTHAMMG347" target="_blank">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0 0 24 12c0-6.63-5.37-12-12-12z"/></svg>
          View Repo
        </a>
      </div>
    </div>

    <div class="proj-card">
      <div class="proj-number">02 / PROJECT</div>
      <h3 class="proj-title">Predicting Startup Status</h3>
      <p class="proj-desc">Classifies startups as Acquired, Operating, IPO, or Closed using ensemble ML models. Full MLOps pipeline from data to live Flask deployment on AWS.</p>
      <div class="proj-stack">
        <span class="stack-tag">XGBoost</span><span class="stack-tag">Flask</span><span class="stack-tag">Docker</span><span class="stack-tag">AWS</span>
      </div>
      <div class="proj-links">
        <a class="proj-link" href="https://github.com/GOWTHAMMG347/Startup_Prediction" target="_blank">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0 0 24 12c0-6.63-5.37-12-12-12z"/></svg>
          View Repo
        </a>
        <a class="proj-link" href="https://vercel347.onrender.com/" target="_blank">
          <svg width="14" height="14" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"/><polyline points="15 3 21 3 21 9"/><line x1="10" y1="14" x2="21" y2="3"/></svg>
          Live Demo
        </a>
      </div>
    </div>

    <div class="proj-card">
      <div class="proj-number">03 / PROJECT</div>
      <h3 class="proj-title">Bank Note Authentication</h3>
      <p class="proj-desc">Detects counterfeit banknotes using features extracted from scanned note images (Variance, Skewness) with a clean MLOps pipeline from training to deployment.</p>
      <div class="proj-stack">
        <span class="stack-tag">Keras</span><span class="stack-tag">Scikit-learn</span><span class="stack-tag">Pandas</span><span class="stack-tag">Matplotlib</span>
      </div>
      <div class="proj-links">
        <a class="proj-link" href="https://github.com/GOWTHAMMG347/Bank-Note-Authentication" target="_blank">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0 0 24 12c0-6.63-5.37-12-12-12z"/></svg>
          View Repo
        </a>
        <a class="proj-link" href="https://bank-note-authentication-4taz.onrender.com/" target="_blank">
          <svg width="14" height="14" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"/><polyline points="15 3 21 3 21 9"/><line x1="10" y1="14" x2="21" y2="3"/></svg>
          Live Demo
        </a>
      </div>
    </div>

  </div>
</div>
</section>

<div class="glow-divider"></div>

<!-- ═══ EDUCATION ═══ -->
<section id="education">
<div class="wrap">
  <div class="sec-label">Academic</div>
  <h2 class="sec-title">Education <em>&amp; Background</em></h2>
  <div class="edu-cards">

    <div class="edu-card">
      <div>
        <div class="edu-degree">Master of Computer Applications</div>
        <div class="edu-college">P.E.S College of Engineering · Mandya</div>
        <div class="edu-year">2023 – 2025</div>
      </div>
      <div>
        <div class="edu-gpa">7.95<span>CGPA</span></div>
      </div>
    </div>

    <div class="edu-card">
      <div>
        <div class="edu-degree">B.Sc. Computer Science</div>
        <div class="edu-college">University of Mysore</div>
        <div class="edu-year">2018 – 2021</div>
      </div>
      <div>
        <div class="edu-gpa">59.6%<span>Score</span></div>
      </div>
    </div>

  </div>
</div>
</section>

<div class="glow-divider"></div>

<!-- ═══ CERTS ═══ -->
<section id="certs">
<div class="wrap">
  <div class="sec-label">Credentials</div>
  <h2 class="sec-title">Certifications <em>&amp; Learning</em></h2>
  <div class="certs-grid">
    <div class="cert-card">
      <div class="cert-icon">🛡️</div>
      <div class="cert-name">TryHackMe SOC Level 1</div>
      <div class="cert-issuer">TryHackMe</div>
    </div>
    <div class="cert-card">
      <div class="cert-icon">⚙️</div>
      <div class="cert-name">DevOps</div>
      <div class="cert-issuer">JSPIDERS · Jun 2023</div>
    </div>
    <div class="cert-card">
      <div class="cert-icon">☕</div>
      <div class="cert-name">Java Full Stack</div>
      <div class="cert-issuer">JSPIDERS · Jun 2023</div>
    </div>
    <div class="cert-card">
      <div class="cert-icon">☁️</div>
      <div class="cert-name">AWS IAM</div>
      <div class="cert-issuer">Amazon Web Services · Jun 2023</div>
    </div>
  </div>
</div>
</section>

<div class="glow-divider"></div>

<!-- ═══ CONTACT ═══ -->
<section id="contact">
<div class="wrap">
  <div class="sec-label" style="justify-content:center;">Connect</div>
  <h2 class="sec-title" style="text-align:center;">Let's Build<br><em>Something Together</em></h2>
  <p class="contact-subtext">Whether it's an ML project, a security discussion, or just a chat — reach out. I'm always up for interesting conversations.</p>
  <div class="contact-links">
    <a class="contact-link" href="mailto:mggowtham347@gmail.com">
      <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="m2 7 10 6 10-6"/></svg>
      mggowtham347@gmail.com
    </a>
    <a class="contact-link" href="tel:+919035724265">
      <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07A19.5 19.5 0 0 1 4.69 9.1 19.79 19.79 0 0 1 1.61 .44 2 2 0 0 1 3.6 0h3a2 2 0 0 1 2 1.72c.127.96.361 1.903.7 2.81a2 2 0 0 1-.45 2.11L7.91 7.91a16 16 0 0 0 6.16 6.16l.94-.94a2 2 0 0 1 2.11-.45c.907.339 1.85.573 2.81.7A2 2 0 0 1 22 16.92z"/></svg>
      +91 90357 24265
    </a>
    <a class="contact-link" href="https://linkedin.com/in/gowtham-m-g-7266aa325" target="_blank">
      <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6zM2 9h4v12H2z"/><circle cx="4" cy="4" r="2"/></svg>
      LinkedIn
    </a>
    <a class="contact-link" href="https://github.com/GOWTHAMMG347" target="_blank">
      <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0 0 24 12c0-6.63-5.37-12-12-12z"/></svg>
      GitHub
    </a>
  </div>
</div>
</section>

<footer>
  <div class="wrap">
    Built with <span class="footer-gradient">precision &amp; passion</span> · Gowtham MG · 2025
  </div>
</footer>

<script>
// ── STARFIELD CANVAS ──
const canvas = document.getElementById('starfield');
const ctx = canvas.getContext('2d');
let W, H, stars = [];

function resize() {
  W = canvas.width = window.innerWidth;
  H = canvas.height = window.innerHeight;
}

function initStars() {
  stars = [];
  for (let i = 0; i < 160; i++) {
    stars.push({
      x: Math.random() * W,
      y: Math.random() * H,
      r: Math.random() * 1.2 + 0.2,
      a: Math.random(),
      da: (Math.random() - 0.5) * 0.005,
      vx: (Math.random() - 0.5) * 0.05,
      vy: (Math.random() - 0.5) * 0.05,
    });
  }
}

function drawStars() {
  ctx.clearRect(0, 0, W, H);
  for (const s of stars) {
    s.a += s.da;
    if (s.a < 0 || s.a > 1) s.da *= -1;
    s.x += s.vx; s.y += s.vy;
    if (s.x < 0) s.x = W; if (s.x > W) s.x = 0;
    if (s.y < 0) s.y = H; if (s.y > H) s.y = 0;
    ctx.beginPath();
    ctx.arc(s.x, s.y, s.r, 0, Math.PI * 2);
    ctx.fillStyle = `rgba(200, 180, 255, ${s.a * 0.6})`;
    ctx.fill();
  }
  requestAnimationFrame(drawStars);
}

resize(); initStars(); drawStars();
window.addEventListener('resize', () => { resize(); initStars(); });

// ── CURSOR GLOW ──
const glow = document.getElementById('cursorGlow');
document.addEventListener('mousemove', e => {
  glow.style.left = e.clientX + 'px';
  glow.style.top = e.clientY + 'px';
});

// ── SCROLL REVEAL ──
const revealEls = document.querySelectorAll('.exp-item, .proj-card, .cert-card, .edu-card');
const io = new IntersectionObserver((entries) => {
  entries.forEach((e, i) => {
    if (e.isIntersecting) {
      setTimeout(() => e.target.classList.add('visible'), i * 80);
    }
  });
}, { threshold: 0.1 });
revealEls.forEach(el => io.observe(el));
</script>
</body>
</html>
