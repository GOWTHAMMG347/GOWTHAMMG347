<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Gowtham MG — Cybersecurity & AI Portfolio</title>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Share+Tech+Mono&family=Rajdhani:wght@300;500;700&display=swap" rel="stylesheet" />
<style>
:root {
  --bg: #020c14;
  --panel: #040f1a;
  --cyan: #00ffe7;
  --blue: #0ff;
  --red: #ff2d55;
  --gold: #ffd700;
  --text: #c8e6f0;
  --dim: #476474;
  --glow-cyan: 0 0 8px #00ffe7, 0 0 20px #00ffe755;
  --glow-red: 0 0 8px #ff2d55, 0 0 20px #ff2d5555;
}

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

html { scroll-behavior: smooth; }

body {
  font-family: 'Rajdhani', sans-serif;
  background: var(--bg);
  color: var(--text);
  overflow-x: hidden;
  cursor: none;
}

/* ── CUSTOM CURSOR ── */
#cursor {
  position: fixed; width: 12px; height: 12px;
  background: var(--cyan); border-radius: 50%;
  pointer-events: none; z-index: 9999;
  transform: translate(-50%,-50%);
  transition: transform .1s, background .2s;
  box-shadow: var(--glow-cyan);
}
#cursor-ring {
  position: fixed; width: 36px; height: 36px;
  border: 1px solid var(--cyan); border-radius: 50%;
  pointer-events: none; z-index: 9998;
  transform: translate(-50%,-50%);
  transition: transform .18s ease, opacity .2s;
  opacity: .5;
}

/* ── CANVAS BACKGROUND ── */
#matrix-canvas {
  position: fixed; top: 0; left: 0;
  width: 100%; height: 100%;
  z-index: 0; opacity: .13;
  pointer-events: none;
}

/* ── SCANLINE OVERLAY ── */
body::after {
  content: '';
  position: fixed; inset: 0;
  background: repeating-linear-gradient(0deg,
    transparent, transparent 2px,
    rgba(0,255,231,.015) 2px, rgba(0,255,231,.015) 4px);
  pointer-events: none; z-index: 1;
  animation: scanline 8s linear infinite;
}
@keyframes scanline {
  0%{background-position:0 0}100%{background-position:0 400px}
}

/* ── NAV ── */
nav {
  position: fixed; top: 0; left: 0; right: 0;
  z-index: 100;
  display: flex; align-items: center; justify-content: space-between;
  padding: 14px 40px;
  background: rgba(2,12,20,.85);
  backdrop-filter: blur(12px);
  border-bottom: 1px solid rgba(0,255,231,.12);
}
.nav-logo {
  font-family: 'Orbitron', monospace;
  font-size: 1.1rem; color: var(--cyan);
  letter-spacing: 3px;
  text-shadow: var(--glow-cyan);
}
.nav-links { display: flex; gap: 28px; list-style: none; }
.nav-links a {
  font-family: 'Share Tech Mono', monospace;
  font-size: .8rem; color: var(--dim);
  text-decoration: none; letter-spacing: 2px;
  text-transform: uppercase;
  transition: color .25s, text-shadow .25s;
  position: relative;
}
.nav-links a::after {
  content: ''; position: absolute; left: 0; bottom: -4px;
  width: 0; height: 1px; background: var(--cyan);
  transition: width .3s;
}
.nav-links a:hover { color: var(--cyan); text-shadow: var(--glow-cyan); }
.nav-links a:hover::after { width: 100%; }

/* ── SECTIONS ── */
section { position: relative; z-index: 2; }

/* ── HERO ── */
#hero {
  min-height: 100vh;
  display: flex; flex-direction: column;
  align-items: center; justify-content: center;
  text-align: center; padding: 120px 20px 60px;
  overflow: hidden;
}

.hero-glitch-wrapper {
  position: relative; display: inline-block;
}
.hero-name {
  font-family: 'Orbitron', monospace;
  font-size: clamp(2.8rem, 8vw, 6.5rem);
  font-weight: 900;
  color: #fff;
  letter-spacing: 6px;
  text-transform: uppercase;
  animation: glitch-main 4s infinite;
  position: relative;
}
.hero-name::before, .hero-name::after {
  content: 'GOWTHAM MG';
  position: absolute; top: 0; left: 0;
  width: 100%;
}
.hero-name::before {
  color: var(--red); animation: glitch-a 4s infinite;
  clip-path: polygon(0 20%, 100% 20%, 100% 40%, 0 40%);
  transform: translate(-3px, 0);
}
.hero-name::after {
  color: var(--cyan); animation: glitch-b 4s infinite;
  clip-path: polygon(0 60%, 100% 60%, 100% 75%, 0 75%);
  transform: translate(3px, 0);
}
@keyframes glitch-main {
  0%,93%,100%{transform:none;opacity:1}
  94%{transform:skewX(3deg)}95%{transform:skewX(-3deg)}96%{transform:none}
}
@keyframes glitch-a {
  0%,92%,100%{opacity:0;transform:translate(-3px,0)}
  93%{opacity:1;transform:translate(-6px,2px)}
  96%{opacity:0}
}
@keyframes glitch-b {
  0%,92%,100%{opacity:0;transform:translate(3px,0)}
  93%{opacity:1;transform:translate(6px,-2px)}
  96%{opacity:0}
}

.hero-tagline {
  font-family: 'Share Tech Mono', monospace;
  font-size: clamp(.85rem, 2vw, 1.1rem);
  color: var(--cyan);
  letter-spacing: 4px;
  margin-top: 18px;
  text-shadow: var(--glow-cyan);
  overflow: hidden; white-space: nowrap; border-right: 2px solid var(--cyan);
  animation: typing 3.5s steps(60) .5s 1 normal both, blink .75s step-end infinite;
}
@keyframes typing { from{width:0}to{width:100%} }
@keyframes blink { 50%{border-color:transparent} }

.hero-sub {
  font-size: 1.1rem; color: var(--dim);
  margin-top: 12px; letter-spacing: 2px;
  font-weight: 300;
}

