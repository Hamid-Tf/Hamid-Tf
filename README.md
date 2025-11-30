<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

:root {
  --primary: #0066cc;
  --secondary: #00d4ff;
  --tertiary: #7000ff;
  --dark-bg: #0a0e27;
  --darker-bg: #050812;
  --card-bg: rgba(20, 30, 60, 0.4);
  --glass: rgba(255, 255, 255, 0.05);
  --glow-blue: rgba(0, 102, 204, 0.3);
  --text-primary: #e0e6ff;
  --text-secondary: #a8b5cc;
}

html, body {
  width: 100%;
  margin: 0;
  padding: 0;
}

.readme-container {
  width: 100%;
  background: linear-gradient(135deg, var(--darker-bg) 0%, var(--dark-bg) 50%, #1a0033 100%);
  color: var(--text-primary);
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Helvetica Neue', sans-serif;
  position: relative;
  overflow: hidden;
}

.animated-bg {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
  background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 800"><defs><filter id="noise"><feTurbulence type="fractalNoise" baseFrequency="0.9" numOctaves="4" result="noise" seed="2"/><feDisplacementMap in="SourceGraphic" in2="noise" scale="50"/></filter><linearGradient id="grad" x1="0%" y1="0%" x2="100%" y2="100%"><stop offset="0%" style="stop-color:%230066cc;stop-opacity:0.05"/><stop offset="100%" style="stop-color:%237000ff;stop-opacity:0.05"/></linearGradient></defs><rect width="1200" height="800" fill="url(%23grad)" filter="url(%23noise)"/></svg>') no-repeat center;
  background-size: cover;
  opacity: 0.3;
}

.hero {
  position: relative;
  text-align: center;
  padding: 60px 20px 40px;
  min-height: 400px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.wave-divider {
  width: 100%;
  height: 60px;
  background: linear-gradient(to right, var(--primary), var(--secondary), var(--tertiary), var(--primary));
  clip-path: polygon(0 30%, 2.5% 25%, 5% 30%, 7.5% 25%, 10% 30%, 12.5% 25%, 15% 30%, 17.5% 25%, 20% 30%, 22.5% 25%, 25% 30%, 27.5% 25%, 30% 30%, 32.5% 25%, 35% 30%, 37.5% 25%, 40% 30%, 42.5% 25%, 45% 30%, 47.5% 25%, 50% 30%, 52.5% 25%, 55% 30%, 57.5% 25%, 60% 30%, 62.5% 25%, 65% 30%, 67.5% 25%, 70% 30%, 72.5% 25%, 75% 30%, 77.5% 25%, 80% 30%, 82.5% 25%, 85% 30%, 87.5% 25%, 90% 30%, 92.5% 25%, 95% 30%, 97.5% 25%, 100% 30%, 100% 100%, 0 100%);
  animation: wave 8s ease-in-out infinite;
  margin-bottom: 20px;
}

@keyframes wave {
  0%, 100% { transform: translateX(0) translateY(0); }
  25% { transform: translateX(10px) translateY(-5px); }
  50% { transform: translateX(0) translateY(0); }
  75% { transform: translateX(-10px) translateY(-5px); }
}

.profile-orb-container {
  position: relative;
  width: 180px;
  height: 180px;
  margin: 40px auto;
  perspective: 1000px;
}

.profile-orb {
  width: 100%;
  height: 100%;
  border-radius: 50%;
  background: linear-gradient(135deg, var(--primary), var(--secondary));
  padding: 3px;
  position: relative;
  animation: float 4s ease-in-out infinite;
  transform-style: preserve-3d;
}

.profile-orb::before {
  content: '';
  position: absolute;
  top: -10px;
  left: -10px;
  right: -10px;
  bottom: -10px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(0, 102, 204, 0.4), transparent);
  animation: glow 2s ease-in-out infinite alternate;
}

.profile-orb img {
  width: 100%;
  height: 100%;
  border-radius: 50%;
  object-fit: cover;
  display: block;
  position: relative;
  z-index: 2;
}

@keyframes float {
  0%, 100% { transform: translateY(0) rotateX(0deg); }
  50% { transform: translateY(-25px) rotateX(5deg); }
}

@keyframes glow {
  from { box-shadow: 0 0 30px rgba(0, 102, 204, 0.4), 0 0 60px rgba(0, 212, 255, 0.2); }
  to { box-shadow: 0 0 50px rgba(0, 102, 204, 0.8), 0 0 100px rgba(0, 212, 255, 0.4); }
}

.title-container {
  margin: 30px 0;
  min-height: 80px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.name {
  font-size: 2.5em;
  font-weight: 800;
  background: linear-gradient(90deg, var(--primary), var(--secondary), var(--tertiary));
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  margin: 10px 0;
  line-height: 1.2;
}

.typing-animation {
  min-height: 50px;
  font-size: 1.3em;
  font-weight: 600;
  color: var(--secondary);
  letter-spacing: 2px;
  font-family: 'Courier New', monospace;
  position: relative;
}

.typing-animation::after {
  content: '';
  position: absolute;
  right: -8px;
  top: 50%;
  transform: translateY(-50%);
  height: 0.9em;
  width: 3px;
  background: var(--secondary);
  animation: blink 0.8s infinite;
}

@keyframes blink {
  0%, 49% { opacity: 1; }
  50%, 100% { opacity: 0; }
}

.subtitle {
  font-size: 1.1em;
  color: var(--text-secondary);
  margin-top: 15px;
  font-weight: 500;
}

.location-badge {
  display: inline-block;
  padding: 8px 16px;
  background: var(--card-bg);
  border: 1px solid var(--glow-blue);
  border-radius: 25px;
  margin-top: 15px;
  font-size: 0.95em;
  backdrop-filter: blur(10px);
  transition: all 0.3s ease;
}

.location-badge:hover {
  border-color: var(--secondary);
  box-shadow: 0 0 20px rgba(0, 212, 255, 0.3);
  transform: translateY(-2px);
}

.section {
  padding: 40px 20px;
  max-width: 1000px;
  margin: 0 auto;
}

.section-title {
  font-size: 1.8em;
  font-weight: 700;
  text-align: center;
  margin-bottom: 35px;
  position: relative;
  display: inline-block;
  width: 100%;
}

.section-title::after {
  content: '';
  position: absolute;
  bottom: -10px;
  left: 50%;
  transform: translateX(-50%);
  width: 80px;
  height: 3px;
  background: linear-gradient(90deg, var(--primary), var(--secondary), var(--tertiary));
  border-radius: 3px;
  animation: pulse 2s ease-in-out infinite;
}

@keyframes pulse {
  0%, 100% { width: 80px; opacity: 1; }
  50% { width: 120px; opacity: 0.7; }
}

.about-content {
  background: var(--card-bg);
  border: 1px solid rgba(0, 212, 255, 0.1);
  border-radius: 15px;
  padding: 30px;
  backdrop-filter: blur(15px);
  margin-top: 20px;
  line-height: 1.8;
  color: var(--text-secondary);
  animation: slideIn 0.6s ease-out;
}

@keyframes slideIn {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
  margin-top: 30px;
}

.stat-card {
  background: var(--card-bg);
  border: 1px solid rgba(0, 212, 255, 0.1);
  border-radius: 15px;
  padding: 25px;
  text-align: center;
  backdrop-filter: blur(15px);
  transition: all 0.3s ease;
  cursor: pointer;
  position: relative;
  overflow: hidden;
}

.stat-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(0, 212, 255, 0.1), transparent);
  animation: shimmer 3s infinite;
}

