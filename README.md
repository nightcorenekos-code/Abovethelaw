<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Above the Law — How America's Most Powerful Escape Justice</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:wght@300;400;500&family=DM+Mono:wght@400;500&display=swap');

  :root {
    --black: #0A0A0A;
    --red: #C8102E;
    --red-dark: #8B0000;
    --red-light: #FF1F30;
    --white: #F5F4F0;
    --gray: #1A1A1A;
    --gray-mid: #2C2C2C;
    --gray-light: #444;
    --border: rgba(255,255,255,0.08);
    --border-red: rgba(200,16,46,0.4);
    --blue: #185fa5;
    --border-blue: rgba(24,95,165,0.4);
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--black);
    color: var(--white);
    font-family: 'DM Sans', sans-serif;
    font-weight: 300;
    min-height: 100vh;
  }

  ::-webkit-scrollbar { width: 4px; }
  ::-webkit-scrollbar-track { background: var(--black); }
  ::-webkit-scrollbar-thumb { background: var(--red); border-radius: 2px; }

  /* ── NAV ── */
  nav {
    position: sticky; top: 0; z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 0 32px; height: 56px;
    background: rgba(10,10,10,0.95);
    backdrop-filter: blur(12px);
    border-bottom: 0.5px solid var(--border);
  }
  .nav-logo {
    display: flex; align-items: center; gap: 10px;
    font-family: 'Bebas Neue', sans-serif;
    font-size: 20px; letter-spacing: 0.08em;
    color: var(--white); text-decoration: none; cursor: pointer;
  }
  .logo-accent { width: 3px; height: 22px; background: var(--red); border-radius: 2px; }
  .nav-links { display: flex; gap: 4px; flex-wrap: wrap; }
  .nav-link {
    padding: 6px 14px; font-size: 12px; font-family: 'DM Mono', monospace;
    border: 0.5px solid var(--border); border-radius: 2px;
    background: transparent; color: rgba(245,244,240,0.5);
    cursor: pointer; transition: all 0.2s; letter-spacing: 0.04em;
  }
  .nav-link:hover { color: var(--white); border-color: var(--border-red); }
  .nav-link.active { color: var(--white); border-color: var(--red); background: rgba(200,16,46,0.1); }

  /* ── SECTIONS ── */
  .section { display: none; }
  .section.active { display: block; }

  /* ── HERO ── */
  .hero {
    position: relative; overflow: hidden;
    padding: 80px 48px 64px;
    border-bottom: 0.5px solid var(--border);
    min-height: 480px;
    display: flex; flex-direction: column; justify-content: flex-end;
  }
  .hero-bg {
    position: absolute; inset: 0;
    background: linear-gradient(135deg, #0A0A0A 50%, #1a0000 100%);
  }
  .hero-line { position: absolute; bottom: 0; left: 0; width: 100%; height: 3px; background: var(--red); }
  .hero-number {
    position: absolute; right: -20px; top: -40px;
    font-family: 'Bebas Neue', sans-serif; font-size: 320px; line-height: 1;
    color: rgba(200,16,46,0.06); user-select: none; pointer-events: none;
  }
  .hero-eyebrow {
    position: relative;
    font-family: 'DM Mono', monospace; font-size: 11px;
    letter-spacing: 0.14em; text-transform: uppercase;
    color: var(--red); margin-bottom: 20px;
  }
  .hero-title {
    position: relative;
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(64px, 10vw, 120px); line-height: 0.9;
    letter-spacing: 0.02em; color: var(--white); margin-bottom: 28px;
  }
  .hero-title .accent { color: var(--red); }
  .hero-sub {
    position: relative;
    font-size: 15px; line-height: 1.75; font-weight: 300;
    color: rgba(245,244,240,0.65); max-width: 560px; margin-bottom: 40px;
  }
  .stat-row { position: relative; display: grid; grid-template-columns: repeat(3,1fr); gap: 1px; }
  .stat-card { background: var(--gray); padding: 20px; border-top: 2px solid var(--red); }
  .stat-num {
    font-family: 'Bebas Neue', sans-serif; font-size: 48px;
    line-height: 1; color: var(--red); letter-spacing: 0.02em;
  }
  .stat-label { font-size: 12px; color: rgba(245,244,240,0.5); margin-top: 6px; line-height: 1.5; }

  /* ── HUB GRID ── */
  .hub-section { padding: 40px 48px; border-bottom: 0.5px solid var(--border); }
  .section-label {
    font-family: 'DM Mono', monospace; font-size: 10px;
    letter-spacing: 0.14em; text-transform: uppercase;
    color: rgba(245,244,240,0.3); margin-bottom: 20px;
  }
  .hub-grid { display: grid; grid-template-columns: repeat(3,1fr); gap: 1px; background: var(--border); }
  .hub-card {
    background: var(--black); padding: 28px 24px;
    cursor: pointer; transition: background 0.2s;
    display: flex; flex-direction: column; gap: 12px;
  }
  .hub-card:hover { background: var(--gray); }
  .hub-tag { font-family: 'DM Mono', monospace; font-size: 10px; letter-spacing: 0.1em; text-transform: uppercase; color: var(--red); }
  .hub-name { font-family: 'Bebas Neue', sans-serif; font-size: 28px; letter-spacing: 0.04em; line-height: 1.1; }
  .hub-desc { font-size: 12px; color: rgba(245,244,240,0.45); line-height: 1.6; }
  .hub-arrow { font-size: 18px; color: var(--red); margin-top: auto; }

  /* ── PAGE LAYOUT ── */
  .page-wrap { padding: 48px; max-width: 860px; }
  .page-eyebrow {
    font-family: 'DM Mono', monospace; font-size: 10px;
    letter-spacing: 0.14em; text-transform: uppercase;
    color: var(--red); margin-bottom: 12px;
  }
  .page-title {
    font-family: 'Bebas Neue', sans-serif; font-size: 52px;
    letter-spacing: 0.04em; line-height: 1; margin-bottom: 14px;
  }
  .page-desc { font-size: 14px; color: rgba(245,244,240,0.55); line-height: 1.75; margin-bottom: 36px; max-width: 600px; }

  /* ── CASE CARDS ── */
  .case-list { display: flex; flex-direction: column; gap: 1px; background: var(--border); }
  .case-card { background: var(--black); cursor: pointer; transition: background 0.2s; }
  .case-card:hover { background: var(--gray); }
  .case-header { display: flex; justify-content: space-between; align-items: flex-start; padding: 20px 24px 0; gap: 16px; }
  .case-name { font-size: 15px; font-weight: 500; }
  .badge {
    font-family: 'DM Mono', monospace; font-size: 10px; letter-spacing: 0.08em;
    padding: 4px 10px; border: 0.5px solid; white-space: nowrap; flex-shrink: 0;
  }
  .badge.lenient { border-color: rgba(200,16,46,0.5); color: var(--red); }
  .badge.convicted { border-color: rgba(245,244,240,0.2); color: rgba(245,244,240,0.5); }
  .case-charge {
    font-family: 'DM Mono', monospace; font-size: 11px;
    color: rgba(245,244,240,0.35); padding: 8px 24px 0; letter-spacing: 0.03em;
  }
  .case-outcome { font-size: 13px; color: rgba(245,244,240,0.7); line-height: 1.65; padding: 8px 24px 20px; }
  .case-expand { display: none; padding: 0 24px 20px; border-top: 0.5px solid var(--border); }
  .case-expand.open { display: block; }
  .case-detail { font-size: 13px; color: rgba(245,244,240,0.5); line-height: 1.75; padding-top: 16px; }
  .case-src { font-family: 'DM Mono', monospace; font-size: 10px; color: rgba(245,244,240,0.2); margin-top: 10px; letter-spacing: 0.04em; }

  /* ── COMPARE TOOL ── */
  .compare-wrap { padding: 48px; }
  .legend { display: flex; gap: 16px; margin-bottom: 24px; flex-wrap: wrap; }
  .legend-item { display: flex; align-items: center; gap: 6px; font-size: 11px; color: rgba(245,244,240,0.5); }
  .legend-dot { width: 8px; height: 8px; border-radius: 50%; }
  .pick-row { display: grid; grid-template-columns: 1fr 40px 1fr; margin-bottom: 16px; align-items: start; }
  .pick-col { display: flex; flex-direction: column; gap: 8px; }
  .pick-label {
    font-family: 'DM Mono', monospace; font-size: 10px; letter-spacing: 0.1em;
    text-transform: uppercase; color: rgba(245,244,240,0.3); margin-bottom: 4px;
  }
  .pick-category { display: flex; gap: 6px; flex-wrap: wrap; margin-bottom: 4px; }
  .cat-btn {
    font-size: 11px; padding: 5px 12px;
    border: 0.5px solid var(--border); border-radius: 2px;
    background: transparent; color: rgba(245,244,240,0.4);
    cursor: pointer; transition: all 0.2s; font-family: 'DM Mono', monospace; letter-spacing: 0.04em;
  }
  .cat-btn:hover { color: var(--white); }
  .cat-pol { border-color: var(--border-red); color: var(--red); background: rgba(200,16,46,0.08); }
  .cat-cel { border-color: rgba(133,100,4,0.5); color: #856404; background: rgba(133,100,4,0.08); }
  .cat-bil { border-color: rgba(10,54,34,0.8); color: #4ade80; background: rgba(10,54,34,0.15); }
  .cat-low { border-color: var(--border-blue); color: var(--blue); background: rgba(24,95,165,0.08); }
  .case-select {
    width: 100%; padding: 10px 14px; font-size: 13px;
    border: 0.5px solid rgba(255,255,255,0.12); border-radius: 2px;
    background: var(--gray); color: var(--white);
    font-family: 'DM Sans', sans-serif; cursor: pointer;
  }
  .case-select:focus { outline: none; border-color: var(--border-red); }
  .case-select option { background: var(--gray); }
  .vs-mid { display: flex; align-items: center; justify-content: center; padding-top: 56px; }
  .vs-badge {
    font-family: 'Bebas Neue', sans-serif; font-size: 16px; letter-spacing: 0.08em;
    color: var(--red); border: 0.5px solid var(--border-red);
    padding: 4px 10px; border-radius: 2px;
  }
  .cmp-grid { display: grid; grid-template-columns: 1fr 40px 1fr; margin-bottom: 1px; align-items: start; }
  .cmp-card { background: var(--gray); padding: 24px; border-top: 2px solid var(--red); }
  .cmp-card.low-income { border-top-color: var(--blue); }
  .cmp-label {
    font-family: 'DM Mono', monospace; font-size: 10px; letter-spacing: 0.1em;
    text-transform: uppercase; color: rgba(245,244,240,0.3); margin-bottom: 16px;
  }
  .cmp-name { font-family: 'Bebas Neue', sans-serif; font-size: 26px; letter-spacing: 0.04em; margin-bottom: 6px; }
  .cmp-bg { font-size: 12px; color: rgba(245,244,240,0.45); margin-bottom: 20px; line-height: 1.55; }
  .cmp-tag { font-size: 10px; letter-spacing: 0.08em; text-transform: uppercase; font-weight: 500; margin-bottom: 12px; }
  .tag-pol { color: var(--red); }
  .tag-cel { color: #856404; }
  .tag-bil { color: #4ade80; }
  .tag-low { color: var(--blue); }
  .cmp-row {
    display: flex; justify-content: space-between; padding: 8px 0;
    border-bottom: 0.5px solid var(--border); font-size: 12px; gap: 8px;
  }
  .cmp-row:last-child { border: none; }
  .cmp-key { font-family: 'DM Mono', monospace; color: rgba(245,244,240,0.35); letter-spacing: 0.03em; flex-shrink: 0; }
  .cmp-val { font-weight: 500; text-align: right; }
  .cmp-val.g { color: #4ade80; }
  .cmp-val.r { color: var(--red); }
  .vs-col { display: flex; align-items: center; justify-content: center; background: var(--black); }
  .vs-text { font-family: 'Bebas Neue', sans-serif; font-size: 18px; color: rgba(245,244,240,0.2); letter-spacing: 0.08em; }
  .empty-card {
    background: var(--gray); padding: 48px 24px;
    display: flex; align-items: center; justify-content: center;
    text-align: center; min-height: 260px; border-top: 2px solid var(--border);
  }
  .empty-text { font-size: 13px; color: rgba(245,244,240,0.25); line-height: 1.7; }
  .note-box {
    background: var(--gray); padding: 18px 24px;
    font-size: 13px; color: rgba(245,244,240,0.45);
    line-height: 1.75; font-style: italic;
    border-left: 3px solid var(--red); margin-bottom: 1px;
  }
  .diff-box { background: var(--gray); padding: 18px 24px; display: none; }
  .diff-box.show { display: block; }
  .diff-title {
    font-family: 'DM Mono', monospace; font-size: 10px; letter-spacing: 0.1em;
    text-transform: uppercase; color: rgba(245,244,240,0.3); margin-bottom: 12px;
  }
  .diff-row { display: flex; gap: 12px; font-size: 13px; margin-bottom: 8px; align-items: flex-start; }
  .diff-row:last-child { margin-bottom: 0; }
  .diff-dot { width: 8px; height: 8px; border-radius: 50%; flex-shrink: 0; margin-top: 5px; }
  .diff-dot.r { background: var(--red); }
  .diff-dot.b { background: var(--blue); }
  .diff-text { color: rgba(245,244,240,0.55); line-height: 1.65; }

  /* ── REFORM ── */
  .reform-wrap { padding: 48px; }
  .reform-item {
    border-left: 3px solid var(--red); padding: 20px 24px;
    margin-bottom: 1px; background: var(--gray);
  }
  .reform-title { font-family: 'Bebas Neue', sans-serif; font-size: 24px; letter-spacing: 0.04em; margin-bottom: 8px; }
  .reform-text { font-size: 13px; color: rgba(245,244,240,0.55); line-height: 1.75; }
  .org-box { margin-top: 32px; padding: 24px; border: 0.5px solid var(--border-red); }
  .org-title {
    font-family: 'DM Mono', monospace; font-size: 10px; letter-spacing: 0.12em;
    text-transform: uppercase; color: var(--red); margin-bottom: 16px;
  }
  .org-item { font-size: 13px; color: rgba(245,244,240,0.5); padding: 10px 0; border-bottom: 0.5px solid var(--border); line-height: 1.5; }
  .org-item:last-child { border: none; }

  /* ── SOURCES ── */
  .sources-wrap { padding: 48px; }
  .src-card {
    border-left: 0.5px solid var(--border-red); padding: 20px 24px;
    margin-bottom: 1px; background: var(--gray); transition: background 0.2s;
  }
  .src-card:hover { background: var(--gray-mid); }
  .src-num { font-family: 'DM Mono', monospace; font-size: 10px; letter-spacing: 0.1em; color: var(--red); margin-bottom: 4px; }
  .src-name { font-size: 14px; font-weight: 500; margin-bottom: 4px; }
  .src-url { font-family: 'DM Mono', monospace; font-size: 10px; color: rgba(245,244,240,0.25); margin-bottom: 10px; }
  .src-ann { font-size: 13px; color: rgba(245,244,240,0.5); line-height: 1.7; }

  /* ── FOOTER ── */
  footer {
    padding: 32px 48px; border-top: 0.5px solid var(--border);
    display: flex; justify-content: space-between; align-items: center;
  }
  .footer-logo { font-family: 'Bebas Neue', sans-serif; font-size: 16px; letter-spacing: 0.08em; color: rgba(245,244,240,0.2); }
  .footer-text { font-family: 'DM Mono', monospace; font-size: 10px; color: rgba(245,244,240,0.2); letter-spacing: 0.06em; }
</style>
</head>
<body>

<nav>
  <div class="nav-logo" onclick="show('home')">
    <div class="logo-accent"></div>
    ABOVE THE LAW
  </div>
  <div class="nav-links">
    <button class="nav-link active" onclick="show('home')">Home</button>
    <button class="nav-link" onclick="show('politicians')">Politicians</button>
    <button class="nav-link" onclick="show('celebrities')">Celebrities</button>
    <button class="nav-link" onclick="show('billionaires')">Billionaires</button>
    <button class="nav-link" onclick="show('compare')">Compare</button>
    <button class="nav-link" onclick="show('reform')">Reform</button>
  </div>
</nav>

<!-- ══════════════════════════════════════════════════
     HOME
══════════════════════════════════════════════════ -->
<div id="home" class="section active">
  <div class="hero">
    <div class="hero-bg"></div>
    <div class="hero-number">$</div>
    <div class="hero-line"></div>
    <div class="hero-eyebrow">A public awareness project</div>
    <div class="hero-title">IN AMERICA,<br>JUSTICE HAS A <span class="accent">PRICE TAG.</span></div>
    <div class="hero-sub">The wealthier and more powerful you are, the less accountable you become. This site documents how politicians, celebrities, and billionaires systematically escape consequences that everyday citizens cannot.</div>
    <div class="stat-row">
      <div class="stat-card">
        <div class="stat-num">60%</div>
        <div class="stat-label">Shorter sentences for defendants with private attorneys vs. public defenders for similar offenses (NBER, 2018)</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">$500K</div>
        <div class="stat-label">Cost of rehab center paid by Ethan Couch's parents after he killed four people drunk driving instead of going to prison</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">0</div>
        <div class="stat-label">Individual Sackler family members criminally charged after 500,000+ opioid deaths linked to their company</div>
      </div>
    </div>
  </div>
  <div class="hub-section">
    <div class="section-label">Explore by category</div>
    <div class="hub-grid">
      <div class="hub-card" onclick="show('politicians')">
        <div class="hub-tag">01 — Politicians</div>
        <div class="hub-name">POLITICIANS &amp; LAWMAKERS</div>
        <div class="hub-desc">When the people who make the laws break them and face no consequences.</div>
        <div class="hub-arrow">→</div>
      </div>
      <div class="hub-card" onclick="show('celebrities')">
        <div class="hub-tag">02 — Celebrities</div>
        <div class="hub-name">CELEBRITIES & ENTERTAINERS</div>
        <div class="hub-desc">How fame and fortune act as the most powerful legal defense in America.</div>
        <div class="hub-arrow">→</div>
      </div>
      <div class="hub-card" onclick="show('billionaires')">
        <div class="hub-tag">03 — Billionaires</div>
        <div class="hub-name">BILLIONAIRES & CEOs</div>
        <div class="hub-desc">When money can replace jail time and criminal charges.</div>
        <div class="hub-arrow">→</div>
      </div>
    </div>
  </div>
</div>

<!-- ══════════════════════════════════════════════════
     POLITICIANS
══════════════════════════════════════════════════ -->
<div id="politicians" class="section">
  <div class="page-wrap">
    <div class="page-eyebrow">01 — Politicians &amp; Lawmakers</div>
    <div class="page-title">WHEN THE PEOPLE WHO MAKE THE LAWS BREAK THEM</div>
    <div class="page-desc"> Having a upper hand in politics grants individuals the ability to avoid proper accountability. It allows them to hide evidence and manipulate the legal system by utilizing the connections they have. Click any case to expand.</div>
    <div class="case-list">

      <div class="case-card" onclick="toggle(this)">
        <div class="case-header"><div class="case-name">Paul Manafort: Political Consultant</div><span class="badge lenient">Reduced sentence</span></div>
        <div class="case-charge">CHARGE: Tax and bank fraud; recommended 19–24 years</div>
        <div class="case-outcome">Received 47 months. Judge called the guidelines "excessive." Later received a presidential pardon.</div>
        <div class="case-expand">
          <div class="case-detail">Manafort’s legal team, which was funded by high-paying lobbying work, created a strong defense that would delay proceedings and secured a “questionable” judge. Manafort also initially received house arrest rather than pretrial detention, a luxury unavailable to those who can’t post bail.</div>
          <div class="case-src">SOURCE: Forensics Colleges (2020) · DOJ records</div>
        </div>
      </div>

      <div class="case-card" onclick="toggle(this)">
        <div class="case-header"><div class="case-name">Ted Stevens: U.S. Senator, Alaska</div><span class="badge lenient">Charges dropped</span></div>
        <div class="case-charge">CHARGE: Failing to disclose $250,000 in gifts from oil contractor VECO Corp</div>
        <div class="case-outcome">Convicted in 2008. Charges dropped in 2009 after DOJ misconduct was revealed. Stevens died before retrial.</div>
        <div class="case-expand">
          <div class="case-detail">Stevens had access to top-tier legal counsel who was able to uncover prosecutorial misconduct, which is a resource unavailable to most defendants. It shows how the wealthy can fight charges and get them dropped, while everyday citizens can’t.</div>
          <div class="case-src">SOURCE: Public court records · DOJ press releases</div>
        </div>
      </div>

      <div class="case-card" onclick="toggle(this)">
        <div class="case-header"><div class="case-name">NYC Bar Report: Presidential Conduct (2025)</div><span class="badge lenient">No prosecution</span></div>
        <div class="case-charge">DOCUMENTED: Use of executive power for personal financial enrichment</div>
        <div class="case-outcome">The NYC Bar Association formally documented the use of regulatory and foreign policy decisions to benefit personal businesses, which it described as likely violating the Emoluments Clause. No criminal charges filed.</div>
        <div class="case-expand">
          <div class="case-detail">The report concluded that President Donald J. Trump and his administration abused their powers in favor of themselves and not the Constitution. This included enriching their lives, dismantling federal programs, and so on. The significance of it is that it comes from a legal establishment, not critics.</div>
          <div class="case-src">SOURCE: NYC Bar Association Rule of Law Task Force, Dec. 2025</div>
        </div>
      </div>

      <div class="case-card" onclick="toggle(this)">
        <div class="case-header"><div class="case-name">William Jefferson: U.S. Representative, Louisiana</div><span class="badge convicted">13 years</span></div>
        <div class="case-charge">CHARGE: Bribery — $90,000 found in his freezer</div>
        <div class="case-outcome">Received 13 years. Unusually severe for a political corruption case. Jefferson lacked the high-powered connections of wealthier defendants.</div>
        <div class="case-expand">
          <div class="case-detail">Jefferson’s case contrasts with that of the political category - a politician without the same wealth or connections as colleagues received a harsher sentence than most corruption cases. Even within the powerful, wealth differences still determine outcomes.</div>
          <div class="case-src">SOURCE: DOJ press release · Federal court records</div>
        </div>
      </div>

    </div>
  </div>
</div>

<!-- ══════════════════════════════════════════════════
     CELEBRITIES
══════════════════════════════════════════════════ -->
<div id="celebrities" class="section">
  <div class="page-wrap">
    <div class="page-eyebrow">02 — Celebrities &amp; Entertainers</div>
    <div class="page-title">FAME AS A LEGAL DEFENSE</div>
    <div class="page-desc">Celebrity fame allows them to navigate the legal system more easily and with greater support. Their fans exert public pressure that can influence legal outcomes, while their resources enable prolonged legal battles. Click any case to expand.

</div>
    <div class="case-list">

      <div class="case-card" onclick="toggle(this)">
        <div class="case-header"><div class="case-name">Ethan Couch: "Affluenza" Defendant</div><span class="badge lenient">Probation only</span></div>
        <div class="case-charge">CHARGE: Intoxication manslaughter with with a BAC of 0.24, killed four pedestrians</div>
        <div class="case-outcome">10 years probation. Parents paid for a $500,000/year rehabilitation center. No prison time at initial sentencing.</div>
        <div class="case-expand">
          <div class="case-detail">Couch’s attonery argued “affluenza” - a psychological condition used to help children of celebrities get out of serious crimes as they never learned to understand consequences. When Couch violated probation, he received only 720 years in jail, whereas in an equivalent case involving a poor defendant, the sentence would have been longer. </div>
          <div class="case-src">SOURCE: Prison Legal News (2023) · CBS News court records</div>
        </div>
      </div>

      <div class="case-card" onclick="toggle(this)">
        <div class="case-header"><div class="case-name">Jeffrey Epstein: Financier</div><span class="badge lenient">Secret plea deal</span></div>
        <div class="case-charge">CHARGE: Sex trafficking of minors, dozens of known victims</div>
        <div class="case-outcome">2008: Pled guilty to two state charges, served 13 months with daily work release. Federal prosecutors gave him a secret non-prosecution agreement later ruled illegal.</div>
        <div class="case-expand">
          <div class="case-detail">Epstein’s defense team negotiated directly with U.S. Attorney Alexander Acosta, which allowed him to secure a deal that violated Justice Department policy by keeping victims in the dark. His wealth allowed him to avoid a second federal prosecution until 2019.</div>
          <div class="case-src">SOURCE: Miami Herald investigation · Federal court filings · DOJ Inspector General report</div>
        </div>
      </div>

      <div class="case-card" onclick="toggle(this)">
        <div class="case-header"><div class="case-name">Robert Durst: Real Estate Heir</div><span class="badge lenient">Acquitted (2003)</span></div>
        <div class="case-charge">CHARGE: Murder: dismembered neighbor Morris Black</div>
        <div class="case-outcome">Acquitted in 2003 after high-powered legal team argued self-defense. Convicted in a separate case only in 2021 which came two decades later.</div>
        <div class="case-expand">
          <div class="case-detail">Durst's defense team cost millions. His family's real estate wealth allowed decades of legal maneuvering. This is not something low-income defendants can afford, and shows that wealth comes a long way when a defendant has the resources to fight the system.</div>
          <div class="case-src">SOURCE: NYT · Court records</div>
        </div>
      </div>

      <div class="case-card" onclick="toggle(this)">
        <div class="case-header"><div class="case-name">Harvey Weinstein: Film Producer</div><span class="badge convicted">Convicted</span></div>
        <div class="case-charge">CHARGE: Rape and sexual assault, decades of alleged abuse</div>
        <div class="case-outcome">Convicted 2020, sentenced to 23 years. NY conviction overturned on appeal in 2024, wealth enabled an appeal unavailable to most defendants.</div>
        <div class="case-expand">
          <div class="case-detail">Even when convicted, wealth plays a role. Weinstein’s legal team was able to appeal his NY conviction, which required expensive, prolonged appeals. This is something most defendants could never fund. It took 30+ years from the first known allegations for him to get convicted.</div>
          <div class="case-src">SOURCE: NYT · Court records · AP News</div>
        </div>
      </div>

    </div>
  </div>
</div>

<!-- ══════════════════════════════════════════════════
     BILLIONAIRES
══════════════════════════════════════════════════ -->
<div id="billionaires" class="section">
  <div class="page-wrap">
    <div class="page-eyebrow">03 — Billionaires &amp; CEOs</div>
    <div class="page-title">WHEN MONEY IS THE ONLY SENTENCE</div>
    <div class="page-desc">For the rich, criminal charges are often replaced by civil settlements. Money talks, it buys away charges and jail time, which many defendants cannot afford. Click any case to expand.</div>
    <div class="case-list">

      <div class="case-card" onclick="toggle(this)">
        <div class="case-header"><div class="case-name">Elon Musk: Tesla CEO (SEC violation)</div><span class="badge lenient">$20M fine</span></div>
        <div class="case-charge">CHARGE: Securities fraud: "funding secured" tweet misled investors</div>
        <div class="case-outcome">Paid $20M personal fine. No criminal charges. $20M ≈ 0.02% of his net worth at the time.</div>
        <div class="case-expand">
          <div class="case-detail">Musk paid a $20 million settlement for misleading investors, which resulted in 0 jail time; however, if a low-income individual stole $20, they most likely would face jail time. Fines for the wealthy constitute a different category of punishment than those for low-income defendants.</div>
          <div class="case-src">SOURCE: SEC v. Tesla settlement · Reuters</div>
        </div>
      </div>

      <div class="case-card" onclick="toggle(this)">
        <div class="case-header"><div class="case-name">Martin Shkreli: Pharma CEO</div><span class="badge convicted">7 years</span></div>
        <div class="case-charge">CHARGE: Securities fraud: defrauded hedge fund investors</div>
        <div class="case-outcome">Sentenced to 7 years. Not for his 5,000% drug price hike, but for investor fraud. Released early after 4 years.</div>
        <div class="case-expand">
          <div class="case-detail">Shkreli’s conviction was not due to his drug price hike, which harmed the poor patients, but for defrauding wealthy investors - a class the system protects.</div>
          <div class="case-src">SOURCE: DOJ press release · Federal court records</div>
        </div>
      </div>

      <div class="case-card" onclick="toggle(this)">
        <div class="case-header"><div class="case-name">Purdue Pharma / Sackler Family</div><span class="badge lenient">Civil settlement</span></div>
        <div class="case-charge">CHARGE: Fueling the opioid epidemic: 500,000+ deaths linked to OxyContin</div>
        <div class="case-outcome">Sackler family paid approximately $6B in civil settlements. No individual family member faced criminal charges in the U.S.</div>
        <div class="case-expand">
          <div class="case-detail">Half a million Americans died. The Sackler family manufactured and marketed the drug through deceptive practices and paid approximately $6 billion to avoid criminal prosecution. In comparison, individuals caught selling any amount of opioids would receive jail time.</div>
          <div class="case-src">SOURCE: DOJ settlement documents · NYT investigation</div>
        </div>
      </div>

    </div>
  </div>
</div>

<!-- ══════════════════════════════════════════════════
     COMPARE
══════════════════════════════════════════════════ -->
<div id="compare" class="section">
  <div class="compare-wrap">
    <div class="page-eyebrow">Case comparison tool</div>
    <div class="page-title">SAME CRIME.<br>DIFFERENT OUTCOME.</div>
    <div class="page-desc">Select any two defendants to compare charges, attorneys, bail, and sentences side by side.</div>

    <div class="legend">
      <div class="legend-item"><div class="legend-dot" style="background:#c8102e"></div>Politicians</div>
      <div class="legend-item"><div class="legend-dot" style="background:#856404"></div>Celebrities</div>
      <div class="legend-item"><div class="legend-dot" style="background:#4ade80"></div>Billionaires</div>
      <div class="legend-item"><div class="legend-dot" style="background:#185fa5"></div>Low-income defendants</div>
    </div>

    <div class="pick-row">
      <div class="pick-col">
        <div class="pick-label">Left — select a defendant</div>
        <div class="pick-category" id="lcat">
          <button class="cat-btn cat-pol" onclick="filterCat('l','Politicians',this)">Politicians</button>
          <button class="cat-btn" onclick="filterCat('l','Celebrities',this)">Celebrities</button>
          <button class="cat-btn" onclick="filterCat('l','Billionaires',this)">Billionaires</button>
          <button class="cat-btn" onclick="filterCat('l','Low-Income',this)">Low-Income</button>
        </div>
        <select class="case-select" id="lsel" onchange="render()"></select>
      </div>
      <div class="vs-mid"><div class="vs-badge">VS</div></div>
      <div class="pick-col">
        <div class="pick-label">Right — select a defendant</div>
        <div class="pick-category" id="rcat">
          <button class="cat-btn" onclick="filterCat('r','Politicians',this)">Politicians</button>
          <button class="cat-btn" onclick="filterCat('r','Celebrities',this)">Celebrities</button>
          <button class="cat-btn" onclick="filterCat('r','Billionaires',this)">Billionaires</button>
          <button class="cat-btn cat-low" onclick="filterCat('r','Low-Income',this)">Low-Income</button>
        </div>
        <select class="case-select" id="rsel" onchange="render()"></select>
      </div>
    </div>

    <div class="cmp-grid">
      <div id="left-card" class="cmp-card"></div>
      <div class="vs-col"><div class="vs-text">VS</div></div>
      <div id="right-card" class="cmp-card low-income"></div>
    </div>

    <div class="note-box" id="note-box">Select two defendants above to see a comparison note.</div>
    <div class="diff-box" id="diff-box">
      <div class="diff-title">Side-by-side outcome breakdown</div>
      <div id="diff-content"></div>
    </div>

  </div>
</div>

<!-- ══════════════════════════════════════════════════
     REFORM
══════════════════════════════════════════════════ -->
<div id="reform" class="section">
  <div class="reform-wrap">
    <div class="page-eyebrow">What needs to change</div>
    <div class="page-title">REFORMS</div>
    <div class="page-desc">Awareness is the first step. These reforms are supported by legal scholars and advocacy organizations working to reduce wealth-based inequality in the justice system.</div>

    <div class="reform-item">
      <div class="reform-title">01 — ELIMINATE CASH BAIL</div>
      <div class="reform-text">Cash bail hurts people experiencing poverty by destroying jobs, housing, and families. It aims to pressure innocent people into guilty pleas. There are ways to combat this, as Equal Justice Under Law has demonstrated by filing and winning statewide legal challenges to money bail, proving reform is possible.</div>
    </div>
    <div class="reform-item">
      <div class="reform-title">02 — INDIVIDUAL ACCOUNTABILITY FOR CORPORATE CRIME</div>
      <div class="reform-text">Corporate fines without individual prosecution create no deterrent. The DOJ's "Yates Memo" requires focusing on individual executives in corporate investigations, but enforcement has been inconsistent. Fines paid by shareholders protect the very executives who made the decisions.</div>
    </div>
    <div class="reform-item">
      <div class="reform-title">03 — PUBLIC DEFENDER FUNDING PARITY</div>
      <div class="reform-text">The Sixth Amendment guarantees the right to counsel. Public defenders usually carry caseloads 3–5 times the recommended maximum. Making resources equal between public defense and prosecution would dramatically improve outcomes for low-income defendants.</div>
    </div>
    <div class="reform-item">
      <div class="reform-title">04 — SENTENCING DISPARITY REPORTING</div>
      <div class="reform-text">Require federal courts to publish annual reports on sentencing outcomes categorized by defendant income, attorney type, and offense category. This would expose sentencing inequality that is currently uncollected or unpublished.</div>
    </div>

    <div class="org-box">
      <div class="org-title">Organizations working on these issues</div>
      <div class="org-item">Equal Justice Under Law — equaljusticeunderlaw.org</div>
      <div class="org-item">The Sentencing Project — sentencingproject.org</div>
      <div class="org-item">ACLU Criminal Law Reform — aclu.org/criminal-law-reform</div>
      <div class="org-item">Innocence Project — innocenceproject.org</div>
    </div>
  </div>
</div>


<footer>
  <div class="footer-logo">ABOVE THE LAW</div>
  <div class="footer-text">A public awareness project · All sources verified · 2026</div>
</footer>

<script>
// ── Case data ──────────────────────────────────────────────────────────────────
const allCases = {
  Politicians: [
    { name:'Paul Manafort', bg:'Political consultant, net worth ~$60M. Hired 10+ attorneys.', charge:'Tax & bank fraud', atty:'Private (top-tier firm)', bail:'$10M bond, house arrest', sentence:'47 months (pardoned)', guide:'19–24 years', bailC:'g', sentC:'g', note:'Recommended 19–24 years. Received 47 months then was pardoned. His resources allowed him to fight every stage of prosecution.' },
    { name:'Ted Stevens', bg:'U.S. Senator, Alaska. Top-tier legal counsel throughout.', charge:'Failing to disclose $250K in gifts', atty:'Private (top-tier)', bail:'Released on own recognizance', sentence:'Charges dropped (2009)', guide:'Up to 5 years', bailC:'g', sentC:'g', note:'Charges dropped after prosecutors\' misconduct was uncovered — a resource-intensive legal move unavailable to most defendants.' },
    { name:'Presidential conduct (NYC Bar 2025)', bg:'Executive power used for personal enrichment per NYC Bar report.', charge:'Emoluments violations (documented)', atty:'White House + private counsel', bail:'Not applicable', sentence:'No prosecution', guide:'Up to 20 years', bailC:'g', sentC:'g', note:'The NYC Bar Association documented likely Emoluments Clause violations. No charges were ever filed.' },
    { name:'William Jefferson', bg:'U.S. Representative, Louisiana. Less connected than wealthier peers.', charge:'Bribery ($90K found in freezer)', atty:'Private (less prominent)', bail:'Released on bond', sentence:'13 years', guide:'10–12 years', bailC:'g', sentC:'r', note:'Received 13 years — unusually harsh for political corruption. He lacked the elite legal network of wealthier colleagues.' },
  ],
  Celebrities: [
    { name:'Ethan Couch', bg:'Teenager from wealthy Texas family. Parents paid $500K/yr for rehab.', charge:'Intoxication manslaughter × 4 (BAC 0.24)', atty:'Private (argued "affluenza")', bail:'Released to parents', sentence:'10 years probation', guide:'Up to 20 years', bailC:'g', sentC:'g', note:'"Affluenza" defense argued his wealth meant he couldn\'t understand consequences. Four people were killed. He received probation.' },
    { name:'Jeffrey Epstein', bg:'Financier with vast wealth and elite government connections.', charge:'Sex trafficking of minors', atty:'Top-tier private counsel', bail:'$5M bond (2019)', sentence:'13 months + work release (2008)', guide:'Life in federal prison', bailC:'g', sentC:'g', note:'2008 plea deal was later ruled illegal. Attorneys negotiated directly with prosecutors to shield him and unnamed co-conspirators.' },
    { name:'Robert Durst', bg:'Real estate heir. Family wealth funded decades of legal battles.', charge:'Murder (dismembered neighbor)', atty:'Private (millions spent)', bail:'$250K bond (2003)', sentence:'Acquitted 2003; convicted 2021', guide:'Life in prison', bailC:'g', sentC:'g', note:'Acquitted in 2003 despite evidence. Only convicted in a separate murder case in 2021, nearly 20 years later.' },
    { name:'Harvey Weinstein', bg:'Film producer. Decades of alleged abuse before charges.', charge:'Rape and sexual assault', atty:'Private (top-tier)', bail:'$1M cash bond', sentence:'23 years (NY conviction overturned)', guide:'Life in prison', bailC:'g', sentC:'r', note:'Even in conviction, wealth enabled a successful NY appeal. The case took 30+ years from first known allegations to conviction.' },
  ],
  Billionaires: [
    { name:'Elon Musk (SEC violation)', bg:'Tesla CEO. Tweet misled millions of investors.', charge:'Securities fraud', atty:'Top corporate defense', bail:'Not applicable', sentence:'$20M fine, no jail', guide:'Up to 20 years', bailC:'g', sentC:'g', note:'$20M fine = ~0.02% of his net worth. Zero jail time. A comparable fraud by an ordinary person results in federal prison.' },
    { name:'Martin Shkreli', bg:'Pharma CEO. Defrauded wealthy investors, not poor patients.', charge:'Securities fraud (hedge fund investors)', atty:'Private counsel', bail:'$5M bond', sentence:'7 years (served 4)', guide:'10–12 years', bailC:'g', sentC:'r', note:'One of the rare exceptions. Convicted because he defrauded wealthy investors. His 5,000% drug price hike harming poor patients drew zero charges.' },
    { name:'Sackler Family / Purdue Pharma', bg:'Billionaire pharmaceutical family. Net worth $10B+.', charge:'Deceptive opioid marketing (500K+ deaths)', atty:'Top-tier law firms nationwide', bail:'Not applicable', sentence:'Civil settlement ~$6B. No jail.', guide:'Decades for fraud', bailC:'g', sentC:'g', note:'500,000 Americans died. The family paid billions and kept billions more. Zero criminal charges for any individual family member.' },
  ],
  'Low-Income': [
    { name:'Paul Carter', bg:'New Orleans resident struggling with heroin addiction. No financial resources.', charge:'Drug possession (trace heroin residue)', atty:'Public defender (overworked)', bail:'Could not post - jailed pretrial', sentence:'10 years (initial)', guide:'0–2 years (typical)', bailC:'r', sentC:'r', note:'Offense involved trace amounts prosecutors called "too insignificant to weigh." Could not post bail, jailed pretrial, pressured into a plea. Received 10 years.' },
    { name:'Sandra Bland', bg:'Black woman stopped for a minor traffic violation. Could not afford bail.', charge:'Failure to signal (traffic stop)', atty:'None assigned in time', bail:'$5,000 - could not post', sentence:'Died in jail after 3 days', guide:'Fine only (traffic)', bailC:'r', sentC:'r', note:'Arrested over a minor traffic stop. Died in custody after 3 days because she could not post $5,000 bail. Never went to trial.' },
    { name:'Kalief Browder', bg:'16-year-old accused of stealing a backpack. Family could not afford bail.', charge:'Robbery (alleged — never proven)', atty:'Public defender', bail:'$3,000 - family could not post', sentence:'3 years Rikers (no trial) - case dismissed', guide:'Charges dismissed', bailC:'r', sentC:'r', note:'Held at Rikers Island for 3 years,including 2 in solitary confinement, without ever being convicted. Case dismissed. Browder died by suicide in 2015.' },
    { name:'Fate Vincent Winslow', bg:'Homeless man in Louisiana. No income, no legal resources.', charge:'Selling $20 worth of marijuana to undercover officer', atty:'Public defender', bail:'Could not post - jailed pretrial', sentence:'Life in prison without parole', guide:'Mandatory minimum (repeat)', bailC:'r', sentC:'r', note:'Sold $20 of marijuana to survive. Sentenced to life without parole under Louisiana\'s habitual offender law. Never had resources to mount a real defense.' },
    { name:'Corvain Cooper', bg:'First-time non-violent drug offender. No wealth or connections.', charge:'Marijuana conspiracy (non-violent)', atty:'Public defender', bail:'Denied - held pretrial', sentence:'Life in prison without parole', guide:'Mandatory minimum', bailC:'r', sentC:'r', note:'Given life without parole for a non-violent marijuana offense. Commuted in 2020 only after years of public advocacy.' },
    { name:'Richard Wershe Jr.', bg:'Teen FBI informant from Detroit. Arrested at 17, no legal resources.', charge:'Drug possession (cocaine) at age 17', atty:'Public defender', bail:'Denied', sentence:'Life in prison - served 30 years', guide:'Mandatory minimum', bailC:'r', sentC:'r', note:'Worked as an FBI informant as a teenager, then was arrested on drug charges. Given life at 17. Released in 2020 after 30 years, far longer than many violent offenders.' },
  ]
};

// ── Navigation ─────────────────────────────────────────────────────────────────
function show(id) {
  document.querySelectorAll('.section').forEach(s => s.classList.remove('active'));
  document.querySelectorAll('.nav-link').forEach(b => b.classList.remove('active'));
  document.getElementById(id).classList.add('active');
  document.querySelectorAll('.nav-link').forEach(b => {
    if (b.getAttribute('onclick') && b.getAttribute('onclick').includes("'" + id + "'"))
      b.classList.add('active');
  });
  window.scrollTo(0, 0);
}

// ── Case expand ────────────────────────────────────────────────────────────────
function toggle(el) {
  el.querySelector('.case-expand').classList.toggle('open');
}

// ── Compare tool ───────────────────────────────────────────────────────────────
let lCat = 'Politicians', rCat = 'Low-Income';

function catClass(cat) {
  return cat === 'Politicians' ? 'cat-pol'
       : cat === 'Celebrities' ? 'cat-cel'
       : cat === 'Billionaires' ? 'cat-bil'
       : 'cat-low';
}
function tagClass(cat) {
  return cat === 'Politicians' ? 'tag-pol'
       : cat === 'Celebrities' ? 'tag-cel'
       : cat === 'Billionaires' ? 'tag-bil'
       : 'tag-low';
}

function filterCat(side, cat, btn) {
  if (side === 'l') lCat = cat; else rCat = cat;
  const row = document.getElementById(side + 'cat');
  row.querySelectorAll('.cat-btn').forEach(b => { b.className = 'cat-btn'; });
  btn.className = 'cat-btn ' + catClass(cat);
  populateSelect(side);
  render();
}

function populateSelect(side) {
  const cat = side === 'l' ? lCat : rCat;
  const sel = document.getElementById(side + 'sel');
  sel.innerHTML = '<option value="">— choose a defendant —</option>';
  allCases[cat].forEach((c, i) => {
    const opt = document.createElement('option');
    opt.value = cat + '|' + i;
    opt.textContent = c.name;
    sel.appendChild(opt);
  });
}

function getSelected(side) {
  const val = document.getElementById(side + 'sel').value;
  if (!val) return null;
  const parts = val.split('|');
  return { cat: parts[0], data: allCases[parts[0]][parseInt(parts[1])] };
}

function buildInner(sel) {
  const c = sel.data, cat = sel.cat;
  return `
    <div class="cmp-tag ${tagClass(cat)}">${cat}</div>
    <div class="cmp-name">${c.name}</div>
    <div class="cmp-bg">${c.bg}</div>
    <div class="cmp-row"><span class="cmp-key">Charge</span><span class="cmp-val">${c.charge}</span></div>
    <div class="cmp-row"><span class="cmp-key">Attorney</span><span class="cmp-val">${c.atty}</span></div>
    <div class="cmp-row"><span class="cmp-key">Bail</span><span class="cmp-val ${c.bailC}">${c.bail}</span></div>
    <div class="cmp-row"><span class="cmp-key">Sentence</span><span class="cmp-val ${c.sentC}">${c.sentence}</span></div>
    <div class="cmp-row"><span class="cmp-key">Guideline</span><span class="cmp-val">${c.guide}</span></div>`;
}

function render() {
  const l = getSelected('l'), r = getSelected('r');
  const lCard = document.getElementById('left-card');
  const rCard = document.getElementById('right-card');

  if (l) {
    lCard.innerHTML = buildInner(l);
    lCard.className = 'cmp-card' + (l.cat === 'Low-Income' ? ' low-income' : '');
  } else {
    lCard.innerHTML = '<div class="empty-text">Select a defendant<br>on the left to begin</div>';
    lCard.className = 'empty-card';
  }

  if (r) {
    rCard.innerHTML = buildInner(r);
    rCard.className = 'cmp-card' + (r.cat === 'Low-Income' ? ' low-income' : '');
  } else {
    rCard.innerHTML = '<div class="empty-text">Select a defendant<br>on the right to begin</div>';
    rCard.className = 'empty-card';
  }

  const noteBox = document.getElementById('note-box');
  const diffBox = document.getElementById('diff-box');
  const diffContent = document.getElementById('diff-content');

  if (l && r) {
    noteBox.textContent = l.data.note + ' Meanwhile: ' + r.data.note;
    diffBox.classList.add('show');
    diffContent.innerHTML = `
      <div class="diff-row">
        <div class="diff-dot r"></div>
        <div class="diff-text"><strong>${l.data.name}</strong> - Sentence: ${l.data.sentence} | Bail: ${l.data.bail} | Attorney: ${l.data.atty}</div>
      </div>
      <div class="diff-row">
        <div class="diff-dot b"></div>
        <div class="diff-text"><strong>${r.data.name}</strong> - Sentence: ${r.data.sentence} | Bail: ${r.data.bail} | Attorney: ${r.data.atty}</div>
      </div>`;
  } else {
    noteBox.textContent = 'Select two defendants above to see a comparison note.';
    diffBox.classList.remove('show');
  }
}

function init() {
  populateSelect('l');
  populateSelect('r');
  document.getElementById('lsel').value = 'Politicians|0';
  document.getElementById('rsel').value = 'Low-Income|0';
  render();
}

init();
</script>
</body>
</html>
