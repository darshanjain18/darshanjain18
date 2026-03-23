<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Darshan Jain</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Mono:ital,wght@0,300;0,400;1,300&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #0a0a0f;
    --surface: #111118;
    --border: #1e1e2e;
    --accent: #7c6aff;
    --accent2: #ff6a9e;
    --accent3: #6affd4;
    --text: #e8e8f0;
    --muted: #6b6b8a;
    --glow: rgba(124,106,255,0.25);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Syne', sans-serif;
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 40px 20px;
    overflow-x: hidden;
  }

  /* Background grid */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(var(--border) 1px, transparent 1px),
      linear-gradient(90deg, var(--border) 1px, transparent 1px);
    background-size: 48px 48px;
    opacity: 0.4;
    pointer-events: none;
    z-index: 0;
  }

  /* Ambient blobs */
  body::after {
    content: '';
    position: fixed;
    width: 600px;
    height: 600px;
    background: radial-gradient(circle, rgba(124,106,255,0.12) 0%, transparent 70%);
    top: -100px; left: -100px;
    pointer-events: none;
    z-index: 0;
    animation: blobDrift 12s ease-in-out infinite alternate;
  }

  @keyframes blobDrift {
    from { transform: translate(0, 0); }
    to   { transform: translate(80px, 60px); }
  }

  .card {
    position: relative;
    z-index: 1;
    max-width: 680px;
    width: 100%;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 24px;
    padding: 56px 52px;
    animation: fadeUp 0.8s cubic-bezier(0.16,1,0.3,1) both;
    overflow: hidden;
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(40px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  /* Corner accent line */
  .card::before {
    content: '';
    position: absolute;
    top: 0; left: 0;
    width: 160px; height: 4px;
    background: linear-gradient(90deg, var(--accent), var(--accent2));
    border-radius: 0 0 4px 0;
  }

  .card::after {
    content: '';
    position: absolute;
    bottom: -120px; right: -120px;
    width: 360px; height: 360px;
    background: radial-gradient(circle, rgba(106,255,212,0.07) 0%, transparent 70%);
    pointer-events: none;
  }

  /* Header */
  .header {
    display: flex;
    align-items: flex-start;
    gap: 28px;
    margin-bottom: 40px;
    animation: fadeUp 0.8s 0.1s cubic-bezier(0.16,1,0.3,1) both;
  }

  .avatar {
    flex-shrink: 0;
    width: 72px; height: 72px;
    border-radius: 18px;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    display: flex; align-items: center; justify-content: center;
    font-size: 28px; font-weight: 800;
    color: #fff;
    position: relative;
    box-shadow: 0 0 32px rgba(124,106,255,0.45);
  }

  .avatar::after {
    content: '';
    position: absolute;
    inset: -3px;
    border-radius: 20px;
    background: linear-gradient(135deg, var(--accent), var(--accent2), var(--accent3));
    z-index: -1;
    opacity: 0.5;
  }

  .header-text h1 {
    font-size: 2rem;
    font-weight: 800;
    line-height: 1.1;
    background: linear-gradient(135deg, var(--text) 40%, var(--accent));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .header-text .wave { display: inline-block; animation: wave 2s infinite; }
  @keyframes wave {
    0%,100% { transform: rotate(0deg); }
    25%      { transform: rotate(20deg); }
    75%      { transform: rotate(-10deg); }
  }

  .status-badge {
    display: inline-flex;
    align-items: center;
    gap: 7px;
    margin-top: 10px;
    background: rgba(124,106,255,0.1);
    border: 1px solid rgba(124,106,255,0.3);
    color: var(--accent);
    font-family: 'DM Mono', monospace;
    font-size: 0.72rem;
    padding: 4px 12px;
    border-radius: 100px;
    letter-spacing: 0.04em;
  }

  .status-dot {
    width: 7px; height: 7px;
    border-radius: 50%;
    background: var(--accent3);
    box-shadow: 0 0 8px var(--accent3);
    animation: pulse 2s infinite;
  }

  @keyframes pulse {
    0%,100% { opacity: 1; }
    50%      { opacity: 0.4; }
  }

  /* Divider */
  .divider {
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--border), transparent);
    margin: 32px 0;
  }

  /* Bio */
  .bio {
    animation: fadeUp 0.8s 0.2s cubic-bezier(0.16,1,0.3,1) both;
  }

  .bio p {
    font-size: 1rem;
    line-height: 1.75;
    color: #b0b0cc;
    margin-bottom: 16px;
  }

  .bio strong { color: var(--text); }

  .quote-block {
    border-left: 3px solid var(--accent);
    padding: 12px 20px;
    margin-top: 20px;
    background: rgba(124,106,255,0.05);
    border-radius: 0 10px 10px 0;
    font-family: 'DM Mono', monospace;
    font-style: italic;
    font-size: 0.82rem;
    color: var(--muted);
    line-height: 1.6;
  }

  /* Tags */
  .tags {
    display: flex; flex-wrap: wrap; gap: 10px;
    margin-top: 28px;
    animation: fadeUp 0.8s 0.3s cubic-bezier(0.16,1,0.3,1) both;
  }

  .tag {
    font-family: 'DM Mono', monospace;
    font-size: 0.72rem;
    padding: 5px 14px;
    border-radius: 8px;
    border: 1px solid;
    letter-spacing: 0.05em;
    text-transform: uppercase;
    transition: transform 0.2s, box-shadow 0.2s;
    cursor: default;
  }

  .tag:hover { transform: translateY(-2px); }

  .tag-fe  { color: var(--accent);  border-color: rgba(124,106,255,0.35); background: rgba(124,106,255,0.08); }
  .tag-fs  { color: var(--accent2); border-color: rgba(255,106,158,0.35); background: rgba(255,106,158,0.08); }
  .tag-da  { color: var(--accent3); border-color: rgba(106,255,212,0.35); background: rgba(106,255,212,0.08); }
  .tag-ds  { color: #ffd06a;        border-color: rgba(255,208,106,0.35); background: rgba(255,208,106,0.08); }

  /* Links section */
  .links {
    margin-top: 36px;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 14px;
    animation: fadeUp 0.8s 0.4s cubic-bezier(0.16,1,0.3,1) both;
  }

  .link-btn {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 14px 18px;
    border-radius: 14px;
    border: 1px solid var(--border);
    background: rgba(255,255,255,0.02);
    text-decoration: none;
    color: var(--text);
    font-size: 0.88rem;
    font-weight: 600;
    transition: all 0.25s ease;
    position: relative;
    overflow: hidden;
  }

  .link-btn::before {
    content: '';
    position: absolute;
    inset: 0;
    opacity: 0;
    transition: opacity 0.25s;
  }

  .link-btn:hover { transform: translateY(-3px); box-shadow: 0 8px 32px rgba(0,0,0,0.4); }

  .link-btn.li  { --clr: #0a66c2; }
  .link-btn.ig  { --clr: #e1306c; }
  .link-btn.em  { --clr: #ea4335; }
  .link-btn.cv  { --clr: var(--accent3); }

  .link-btn:hover { border-color: var(--clr); background: rgba(255,255,255,0.04); }
  .link-btn:hover .link-icon { background: var(--clr); box-shadow: 0 0 16px color-mix(in srgb, var(--clr) 60%, transparent); }

  .link-icon {
    width: 36px; height: 36px;
    border-radius: 10px;
    background: var(--border);
    display: flex; align-items: center; justify-content: center;
    font-size: 1.05rem;
    flex-shrink: 0;
    transition: background 0.25s, box-shadow 0.25s;
  }

  .link-arrow {
    margin-left: auto;
    color: var(--muted);
    font-size: 0.8rem;
    transition: transform 0.2s, color 0.2s;
  }

  .link-btn:hover .link-arrow { transform: translate(3px, -3px); color: var(--text); }

  /* Footer mono */
  .footer-mono {
    margin-top: 36px;
    font-family: 'DM Mono', monospace;
    font-size: 0.7rem;
    color: var(--muted);
    display: flex;
    align-items: center;
    gap: 10px;
    animation: fadeUp 0.8s 0.5s cubic-bezier(0.16,1,0.3,1) both;
  }

  .footer-mono span { color: var(--accent); }

  @media (max-width: 520px) {
    .card { padding: 36px 28px; }
    .links { grid-template-columns: 1fr; }
    .header { flex-direction: column; gap: 18px; }
    .header-text h1 { font-size: 1.6rem; }
  }
</style>
</head>
<body>

<div class="card">

  <div class="header">
    <div class="avatar">DJ</div>
    <div class="header-text">
      <h1>Darshan Jain <span class="wave">👋</span></h1>
      <div class="status-badge">
        <span class="status-dot"></span>
        Open to opportunities
      </div>
    </div>
  </div>

  <div class="divider"></div>

  <div class="bio">
    <p>
      Computer Engineering student focused on building
      <strong>scalable frontend applications</strong>.
      Currently working across <strong>Full-Stack Development</strong> while
      venturing into <strong>Data Analytics</strong> as a Power BI Developer.
    </p>
    <p>
      Passionate about <strong>Data Science</strong> and turning raw data into
      meaningful, data-driven insights that solve real-world problems.
    </p>
    <div class="quote-block">
      "Learning continuously, building real-world projects,<br>
      and turning data into meaningful insights."
    </div>
  </div>

  <div class="tags">
    <span class="tag tag-fe">Frontend</span>
    <span class="tag tag-fs">Full-Stack</span>
    <span class="tag tag-da">Power BI</span>
    <span class="tag tag-ds">Data Science</span>
  </div>

  <div class="divider"></div>

  <div class="links">

    <a class="link-btn li" href="https://www.linkedin.com/in/darshan-jain-377372205/" target="_blank">
      <div class="link-icon">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 0 1-2.063-2.065 2.064 2.064 0 1 1 2.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
      </div>
      LinkedIn
      <span class="link-arrow">↗</span>
    </a>

    <a class="link-btn ig" href="https://instagram.com/darshann__18" target="_blank">
      <div class="link-icon">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zM12 0C8.741 0 8.333.014 7.053.072 2.695.272.273 2.69.073 7.052.014 8.333 0 8.741 0 12c0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98C8.333 23.986 8.741 24 12 24c3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98C15.668.014 15.259 0 12 0zm0 5.838a6.162 6.162 0 1 0 0 12.324 6.162 6.162 0 0 0 0-12.324zM12 16a4 4 0 1 1 0-8 4 4 0 0 1 0 8zm6.406-11.845a1.44 1.44 0 1 0 0 2.881 1.44 1.44 0 0 0 0-2.881z"/></svg>
      </div>
      Instagram
      <span class="link-arrow">↗</span>
    </a>

    <a class="link-btn em" href="mailto:jaindarshan1804@gmail.com" target="_blank">
      <div class="link-icon">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M24 5.457v13.909c0 .904-.732 1.636-1.636 1.636h-3.819V11.73L12 16.64l-6.545-4.91v9.273H1.636A1.636 1.636 0 0 1 0 19.366V5.457c0-2.023 2.309-3.178 3.927-1.964L5.455 4.64 12 9.548l6.545-4.91 1.528-1.145C21.69 2.28 24 3.434 24 5.457z"/></svg>
      </div>
      Email Me
      <span class="link-arrow">↗</span>
    </a>

    <a class="link-btn cv" href="https://drive.google.com/file/d/1qOP0_wDuO9mQ1a-H0y2QcFklOKPTaYiz/view?usp=sharing" target="_blank">
      <div class="link-icon">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8l-6-6zm-1 1.5L18.5 9H13V3.5zM6 20V4h5v7h7v9H6z"/></svg>
      </div>
      View Resume
      <span class="link-arrow">↗</span>
    </a>

  </div>

  <div class="footer-mono">
    <span>~/darshan</span> · CE Student · India 🇮🇳
  </div>

</div>

</body>
</html>