@keyframes shimmer {
  0% { left: -100%; }
  100% { left: 100%; }
}

.stat-card:hover {
  transform: translateY(-8px) rotateX(5deg);
  border-color: var(--secondary);
  box-shadow: 0 15px 40px rgba(0, 102, 204, 0.2), 0 0 20px rgba(0, 212, 255, 0.2);
}

.stat-number {
  font-size: 2.5em;
  font-weight: 800;
  background: linear-gradient(90deg, var(--primary), var(--secondary));
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  margin-bottom: 10px;
}

.stat-label {
  font-size: 0.95em;
  color: var(--text-secondary);
  font-weight: 600;
}

.tech-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
  gap: 15px;
  margin-top: 30px;
}

.tech-badge {
  background: var(--card-bg);
  border: 1px solid rgba(0, 212, 255, 0.1);
  border-radius: 12px;
  padding: 15px;
  text-align: center;
  font-size: 0.9em;
  font-weight: 600;
  backdrop-filter: blur(10px);
  transition: all 0.3s ease;
  cursor: pointer;
}

.tech-badge:hover {
  transform: translateY(-5px);
  border-color: var(--secondary);
  box-shadow: 0 10px 30px rgba(0, 212, 255, 0.2);
  color: var(--secondary);
}

.connect-section {
  text-align: center;
}

.connect-buttons {
  display: flex;
  flex-wrap: wrap;
  gap: 15px;
  justify-content: center;
  margin-top: 30px;
}

