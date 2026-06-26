<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Ethical Hacking Portfolio — MKKarim</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Inter:wght@300;400;600;700&display=swap');

  :root {
    --bg:       #0a0e14;
    --surface:  #111720;
    --border:   #1e2d3d;
    --green:    #00ff88;
    --cyan:     #00c8ff;
    --red:      #ff4d6d;
    --orange:   #ff9900;
    --text:     #c9d1d9;
    --muted:    #5a6a7a;
    --mono:     'Share Tech Mono', monospace;
    --sans:     'Inter', sans-serif;
  }

  * { margin:0; padding:0; box-sizing:border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--sans);
    font-size: 15px;
    line-height: 1.7;
  }

  /* ── SCANLINE overlay ── */
  body::before {
    content:'';
    position:fixed; inset:0;
    background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(0,255,136,0.015) 2px,
      rgba(0,255,136,0.015) 4px
    );
    pointer-events:none;
    z-index:999;
  }

  a { color: var(--cyan); text-decoration:none; }

  /* ── HEADER ── */
  header {
    border-bottom: 1px solid var(--border);
    padding: 28px 40px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    position: sticky; top:0;
    background: rgba(10,14,20,0.92);
    backdrop-filter: blur(8px);
    z-index: 100;
  }
  .logo {
    font-family: var(--mono);
    font-size: 18px;
    color: var(--green);
    letter-spacing: 2px;
  }
  .logo span { color: var(--cyan); }
  nav { display:flex; gap:28px; }
  nav a {
    font-size:13px;
    color: var(--muted);
    letter-spacing:1px;
    text-transform: uppercase;
    transition: color .2s;
  }
  nav a:hover { color: var(--green); }

  /* ── HERO ── */
  .hero {
    padding: 90px 40px 70px;
    max-width: 860px;
    margin: 0 auto;
  }
  .eyebrow {
    font-family: var(--mono);
    font-size: 12px;
    color: var(--green);
    letter-spacing: 3px;
    text-transform: uppercase;
    margin-bottom: 18px;
  }
  .eyebrow::before { content: '> '; }
  h1 {
    font-size: clamp(32px, 5vw, 52px);
    font-weight: 700;
    line-height: 1.15;
    color: #e6edf3;
    margin-bottom: 20px;
  }
  h1 em {
    font-style: normal;
    color: var(--green);
  }
  .hero-sub {
    font-size: 17px;
    color: var(--muted);
    max-width: 560px;
    margin-bottom: 36px;
  }
  .badges {
    display: flex;
    gap: 10px;
    flex-wrap: wrap;
  }
  .badge {
    font-family: var(--mono);
    font-size: 12px;
    padding: 5px 14px;
    border-radius: 3px;
    border: 1px solid;
  }
  .badge.g { color: var(--green); border-color: var(--green); background: rgba(0,255,136,.06); }
  .badge.c { color: var(--cyan);  border-color: var(--cyan);  background: rgba(0,200,255,.06); }
  .badge.o { color: var(--orange);border-color: var(--orange);background: rgba(255,153,0,.06); }

  /* ── SECTION WRAPPER ── */
  section {
    max-width: 900px;
    margin: 0 auto;
    padding: 60px 40px;
    border-top: 1px solid var(--border);
  }
  .sec-label {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 3px;
    text-transform: uppercase;
    margin-bottom: 8px;
  }
  h2 {
    font-size: 26px;
    font-weight: 700;
    color: #e6edf3;
    margin-bottom: 32px;
  }

  /* ── CASE STUDY CARDS ── */
  .cards { display: grid; gap: 20px; }
  .card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 28px 30px;
    transition: border-color .25s, transform .2s;
    position: relative;
    overflow: hidden;
  }
  .card::before {
    content:'';
    position:absolute; top:0; left:0;
    width:3px; height:100%;
    background: var(--green);
  }
  .card.red::before  { background: var(--red); }
  .card.cyan::before { background: var(--cyan); }
  .card.orange::before { background: var(--orange); }
  .card:hover { border-color: var(--green); transform: translateY(-2px); }
  .card.red:hover  { border-color: var(--red); }
  .card.cyan:hover { border-color: var(--cyan); }

  .card-head {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    margin-bottom: 12px;
    flex-wrap: wrap;
    gap: 8px;
  }
  .card-title {
    font-size: 17px;
    font-weight: 600;
    color: #e6edf3;
  }
  .sev {
    font-family: var(--mono);
    font-size: 11px;
    padding: 3px 10px;
    border-radius: 2px;
    font-weight: 600;
    letter-spacing: 1px;
  }
  .sev.critical { background: rgba(255,77,109,.15); color: var(--red); border:1px solid var(--red); }
  .sev.high     { background: rgba(255,153,0,.12);  color: var(--orange); border:1px solid var(--orange); }
  .sev.medium   { background: rgba(0,200,255,.1);   color: var(--cyan); border:1px solid var(--cyan); }

  .card p { color: var(--muted); font-size:14px; margin-bottom:14px; }

  .findings {
    display: flex; gap: 8px; flex-wrap: wrap;
    margin-bottom: 14px;
  }
  .tag {
    font-family: var(--mono);
    font-size: 11px;
    padding: 3px 9px;
    background: rgba(255,255,255,.04);
    border: 1px solid var(--border);
    border-radius: 3px;
    color: var(--muted);
  }

  .tools-used {
    font-family: var(--mono);
    font-size: 12px;
    color: var(--green);
  }
  .tools-used span { color: var(--muted); }

  /* ── TERMINAL BLOCK ── */
  .terminal {
    background: #070b10;
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 20px 24px;
    font-family: var(--mono);
    font-size: 13px;
    line-height: 1.9;
    margin-top: 16px;
    overflow-x: auto;
  }
  .terminal .prompt { color: var(--green); }
  .terminal .cmd    { color: #e6edf3; }
  .terminal .out    { color: var(--muted); }
  .terminal .vuln   { color: var(--red); }
  .terminal .ok     { color: var(--green); }
  .terminal .info   { color: var(--cyan); }

  /* ── SKILLS GRID ── */
  .skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 16px;
  }
  .skill-box {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 20px;
  }
  .skill-box h4 {
    font-size: 13px;
    font-weight: 600;
    color: #e6edf3;
    margin-bottom: 10px;
  }
  .bar-wrap { background: #1a2535; border-radius: 2px; height:4px; margin-bottom:6px; }
  .bar { height:4px; border-radius:2px; background: var(--green); }
  .bar.c { background: var(--cyan); }
  .bar.o { background: var(--orange); }
  .skill-label { display:flex; justify-content:space-between; font-size:12px; color:var(--muted); font-family:var(--mono); }

  /* ── REPORT PREVIEW ── */
  .report-box {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 30px;
  }
  .report-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 24px;
    padding-bottom: 16px;
    border-bottom: 1px solid var(--border);
    flex-wrap: wrap; gap:12px;
  }
  .report-title { font-size:18px; font-weight:700; color:#e6edf3; }
  .report-meta  { font-family:var(--mono); font-size:12px; color:var(--muted); line-height:1.8; }
  .vuln-table   { width:100%; border-collapse:collapse; margin-top:8px; }
  .vuln-table th {
    font-family: var(--mono);
    font-size: 11px;
    text-align:left;
    color:var(--muted);
    letter-spacing:1px;
    padding: 8px 12px;
    border-bottom:1px solid var(--border);
    text-transform:uppercase;
  }
  .vuln-table td {
    padding: 10px 12px;
    font-size: 13px;
    border-bottom: 1px solid rgba(30,45,61,.5);
    vertical-align: middle;
  }
  .vuln-table tr:last-child td { border-bottom:none; }
  .cvss {
    font-family: var(--mono);
    font-size:12px;
    padding:2px 8px;
    border-radius:3px;
  }
  .cvss.c { background:rgba(255,77,109,.15); color:var(--red); }
  .cvss.h { background:rgba(255,153,0,.12);  color:var(--orange); }
  .cvss.m { background:rgba(0,200,255,.1);   color:var(--cyan); }

  /* ── CTA ── */
  .cta-section {
    text-align: center;
    padding: 80px 40px;
    border-top: 1px solid var(--border);
    max-width:900px;
    margin:0 auto;
  }
  .cta-section h2 { margin-bottom:12px; }
  .cta-section p  { color:var(--muted); margin-bottom:32px; max-width:480px; margin-left:auto; margin-right:auto; }
  .btn {
    display: inline-block;
    padding: 13px 34px;
    border-radius: 4px;
    font-weight: 600;
    font-size: 14px;
    cursor: pointer;
    border: none;
    transition: opacity .2s, transform .15s;
  }
  .btn:hover { opacity:.85; transform:translateY(-1px); }
  .btn.primary { background: var(--green); color: #0a0e14; }
  .btn.outline { border:1px solid var(--border); background:transparent; color:var(--text); margin-left:12px; }

  /* ── FOOTER ── */
  footer {
    text-align:center;
    padding: 28px 40px;
    border-top: 1px solid var(--border);
    font-family: var(--mono);
    font-size: 12px;
    color: var(--muted);
  }

  @media(max-width:600px){
    header { padding:18px 20px; flex-direction:column; gap:14px; }
    .hero, section { padding-left:20px; padding-right:20px; }
    nav { gap:16px; }
  }
</style>
</head>
<body>

<!-- HEADER -->
<header>
  <div class="logo">MK<span>Karim</span>.sec</div>
  <nav>
    <a href="#projects">Projects</a>
    <a href="#skills">Skills</a>
    <a href="#report">Sample Report</a>
    <a href="#contact">Hire Me</a>
  </nav>
</header>

<!-- HERO -->
<div class="hero">
  <p class="eyebrow">Ethical Hacker & Security Researcher</p>
  <h1>Finding Vulnerabilities<br>Before <em>Hackers Do</em></h1>
  <p class="hero-sub">
    I perform professional vulnerability assessments and penetration tests to protect your web applications, networks, and systems — with a detailed report and fix guide delivered every time.
  </p>
  <div class="badges">
    <span class="badge g">Penetration Testing</span>
    <span class="badge c">Vulnerability Assessment</span>
    <span class="badge o">OWASP Top 10</span>
    <span class="badge g">Burp Suite</span>
    <span class="badge c">Nmap · Metasploit</span>
    <span class="badge o">Detailed PDF Reports</span>
  </div>
</div>

<!-- CASE STUDIES -->
<section id="projects">
  <p class="sec-label">Portfolio</p>
  <h2>Case Studies</h2>

  <div class="cards">

    <!-- Card 1 -->
    <div class="card">
      <div class="card-head">
        <span class="card-title">Web App Pentest — E-Commerce Platform (Lab)</span>
        <span class="sev critical">CRITICAL</span>
      </div>
      <p>Performed a full black-box penetration test on a deliberately vulnerable e-commerce application (DVWA + custom lab). Discovered SQL injection, broken authentication, and exposed admin panel.</p>
      <div class="findings">
        <span class="tag">SQL Injection</span>
        <span class="tag">Broken Auth</span>
        <span class="tag">Exposed Admin</span>
        <span class="tag">Session Hijacking</span>
        <span class="tag">XSS</span>
      </div>
      <div class="terminal">
        <div><span class="prompt">$</span> <span class="cmd">sqlmap -u "http://target.lab/product?id=1" --dbs --batch</span></div>
        <div><span class="out">[*] starting @ 10:42:01</span></div>
        <div><span class="vuln">[CRITICAL] parameter 'id' is vulnerable to SQL injection</span></div>
        <div><span class="out">available databases:</span></div>
        <div><span class="vuln">  [*] users_db  [*] orders_db  [*] admin_panel</span></div>
        <div><span class="ok">[+] Report generated: pentest_report_ecommerce.pdf</span></div>
      </div>
      <br>
      <div class="tools-used"><span>Tools: </span>Burp Suite · SQLMap · OWASP ZAP · Nmap</div>
    </div>

    <!-- Card 2 -->
    <div class="card red">
      <div class="card-head">
        <span class="card-title">Network Vulnerability Scan — Home Lab (Kali Linux)</span>
        <span class="sev high">HIGH</span>
      </div>
      <p>Conducted a full network scan on an isolated lab environment simulating a small business network. Identified open ports, outdated services, and misconfigured firewall rules.</p>
      <div class="findings">
        <span class="tag">Open Ports</span>
        <span class="tag">Outdated SMB</span>
        <span class="tag">Weak Credentials</span>
        <span class="tag">Firewall Bypass</span>
      </div>
      <div class="terminal">
        <div><span class="prompt">$</span> <span class="cmd">nmap -sV -sC -O 192.168.1.0/24</span></div>
        <div><span class="info">[*] Scanning 254 hosts...</span></div>
        <div><span class="vuln">[HIGH] Host 192.168.1.5 — SMB port 445 open (MS17-010)</span></div>
        <div><span class="vuln">[HIGH] Host 192.168.1.8 — Telnet port 23 open (weak auth)</span></div>
        <div><span class="ok">[*] 3 critical issues found — Remediation report ready</span></div>
      </div>
      <br>
      <div class="tools-used"><span>Tools: </span>Nmap · Nessus · Metasploit · Wireshark</div>
    </div>

    <!-- Card 3 -->
    <div class="card cyan">
      <div class="card-head">
        <span class="card-title">WordPress Security Audit — Practice Site</span>
        <span class="sev medium">MEDIUM</span>
      </div>
      <p>Audited a self-hosted WordPress site for common CMS vulnerabilities including plugin exploits, user enumeration, and brute-force susceptibility.</p>
      <div class="findings">
        <span class="tag">User Enumeration</span>
        <span class="tag">Outdated Plugins</span>
        <span class="tag">XML-RPC Enabled</span>
        <span class="tag">Weak Passwords</span>
      </div>
      <div class="terminal">
        <div><span class="prompt">$</span> <span class="cmd">wpscan --url http://mylab.local --enumerate u,p</span></div>
        <div><span class="info">[i] WordPress version 6.2 detected</span></div>
        <div><span class="vuln">[!] 3 vulnerable plugins found</span></div>
        <div><span class="vuln">[!] User enumeration possible via REST API</span></div>
        <div><span class="ok">[+] Full audit report with fix checklist generated</span></div>
      </div>
      <br>
      <div class="tools-used"><span>Tools: </span>WPScan · Nikto · Burp Suite · Hydra</div>
    </div>

  </div>
</section>

<!-- SKILLS -->
<section id="skills">
  <p class="sec-label">Technical Skills</p>
  <h2>Tools & Expertise</h2>
  <div class="skills-grid">

    <div class="skill-box">
      <h4>Burp Suite</h4>
      <div class="skill-label"><span>Web App Testing</span><span>90%</span></div>
      <div class="bar-wrap"><div class="bar" style="width:90%"></div></div>
    </div>

    <div class="skill-box">
      <h4>Nmap</h4>
      <div class="skill-label"><span>Network Scanning</span><span>88%</span></div>
      <div class="bar-wrap"><div class="bar" style="width:88%"></div></div>
    </div>

    <div class="skill-box">
      <h4>Metasploit</h4>
      <div class="skill-label"><span>Exploitation</span><span>80%</span></div>
      <div class="bar-wrap"><div class="bar c" style="width:80%"></div></div>
    </div>

    <div class="skill-box">
      <h4>OWASP ZAP</h4>
      <div class="skill-label"><span>Vulnerability Scan</span><span>85%</span></div>
      <div class="bar-wrap"><div class="bar c" style="width:85%"></div></div>
    </div>

    <div class="skill-box">
      <h4>Nessus</h4>
      <div class="skill-label"><span>Vuln Assessment</span><span>78%</span></div>
      <div class="bar-wrap"><div class="bar o" style="width:78%"></div></div>
    </div>

    <div class="skill-box">
      <h4>Wireshark</h4>
      <div class="skill-label"><span>Traffic Analysis</span><span>82%</span></div>
      <div class="bar-wrap"><div class="bar o" style="width:82%"></div></div>
    </div>

    <div class="skill-box">
      <h4>Kali Linux</h4>
      <div class="skill-label"><span>OS & CLI</span><span>92%</span></div>
      <div class="bar-wrap"><div class="bar" style="width:92%"></div></div>
    </div>

    <div class="skill-box">
      <h4>Report Writing</h4>
      <div class="skill-label"><span>PDF Reports</span><span>88%</span></div>
      <div class="bar-wrap"><div class="bar" style="width:88%"></div></div>
    </div>

  </div>
</section>

<!-- SAMPLE REPORT -->
<section id="report">
  <p class="sec-label">Sample Output</p>
  <h2>Vulnerability Report Preview</h2>
  <div class="report-box">
    <div class="report-header">
      <div>
        <div class="report-title">Web Application Penetration Test Report</div>
        <div style="font-size:13px;color:var(--muted);margin-top:4px;">Target: demo-ecommerce.lab | Tester: MKKarim | Type: Black Box</div>
      </div>
      <div class="report-meta">
        Date: June 2025<br>
        Status: <span style="color:var(--red)">● 2 Critical</span> &nbsp;
                <span style="color:var(--orange)">● 1 High</span> &nbsp;
                <span style="color:var(--cyan)">● 2 Medium</span>
      </div>
    </div>

    <table class="vuln-table">
      <thead>
        <tr>
          <th>#</th>
          <th>Vulnerability</th>
          <th>CVSS</th>
          <th>Location</th>
          <th>Status</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td style="font-family:var(--mono);color:var(--muted)">01</td>
          <td style="color:#e6edf3">SQL Injection</td>
          <td><span class="cvss c">9.8</span></td>
          <td style="font-family:var(--mono);font-size:12px;color:var(--muted)">/product?id=</td>
          <td style="color:var(--red);font-size:13px">● Critical</td>
        </tr>
        <tr>
          <td style="font-family:var(--mono);color:var(--muted)">02</td>
          <td style="color:#e6edf3">Broken Authentication</td>
          <td><span class="cvss c">9.1</span></td>
          <td style="font-family:var(--mono);font-size:12px;color:var(--muted)">/admin/login</td>
          <td style="color:var(--red);font-size:13px">● Critical</td>
        </tr>
        <tr>
          <td style="font-family:var(--mono);color:var(--muted)">03</td>
          <td style="color:#e6edf3">Stored XSS</td>
          <td><span class="cvss h">7.4</span></td>
          <td style="font-family:var(--mono);font-size:12px;color:var(--muted)">/comments</td>
          <td style="color:var(--orange);font-size:13px">● High</td>
        </tr>
        <tr>
          <td style="font-family:var(--mono);color:var(--muted)">04</td>
          <td style="color:#e6edf3">Sensitive Data Exposure</td>
          <td><span class="cvss m">5.3</span></td>
          <td style="font-family:var(--mono);font-size:12px;color:var(--muted)">/api/users</td>
          <td style="color:var(--cyan);font-size:13px">● Medium</td>
        </tr>
        <tr>
          <td style="font-family:var(--mono);color:var(--muted)">05</td>
          <td style="color:#e6edf3">Missing Security Headers</td>
          <td><span class="cvss m">4.8</span></td>
          <td style="font-family:var(--mono);font-size:12px;color:var(--muted)">All Pages</td>
          <td style="color:var(--cyan);font-size:13px">● Medium</td>
        </tr>
      </tbody>
    </table>

    <div style="margin-top:20px;padding:16px;background:#070b10;border-radius:4px;border:1px solid var(--border);">
      <p style="font-family:var(--mono);font-size:12px;color:var(--green);margin-bottom:6px;">// Executive Summary</p>
      <p style="font-size:13px;color:var(--muted);">
        5 vulnerabilities were identified during this assessment. 2 critical issues require immediate remediation. A detailed fix guide with code-level recommendations is included in the full report. Re-testing available after fixes are applied.
      </p>
    </div>
  </div>
</section>

<!-- CTA -->
<div class="cta-section" id="contact">
  <p class="sec-label">Ready to secure your system?</p>
  <h2>Let's Work Together</h2>
  <p>I offer professional penetration testing and vulnerability assessments with clear, actionable reports. New clients get a free scope review before ordering.</p>
  <a href="#" class="btn primary">Hire Me on Upwork</a>
  <a href="#" class="btn outline">View Sample Report</a>
</div>

<footer>
  MKKarim · Ethical Hacker & Security Researcher · Built for Upwork Portfolio
</footer>

</body>
</html>