.hero-badges {
  display: flex; flex-wrap: wrap; gap: 12px;
  justify-content: center; margin-top: 36px;
}
.badge {
  font-family: 'Share Tech Mono', monospace;
  font-size: .75rem; letter-spacing: 2px;
  padding: 8px 18px;
  border: 1px solid var(--cyan);
  color: var(--cyan);
  background: rgba(0,255,231,.05);
  text-transform: uppercase;
  clip-path: polygon(8px 0%, 100% 0%, calc(100% - 8px) 100%, 0% 100%);
  animation: badge-pulse 3s ease-in-out infinite;
  transition: background .2s, box-shadow .2s;
}
.badge:hover {
  background: rgba(0,255,231,.15);
  box-shadow: var(--glow-cyan);
}
.badge.red { border-color: var(--red); color: var(--red); clip-path: polygon(8px 0%, 100% 0%, calc(100% - 8px) 100%, 0% 100%); }
.badge.red:hover { box-shadow: var(--glow-red); background: rgba(255,45,85,.15); }
@keyframes badge-pulse {
  0%,100%{box-shadow:none}50%{box-shadow:0 0 10px rgba(0,255,231,.25)}
}

.hero-cta {
  display: flex; gap: 20px; margin-top: 40px; flex-wrap: wrap; justify-content: center;
}
.btn {
  font-family: 'Orbitron', monospace;
  font-size: .75rem; letter-spacing: 3px;
  padding: 14px 32px;
  border: none; cursor: none;
  text-decoration: none; text-transform: uppercase;
  display: inline-flex; align-items: center; gap: 8px;
  transition: all .25s;
  position: relative; overflow: hidden;
}
.btn-primary {
  background: var(--cyan); color: #020c14;
  clip-path: polygon(12px 0%, 100% 0%, calc(100% - 12px) 100%, 0% 100%);
}
.btn-primary:hover { box-shadow: var(--glow-cyan); transform: translateY(-2px); }
.btn-outline {
  background: transparent; color: var(--cyan);
  border: 1px solid var(--cyan);
  clip-path: polygon(12px 0%, 100% 0%, calc(100% - 12px) 100%, 0% 100%);
}
.btn-outline:hover { background: rgba(0,255,231,.1); box-shadow: var(--glow-cyan); transform: translateY(-2px); }

/* rotating hex */
.hero-hex {
  position: absolute; right: 8%; top: 50%; transform: translateY(-50%);
  width: 220px; height: 220px; opacity: .18;
  animation: spin-slow 18s linear infinite;
  pointer-events: none;
}
@keyframes spin-slow { to{transform:translateY(-50%) rotate(360deg)} }
.hex-inner { width: 100%; height: 100%; animation: spin-slow 12s linear infinite reverse; }

/* ── SECTION HEADER ── */
.sec-header {
  text-align: center; margin-bottom: 60px;
}
.sec-label {
  font-family: 'Share Tech Mono', monospace;
  font-size: .75rem; letter-spacing: 5px;
  color: var(--cyan); text-transform: uppercase;
  margin-bottom: 8px;
}
.sec-title {
  font-family: 'Orbitron', monospace;
  font-size: clamp(1.6rem, 4vw, 2.6rem);
  font-weight: 900; color: #fff;
  text-shadow: 0 0 30px rgba(0,255,231,.2);
}
.sec-line {
  width: 80px; height: 2px;
  background: linear-gradient(90deg, transparent, var(--cyan), transparent);
  margin: 16px auto 0;
  animation: pulse-line 2s ease-in-out infinite;
}
@keyframes pulse-line { 0%,100%{opacity:.4}50%{opacity:1} }

/* ── ABOUT ── */
#about { padding: 120px 40px; max-width: 1100px; margin: auto; }
.about-grid {
  display: grid; grid-template-columns: 1fr 1.4fr; gap: 60px; align-items: center;
}
.about-visual {
  position: relative; display: flex; align-items: center; justify-content: center;
}
.about-avatar {
  width: 220px; height: 220px;
  border-radius: 50%;
  background: linear-gradient(135deg, rgba(0,255,231,.12), rgba(0,80,255,.12));
  border: 2px solid var(--cyan);
  display: flex; align-items: center; justify-content: center;
  font-size: 5rem;
  box-shadow: var(--glow-cyan), inset 0 0 40px rgba(0,255,231,.06);
  animation: float 4s ease-in-out infinite;
  position: relative; z-index: 1;
}
@keyframes float { 0%,100%{transform:translateY(0)}50%{transform:translateY(-14px)} }
.orbit {
  position: absolute;
  border: 1px dashed rgba(0,255,231,.25);
  border-radius: 50%;
  animation: orbit-spin 8s linear infinite;
}
.orbit:nth-child(1) { width: 290px; height: 290px; animation-duration: 10s; }
.orbit:nth-child(2) { width: 360px; height: 360px; animation-duration: 15s; animation-direction: reverse; }
.orbit:nth-child(3) { width: 430px; height: 430px; animation-duration: 20s; }
.orbit-dot {
  position: absolute; top: -4px; left: 50%;
  transform: translateX(-50%);
  width: 8px; height: 8px; border-radius: 50%;
  background: var(--cyan);
  box-shadow: var(--glow-cyan);
}
@keyframes orbit-spin { to{transform:rotate(360deg)} }

.stat-ring {
  position: absolute; bottom: 10px; right: -10px;
}
.stat-chip {
  display: flex; align-items: center; gap: 8px;
  background: rgba(4,15,26,.9);
  border: 1px solid rgba(0,255,231,.3);
  padding: 8px 14px; border-radius: 4px;
  font-family: 'Share Tech Mono', monospace; font-size: .8rem;
  color: var(--cyan);
  animation: chip-pop .5s ease both;
  margin-bottom: 8px;
}