.connect-btn {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 12px 24px;
  background: var(--card-bg);
  border: 1px solid rgba(0, 212, 255, 0.2);
  border-radius: 10px;
  color: var(--text-primary);
  text-decoration: none;
  font-weight: 600;
  backdrop-filter: blur(10px);
  transition: all 0.3s ease;
  cursor: pointer;
}

.connect-btn:hover {
  transform: translateY(-3px);
  border-color: var(--secondary);
  box-shadow: 0 10px 30px rgba(0, 212, 255, 0.3);
  color: var(--secondary);
}

.icon-svg {
  width: 20px;
  height: 20px;
  display: inline-block;
}

.footer-section {
  text-align: center;
  padding: 50px 20px 40px;
  border-top: 1px solid rgba(0, 212, 255, 0.1);
}

.footer-quote {
  background: linear-gradient(135deg, var(--card-bg), rgba(0, 212, 255, 0.1));
  border: 1px solid rgba(0, 212, 255, 0.2);
  border-radius: 15px;
  padding: 30px;
  margin: 30px 0;
  font-size: 1.1em;
  font-style: italic;
  font-weight: 500;
  color: var(--secondary);
  backdrop-filter: blur(15px);
  line-height: 1.8;
}

.visitor-counter {
  margin: 30px 0;
  font-size: 0.9em;
  color: var(--text-secondary);
}

.footer-text {
  margin-top: 20px;
  color: var(--text-secondary);
  font-size: 0.95em;
}

@media (max-width: 768px) {
  .name {
    font-size: 1.8em;
  }

  .typing-animation {
    font-size: 1em;
  }

  .subtitle {
    font-size: 1em;
  }

  .tech-grid {
    grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
    gap: 12px;
  }

  .stats-grid {
    grid-template-columns: 1fr;
  }

  .connect-buttons {
    flex-direction: column;
  }

  .connect-btn {
    width: 100%;
    justify-content: center;
  }

  .section {
    padding: 30px 15px;
  }
}

@media (max-width: 480px) {
  .hero {
    padding: 40px 15px 30px;
  }

  .profile-orb-container {
    width: 140px;
    height: 140px;
    margin: 30px auto;
  }

  .name {
    font-size: 1.5em;
  }

  .typing-animation {
    font-size: 0.85em;
  }

  .section-title {
    font-size: 1.4em;
  }

  .tech-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}
</style>
</head>
<body>

<div class="animated-bg"></div>

