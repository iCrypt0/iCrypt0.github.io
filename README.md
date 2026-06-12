<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>chandler — cybersecurity & IT</title>
<meta name="description" content="IT student and cybersecurity enthusiast. Home lab builder running Proxmox, OPNsense, Wazuh SIEM.">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500;700&family=Inter:wght@400;500;600&display=swap" rel="stylesheet">
<style>
:root {
  --bg: #050a14;
  --bg-raise: #0a1322;
  --bg-card: #0d1726;
  --line: #16243a;
  --line-bright: #1f3553;
  --blue-100: #b5d4f4;
  --blue-200: #85b7eb;
  --blue-400: #378add;
  --blue-600: #185fa5;
  --blue-deep: #0c447c;
  --text: #c4d3e6;
  --text-dim: #6b7f99;
  --text-faint: #3d4f66;
  --mono: 'JetBrains Mono', monospace;
  --sans: 'Inter', sans-serif;
}
* { margin: 0; padding: 0; box-sizing: border-box; }
html { scroll-behavior: smooth; }
body {
  background: var(--bg);
  color: var(--text);
  font-family: var(--sans);
  font-size: 16px;
  line-height: 1.7;
  overflow-x: hidden;
}
::selection { background: var(--blue-deep); color: #fff; }
 
/* grid backdrop */
.gridlines {
  position: fixed; inset: 0; z-index: 0; pointer-events: none;
  background-image:
    linear-gradient(var(--line) 1px, transparent 1px),
    linear-gradient(90deg, var(--line) 1px, transparent 1px);
  background-size: 56px 56px;
  opacity: 0.35;
  mask-image: radial-gradient(ellipse 90% 70% at 50% 0%, black 0%, transparent 75%);
  -webkit-mask-image: radial-gradient(ellipse 90% 70% at 50% 0%, black 0%, transparent 75%);
}
 
main { position: relative; z-index: 1; max-width: 1060px; margin: 0 auto; padding: 0 24px; }
 
/* nav */
nav {
  display: flex; justify-content: space-between; align-items: center;
  padding: 28px 0; font-family: var(--mono); font-size: 13px;
}
nav .logo { color: var(--blue-400); font-weight: 700; letter-spacing: 0.05em; }
nav .logo span { color: var(--text-faint); }
nav .links a {
  color: var(--text-dim); text-decoration: none; margin-left: 28px;
  transition: color .2s;
}
nav .links a:hover { color: var(--blue-200); }
nav .links a::before { content: '/'; color: var(--text-faint); margin-right: 4px; }
 
/* hero */
.hero { padding: 64px 0 24px; }
.hero .kicker {
  font-family: var(--mono); font-size: 13px; color: var(--blue-400);
  letter-spacing: 0.12em; margin-bottom: 18px;
}
.hero .kicker::before { content: '> '; color: var(--text-faint); }
.hero h1 {
  font-size: clamp(34px, 6vw, 58px); font-weight: 600; color: #e8f0fa;
  line-height: 1.12; letter-spacing: -0.02em; max-width: 720px;
}
.hero h1 em { font-style: normal; color: var(--blue-400); }
.hero p.sub {
  margin-top: 22px; max-width: 600px; color: var(--text-dim); font-size: 17px;
}
.hero .cursor {
  display: inline-block; width: 3px; height: 1em; background: var(--blue-400);
  vertical-align: text-bottom; margin-left: 6px;
  animation: blink 1.1s steps(1) infinite;
}
@keyframes blink { 50% { opacity: 0; } }
 
/* lab topology — signature element */
.topo-wrap { padding: 40px 0 10px; }
.topo-label {
  font-family: var(--mono); font-size: 12px; color: var(--text-faint);
  letter-spacing: 0.14em; text-transform: uppercase; margin-bottom: 10px;
}
.topo-label b { color: var(--blue-400); font-weight: 500; }
.topo-label b::before {
  content: ''; display: inline-block; width: 7px; height: 7px; border-radius: 50%;
  background: #2ea843; margin-right: 7px;
  animation: pulse 2s ease-in-out infinite;
}
@keyframes pulse { 50% { opacity: 0.35; } }
.topo {
  border: 1px solid var(--line-bright); border-radius: 10px;
  background: var(--bg-raise); overflow: hidden;
}
.topo svg { display: block; width: 100%; height: auto; }
 
/* sections */
section { padding: 72px 0 8px; }
.sec-head {
  font-family: var(--mono); font-size: 14px; color: var(--blue-200);
  letter-spacing: 0.1em; margin-bottom: 30px; display: flex; align-items: center; gap: 14px;
}
.sec-head::before { content: attr(data-n); color: var(--text-faint); font-size: 12px; }
.sec-head::after { content: ''; flex: 1; height: 1px; background: var(--line-bright); }
 
/* about */
.about-grid { display: grid; grid-template-columns: 1.4fr 1fr; gap: 48px; }
.about-grid p { color: var(--text-dim); margin-bottom: 16px; }
.about-grid p strong { color: var(--text); font-weight: 500; }
.facts { font-family: var(--mono); font-size: 13px; }
.facts div {
  display: flex; justify-content: space-between; padding: 10px 0;
  border-bottom: 1px dashed var(--line-bright);
}
.facts .k { color: var(--text-faint); }
.facts .v { color: var(--blue-200); text-align: right; }
 
/* skills */
.skill-cols { display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 14px; }
.skill-card {
  background: var(--bg-card); border: 1px solid var(--line-bright);
  border-radius: 10px; padding: 20px 22px; transition: border-color .25s, transform .25s;
}
.skill-card:hover { border-color: var(--blue-600); transform: translateY(-2px); }
.skill-card h3 {
  font-family: var(--mono); font-size: 12px; font-weight: 500; color: var(--text-faint);
  text-transform: uppercase; letter-spacing: 0.12em; margin-bottom: 14px;
}
.skill-card ul { list-style: none; }
.skill-card li {
  font-size: 14px; color: var(--text); padding: 5px 0;
  display: flex; align-items: center; gap: 9px;
}
.skill-card li::before {
  content: ''; width: 5px; height: 5px; background: var(--blue-400);
  transform: rotate(45deg); flex-shrink: 0;
}
 
/* lab detail */
.lab-rows { display: flex; flex-direction: column; gap: 12px; }
.lab-row {
  display: grid; grid-template-columns: 170px 1fr auto; gap: 20px; align-items: center;
  background: var(--bg-card); border: 1px solid var(--line-bright);
  border-radius: 10px; padding: 18px 24px; transition: border-color .25s;
}
.lab-row:hover { border-color: var(--blue-600); }
.lab-row .name { font-family: var(--mono); font-size: 14px; color: var(--blue-200); font-weight: 500; }
.lab-row .desc { font-size: 14px; color: var(--text-dim); }
.lab-row .tag {
  font-family: var(--mono); font-size: 11px; color: var(--blue-400);
  border: 1px solid var(--blue-deep); border-radius: 4px; padding: 3px 9px;
  white-space: nowrap;
}
 
/* contact */
.contact-box {
  background: var(--bg-card); border: 1px solid var(--line-bright); border-radius: 12px;
  padding: 44px; text-align: center; margin-bottom: 40px;
}
.contact-box h2 { font-size: 26px; font-weight: 600; color: #e8f0fa; margin-bottom: 10px; }
.contact-box p { color: var(--text-dim); max-width: 460px; margin: 0 auto 28px; font-size: 15px; }
.contact-links { display: flex; gap: 14px; justify-content: center; flex-wrap: wrap; }
.contact-links a {
  font-family: var(--mono); font-size: 13px; text-decoration: none;
  color: var(--blue-200); border: 1px solid var(--blue-deep); border-radius: 7px;
  padding: 11px 22px; transition: background .2s, color .2s;
}
.contact-links a:hover { background: var(--blue-deep); color: #fff; }
 
footer {
  font-family: var(--mono); font-size: 12px; color: var(--text-faint);
  text-align: center; padding: 30px 0 40px;
}
 
@media (max-width: 760px) {
  .about-grid { grid-template-columns: 1fr; }
  .lab-row { grid-template-columns: 1fr; gap: 6px; }
  .lab-row .tag { justify-self: start; }
  nav .links a { margin-left: 16px; }
}
@media (prefers-reduced-motion: reduce) {
  .hero .cursor { animation: none; }
  .packet { display: none; }
  * { transition: none !important; }
}
</style>
</head>
<body>
<div class="gridlines"></div>
<main>
 
<nav>
  <div class="logo">iCrypt0<span>@homelab:~$</span></div>
  <div class="links">
    <a href="#about">about</a>
    <a href="#skills">skills</a>
    <a href="#lab">lab</a>
    <a href="#contact">contact</a>
  </div>
</nav>
 
<div class="hero">
  <div class="kicker">chandler — north georgia</div>
  <h1>i learn by <em>patterns</em> and <em>puzzles</em>.<br>cybersecurity is the best one yet.<span class="cursor"></span></h1>
  <p class="sub">IT student at Kennesaw State, A.S. in Cybersecurity from Lanier Tech. Always been the tech kid — fixing the router, picking the hacker class in every co-op game. Now I run a live home lab and break down problems for fun.</p>
</div>
 
<div class="topo-wrap">
  <div class="topo-label"><b>lab status: online</b> &nbsp;·&nbsp; live network topology</div>
  <div class="topo">
    <svg viewBox="0 0 1000 340" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Home lab network topology showing internet traffic flowing through OPNsense firewall to Proxmox host running Wazuh SIEM and a honeypot">
      <defs>
        <radialGradient id="nodeGlow" cx="50%" cy="50%" r="50%">
          <stop offset="0%" stop-color="#185fa5" stop-opacity="0.25"/>
          <stop offset="100%" stop-color="#185fa5" stop-opacity="0"/>
        </radialGradient>
      </defs>
 
      <path id="p1" d="M 120 170 L 330 170" stroke="#1f3553" stroke-width="2" fill="none"/>
      <path id="p2" d="M 430 170 L 600 170" stroke="#1f3553" stroke-width="2" fill="none"/>
      <path id="p3" d="M 700 170 Q 760 170 790 110 L 820 80" stroke="#1f3553" stroke-width="2" fill="none"/>
      <path id="p4" d="M 700 170 Q 760 170 790 230 L 820 260" stroke="#1f3553" stroke-width="2" fill="none"/>
 
      <circle cx="120" cy="170" r="70" fill="url(#nodeGlow)"/>
      <circle cx="120" cy="170" r="34" fill="#0a1322" stroke="#378add" stroke-width="1.5"/>
      <text x="120" y="175" text-anchor="middle" font-family="JetBrains Mono, monospace" font-size="13" fill="#85b7eb">WAN</text>
      <text x="120" y="232" text-anchor="middle" font-family="JetBrains Mono, monospace" font-size="11" fill="#6b7f99">internet</text>
 
      <rect x="330" y="130" width="100" height="80" rx="8" fill="#0d1726" stroke="#378add" stroke-width="1.5"/>
      <text x="380" y="165" text-anchor="middle" font-family="JetBrains Mono, monospace" font-size="13" fill="#b5d4f4">OPNsense</text>
      <text x="380" y="186" text-anchor="middle" font-family="JetBrains Mono, monospace" font-size="10" fill="#6b7f99">firewall</text>
 
      <rect x="600" y="120" width="100" height="100" rx="8" fill="#0d1726" stroke="#185fa5" stroke-width="1.5"/>
      <text x="650" y="160" text-anchor="middle" font-family="JetBrains Mono, monospace" font-size="13" fill="#b5d4f4">Proxmox</text>
      <text x="650" y="181" text-anchor="middle" font-family="JetBrains Mono, monospace" font-size="10" fill="#6b7f99">beelink host</text>
 
      <rect x="820" y="45" width="120" height="70" rx="8" fill="#0d1726" stroke="#185fa5" stroke-width="1.5"/>
      <text x="880" y="75" text-anchor="middle" font-family="JetBrains Mono, monospace" font-size="13" fill="#b5d4f4">Wazuh</text>
      <text x="880" y="96" text-anchor="middle" font-family="JetBrains Mono, monospace" font-size="10" fill="#6b7f99">SIEM</text>
 
      <rect x="820" y="225" width="120" height="70" rx="8" fill="#0d1726" stroke="#185fa5" stroke-width="1.5"/>
      <text x="880" y="255" text-anchor="middle" font-family="JetBrains Mono, monospace" font-size="13" fill="#b5d4f4">honeypot</text>
      <text x="880" y="276" text-anchor="middle" font-family="JetBrains Mono, monospace" font-size="10" fill="#6b7f99">threat intel</text>
 
      <circle class="packet" r="4" fill="#378add">
        <animateMotion dur="3s" repeatCount="indefinite"><mpath href="#p1"/></animateMotion>
      </circle>
      <circle class="packet" r="4" fill="#378add">
        <animateMotion dur="3s" begin="1s" repeatCount="indefinite"><mpath href="#p2"/></animateMotion>
      </circle>
      <circle class="packet" r="4" fill="#85b7eb">
        <animateMotion dur="2.5s" begin="0.5s" repeatCount="indefinite"><mpath href="#p3"/></animateMotion>
      </circle>
      <circle class="packet" r="4" fill="#85b7eb">
        <animateMotion dur="2.8s" begin="1.4s" repeatCount="indefinite"><mpath href="#p4"/></animateMotion>
      </circle>
    </svg>
  </div>
</div>
 
<section id="about">
  <div class="sec-head" data-n="01">about</div>
  <div class="about-grid">
    <div>
      <p>Always loved tech growing up — as a kid I was fixing the router, picking the hacker class in every co-op game, figuring out how things work just to see if I could and because it was fun.</p>
      <p>Now I'm studying <strong>IT at Kennesaw State</strong> after finishing an <strong>A.S. in Cybersecurity at Lanier Tech</strong>, working toward Security+ and building out a home lab that I treat like a production network.</p>
      <p>I learn by patterns and puzzles. Cybersecurity clicked because that's the whole job: figure out how the system works, find where it's weak, solve it.</p>
    </div>
    <div class="facts">
      <div><span class="k">degree</span><span class="v">B.A.S. IT — KSU</span></div>
      <div><span class="k">prior</span><span class="v">A.S. Cybersecurity</span></div>
      <div><span class="k">cert path</span><span class="v">Security+ (in progress)</span></div>
      <div><span class="k">practice</span><span class="v">TryHackMe / CTFs</span></div>
      <div><span class="k">grad target</span><span class="v">Fall 2027</span></div>
      <div><span class="k">location</span><span class="v">north georgia</span></div>
    </div>
  </div>
</section>
 
<section id="skills">
  <div class="sec-head" data-n="02">skills</div>
  <div class="skill-cols">
    <div class="skill-card">
      <h3>security</h3>
      <ul>
        <li>Wazuh SIEM</li>
        <li>honeypot deployment</li>
        <li>network segmentation</li>
        <li>TryHackMe labs</li>
      </ul>
    </div>
    <div class="skill-card">
      <h3>infrastructure</h3>
      <ul>
        <li>Proxmox VE</li>
        <li>OPNsense</li>
        <li>Linux administration</li>
        <li>VLANs + firewall rules</li>
      </ul>
    </div>
    <div class="skill-card">
      <h3>tools & code</h3>
      <ul>
        <li>Python</li>
        <li>Wireshark</li>
        <li>bash</li>
        <li>git / GitHub</li>
      </ul>
    </div>
  </div>
</section>
 
<section id="lab">
  <div class="sec-head" data-n="03">home lab</div>
  <div class="lab-rows">
    <div class="lab-row">
      <span class="name">beelink mini pc</span>
      <span class="desc">Bare metal Proxmox hypervisor hosting the entire lab as virtual machines</span>
      <span class="tag">hypervisor</span>
    </div>
    <div class="lab-row">
      <span class="name">opnsense</span>
      <span class="desc">Virtualized firewall handling routing, segmentation, and traffic filtering for the lab network</span>
      <span class="tag">firewall</span>
    </div>
    <div class="lab-row">
      <span class="name">wazuh</span>
      <span class="desc">SIEM collecting and correlating logs across the lab, alerting on suspicious activity</span>
      <span class="tag">siem</span>
    </div>
    <div class="lab-row">
      <span class="name">honeypot</span>
      <span class="desc">Live decoy capturing real-world attack attempts for analysis and threat intel practice</span>
      <span class="tag">deception</span>
    </div>
  </div>
</section>
 
<section id="contact">
  <div class="sec-head" data-n="04">contact</div>
  <div class="contact-box">
    <h2>let's connect</h2>
    <p>Open to help desk, SOC analyst, and IT support opportunities in the Metro Atlanta Area. Always down to talk home labs.</p>
    <div class="contact-links">
      <a href="https://github.com/iCrypt0" target="_blank" rel="noopener">github</a>
      <a href="https://www.linkedin.com/chandlerkirk" target="_blank" rel="noopener">linkedin</a>
    </div>
  </div>
</section>
 
<footer>iCrypt0 © 2026 · built from scratch, hosted on github pages</footer>
 
</main>
</body>
</html>