.about-text h3 {
  font-family: 'Orbitron', monospace;
  font-size: 1.5rem; color: #fff; margin-bottom: 16px;
}
.about-text p {
  font-size: 1.05rem; line-height: 1.8; color: var(--text);
  margin-bottom: 16px; font-weight: 300;
}
.highlight { color: var(--cyan); font-weight: 700; }

.info-grid {
  display: grid; grid-template-columns: 1fr 1fr; gap: 12px; margin-top: 24px;
}
.info-item {
  background: rgba(0,255,231,.04);
  border: 1px solid rgba(0,255,231,.12);
  border-left: 3px solid var(--cyan);
  padding: 10px 14px;
  font-family: 'Share Tech Mono', monospace;
  font-size: .78rem;
}
.info-item .label { color: var(--dim); font-size: .68rem; letter-spacing: 2px; }
.info-item .val { color: #fff; margin-top: 2px; }

/* ── EXPERIENCE ── */
#experience { padding: 100px 40px; background: rgba(0,255,231,.02); }
.exp-container { max-width: 900px; margin: auto; }
.exp-card {
  display: grid; grid-template-columns: auto 1fr; gap: 0 32px;
  position: relative;
}
.exp-line-col {
  display: flex; flex-direction: column; align-items: center;
}
.exp-dot {
  width: 16px; height: 16px; border-radius: 50%;
  background: var(--bg);
  border: 2px solid var(--cyan);
  box-shadow: var(--glow-cyan);
  flex-shrink: 0;
  animation: dot-pulse 2s ease-in-out infinite;
}
@keyframes dot-pulse { 0%,100%{box-shadow:var(--glow-cyan)}50%{box-shadow:0 0 20px var(--cyan),0 0 40px rgba(0,255,231,.4)} }
.exp-vert-line { flex: 1; width: 1px; background: linear-gradient(to bottom, var(--cyan), transparent); margin-top: 8px; }

.exp-body {
  background: rgba(4,15,26,.7);
  border: 1px solid rgba(0,255,231,.15);
  border-left: 3px solid var(--cyan);
  padding: 28px 32px;
  margin-bottom: 40px;
  clip-path: polygon(0 0, calc(100% - 16px) 0, 100% 16px, 100% 100%, 16px 100%, 0 calc(100% - 16px));
  transition: border-color .3s, box-shadow .3s;
}
.exp-body:hover {
  border-color: var(--cyan);
  box-shadow: 0 0 30px rgba(0,255,231,.08);
}
.exp-role {
  font-family: 'Orbitron', monospace;
  font-size: 1.1rem; color: var(--cyan); margin-bottom: 4px;
}
.exp-org { font-weight: 700; color: #fff; font-size: 1rem; margin-bottom: 4px; }
.exp-date {
  font-family: 'Share Tech Mono', monospace;
  font-size: .78rem; color: var(--dim); margin-bottom: 16px;
}
.exp-bullets { list-style: none; }
.exp-bullets li {
  padding: 6px 0 6px 20px;
  position: relative; font-size: .95rem; color: var(--text);
  border-bottom: 1px solid rgba(0,255,231,.05);
}
.exp-bullets li::before {
  content: '▹'; position: absolute; left: 0; color: var(--cyan);
}

/* ── SKILLS ── */
#skills { padding: 100px 40px; }
.skills-container { max-width: 1100px; margin: auto; }

.skills-tabs {
  display: flex; flex-wrap: wrap; gap: 8px; justify-content: center; margin-bottom: 50px;
}
.tab-btn {
  font-family: 'Share Tech Mono', monospace;
  font-size: .75rem; letter-spacing: 2px;
  padding: 8px 20px; border: 1px solid rgba(0,255,231,.25);
  background: transparent; color: var(--dim); cursor: none;
  text-transform: uppercase; transition: all .25s;
  clip-path: polygon(6px 0,100% 0,calc(100% - 6px) 100%,0 100%);
}
.tab-btn.active, .tab-btn:hover {
  border-color: var(--cyan); color: var(--cyan);
  background: rgba(0,255,231,.08);
  box-shadow: var(--glow-cyan);
}

.skills-panel { display: none; }
.skills-panel.active { display: grid; grid-template-columns: repeat(auto-fill, minmax(180px, 1fr)); gap: 16px; }

.skill-card {
  background: rgba(4,15,26,.8);
  border: 1px solid rgba(0,255,231,.15);
  padding: 20px 16px;
  text-align: center;
  clip-path: polygon(0 0, calc(100% - 12px) 0, 100% 12px, 100% 100%, 12px 100%, 0 calc(100% - 12px));
  transition: all .3s;
  animation: card-in .4s ease both;
}
.skill-card:hover {
  border-color: var(--cyan);
  box-shadow: var(--glow-cyan);
  transform: translateY(-4px);
  background: rgba(0,255,231,.06);
}
@keyframes card-in { from{opacity:0;transform:translateY(20px)}to{opacity:1;transform:none} }
.skill-icon { font-size: 2rem; margin-bottom: 10px; }
.skill-name {
  font-family: 'Share Tech Mono', monospace;
  font-size: .75rem; letter-spacing: 1px; color: #fff;
}
.skill-bar-wrap {
  width: 100%; background: rgba(0,255,231,.08);
  height: 3px; border-radius: 2px; margin-top: 10px; overflow: hidden;
}
.skill-bar {
  height: 100%; background: var(--cyan);
  box-shadow: var(--glow-cyan);
  transform-origin: left;
  animation: bar-fill 1.2s ease forwards .2s;
  transform: scaleX(0);
}
@keyframes bar-fill { to{transform:scaleX(1)} }

/* ── PROJECTS ── */
#projects { padding: 100px 40px; background: rgba(0,255,231,.02); }
.projects-container { max-width: 1100px; margin: auto; }
.projects-grid {
  display: grid; grid-template-columns: repeat(auto-fill, minmax(320px, 1fr)); gap: 28px;
}
.project-card {
  background: rgba(4,15,26,.9);
  border: 1px solid rgba(0,255,231,.15);
  padding: 32px 28px;
  position: relative; overflow: hidden;
  clip-path: polygon(0 0, calc(100% - 20px) 0, 100% 20px, 100% 100%, 20px 100%, 0 calc(100% - 20px));
  transition: all .3s;
}
.project-card::before {
  content: ''; position: absolute; inset: 0;
  background: linear-gradient(135deg, rgba(0,255,231,.05) 0%, transparent 60%);
  opacity: 0; transition: opacity .3s;
}
.project-card:hover {
  border-color: var(--cyan);
  box-shadow: var(--glow-cyan), 0 20px 40px rgba(0,0,0,.4);
  transform: translateY(-6px);
}
.project-card:hover::before { opacity: 1; }

.project-num {
  font-family: 'Orbitron', monospace;
  font-size: 3rem; font-weight: 900;
  color: rgba(0,255,231,.06);
  position: absolute; top: 16px; right: 20px;
  line-height: 1;
}
.project-tag {
  font-family: 'Share Tech Mono', monospace;
  font-size: .68rem; letter-spacing: 3px;
  color: var(--red); text-transform: uppercase;
  margin-bottom: 12px;
}
.project-title {
  font-family: 'Orbitron', monospace;
  font-size: 1rem; color: #fff; margin-bottom: 14px; line-height: 1.4;
}
.project-desc { font-size: .9rem; color: var(--text); line-height: 1.7; margin-bottom: 20px; }
.tech-tags { display: flex; flex-wrap: wrap; gap: 6px; margin-bottom: 20px; }
.tech-tag {
  font-family: 'Share Tech Mono', monospace;
  font-size: .65rem; letter-spacing: 1px;
  padding: 3px 10px;
  border: 1px solid rgba(0,255,231,.3);
  color: var(--cyan); border-radius: 2px;
}
.project-links { display: flex; gap: 12px; }
.project-link {
  font-family: 'Share Tech Mono', monospace;
  font-size: .72rem; letter-spacing: 2px;
  color: var(--cyan); text-decoration: none;
  border: 1px solid rgba(0,255,231,.3);
  padding: 6px 14px;
  transition: all .2s;
  display: flex; align-items: center; gap: 6px;
}
.project-link:hover {
  background: rgba(0,255,231,.1);
  box-shadow: var(--glow-cyan);
}

/* ── CERTS ── */
#certifications { padding: 100px 40px; }
.certs-container { max-width: 1000px; margin: auto; }
.certs-grid {
  display: grid; grid-template-columns: repeat(auto-fill, minmax(220px, 1fr)); gap: 20px;
}
.cert-card {
  background: rgba(4,15,26,.8);
  border: 1px solid rgba(0,255,231,.15);
  padding: 28px 22px;
  text-align: center;
  position: relative; overflow: hidden;
  transition: all .3s;
}
.cert-card::after {
  content: '';
  position: absolute; top: -50%; left: -50%;
  width: 200%; height: 200%;
  background: conic-gradient(from 0deg, transparent 70%, rgba(0,255,231,.1) 80%, transparent 90%);
  animation: cert-rotate 4s linear infinite;
  opacity: 0; transition: opacity .3s;
}
.cert-card:hover::after { opacity: 1; }
.cert-card:hover { border-color: var(--cyan); box-shadow: var(--glow-cyan); transform: scale(1.03); }
@keyframes cert-rotate { to{transform:rotate(360deg)} }
.cert-icon { font-size: 2.5rem; margin-bottom: 12px; display: block; }
.cert-name {
  font-family: 'Orbitron', monospace;
  font-size: .78rem; color: #fff; line-height: 1.5; margin-bottom: 8px;
}
.cert-issuer {
  font-family: 'Share Tech Mono', monospace;
  font-size: .68rem; color: var(--cyan); letter-spacing: 1px;
}
.cert-date { font-size: .7rem; color: var(--dim); margin-top: 4px; }
.cert-badge {
  display: inline-block; padding: 3px 10px;
  background: rgba(255,45,85,.15);
  border: 1px solid var(--red); color: var(--red);
  font-family: 'Share Tech Mono', monospace;
  font-size: .65rem; letter-spacing: 2px;
  margin-top: 10px; border-radius: 2px;
}
.cert-badge.active { background: rgba(0,255,231,.1); border-color: var(--cyan); color: var(--cyan); }

/* ── CONTACT ── */
#contact { padding: 100px 40px; }
.contact-container { max-width: 900px; margin: auto; }
.contact-grid {
  display: grid; grid-template-columns: 1fr 1fr; gap: 60px; align-items: start;
}
.contact-info h3 {
  font-family: 'Orbitron', monospace;
  font-size: 1.3rem; color: #fff; margin-bottom: 16px;
}
.contact-info p { font-size: .95rem; color: var(--text); line-height: 1.8; margin-bottom: 30px; }
.contact-links { display: flex; flex-direction: column; gap: 14px; }
.contact-link {
  display: flex; align-items: center; gap: 14px;
  text-decoration: none; color: var(--text);
  padding: 14px 18px;
  border: 1px solid rgba(0,255,231,.15);
  background: rgba(4,15,26,.7);
  transition: all .3s;
  position: relative; overflow: hidden;
}
.contact-link::before {
  content: ''; position: absolute; left: 0; top: 0; bottom: 0;
  width: 3px; background: var(--cyan);
  transform: scaleY(0); transform-origin: bottom;
  transition: transform .3s;
}
.contact-link:hover { border-color: rgba(0,255,231,.5); box-shadow: var(--glow-cyan); color: #fff; }
.contact-link:hover::before { transform: scaleY(1); }
.contact-link .icon { font-size: 1.4rem; }
.contact-link .detail { font-family: 'Share Tech Mono', monospace; font-size: .8rem; }
.contact-link .detail span { display: block; color: var(--dim); font-size: .68rem; letter-spacing: 2px; }

.terminal-box {
  background: rgba(4,15,26,.9);
  border: 1px solid rgba(0,255,231,.2);
  padding: 24px;
  font-family: 'Share Tech Mono', monospace;
}
.terminal-header {
  display: flex; align-items: center; gap: 8px; margin-bottom: 16px;
}
.t-dot { width: 10px; height: 10px; border-radius: 50%; }
.t-red { background: #ff5f57; }
.t-yellow { background: #febc2e; }
.t-green { background: #28c840; }
.terminal-body { font-size: .78rem; line-height: 2; color: var(--cyan); }
.t-prompt { color: var(--dim); }
.t-cmd { color: #fff; }
.t-out { color: var(--text); padding-left: 16px; }
.t-blink {
  display: inline-block; width: 8px; height: 14px;
  background: var(--cyan); vertical-align: middle;
  animation: blink .75s step-end infinite;
}

/* ── FOOTER ── */
footer {
  text-align: center; padding: 40px;
  border-top: 1px solid rgba(0,255,231,.1);
  font-family: 'Share Tech Mono', monospace;
  font-size: .75rem; color: var(--dim); letter-spacing: 2px;
  position: relative; z-index: 2;
}
footer span { color: var(--cyan); }

/* ── SCROLL REVEAL ── */
.reveal { opacity: 0; transform: translateY(40px); transition: opacity .6s ease, transform .6s ease; }
.reveal.visible { opacity: 1; transform: none; }

/* ── RESPONSIVE ── */
@media (max-width: 768px) {
  nav { padding: 12px 20px; }
  .nav-links { display: none; }
  .about-grid, .contact-grid { grid-template-columns: 1fr; }
  .hero-hex { display: none; }
  .orbit:nth-child(2), .orbit:nth-child(3) { display: none; }
}

/* ── PARTICLES ── */
.particles { position: fixed; inset: 0; pointer-events: none; z-index: 0; overflow: hidden; }
.particle {
  position: absolute; border-radius: 50%;
  background: var(--cyan); opacity: 0;
  animation: particle-float linear infinite;
}
@keyframes particle-float {
  0%{transform:translateY(100vh) scale(0);opacity:0}
  10%{opacity:.5}
  90%{opacity:.2}
  100%{transform:translateY(-10vh) scale(1);opacity:0}
}
</style>
</head>
<body>

<!-- Cursor -->
<div id="cursor"></div>
<div id="cursor-ring"></div>

<!-- Matrix Rain -->
<canvas id="matrix-canvas"></canvas>

<!-- Particles -->
<div class="particles" id="particles"></div>

<!-- NAV -->
<nav>
  <div class="nav-logo">GMG<span style="color:var(--red);">_</span></div>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#experience">Experience</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#certifications">Certs</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<!-- HERO -->
<section id="hero">
  <svg class="hero-hex" viewBox="0 0 200 200" fill="none" xmlns="http://www.w3.org/2000/svg">
    <polygon points="100,5 195,52.5 195,147.5 100,195 5,147.5 5,52.5" stroke="#00ffe7" stroke-width="1" fill="none"/>
    <g class="hex-inner">
      <polygon points="100,20 180,62.5 180,137.5 100,180 20,137.5 20,62.5" stroke="#00ffe7" stroke-width=".5" fill="none" opacity=".5"/>
      <polygon points="100,38 162,73 162,127 100,162 38,127 38,73" stroke="#00ffe7" stroke-width=".5" fill="none" opacity=".3"/>
    </g>
  </svg>

  <div class="hero-glitch-wrapper">
    <h1 class="hero-name">GOWTHAM MG</h1>
  </div>
  <p class="hero-tagline">Assistant Professor &nbsp;|&nbsp; AI/ML &nbsp;|&nbsp; Cybersecurity</p>
  <p class="hero-sub">MCA Graduate · PES College of Engineering · 7.95 CGPA</p>

  <div class="hero-badges">
    <span class="badge">SOC Analyst</span>
    <span class="badge red">Pen Tester</span>
    <span class="badge">ML / Deep Learning</span>
    <span class="badge red">Threat Intelligence</span>
    <span class="badge">Cloud & DevOps</span>
  </div>

  <div class="hero-cta">
    <a href="#projects" class="btn btn-primary">⚡ View Projects</a>
    <a href="#contact" class="btn btn-outline">📡 Contact</a>
  </div>
</section>

<!-- ABOUT -->
<section id="about">
  <div class="sec-header reveal">
    <p class="sec-label">// 01 — about</p>
    <h2 class="sec-title">WHO AM I?</h2>
    <div class="sec-line"></div>
  </div>

  <div class="about-grid">
    <div class="about-visual reveal">
      <div class="orbit" style="animation-duration:12s"><div class="orbit-dot"></div></div>
      <div class="orbit" style="animation-duration:18s;animation-direction:reverse"><div class="orbit-dot" style="background:var(--red);box-shadow:var(--glow-red)"></div></div>
      <div class="orbit" style="animation-duration:25s"><div class="orbit-dot" style="background:#ffd700;box-shadow:0 0 8px #ffd700"></div></div>
      <div class="about-avatar">🛡️</div>
      <div style="position:absolute;bottom:-60px;left:0;">
        <div class="stat-chip">📍 Mysore, Karnataka</div>
        <div class="stat-chip">🎓 MCA — 7.95 CGPA</div>
        <div class="stat-chip">👩‍🏫 100+ Students/Sem</div>
      </div>
    </div>

    <div class="about-text reveal">
      <h3>Building the Bridge Between <span class="highlight">AI</span> and <span class="highlight">Security</span></h3>
      <p>
        I'm an <span class="highlight">MCA postgraduate</span> and <span class="highlight">Assistant Professor</span> at ATME College of Engineering, Mysore. I'm passionate about understanding how cyber attacks work, dissecting threats, and engineering defenses that matter.
      </p>
      <p>
        My work sits at the intersection of <span class="highlight">Machine Learning</span> and <span class="highlight">Cybersecurity</span> — from anomaly detection models to AI-powered penetration testing toolkits. I believe the best defenders think like attackers.
      </p>
      <p>
        Currently levelling up through <span class="highlight">TryHackMe SOC Level 1</span> while concurrently teaching 100+ students and building real-world security tools.
      </p>

      <div class="info-grid">
        <div class="info-item"><div class="label">ROLE</div><div class="val">Assistant Professor</div></div>
        <div class="info-item"><div class="label">INSTITUTION</div><div class="val">ATME College, Mysore</div></div>
        <div class="info-item"><div class="label">DEGREE</div><div class="val">MCA — PES CoE, Mandya</div></div>
        <div class="info-item"><div class="label">FOCUS</div><div class="val">SOC · AI/ML · Pen Test</div></div>
        <div class="info-item"><div class="label">EMAIL</div><div class="val">mggowtham347@gmail.com</div></div>
        <div class="info-item"><div class="label">PHONE</div><div class="val">+91 9035724265</div></div>
      </div>
    </div>
  </div>
</section>

<!-- EXPERIENCE -->
<section id="experience">
  <div style="max-width:900px;margin:auto;padding:0 0 60px;">
    <div class="sec-header reveal">
      <p class="sec-label">// 02 — experience</p>
      <h2 class="sec-title">BATTLE LOG</h2>
      <div class="sec-line"></div>
    </div>

    <div class="exp-container">
      <div class="exp-card reveal">
        <div class="exp-line-col">
          <div class="exp-dot"></div>
          <div class="exp-vert-line"></div>
        </div>
        <div class="exp-body">
          <div class="exp-role">🎓 Assistant Professor</div>
          <div class="exp-org">ATME College of Engineering — Mysore, Karnataka</div>
          <div class="exp-date">[ 2025 — PRESENT ]</div>
          <ul class="exp-bullets">
            <li>Teaching <strong>100+ students per semester</strong> across core computer science subjects</li>
            <li>Concurrently upskilling in <strong>security monitoring, threat detection & incident response</strong></li>
            <li>Managing high-pressure, multi-task academic and technical responsibilities</li>
            <li>Bridging academic instruction with real-world cybersecurity and AI applications</li>
          </ul>
        </div>
      </div>
    </div>

    <!-- Education in timeline style -->
    <div class="sec-header reveal" style="margin-top:60px;margin-bottom:30px;">
      <p class="sec-label">// education</p>
      <h2 class="sec-title" style="font-size:1.6rem;">ACADEMIC RECORD</h2>
    </div>

    <div style="display:grid;grid-template-columns:1fr 1fr;gap:20px;" class="reveal">
      <div class="exp-body" style="margin:0;padding:24px;">
        <div class="project-tag">2023 — 2025</div>
        <div class="exp-org">Master of Computer Applications</div>
        <div style="color:var(--dim);font-family:'Share Tech Mono',monospace;font-size:.78rem;margin:4px 0 12px;">PES College of Engineering, Mandya</div>
        <div style="font-family:'Orbitron',monospace;font-size:1.6rem;color:var(--cyan);text-shadow:var(--glow-cyan);">7.95</div>
        <div style="font-family:'Share Tech Mono',monospace;font-size:.7rem;color:var(--dim);">CGPA / 10.0</div>
      </div>
      <div class="exp-body" style="margin:0;padding:24px;">
        <div class="project-tag">2018 — 2021</div>
        <div class="exp-org">B.Sc. Computer Science</div>
        <div style="color:var(--dim);font-family:'Share Tech Mono',monospace;font-size:.78rem;margin:4px 0 12px;">University of Mysore</div>
        <div style="font-family:'Orbitron',monospace;font-size:1.6rem;color:var(--cyan);text-shadow:var(--glow-cyan);">59.56</div>
        <div style="font-family:'Share Tech Mono',monospace;font-size:.7rem;color:var(--dim);">PERCENTAGE</div>
      </div>
    </div>
  </div>
</section>

<!-- SKILLS -->
<section id="skills">
  <div class="skills-container">
    <div class="sec-header reveal">
      <p class="sec-label">// 03 — skills</p>
      <h2 class="sec-title">TECH ARSENAL</h2>
      <div class="sec-line"></div>
    </div>

    <div class="skills-tabs reveal">
      <button class="tab-btn active" onclick="switchTab('cyber')">🔐 Cybersecurity</button>
      <button class="tab-btn" onclick="switchTab('ml')">🤖 ML / DL</button>
      <button class="tab-btn" onclick="switchTab('cloud')">☁️ Cloud & DevOps</button>
      <button class="tab-btn" onclick="switchTab('lang')">💻 Languages</button>
    </div>

    <div id="panel-cyber" class="skills-panel active">
      <div class="skill-card"><div class="skill-icon">🔍</div><div class="skill-name">Splunk SIEM</div><div class="skill-bar-wrap"><div class="skill-bar" style="--w:.85;transform:scaleX(.85)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">🦈</div><div class="skill-name">Wireshark</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.8)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">📡</div><div class="skill-name">Nmap</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.88)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">⚔️</div><div class="skill-name">Kali Linux</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.82)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">💥</div><div class="skill-name">Metasploit</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.75)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">🕷️</div><div class="skill-name">Burp Suite</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.78)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">🧱</div><div class="skill-name">Nessus</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.72)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">🎯</div><div class="skill-name">MITRE ATT&CK</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.8)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">🔎</div><div class="skill-name">OWASP ZAP</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.77)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">🛡️</div><div class="skill-name">IDS / IPS</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.73)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">📊</div><div class="skill-name">Log Analysis</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.85)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">⚠️</div><div class="skill-name">CVE Analysis</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.79)"></div></div></div>
    </div>

    <div id="panel-ml" class="skills-panel">
      <div class="skill-card"><div class="skill-icon">🐍</div><div class="skill-name">Python</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.92)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">🔥</div><div class="skill-name">PyTorch</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.8)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">🧠</div><div class="skill-name">TensorFlow</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.82)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">⚗️</div><div class="skill-name">Keras</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.85)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">📦</div><div class="skill-name">Scikit-learn</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.88)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">🤗</div><div class="skill-name">Hugging Face</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.75)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">📷</div><div class="skill-name">CNN / ResNet</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.82)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">🔄</div><div class="skill-name">LSTM / RNN</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.78)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">🎨</div><div class="skill-name">GANs</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.72)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">💬</div><div class="skill-name">LLM / RAG</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.76)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">📈</div><div class="skill-name">NLTK / SpaCy</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.79)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">🌐</div><div class="skill-name">Flask / API</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.83)"></div></div></div>
    </div>

    <div id="panel-cloud" class="skills-panel">
      <div class="skill-card"><div class="skill-icon">☁️</div><div class="skill-name">AWS (EC2/S3/IAM)</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.78)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">🔷</div><div class="skill-name">Microsoft Azure</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.75)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">🐳</div><div class="skill-name">Docker</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.8)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">⚙️</div><div class="skill-name">Kubernetes</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.72)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">🐧</div><div class="skill-name">Linux / Ubuntu</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.88)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">🔀</div><div class="skill-name">Git / GitHub</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.9)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">🖥️</div><div class="skill-name">PowerShell</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.76)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">📜</div><div class="skill-name">Bash Scripting</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.83)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">🗄️</div><div class="skill-name">Active Directory</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.73)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">🔑</div><div class="skill-name">Azure AD / IAM</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.75)"></div></div></div>
    </div>

    <div id="panel-lang" class="skills-panel">
      <div class="skill-card"><div class="skill-icon">🐍</div><div class="skill-name">Python</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.92)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">☕</div><div class="skill-name">Core Java</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.8)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">⚡</div><div class="skill-name">C</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.75)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">🗃️</div><div class="skill-name">SQL</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.83)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">🐚</div><div class="skill-name">Shell Scripting</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.82)"></div></div></div>
      <div class="skill-card"><div class="skill-icon">🔍</div><div class="skill-name">KQL</div><div class="skill-bar-wrap"><div class="skill-bar" style="transform:scaleX(.7)"></div></div></div>
    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects">
  <div class="projects-container">
    <div class="sec-header reveal">
      <p class="sec-label">// 04 — projects</p>
      <h2 class="sec-title">MISSION FILES</h2>
      <div class="sec-line"></div>
    </div>

    <div class="projects-grid">
      <div class="project-card reveal">
        <div class="project-num">01</div>
        <div class="project-tag">AI · Security · Automation</div>
        <h3 class="project-title">Generative AI for Ethical Hacking & Penetration Testing</h3>
        <p class="project-desc">AI-powered penetration testing toolkit integrating Nmap, SQLMap, and Gemini API to automate reconnaissance, vulnerability detection, and exploit suggestions. Auto-generates PDF security audit reports.</p>
        <div class="tech-tags">
          <span class="tech-tag">Python</span>
          <span class="tech-tag">Gemini API</span>
          <span class="tech-tag">Nmap</span>
          <span class="tech-tag">SQLMap</span>
          <span class="tech-tag">Flask</span>
        </div>
        <div class="project-links">
          <a href="https://github.com/GOWTHAMMG347" target="_blank" class="project-link">⚡ GitHub</a>
        </div>
      </div>

      <div class="project-card reveal">
        <div class="project-num">02</div>
        <div class="project-tag">ML · MLOps · Finance</div>
        <h3 class="project-title">Bank Note Authentication — Machine Learning (MLOps)</h3>
        <p class="project-desc">ML model distinguishing real vs counterfeit banknotes using features like Variance and Skewness extracted from scanned note images. Full MLOps pipeline with live demo deployed on Render.</p>
        <div class="tech-tags">
          <span class="tech-tag">NumPy</span>
          <span class="tech-tag">Scikit-learn</span>
          <span class="tech-tag">Pandas</span>
          <span class="tech-tag">Keras</span>
          <span class="tech-tag">Matplotlib</span>
        </div>
        <div class="project-links">
          <a href="https://github.com/GOWTHAMMG347/Bank-Note-Authentication" target="_blank" class="project-link">⚡ GitHub</a>
          <a href="https://bank-note-authentication-4taz.onrender.com/" target="_blank" class="project-link">🌐 Live Demo</a>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- CERTIFICATIONS -->