<div class="readme-container">
  <!-- Hero Section -->
  <div class="hero">
    <div class="wave-divider"></div>

    <div class="profile-orb-container">
      <div class="profile-orb">
        <img src="https://hamidtf.me/images/settings/1758620651_favicon_apple-touch-icon.png" alt="Hamid Tafreshinia">
      </div>
    </div>

    <div class="title-container">
      <h1 class="name">Hamid Tafreshinia</h1>
      <div class="typing-animation">Web Developer × Backend Enthusiast</div>
      <p class="subtitle">Crafting elegant solutions, one pixel at a time</p>
      <div class="location-badge">
        <svg class="icon-svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"></path>
          <circle cx="12" cy="10" r="3"></circle>
        </svg>
        Qom, Iran
      </div>
    </div>
  </div>

  <!-- About Section -->
  <div class="section">
    <h2 class="section-title">About Me</h2>
    <div class="about-content">
      I'm a passionate web developer focused on creating clean, functional, and visually stunning digital experiences. With expertise spanning frontend design and backend architecture, I bridge the gap between beautiful UI and robust systems. Constantly exploring new technologies and best practices to deliver production-ready solutions that solve real problems.
    </div>
  </div>

  <!-- Stats Section -->
  <div class="section">
    <h2 class="section-title">Expertise Areas</h2>
    <div class="stats-grid">
      <div class="stat-card">
        <div class="stat-number">10+</div>
        <div class="stat-label">Projects Completed</div>
      </div>
      <div class="stat-card">
        <div class="stat-number">5+</div>
        <div class="stat-label">Years Experience</div>
      </div>
      <div class="stat-card">
        <div class="stat-number">100%</div>
        <div class="stat-label">Code Quality Focus</div>
      </div>
    </div>
  </div>

  <!-- Tech Stack Section -->
  <div class="section">
    <h2 class="section-title">Tech Arsenal</h2>

    <div style="margin-top: 40px;">
      <h3 style="color: var(--secondary); margin-bottom: 15px; text-align: center; font-size: 1.1em;">Frontend</h3>
      <div class="tech-grid">
        <div class="tech-badge">HTML5</div>
        <div class="tech-badge">CSS3</div>
        <div class="tech-badge">JavaScript</div>
        <div class="tech-badge">Bootstrap</div>
      </div>
    </div>

    <div style="margin-top: 40px;">
      <h3 style="color: var(--tertiary); margin-bottom: 15px; text-align: center; font-size: 1.1em;">Backend</h3>
      <div class="tech-grid">
        <div class="tech-badge">PHP</div>
        <div class="tech-badge">Laravel</div>
        <div class="tech-badge">Python</div>
        <div class="tech-badge">WordPress</div>
      </div>
    </div>

    <div style="margin-top: 40px;">
      <h3 style="color: var(--primary); margin-bottom: 15px; text-align: center; font-size: 1.1em;">Tools & Design</h3>
      <div class="tech-grid">
        <div class="tech-badge">Git</div>
        <div class="tech-badge">VS Code</div>
        <div class="tech-badge">Photoshop</div>
        <div class="tech-badge">CLI Tools</div>
      </div>
    </div>
  </div>

  <!-- GitHub Stats -->
  <div class="section" style="text-align: center;">
    <h2 class="section-title">GitHub Activity</h2>
    <div style="margin-top: 30px;">
      <img src="https://github-readme-stats.vercel.app/api?username=hamidtf&show_icons=true&theme=tokyonight&hide_border=true&bg_color=0d1117&title_color=0066cc&icon_color=00d4ff&text_color=c9d1d9&ring_color=0066cc" alt="GitHub Stats" style="max-width: 100%; height: auto; margin-bottom: 20px; border-radius: 10px;">
      <img src="https://github-readme-streak-stats.herokuapp.com/?user=hamidtf&theme=tokyonight&hide_border=true&background=0d1117&ring=0066cc&fire=00d4ff&currStreakLabel=00d4ff" alt="GitHub Streak" style="max-width: 100%; height: auto; border-radius: 10px;">
    </div>
  </div>

  <!-- Activity Graph -->
  <div class="section" style="text-align: center;">
    <img src="https://github-readme-activity-graph.vercel.app/graph?username=hamidtf&theme=tokyo-night&hide_border=true&bg_color=0d1117&color=0066cc&line=00d4ff&point=7000ff&area=true&area_color=0066cc" alt="GitHub Activity Graph" style="max-width: 100%; height: auto; border-radius: 10px;">
  </div>

  <!-- Trophies -->
  <div class="section" style="text-align: center;">
    <h2 class="section-title">Achievements</h2>
    <img src="https://github-profile-trophy.vercel.app/?username=hamidtf&theme=tokyonight&no-frame=true&no-bg=true&row=1&column=7&margin-w=15&margin-h=15" alt="GitHub Trophies" style="max-width: 100%; height: auto;">
  </div>

  <!-- Connect Section -->
  <div class="section connect-section">
    <h2 class="section-title">Let's Connect</h2>
    <div class="connect-buttons">
      <a href="https://hamidtf.me" class="connect-btn" target="_blank" rel="noopener noreferrer">
        <svg class="icon-svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <circle cx="12" cy="12" r="1"></circle>
          <path d="M19.07 4.93a10 10 0 0 0-14.14 0M2 12a10 10 0 0 0 20 0M2 12a10 10 0 0 1 20 0"></path>
        </svg>
        Visit Website
      </a>
      <a href="mailto:hamid.tf2004z@gmail.com" class="connect-btn">
        <svg class="icon-svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <rect x="2" y="4" width="20" height="16" rx="2"></rect>
          <path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"></path>
        </svg>
        Send Email
      </a>
      <a href="https://t.me/hmidtf" class="connect-btn" target="_blank" rel="noopener noreferrer">
        <svg class="icon-svg" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <path d="m22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"></path>
        </svg>
        Telegram
      </a>
    </div>
  </div>

  <!-- Visitor Counter -->
  <div class="section" style="text-align: center;">
    <div class="visitor-counter">
      <img src="https://visitcount.itsvg.in/api.php?id=hamidtf&label=Profile%20Views&color=0066cc&icon=6&pretty=true" alt="Visitor Counter" style="max-width: 100%; height: auto;">
    </div>
  </div>

  <!-- Footer Section -->
  <div class="footer-section">
    <div class="footer-quote">
      "Building the future, one elegant solution at a time. Every line of code is an opportunity to create something meaningful."
    </div>
    <div class="footer-text">
      Designed and crafted by Hamid Tafreshinia
      <br>
      Open to collaborations and new opportunities
      <br><br>
      Let's create something extraordinary together
    </div>
  </div>

</div>

</body>
</html>
