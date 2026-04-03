<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Moksh Gala — Cybersecurity Portfolio</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=DM+Mono:wght@300;400&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  :root {
    --ink:   #07090d;
    --ink2:  #0d1117;
    --cream: #ddeeff;
    --cream2:#7a9ab8;
    --cyan:  #38bdf8;
    --cyan2: #00e5ff;
    --green: #22c55e;
    --rust:  #ef4444;
    --rule:  rgba(56,189,248,0.13);
    --rule2: rgba(56,189,248,0.05);
    --mono:  'DM Mono', monospace;
    --serif: 'Cormorant Garamond', Georgia, serif;
    --sans:  'Syne', sans-serif;
    --ease:  cubic-bezier(0.16,1,0.3,1);
  }
  html { scroll-behavior: smooth; }
  body { background: var(--ink); color: var(--cream); font-family: var(--serif); font-size: 18px; line-height: 1.6; overflow-x: hidden; }
 
  /* grid overlay */
  body::after { content:''; position:fixed; inset:0; background-image: linear-gradient(rgba(56,189,248,.025) 1px, transparent 1px), linear-gradient(90deg, rgba(56,189,248,.025) 1px, transparent 1px); background-size: 56px 56px; pointer-events:none; z-index:0; }
  /* grain */
  body::before { content:''; position:fixed; inset:0; background-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E"); pointer-events:none; z-index:9999; opacity:.2; }
 
  ::-webkit-scrollbar { width:3px; } ::-webkit-scrollbar-track { background:var(--ink); } ::-webkit-scrollbar-thumb { background:var(--cyan); }
  ::selection { background:var(--cyan); color:var(--ink); }
 
  /* NAV */
  nav { position:fixed; top:0; left:0; right:0; z-index:100; display:flex; align-items:center; justify-content:space-between; padding:1.4rem 3rem; border-bottom:1px solid var(--rule); backdrop-filter:blur(16px); background:rgba(7,9,13,.82); }
  .nav-logo { font-family:var(--sans); font-size:.72rem; font-weight:800; letter-spacing:.28em; text-transform:uppercase; color:var(--cyan); text-decoration:none; display:flex; align-items:center; gap:.6rem; }
  .pulse { width:7px; height:7px; border-radius:50%; background:var(--green); box-shadow:0 0 8px var(--green); animation:blink 2.2s ease-in-out infinite; }
  .nav-links { display:flex; gap:2.4rem; list-style:none; }
  .nav-links a { font-family:var(--mono); font-size:.64rem; letter-spacing:.1em; text-transform:uppercase; color:var(--cream2); text-decoration:none; transition:color .2s; position:relative; }
  .nav-links a::after { content:''; position:absolute; left:0; bottom:-3px; width:0; height:1px; background:var(--cyan); transition:width .3s var(--ease); }
  .nav-links a:hover { color:var(--cyan); } .nav-links a:hover::after { width:100%; }
 
  /* HERO */
  .hero { min-height:100vh; position:relative; z-index:1; display:flex; flex-direction:column; justify-content:flex-end; padding:8rem 3rem 5rem; border-bottom:1px solid var(--rule); overflow:hidden; }
  .glow { position:absolute; border-radius:50%; pointer-events:none; }
  .glow1 { width:700px; height:700px; top:10%; left:-15%; background:radial-gradient(circle, rgba(56,189,248,.055) 0%, transparent 70%); }
  .glow2 { width:400px; height:400px; bottom:5%; right:5%; background:radial-gradient(circle, rgba(0,229,255,.04) 0%, transparent 70%); }
  .hero-bg-text { position:absolute; right:-.05em; top:50%; transform:translateY(-50%); font-family:var(--sans); font-size:clamp(10rem,26vw,30rem); font-weight:800; color:rgba(56,189,248,.025); line-height:1; pointer-events:none; user-select:none; letter-spacing:-.05em; }
  .eyebrow { font-family:var(--mono); font-size:.68rem; letter-spacing:.28em; text-transform:uppercase; color:var(--cyan); margin-bottom:1.4rem; display:flex; align-items:center; gap:.75rem; opacity:0; transform:translateY(20px); animation:fadeUp .8s var(--ease) .2s forwards; }
  .eyebrow::before { content:''; display:inline-block; width:28px; height:1px; background:var(--cyan); }
  .hero-name { font-family:var(--sans); font-size:clamp(3rem,9vw,8rem); font-weight:800; line-height:.9; letter-spacing:-.03em; color:var(--cream); margin-bottom:.9rem; opacity:0; transform:translateY(30px); animation:fadeUp .9s var(--ease) .35s forwards; }
  .hero-name em { font-family:var(--serif); font-style:italic; font-weight:300; color:var(--cyan); }
  .hero-role { font-family:var(--serif); font-style:italic; font-size:clamp(1.1rem,2.2vw,1.75rem); color:var(--cream2); font-weight:300; margin-bottom:.9rem; opacity:0; transform:translateY(20px); animation:fadeUp .8s var(--ease) .5s forwards; }
  .hero-intro { max-width:620px; font-size:1rem; color:var(--cream2); font-weight:300; line-height:1.85; margin-bottom:2.8rem; opacity:0; transform:translateY(20px); animation:fadeUp .8s var(--ease) .62s forwards; }
  .hero-stats { display:flex; gap:2.8rem; align-items:center; flex-wrap:wrap; opacity:0; transform:translateY(20px); animation:fadeUp .8s var(--ease) .74s forwards; }
  .stat { display:flex; flex-direction:column; }
  .stat-num { font-family:var(--sans); font-size:1.8rem; font-weight:700; color:var(--cyan); line-height:1; }
  .stat-label { font-family:var(--mono); font-size:.59rem; letter-spacing:.15em; text-transform:uppercase; color:var(--cream2); margin-top:.25rem; }
  .vdiv { width:1px; height:2.8rem; background:var(--rule); }
  .hero-cta { display:flex; gap:1rem; margin-top:2.5rem; opacity:0; transform:translateY(20px); animation:fadeUp .8s var(--ease) .87s forwards; }
  .btn { font-family:var(--mono); font-size:.63rem; letter-spacing:.12em; text-transform:uppercase; padding:.72rem 1.4rem; border:1px solid var(--cyan); background:transparent; color:var(--cyan); cursor:pointer; text-decoration:none; transition:all .2s; display:inline-flex; align-items:center; gap:.5rem; }
  .btn:hover { background:var(--cyan); color:var(--ink); }
  .btn.ghost { border-color:var(--rule); color:var(--cream2); }
  .btn.ghost:hover { border-color:var(--cream2); color:var(--cream); background:transparent; }
  .scroll-ind { position:absolute; right:3rem; bottom:3rem; display:flex; flex-direction:column; align-items:center; gap:.5rem; opacity:0; animation:fadeUp 1s var(--ease) 1.1s forwards; }
  .scroll-ind span { font-family:var(--mono); font-size:.57rem; letter-spacing:.2em; text-transform:uppercase; color:var(--cream2); writing-mode:vertical-rl; }
  .scroll-line { width:1px; height:50px; background:linear-gradient(to bottom, var(--cyan), transparent); animation:scrollPulse 2s ease-in-out infinite; }
 
  /* SECTION COMMONS */
  section { padding:6rem 3rem; border-bottom:1px solid var(--rule); position:relative; z-index:1; }
  .sh { display:flex; align-items:baseline; gap:1.5rem; margin-bottom:4rem; }
  .snum { font-family:var(--mono); font-size:.63rem; color:var(--cyan); letter-spacing:.1em; }
  .stitle { font-family:var(--sans); font-size:clamp(1.6rem,3.5vw,2.4rem); font-weight:700; letter-spacing:-.02em; color:var(--cream); }
  .srule { flex:1; height:1px; background:var(--rule); }
 
  /* ABOUT */
  .about-grid { display:grid; grid-template-columns:1.2fr 1fr; gap:5rem; align-items:start; }
  .about-text p { font-size:1.08rem; line-height:1.9; color:var(--cream2); margin-bottom:1.4rem; font-weight:300; }
  .about-text p strong { color:var(--cream); font-weight:400; }
  .badge { display:inline-flex; align-items:center; gap:.5rem; font-family:var(--mono); font-size:.6rem; letter-spacing:.1em; padding:.38rem .9rem; border:1px solid rgba(34,197,94,.3); color:var(--green); background:rgba(34,197,94,.05); margin-bottom:1.5rem; }
  .badge::before { content:'●'; font-size:.48rem; animation:blink 2s infinite; }
  .aside { padding-left:2rem; border-left:1px solid var(--rule); }
  .aside-label { font-family:var(--mono); font-size:.58rem; letter-spacing:.2em; text-transform:uppercase; color:var(--cyan); margin-bottom:.9rem; }
  .tags { display:flex; flex-wrap:wrap; gap:.45rem; margin-bottom:1.8rem; }
  .tag { font-family:var(--mono); font-size:.6rem; padding:.28rem .65rem; border:1px solid var(--rule); color:var(--cream2); letter-spacing:.05em; transition:all .2s; cursor:default; }
  .tag:hover { border-color:var(--cyan); color:var(--cyan); background:rgba(56,189,248,.05); }
  .ilist { list-style:none; }
  .ilist li { display:flex; gap:1rem; align-items:flex-start; padding:.65rem 0; border-bottom:1px solid var(--rule); font-family:var(--mono); font-size:.66rem; }
  .ilist li span:first-child { min-width:22px; }
  .ilist li span:last-child { color:var(--cream2); }
 
  /* PROJECTS */
  .proj-grid { display:grid; grid-template-columns:repeat(auto-fill,minmax(380px,1fr)); gap:1px; background:var(--rule2); border:1px solid var(--rule2); }
  .proj-card { background:var(--ink); padding:2.5rem; position:relative; overflow:hidden; transition:background .3s; }
  .proj-card::after { content:''; position:absolute; top:0; right:0; width:80px; height:80px; background:radial-gradient(circle at top right, rgba(56,189,248,.07),transparent); opacity:0; transition:opacity .3s; }
  .proj-card:hover { background:var(--ink2); } .proj-card:hover::after { opacity:1; }
  .proj-num { font-family:var(--mono); font-size:2rem; font-weight:300; color:rgba(56,189,248,.14); line-height:1; margin-bottom:1rem; }
  .proj-title { font-family:var(--sans); font-size:1.15rem; font-weight:700; color:var(--cream); margin-bottom:.4rem; letter-spacing:-.02em; }
  .proj-sub { font-family:var(--mono); font-size:.58rem; letter-spacing:.16em; text-transform:uppercase; color:var(--cyan); margin-bottom:1.2rem; }
  .proj-desc { font-size:.9rem; color:var(--cream2); line-height:1.82; font-weight:300; margin-bottom:1.4rem; }
  .proj-feats { list-style:none; margin-bottom:1.4rem; }
  .proj-feats li { font-family:var(--mono); font-size:.63rem; color:var(--cream2); padding:.28rem 0; border-bottom:1px solid var(--rule2); display:flex; align-items:center; gap:.55rem; }
  .proj-feats li::before { content:'›'; color:var(--cyan); }
  .ptags { display:flex; flex-wrap:wrap; gap:.4rem; }
  .ptag { font-family:var(--mono); font-size:.54rem; padding:.18rem .55rem; border:1px solid rgba(56,189,248,.2); color:var(--cyan); letter-spacing:.07em; }
 
  /* TIMELINE */
  .timeline { position:relative; }
  .timeline::before { content:''; position:absolute; left:0; top:0; bottom:0; width:1px; background:var(--rule); }
  .titem { display:grid; grid-template-columns:155px 1fr; gap:2rem; padding-left:3rem; margin-bottom:3.5rem; position:relative; }
  .titem::before { content:''; position:absolute; left:-4px; top:.35rem; width:9px; height:9px; border:1px solid var(--cyan); background:var(--ink); transform:rotate(45deg); }
  .tyear { font-family:var(--mono); font-size:.62rem; letter-spacing:.1em; color:var(--cyan); padding-top:.2rem; }
  .ttitle { font-family:var(--sans); font-size:1rem; font-weight:600; color:var(--cream); margin-bottom:.2rem; }
  .torg { font-family:var(--mono); font-size:.6rem; color:var(--cream2); letter-spacing:.07em; margin-bottom:.7rem; }
  .tdesc { font-size:.9rem; color:var(--cream2); font-weight:300; line-height:1.76; }
 
  /* SKILLS */
  .skills-grid { display:grid; grid-template-columns:repeat(auto-fill,minmax(255px,1fr)); gap:1px; background:var(--rule2); border:1px solid var(--rule2); }
  .sgroup { background:var(--ink); padding:2rem; }
  .sgroup-title { font-family:var(--mono); font-size:.57rem; letter-spacing:.2em; text-transform:uppercase; color:var(--cyan); margin-bottom:1.4rem; }
  .sitem { margin-bottom:1.15rem; }
  .srow { display:flex; justify-content:space-between; margin-bottom:.38rem; }
  .sname { font-family:var(--serif); font-size:.93rem; color:var(--cream); font-weight:300; }
  .slevel { font-family:var(--mono); font-size:.57rem; color:var(--cream2); letter-spacing:.1em; }
  .sbar { height:1px; background:var(--rule); position:relative; overflow:hidden; }
  .sfill { position:absolute; left:0; top:0; bottom:0; background:linear-gradient(to right, var(--cyan), var(--cyan2)); width:0; transition:width 1.3s var(--ease); }
 
  /* TOOLS */
  .tools-row { display:flex; flex-wrap:wrap; gap:1px; background:var(--rule2); border:1px solid var(--rule2); margin-top:2.5rem; }
  .tool { background:var(--ink); padding:1.75rem 2rem; flex:1; min-width:140px; text-align:center; transition:background .2s; }
  .tool:hover { background:var(--ink2); }
  .tool-icon { font-size:1.6rem; margin-bottom:.65rem; display:block; }
  .tool-name { font-family:var(--mono); font-size:.62rem; letter-spacing:.1em; text-transform:uppercase; color:var(--cream2); }
 
  /* CERTS */
  .certs-grid { display:grid; grid-template-columns:repeat(auto-fill,minmax(260px,1fr)); gap:1px; background:var(--rule2); border:1px solid var(--rule2); }
  .cert-card { background:var(--ink); padding:1.6rem 2rem; display:flex; align-items:center; gap:1.1rem; transition:background .25s; position:relative; overflow:hidden; }
  .cert-card::after { content:''; position:absolute; left:0; top:0; bottom:0; width:2px; background:var(--rule); transition:background .25s; }
  .cert-card:hover { background:var(--ink2); }
  .cert-card:hover::after { background:var(--cyan); }
  .cert-card.cert-featured::after { background: linear-gradient(to bottom, var(--cyan), var(--cyan2)); }
  .cert-card.cert-featured { background:rgba(56,189,248,.03); }
  .cert-icon { font-size:1.4rem; flex-shrink:0; }
  .cert-title { font-family:var(--sans); font-size:.82rem; font-weight:600; color:var(--cream); letter-spacing:-.01em; line-height:1.3; margin-bottom:.25rem; }
  .cert-issuer { font-family:var(--mono); font-size:.56rem; letter-spacing:.12em; text-transform:uppercase; color:var(--cyan); }
 
  /* CONTACT */
  .ccta { font-family:var(--serif); font-size:clamp(1.8rem,3.8vw,3.1rem); font-weight:300; line-height:1.2; color:var(--cream); margin-bottom:2rem; }
  .ccta em { font-style:italic; color:var(--cyan); }
  .clinks { list-style:none; }
  .clinks li { display:flex; align-items:flex-start; gap:1rem; padding:.9rem 0; border-bottom:1px solid var(--rule); }
  .clabel { font-family:var(--mono); font-size:.57rem; letter-spacing:.15em; text-transform:uppercase; color:var(--cyan); min-width:78px; padding-top:.1rem; }
  .clinks a { font-family:var(--serif); font-size:.93rem; color:var(--cream); text-decoration:none; font-weight:300; transition:color .2s; word-break:break-all; }
  .clinks a:hover { color:var(--cyan); }
  .cval { font-family:var(--serif); font-size:.93rem; color:var(--cream2); font-weight:300; }
 
  /* TOAST */
  .toast { position:fixed; bottom:2rem; right:2rem; font-family:var(--mono); font-size:.6rem; letter-spacing:.1em; padding:.7rem 1.4rem; background:var(--cyan); color:var(--ink); z-index:9998; transform:translateY(70px); opacity:0; transition:all .4s var(--ease); }
  .toast.show { transform:translateY(0); opacity:1; }
 
  /* FOOTER */
  footer { padding:2.5rem 3rem; display:flex; justify-content:space-between; align-items:center; flex-wrap:wrap; gap:1rem; position:relative; z-index:1; }
  .fcopy { font-family:var(--mono); font-size:.57rem; letter-spacing:.1em; color:var(--cream2); }
 
  /* ANIMATIONS */
  @keyframes fadeUp { to { opacity:1; transform:translateY(0); } }
  @keyframes scrollPulse { 0%,100%{opacity:.4;} 50%{opacity:1;} }
  @keyframes blink { 0%,100%{opacity:1;} 50%{opacity:.25;} }
  .reveal { opacity:0; transform:translateY(22px); transition:opacity .7s var(--ease), transform .7s var(--ease); }
  .reveal.visible { opacity:1; transform:translateY(0); }
 
  @media (max-width:768px) {
    nav { padding:1.2rem 1.5rem; } .nav-links { gap:1.4rem; }
    section { padding:4rem 1.5rem; } .hero { padding:7rem 1.5rem 4rem; }
    .about-grid { grid-template-columns:1fr; gap:3rem; }
    .titem { grid-template-columns:1fr; gap:.2rem; }
    footer { padding:2rem 1.5rem; } .proj-grid { grid-template-columns:1fr; }
  }
  @media (max-width:500px) { .nav-links { display:none; } }
</style>
</head>
<body>
 
<!-- NAV -->
<nav>
  <a class="nav-logo" href="#"><span class="pulse"></span>Moksh Gala</a>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>
 
<!-- HERO -->
<section class="hero" id="home">
  <div class="glow glow1"></div>
  <div class="glow glow2"></div>
  <div class="hero-bg-text">SEC</div>
  <p class="eyebrow">Cybersecurity Portfolio</p>
  <h1 class="hero-name">Moksh<br><em>Gala</em></h1>
  <p class="hero-role">Cybersecurity Enthusiast &amp; Ethical Hacker</p>
  <p class="hero-intro">Passionate about identifying vulnerabilities, securing systems, and learning ethical hacking techniques. Skilled in programming and web technologies with a focus on building and protecting secure digital applications.</p>
  <div class="hero-stats">
    <div class="stat"><span class="stat-num">2</span><span class="stat-label">Projects</span></div>
    <div class="vdiv"></div>
    <div class="stat"><span class="stat-num">2024</span><span class="stat-label">Batch</span></div>
  </div>
  <div class="hero-cta">
    <a class="btn" href="mailto:mokshgala.ijs009@gmail.com">Get In Touch</a>
    <a class="btn ghost" href="https://github.com/MokshGlala01" target="_blank">GitHub ↗</a>
    <a class="btn ghost" href="https://www.linkedin.com/in/moksh-gala-b12684319" target="_blank">LinkedIn ↗</a>
  </div>
  <div class="scroll-ind"><div class="scroll-line"></div><span>Scroll</span></div>
</section>
 
<!-- ABOUT -->
<section id="about">
  <div class="sh reveal"><span class="snum">01 /</span><h2 class="stitle">About</h2><div class="srule"></div></div>
  <div class="about-grid">
    <div class="about-text reveal">
      <div class="badge">Currently Enrolled — BTech CSE 2024–2028</div>
      <p>I'm a <strong>BTech Computer Science &amp; Engineering</strong> student at SVKM's Shri Bhagubhai Mafatlal Polytechnic and College of Engineering, Mumbai — driven by a passion for making digital systems more secure.</p>
      <p>As a <strong>cybersecurity engineer and ethical hacker</strong>, I hunt vulnerabilities to build safer systems. I study attack vectors, exploitation techniques, and defensive architectures to bridge the gap between breaking and protecting.</p>
      <p>My programming toolkit spans from low-level <strong>C / C++</strong> systems work to web technologies and Python scripting, giving me a full-stack view of where software can — and must — be hardened.</p>
    </div>
    <div class="aside reveal" style="transition-delay:.1s">
      <p class="aside-label">Education</p>
      <ul class="ilist" style="margin-bottom:1.8rem">
        <li><span>🎓</span><span>BTech CSE — SVKM's Shri Bhagubhai Mafatlal Polytechnic &amp; College of Engineering</span></li>
        <li><span>📅</span><span>2024 – 2028</span></li>
        <li><span>📍</span><span>Mumbai, Maharashtra</span></li>
        <li><span>🔒</span><span>Focus: Cybersecurity &amp; Ethical Hacking</span></li>
      </ul>
      <p class="aside-label">Interests</p>
      <div class="tags">
        <span class="tag">Ethical Hacking</span><span class="tag">Penetration Testing</span>
        <span class="tag">Blockchain</span><span class="tag">CTF Challenges</span>
        <span class="tag">Secure Coding</span><span class="tag">Open Source</span>
      </div>
    </div>
  </div>
</section>
 
<!-- PROJECTS -->
<section id="projects">
  <div class="sh reveal"><span class="snum">02 /</span><h2 class="stitle">Projects</h2><div class="srule"></div></div>
  <div class="proj-grid">
    <div class="proj-card reveal">
      <div class="proj-num">01</div>
      <div class="proj-title">2048 Game</div>
      <div class="proj-sub">Academic Project — Jan 2025</div>
      <p class="proj-desc">A terminal-based implementation of the classic 2048 puzzle game written entirely in C. Move the tiles, combine them, and try to reach 2048 — no external dependencies required.</p>
      <ul class="proj-feats">
        <li>Pure C implementation — no external libraries</li>
        <li>Fully playable in the terminal / CLI</li>
        <li>Arrow-key movement support</li>
        <li>Real-time score tracking</li>
        <li>Compact, beginner-friendly codebase</li>
      </ul>
      <div class="ptags"><span class="ptag">C</span><span class="ptag">Terminal</span><span class="ptag">ncurses</span><span class="ptag">Academic</span></div>
    </div>
    <div class="proj-card reveal" style="transition-delay:.1s">
      <div class="proj-num">02</div>
      <div class="proj-title">SecureLand</div>
      <div class="proj-sub">SIH Hackathon — Oct 2025</div>
      <p class="proj-desc">A blockchain-powered land registry prototype with robust identity verification. Only verified individuals can register property on-chain, solving trust and fraud issues in traditional property registration systems.</p>
      <ul class="proj-feats">
        <li>Blockchain-backed immutable property records</li>
        <li>Identity verification module</li>
        <li>Prevents fraudulent property registrations</li>
        <li>Transparent, auditable transaction history</li>
        <li>Built for Smart India Hackathon (SIH)</li>
      </ul>
      <div class="ptags"><span class="ptag">Blockchain</span><span class="ptag">Smart Contracts</span><span class="ptag">Identity Verification</span><span class="ptag">SIH</span><span class="ptag">Web3</span></div>
    </div>
  </div>
</section>
 
<!-- JOURNEY -->
<section id="journey">
  <div class="sh reveal"><span class="snum">03 /</span><h2 class="stitle">Journey</h2><div class="srule"></div></div>
  <div class="timeline" id="timeline"></div>
</section>
 
<!-- SKILLS -->
<section id="skills">
  <div class="sh reveal"><span class="snum">04 /</span><h2 class="stitle">Skills &amp; Tools</h2><div class="srule"></div></div>
  <div class="skills-grid" id="skills-grid"></div>
  <div class="tools-row reveal" style="transition-delay:.2s">
    <div class="tool"><span class="tool-icon">💻</span><span class="tool-name">VS Code</span></div>
    <div class="tool"><span class="tool-icon">🐙</span><span class="tool-name">GitHub</span></div>
    <div class="tool"><span class="tool-icon">🎨</span><span class="tool-name">Figma</span></div>
    <div class="tool"><span class="tool-icon">🐧</span><span class="tool-name">Linux</span></div>
  </div>
 
  <!-- CERTIFICATES -->
  <div class="sh" style="margin-top:3.5rem; margin-bottom:2rem;">
    <span class="snum" style="font-family:var(--mono);font-size:.63rem;color:var(--cyan);letter-spacing:.1em;">Certificates /</span>
    <div class="srule"></div>
  </div>
  <div class="certs-grid reveal" style="transition-delay:.15s">
    <div class="cert-card">
      <div class="cert-icon">🏅</div>
      <div class="cert-body">
        <div class="cert-title">C Programming Language</div>
        <div class="cert-issuer">Programming Certificate</div>
      </div>
    </div>
    <div class="cert-card">
      <div class="cert-icon">🏅</div>
      <div class="cert-body">
        <div class="cert-title">C++ &amp; DSA</div>
        <div class="cert-issuer">Programming Certificate</div>
      </div>
    </div>
    <div class="cert-card">
      <div class="cert-icon">🏅</div>
      <div class="cert-body">
        <div class="cert-title">Python Programming Language</div>
        <div class="cert-issuer">Programming Certificate</div>
      </div>
    </div>
    <div class="cert-card">
      <div class="cert-icon">🏅</div>
      <div class="cert-body">
        <div class="cert-title">Java</div>
        <div class="cert-issuer">Programming Certificate</div>
      </div>
    </div>
    <div class="cert-card">
      <div class="cert-icon">🏅</div>
      <div class="cert-body">
        <div class="cert-title">JavaScript</div>
        <div class="cert-issuer">Programming Certificate</div>
      </div>
    </div>
    <div class="cert-card">
      <div class="cert-icon">🏅</div>
      <div class="cert-body">
        <div class="cert-title">HTML</div>
        <div class="cert-issuer">Web Technology Certificate</div>
      </div>
    </div>
    <div class="cert-card">
      <div class="cert-icon">🏅</div>
      <div class="cert-body">
        <div class="cert-title">CSS</div>
        <div class="cert-issuer">Web Technology Certificate</div>
      </div>
    </div>
    <div class="cert-card cert-featured">
      <div class="cert-icon">🔷</div>
      <div class="cert-body">
        <div class="cert-title">Career Essentials in Cybersecurity</div>
        <div class="cert-issuer">Microsoft &amp; LinkedIn</div>
      </div>
    </div>
    <div class="cert-card cert-featured">
      <div class="cert-icon">🔷</div>
      <div class="cert-body">
        <div class="cert-title">The Cybersecurity Threat Landscape</div>
        <div class="cert-issuer">Cybersecurity Certificate</div>
      </div>
    </div>
    <div class="cert-card cert-featured">
      <div class="cert-icon">🔷</div>
      <div class="cert-body">
        <div class="cert-title">Cybersecurity Awareness: Cybersecurity Terminology</div>
        <div class="cert-issuer">Cybersecurity Certificate</div>
      </div>
    </div>
  </div>
</section>
 
<!-- CONTACT -->
<section id="contact">
  <div class="sh reveal"><span class="snum">05 /</span><h2 class="stitle">Contact</h2><div class="srule"></div></div>
  <div class="reveal">
    <p class="ccta">Let's build something <em>secure</em> together.</p>
    <ul class="clinks">
      <li><span class="clabel">Email</span><a href="mailto:mokshgala.ijs009@gmail.com">mokshgala.ijs009@gmail.com</a></li>
      <li><span class="clabel">Phone</span><span class="cval">+91 9967238191</span></li>
      <li><span class="clabel">GitHub</span><a href="https://github.com/MokshGlala01" target="_blank">github.com/MokshGlala01</a></li>
      <li><span class="clabel">LinkedIn</span><a href="https://www.linkedin.com/in/moksh-gala-b12684319" target="_blank">linkedin.com/in/moksh-gala-b12684319</a></li>
      <li><span class="clabel">Location</span><span class="cval">Mumbai, Maharashtra, India</span></li>
    </ul>
  </div>
</section>
 
<!-- FOOTER -->
<footer>
  <span class="fcopy">© 2025 Moksh Gala — Cybersecurity Portfolio</span>
  <span class="fcopy">Mumbai, Maharashtra · BTech CSE 2024–2028</span>
</footer>
 
<div class="toast" id="toast"></div>
 
<script>
const timelineData = [
  { year:'2024 — Now', title:'BTech Computer Science & Engineering', org:"SVKM's Shri Bhagubhai Mafatlal Polytechnic & College of Engineering, Mumbai", desc:'Pursuing a 4-year BTech in CSE with a strong focus on cybersecurity, ethical hacking, blockchain, and secure systems development.' },
  { year:'Oct 2025', title:'SecureLand — Smart India Hackathon', org:'SIH Hackathon Project', desc:'Developed a blockchain-based land registry prototype with a robust identity verification module to eliminate fraud in property registration systems.' },
  { year:'Jan 2025', title:'2048 Game — C Programming', org:'Academic Project', desc:'Built a terminal-based 2048 puzzle game in pure C, demonstrating proficiency in data structures, terminal I/O, and algorithmic thinking.' }
];
const skillsData = [
  { group:'Programming Languages', skills:[{name:'C / C++',pct:80},{name:'Python',pct:75},{name:'Java',pct:70},{name:'DSA',pct:72}] },
  { group:'Web Technologies', skills:[{name:'HTML',pct:85},{name:'CSS',pct:82},{name:'JavaScript',pct:78},{name:'Blockchain/Web3',pct:60}] },
  { group:'Cybersecurity', skills:[{name:'Ethical Hacking',pct:70},{name:'Network Security',pct:65},{name:'Vulnerability Analysis',pct:68},{name:'Secure Coding',pct:72}] },
  { group:'Tools & Platforms', skills:[{name:'GitHub / Git',pct:80},{name:'VS Code',pct:90},{name:'Figma',pct:65},{name:'Linux',pct:70}] }
];
 
/* ── RENDER TIMELINE ── */
function renderTimeline(){
  document.getElementById('timeline').innerHTML=timelineData.map((item,i)=>`
    <div class="titem reveal" style="transition-delay:${i*.1}s">
      <div class="tyear">${item.year}</div>
      <div><div class="ttitle">${item.title}</div><div class="torg">${item.org}</div><div class="tdesc">${item.desc}</div></div>
    </div>`).join('');
}
 
/* ── RENDER SKILLS ── */
function renderSkills(){
  document.getElementById('skills-grid').innerHTML=skillsData.map(g=>`
    <div class="sgroup reveal">
      <div class="sgroup-title">${g.group}</div>
      ${g.skills.map(s=>`<div class="sitem"><div class="srow"><span class="sname">${s.name}</span><span class="slevel">${s.pct}%</span></div><div class="sbar"><div class="sfill" data-pct="${s.pct}"></div></div></div>`).join('')}
    </div>`).join('');
}
 
/* ── TOAST ── */
function showToast(msg){ const t=document.getElementById('toast'); t.textContent=msg; t.classList.add('show'); setTimeout(()=>t.classList.remove('show'),2800); }
 
/* ── SCROLL REVEAL ── */
const io=new IntersectionObserver(entries=>{
  entries.forEach(e=>{ if(e.isIntersecting){ e.target.classList.add('visible'); e.target.querySelectorAll('.sfill').forEach(b=>{b.style.width=b.dataset.pct+'%';}); io.unobserve(e.target); } });
},{threshold:.07});
function observe(){ document.querySelectorAll('.reveal').forEach(el=>io.observe(el)); }
 
/* ── INIT ── */
renderTimeline(); renderSkills(); observe();
</script>
</body>
</html>