<section id="certifications">
  <div class="certs-container">
    <div class="sec-header reveal">
      <p class="sec-label">// 05 — certifications</p>
      <h2 class="sec-title">CLEARANCES</h2>
      <div class="sec-line"></div>
    </div>

    <div class="certs-grid reveal">
      <div class="cert-card">
        <span class="cert-icon">🔴</span>
        <div class="cert-name">TryHackMe SOC Level 1 Learning Path</div>
        <div class="cert-issuer">TryHackMe</div>
        <div class="cert-badge active">IN PROGRESS</div>
      </div>
      <div class="cert-card">
        <span class="cert-icon">☁️</span>
        <div class="cert-name">AWS IAM</div>
        <div class="cert-issuer">Amazon Web Services</div>
        <div class="cert-date">Jun 2023</div>
        <div class="cert-badge" style="background:rgba(255,165,0,.1);border-color:orange;color:orange;">ISSUED</div>
      </div>
      <div class="cert-card">
        <span class="cert-icon">⚙️</span>
        <div class="cert-name">DevOps</div>
        <div class="cert-issuer">JSPIDERS</div>
        <div class="cert-date">Jun 2023</div>
        <div class="cert-badge" style="background:rgba(255,165,0,.1);border-color:orange;color:orange;">ISSUED</div>
      </div>
      <div class="cert-card">
        <span class="cert-icon">☕</span>
        <div class="cert-name">Java Full Stack</div>
        <div class="cert-issuer">JSPIDERS</div>
        <div class="cert-date">Jun 2023</div>
        <div class="cert-badge" style="background:rgba(255,165,0,.1);border-color:orange;color:orange;">ISSUED</div>
      </div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="contact-container">
    <div class="sec-header reveal">
      <p class="sec-label">// 06 — contact</p>
      <h2 class="sec-title">OPEN CHANNEL</h2>
      <div class="sec-line"></div>
    </div>

    <div class="contact-grid">
      <div class="contact-info reveal">
        <h3>Let's Build Something Together</h3>
        <p>Whether you're interested in cybersecurity consulting, AI/ML collaborations, academic partnerships, or just want to talk tech — I'm reachable.</p>

        <div class="contact-links">
          <a href="mailto:mggowtham347@gmail.com" class="contact-link">
            <span class="icon">📧</span>
            <span class="detail"><span>EMAIL</span>mggowtham347@gmail.com</span>
          </a>
          <a href="tel:+919035724265" class="contact-link">
            <span class="icon">📱</span>
            <span class="detail"><span>PHONE</span>+91 9035724265</span>
          </a>
          <a href="https://linkedin.com/in/gowtham-m-g-7266aa325" target="_blank" class="contact-link">
            <span class="icon">💼</span>
            <span class="detail"><span>LINKEDIN</span>gowtham-m-g-7266aa325</span>
          </a>
          <a href="https://github.com/GOWTHAMMG347" target="_blank" class="contact-link">
            <span class="icon">🐙</span>
            <span class="detail"><span>GITHUB</span>GOWTHAMMG347</span>
          </a>
        </div>
      </div>

      <div class="terminal-box reveal">
        <div class="terminal-header">
          <div class="t-dot t-red"></div>
          <div class="t-dot t-yellow"></div>
          <div class="t-dot t-green"></div>
          <span style="font-family:'Share Tech Mono',monospace;font-size:.7rem;color:var(--dim);margin-left:8px;">gowtham@terminal ~ %</span>
        </div>
        <div class="terminal-body">
          <div><span class="t-prompt">$ </span><span class="t-cmd">whoami</span></div>
          <div class="t-out">gowtham_mg — Cybersecurity Analyst + AI Engineer</div>
          <br>
          <div><span class="t-prompt">$ </span><span class="t-cmd">cat skills.txt</span></div>
          <div class="t-out">[SOC] [SIEM] [Pen Testing] [ML/DL] [Cloud]</div>
          <br>
          <div><span class="t-prompt">$ </span><span class="t-cmd">ping linkedin.com</span></div>
          <div class="t-out">64 bytes from linkedin — Connection established ✓</div>
          <br>
          <div><span class="t-prompt">$ </span><span class="t-cmd">status --availability</span></div>
          <div class="t-out" style="color:var(--cyan);">✅ Open to collaborations & opportunities</div>
          <br>
          <div><span class="t-prompt">$ </span><span class="t-blink"></span></div>
        </div>
      </div>
    </div>
  </div>
