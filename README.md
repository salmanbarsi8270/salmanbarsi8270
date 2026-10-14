<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Salman Barsi · AI Agents & Full‑Stack</title>
  <!-- Font Awesome for subtle icon accents (optional) -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <style>
    /* minimal reset + background to make the README pop */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background: #0b0e14;
      font-family: 'Inter', system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
      display: flex;
      justify-content: center;
      padding: 2rem 1rem;
      line-height: 1.5;
    }

    /* main container – same width as typical GitHub README (max 900px) */
    .readme-container {
      max-width: 960px;
      width: 100%;
      background: transparent;
      color: #e6edf3;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 0.5rem;
    }

    /* ---------- global animation keyframes ---------- */
    @keyframes floatGlow {
      0% { filter: drop-shadow(0 0 2px rgba(54, 188, 247, 0.2)); }
      50% { filter: drop-shadow(0 0 12px rgba(54, 188, 247, 0.6)); }
      100% { filter: drop-shadow(0 0 2px rgba(54, 188, 247, 0.2)); }
    }

    @keyframes softPulse {
      0% { opacity: 0.9; transform: scale(1); }
      50% { opacity: 1; transform: scale(1.02); }
      100% { opacity: 0.9; transform: scale(1); }
    }

    @keyframes slideUpFade {
      0% { opacity: 0; transform: translateY(12px); }
      100% { opacity: 1; transform: translateY(0); }
    }

    @keyframes shimmer {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }

    /* ---------- animated header ---------- */
    .header-wrapper {
      width: 100%;
      border-radius: 28px;
      overflow: hidden;
      margin-bottom: 0.5rem;
      animation: slideUpFade 0.8s cubic-bezier(0.2, 0.9, 0.3, 1) forwards;
      box-shadow: 0 10px 30px -10px rgba(0, 0, 0, 0.6);
    }

    .header-wrapper img {
      display: block;
      width: 100%;
      height: auto;
    }

    /* typing animation container – subtle float + glow */
    .typing-wrapper {
      margin: 0.75rem 0 0.25rem;
      animation: slideUpFade 0.8s 0.1s cubic-bezier(0.2, 0.9, 0.3, 1) both;
    }

    .typing-wrapper img {
      display: block;
      max-width: 100%;
      height: auto;
      transition: filter 0.3s ease;
      animation: floatGlow 3.5s infinite ease-in-out;
    }

    .typing-wrapper img:hover {
      filter: drop-shadow(0 0 20px rgba(54, 188, 247, 0.7));
    }

    /* profile views + followers row */
    .badge-row {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      align-items: center;
      gap: 1rem;
      margin: 0.25rem 0 1rem;
      animation: slideUpFade 0.8s 0.2s cubic-bezier(0.2, 0.9, 0.3, 1) both;
    }

    .badge-row img {
      display: block;
      height: 28px;
      width: auto;
      transition: transform 0.2s ease, filter 0.2s;
      border-radius: 6px;
    }

    .badge-row img:hover {
      transform: scale(1.05);
      filter: brightness(1.2);
    }

    /* horizontal rule – gradient */
    .hr-gradient {
      width: 100%;
      height: 2px;
      background: linear-gradient(90deg, transparent, #36bcf7, #a855f7, #36bcf7, transparent);
      background-size: 200% auto;
      border: none;
      margin: 1rem 0 0.75rem;
      animation: shimmer 4s linear infinite;
      border-radius: 2px;
    }

    /* section titles */
    .section-title {
      font-size: 1.8rem;
      font-weight: 700;
      letter-spacing: -0.02em;
      margin: 1.2rem 0 0.5rem;
      display: flex;
      align-items: center;
      gap: 0.6rem;
      color: #f0f6fc;
      animation: slideUpFade 0.8s 0.3s cubic-bezier(0.2, 0.9, 0.3, 1) both;
    }

    .section-title i, .section-title span {
      font-size: 2rem;
      background: linear-gradient(135deg, #36bcf7, #a855f7);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }

    /* project cards (table/stack) */
    .platform-card {
      background: rgba(22, 27, 34, 0.8);
      backdrop-filter: blur(4px);
      border: 1px solid #30363d;
      border-radius: 24px;
      padding: 1.25rem 1.5rem;
      width: 100%;
      box-shadow: 0 8px 20px rgba(0, 0, 0, 0.4);
      transition: border-color 0.3s, box-shadow 0.3s, transform 0.3s;
      animation: slideUpFade 0.8s 0.35s cubic-bezier(0.2, 0.9, 0.3, 1) both;
    }

    .platform-card:hover {
      border-color: #36bcf7;
      box-shadow: 0 8px 30px rgba(54, 188, 247, 0.15);
      transform: translateY(-2px);
    }

    .layer-grid {
      display: flex;
      flex-wrap: wrap;
      gap: 1rem;
      justify-content: space-between;
      margin: 1rem 0 0.5rem;
    }

    .layer-item {
      flex: 1 1 150px;
      background: #1c2128;
      border-radius: 16px;
      padding: 1rem 0.75rem;
      text-align: center;
      border: 1px solid #2d333b;
      transition: all 0.25s ease;
      animation: softPulse 3s infinite ease-in-out;
      animation-delay: calc(var(--i) * 0.2s);
    }

    .layer-item:nth-child(1) { --i: 0; }
    .layer-item:nth-child(2) { --i: 1; }
    .layer-item:nth-child(3) { --i: 2; }

    .layer-item:hover {
      border-color: #36bcf7;
      background: #1f2937;
      transform: scale(1.02);
      animation-play-state: paused;
    }

    .layer-item .emoji {
      font-size: 2rem;
      display: block;
      margin-bottom: 0.4rem;
    }

    .layer-item .layer-name {
      font-weight: 600;
      font-size: 1rem;
      color: #e6edf3;
    }

    .layer-item .layer-desc {
      font-size: 0.85rem;
      color: #8b949e;
      margin-top: 0.2rem;
    }

    /* tech stack icons */
    .tech-icons {
      margin: 0.75rem 0 1.25rem;
      display: flex;
      justify-content: center;
      animation: slideUpFade 0.8s 0.45s cubic-bezier(0.2, 0.9, 0.3, 1) both;
      transition: filter 0.3s;
    }

    .tech-icons img {
      max-width: 100%;
      height: auto;
      filter: drop-shadow(0 0 6px rgba(54, 188, 247, 0.3));
      transition: filter 0.3s, transform 0.3s;
    }

    .tech-icons img:hover {
      filter: drop-shadow(0 0 18px rgba(54, 188, 247, 0.8));
      transform: scale(1.01);
    }

    /* details / projects */
    .projects-container {
      width: 100%;
      display: flex;
      flex-direction: column;
      gap: 1rem;
      animation: slideUpFade 0.8s 0.5s cubic-bezier(0.2, 0.9, 0.3, 1) both;
    }

    details {
      background: #161b22;
      border-radius: 18px;
      border: 1px solid #30363d;
      padding: 0.25rem 0.25rem 0.25rem 0.25rem;
      transition: all 0.3s ease;
      overflow: hidden;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
      animation: softPulse 4s infinite ease-in-out;
      animation-delay: calc(var(--d) * 0.3s);
    }

    details[open] {
      border-color: #36bcf7;
      box-shadow: 0 8px 20px rgba(54, 188, 247, 0.15);
      animation-play-state: paused;
    }

    details:nth-child(1) { --d: 0; }
    details:nth-child(2) { --d: 1; }
    details:nth-child(3) { --d: 2; }
    details:nth-child(4) { --d: 3; }

    summary {
      cursor: pointer;
      padding: 1rem 1.25rem;
      font-weight: 600;
      font-size: 1.1rem;
      list-style: none;
      display: flex;
      align-items: center;
      justify-content: space-between;
      color: #f0f6fc;
      transition: background 0.2s, color 0.2s;
      border-radius: 16px;
    }

    summary::-webkit-details-marker {
      display: none;
    }

    summary::after {
      content: '\f078'; /* chevron down */
      font-family: 'Font Awesome 6 Free';
      font-weight: 900;
      font-size: 0.9rem;
      color: #36bcf7;
      transition: transform 0.3s ease;
    }

    details[open] summary::after {
      transform: rotate(180deg);
    }

    summary:hover {
      background: #1f2937;
      color: #ffffff;
    }

    .details-content {
      padding: 0.25rem 1.25rem 1.25rem 1.25rem;
      color: #c9d1d9;
      border-top: 1px solid #30363d;
      margin-top: 0.25rem;
      animation: slideUpFade 0.4s ease both;
    }

    .details-content p {
      margin: 0.5rem 0;
      font-size: 0.95rem;
    }

    .details-content a {
      color: #58a6ff;
      text-decoration: none;
      font-weight: 500;
      transition: color 0.2s, text-shadow 0.2s;
      display: inline-flex;
      align-items: center;
      gap: 0.4rem;
      margin-right: 1rem;
    }

    .details-content a:hover {
      color: #79c0ff;
      text-shadow: 0 0 8px rgba(88, 166, 255, 0.6);
    }

    .details-content a i {
      font-size: 0.9rem;
    }

    /* stats grid */
    .stats-grid {
      display: flex;
      flex-wrap: wrap;
      gap: 1.25rem;
      justify-content: center;
      width: 100%;
      margin: 1rem 0 0.5rem;
      animation: slideUpFade 0.8s 0.55s cubic-bezier(0.2, 0.9, 0.3, 1) both;
    }

    .stats-grid > div {
      background: #161b22;
      border-radius: 20px;
      padding: 0.75rem;
      border: 1px solid #30363d;
      transition: border-color 0.3s, box-shadow 0.3s;
      animation: softPulse 5s infinite ease-in-out;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .stats-grid > div:hover {
      border-color: #36bcf7;
      box-shadow: 0 0 20px rgba(54, 188, 247, 0.2);
      animation-play-state: paused;
    }

    .stats-grid img {
      max-width: 100%;
      height: auto;
      border-radius: 12px;
    }

    /* activity graph + streak */
    .graph-block {
      width: 100%;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 1.25rem;
      margin: 0.5rem 0;
      animation: slideUpFade 0.8s 0.6s cubic-bezier(0.2, 0.9, 0.3, 1) both;
    }

    .graph-block > div {
      width: 100%;
      background: #161b22;
      border-radius: 24px;
      padding: 1rem 0.75rem;
      border: 1px solid #30363d;
      transition: border-color 0.3s, box-shadow 0.3s;
      animation: softPulse 5s infinite ease-in-out;
      animation-delay: 0.2s;
    }

    .graph-block > div:hover {
      border-color: #36bcf7;
      box-shadow: 0 0 22px rgba(54, 188, 247, 0.2);
    }

    .graph-block img {
      width: 100%;
      height: auto;
      display: block;
      border-radius: 12px;
    }

    /* snake */
    .snake-wrapper {
      width: 100%;
      display: flex;
      justify-content: center;
      background: #0d1117;
      border-radius: 28px;
      padding: 1.25rem 0.5rem;
      border: 1px solid #30363d;
      margin: 0.5rem 0 0.75rem;
      animation: slideUpFade 0.8s 0.65s cubic-bezier(0.2, 0.9, 0.3, 1) both;
      transition: border-color 0.3s;
    }

    .snake-wrapper:hover {
      border-color: #a855f7;
    }

    .snake-wrapper img {
      max-width: 100%;
      height: auto;
      border-radius: 16px;
      animation: floatGlow 4s infinite ease-in-out;
    }

    /* connect buttons */
    .connect-row {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 1rem;
      margin: 0.5rem 0 0.75rem;
      animation: slideUpFade 0.8s 0.7s cubic-bezier(0.2, 0.9, 0.3, 1) both;
    }

    .connect-row a {
      transition: transform 0.25s, filter 0.25s;
      display: inline-block;
    }

    .connect-row a:hover {
      transform: translateY(-5px) scale(1.03);
      filter: drop-shadow(0 0 16px rgba(54, 188, 247, 0.8));
    }

    .connect-row img {
      display: block;
      height: 36px;
      width: auto;
      border-radius: 8px;
    }

    /* footer wave */
    .footer-wave {
      width: 100%;
      margin-top: 1rem;
      animation: slideUpFade 0.8s 0.75s cubic-bezier(0.2, 0.9, 0.3, 1) both;
    }

    .footer-wave img {
      display: block;
      width: 100%;
      height: auto;
    }

    /* ensure everything stays centered */
    .center-flex {
      display: flex;
      justify-content: center;
      align-items: center;
      width: 100%;
    }

    /* small screens */
    @media (max-width: 600px) {
      .section-title { font-size: 1.5rem; }
      summary { font-size: 1rem; padding: 0.85rem; }
      .layer-item { flex: 1 1 100%; }
    }
  </style>
</head>
<body>
<div class="readme-container">

  <!-- Animated header with extra glow -->
  <div class="header-wrapper">
    <img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=200&section=header&text=Salman%20Barsi&fontSize=52&fontAlignY=38&animation=fadeIn&desc=AI%20Agents%20%7C%20Full-Stack%20Developer&descAlignY=60&descSize=18" alt="header" />
  </div>

  <!-- Typing animation (float + glow) -->
  <div class="typing-wrapper">
    <a href="https://github.com/salmanbarsi8270" style="text-decoration: none;">
      <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&pause=1200&color=36BCF7&center=true&vCenter=true&width=650&lines=Building+AI+agent+platforms+end+to+end;Frontend-leaning+full-stack+developer;React+%7C+Next.js+%7C+React+Native+%7C+Node.js;Turning+LLMs+into+real+products" alt="Typing SVG" />
    </a>
  </div>

  <!-- badges: profile views + followers -->
  <div class="badge-row">
    <img src="https://komarev.com/ghpvc/?username=salmanbarsi8270&label=Profile%20views&color=0e75b6&style=flat" alt="profile views" />
    <a href="https://github.com/salmanbarsi8270?tab=followers" style="text-decoration: none;">
      <img src="https://img.shields.io/github/followers/salmanbarsi8270?style=flat&logo=github&label=Followers" alt="followers" />
    </a>
  </div>

  <hr class="hr-gradient" />

  <!-- Currently building -->
  <div class="section-title">
    <span>🚀</span> Currently building
  </div>
  <div class="platform-card">
    <p style="font-size: 1.1rem; margin-bottom: 0.25rem;"><strong>Platform4x</strong> — a multi‑app AI agent platform with three layers:</p>
    <div class="layer-grid">
      <div class="layer-item">
        <span class="emoji">🎨</span>
        <div class="layer-name">Frontend</div>
        <div class="layer-desc">React / Next.js / TypeScript UI</div>
      </div>
      <div class="layer-item">
        <span class="emoji">⚙️</span>
        <div class="layer-name">API backend</div>
        <div class="layer-desc">Node.js services & agent engine</div>
      </div>
      <div class="layer-item">
        <span class="emoji">🧠</span>
        <div class="layer-name">AI engine</div>
        <div class="layer-desc">Agent orchestration, tool calling</div>
      </div>
    </div>
  </div>

  <hr class="hr-gradient" />

  <!-- Tech stack -->
  <div class="section-title">
    <span>🛠️</span> Tech stack
  </div>
  <div class="tech-icons">
    <img src="https://skillicons.dev/icons?i=ts,js,react,nextjs,nodejs,py,tailwind,git,vercel,docker&perline=10" alt="skills" />
  </div>

  <hr class="hr-gradient" />

  <!-- Featured projects -->
  <div class="section-title">
    <span>🧪</span> Featured projects
  </div>
  <div class="projects-container">

    <details>
      <summary><b>💬 Nextjs_AI_sdk</b>: streaming AI chat app</summary>
      <div class="details-content">
        <p>Next.js + Vercel AI SDK, deployed on Vercel.</p>
        <p>
          <a href="https://chatapp-two-murex.vercel.app/" target="_blank"><i class="fas fa-external-link-alt"></i> Live demo</a>
          <a href="https://github.com/salmanbarsi8270/Nextjs_AI_sdk" target="_blank"><i class="fab fa-github"></i> Source</a>
        </p>
      </div>
    </details>

    <details>
      <summary><b>📱 Reactnative_Ai_sdk</b>: AI chat on mobile</summary>
      <div class="details-content">
        <p>React Native + AI SDK.</p>
        <p>
          <a href="https://github.com/salmanbarsi8270/Reactnative_Ai_sdk" target="_blank"><i class="fab fa-github"></i> Source</a>
        </p>
      </div>
    </details>

    <details>
      <summary><b>🗄️ Nextjs_Mssql_crud</b>: CRUD with MSSQL</summary>
      <div class="details-content">
        <p>Next.js + MSSQL + AI SDK.</p>
        <p>
          <a href="https://github.com/salmanbarsi8270/Nextjs_Mssql_crud" target="_blank"><i class="fab fa-github"></i> Source</a>
        </p>
      </div>
    </details>

    <details>
      <summary><b>✉️ Reactnative_mailsender</b>: mobile email sender</summary>
      <div class="details-content">
        <p>React Native + TypeScript.</p>
        <p>
          <a href="https://github.com/salmanbarsi8270/Reactnative_mailsender" target="_blank"><i class="fab fa-github"></i> Source</a>
        </p>
      </div>
    </details>

  </div>

  <hr class="hr-gradient" />

  <!-- GitHub stats -->
  <div class="section-title">
    <span>📊</span> GitHub stats
  </div>

  <div class="stats-grid">
    <div>
      <img height="170" src="https://github-readme-stats.vercel.app/api?username=salmanbarsi8270&show_icons=true&theme=tokyonight&hide_border=true&rank_icon=github" alt="stats" />
    </div>
    <div>
      <img height="170" src="https://github-readme-stats.vercel.app/api/top-langs/?username=salmanbarsi8270&layout=compact&theme=tokyonight&hide_border=true" alt="top langs" />
    </div>
  </div>

  <div class="graph-block">
    <div>
      <img src="https://streak-stats.demolab.com?user=salmanbarsi8270&theme=tokyonight&hide_border=true" alt="streak" />
    </div>
    <div>
      <img src="https://github-readme-activity-graph.vercel.app/graph?username=salmanbarsi8270&theme=tokyo-night&hide_border=true&area=true" alt="activity graph" />
    </div>
  </div>

  <hr class="hr-gradient" />

  <!-- Snake -->
  <div class="section-title">
    <span>🐍</span> Contribution snake
  </div>
  <div class="snake-wrapper">
    <img src="https://raw.githubusercontent.com/salmanbarsi8270/salmanbarsi8270/output/github-snake-dark.svg" alt="snake animation" />
  </div>

  <hr class="hr-gradient" />

  <!-- Connect -->
  <div class="section-title">
    <span>📫</span> Let's connect
  </div>
  <div class="connect-row">
    <a href="https://www.linkedin.com/in/YOUR-ID" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
    <a href="mailto:you@example.com"><img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" /></a>
    <a href="https://YOUR-PORTFOLIO.com" target="_blank"><img src="https://img.shields.io/badge/Portfolio-000000?style=for-the-badge&logo=vercel&logoColor=white" alt="Portfolio" /></a>
  </div>

  <!-- Footer wave -->
  <div class="footer-wave">
    <img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=100&section=footer" width="100%" alt="footer" />
  </div>

</div>
</body>
</html>