</section>

<footer>
  <p>
    <span>GOWTHAM MG</span> &nbsp;·&nbsp;
    Built with ⚡ &nbsp;·&nbsp;
    <span>© 2025</span> &nbsp;·&nbsp;
    All systems operational
  </p>
</footer>

<script>
// ── CURSOR
const cursor = document.getElementById('cursor');
const ring = document.getElementById('cursor-ring');
document.addEventListener('mousemove', e => {
  cursor.style.left = e.clientX + 'px';
  cursor.style.top = e.clientY + 'px';
  setTimeout(() => {
    ring.style.left = e.clientX + 'px';
    ring.style.top = e.clientY + 'px';
  }, 80);
});
document.querySelectorAll('a,button').forEach(el => {
  el.addEventListener('mouseenter', () => { cursor.style.transform = 'translate(-50%,-50%) scale(2)'; ring.style.opacity = '1'; });
  el.addEventListener('mouseleave', () => { cursor.style.transform = 'translate(-50%,-50%) scale(1)'; ring.style.opacity = '.5'; });
});

// ── MATRIX RAIN
const canvas = document.getElementById('matrix-canvas');
const ctx = canvas.getContext('2d');
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;
window.addEventListener('resize', () => { canvas.width = window.innerWidth; canvas.height = window.innerHeight; });

const chars = '01アイウエオカキクケコサシスセソタチツテトナニヌネノ><[]{}|';
const cols = Math.floor(canvas.width / 18);
const drops = Array(cols).fill(1);

function drawMatrix() {
  ctx.fillStyle = 'rgba(2,12,20,.05)';
  ctx.fillRect(0, 0, canvas.width, canvas.height);
  ctx.fillStyle = '#00ffe7';
  ctx.font = '14px Share Tech Mono';
  drops.forEach((y, i) => {
    const c = chars[Math.floor(Math.random() * chars.length)];
    ctx.fillText(c, i * 18, y * 18);
    if (y * 18 > canvas.height && Math.random() > .975) drops[i] = 0;
    drops[i]++;
  });
}
setInterval(drawMatrix, 60);

// ── PARTICLES
const pCont = document.getElementById('particles');
for (let i = 0; i < 30; i++) {
  const p = document.createElement('div');
  p.className = 'particle';
  const size = Math.random() * 3 + 1;
  p.style.cssText = `
    left:${Math.random()*100}%;
    width:${size}px;height:${size}px;
    animation-duration:${Math.random()*15+8}s;
    animation-delay:-${Math.random()*15}s;
    opacity:.4;
  `;
  if (Math.random() > .7) p.style.background = '#ff2d55';
  pCont.appendChild(p);
}

// ── SKILL TABS
function switchTab(id) {
  document.querySelectorAll('.skills-panel').forEach(p => p.classList.remove('active'));
  document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
  document.getElementById('panel-' + id).classList.add('active');
  event.target.classList.add('active');
  // re-trigger bar animations
  document.querySelectorAll('#panel-' + id + ' .skill-bar').forEach(bar => {
    bar.style.animation = 'none';
    bar.offsetHeight;
    bar.style.animation = 'bar-fill 1.2s ease forwards .2s';
  });
}

// ── SCROLL REVEAL
const reveals = document.querySelectorAll('.reveal');
const observer = new IntersectionObserver(entries => {
  entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('visible'); } });
}, { threshold: 0.1 });
reveals.forEach(r => observer.observe(r));
</script>
</body>
</html>
