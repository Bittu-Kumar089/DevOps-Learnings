<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>INT332: DevOps Virtualization & Configuration Management</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;600;700&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0a0c10;
    --surface: #0f1218;
    --surface2: #161b24;
    --border: #1e2736;
    --accent: #00d4ff;
    --accent2: #7c3aed;
    --accent3: #10b981;
    --accent4: #f59e0b;
    --text: #e2e8f0;
    --muted: #64748b;
    --glow: 0 0 30px rgba(0,212,255,0.15);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Syne', sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* Animated background grid */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: 
      linear-gradient(rgba(0,212,255,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,212,255,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  .container {
    max-width: 960px;
    margin: 0 auto;
    padding: 0 24px;
    position: relative;
    z-index: 1;
  }

  /* ── HERO ── */
  .hero {
    padding: 80px 0 60px;
    text-align: center;
    position: relative;
  }

  .hero::after {
    content: '';
    position: absolute;
    bottom: 0; left: 50%;
    transform: translateX(-50%);
    width: 200px; height: 1px;
    background: linear-gradient(90deg, transparent, var(--accent), transparent);
  }

  .course-badge {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    background: rgba(0,212,255,0.08);
    border: 1px solid rgba(0,212,255,0.2);
    border-radius: 50px;
    padding: 6px 16px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    color: var(--accent);
    letter-spacing: 0.1em;
    margin-bottom: 28px;
    animation: fadeDown 0.6s ease both;
  }

  .course-badge::before {
    content: '◈';
    font-size: 10px;
  }

  h1 {
    font-size: clamp(28px, 5vw, 52px);
    font-weight: 800;
    line-height: 1.1;
    letter-spacing: -0.02em;
    animation: fadeDown 0.6s ease 0.1s both;
  }

  h1 span {
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero-sub {
    margin-top: 16px;
    color: var(--muted);
    font-size: 15px;
    font-weight: 400;
    animation: fadeDown 0.6s ease 0.2s both;
  }

  /* meta pills */
  .meta-row {
    display: flex;
    justify-content: center;
    gap: 12px;
    flex-wrap: wrap;
    margin-top: 32px;
    animation: fadeDown 0.6s ease 0.3s both;
  }

  .meta-pill {
    display: flex;
    align-items: center;
    gap: 6px;
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 6px 14px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    color: var(--muted);
  }

  .meta-pill .val {
    color: var(--accent3);
    font-weight: 600;
  }

  /* ── OUTCOMES ── */
  .section { padding: 60px 0; }

  .section-label {
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    color: var(--accent);
    letter-spacing: 0.15em;
    text-transform: uppercase;
    margin-bottom: 24px;
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  .section-title {
    font-size: 22px;
    font-weight: 700;
    margin-bottom: 24px;
    letter-spacing: -0.01em;
  }

  .outcomes-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }

  @media (max-width: 600px) { .outcomes-grid { grid-template-columns: 1fr; } }

  .outcome-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 16px 18px;
    display: flex;
    gap: 12px;
    align-items: flex-start;
    transition: border-color 0.2s, transform 0.2s;
    animation: fadeUp 0.5s ease both;
  }

  .outcome-card:hover {
    border-color: rgba(0,212,255,0.3);
    transform: translateY(-2px);
  }

  .co-badge {
    font-family: 'JetBrains Mono', monospace;
    font-size: 10px;
    font-weight: 600;
    color: var(--bg);
    background: var(--accent);
    border-radius: 5px;
    padding: 3px 7px;
    flex-shrink: 0;
    margin-top: 2px;
  }

  .outcome-text {
    font-size: 13px;
    color: #94a3b8;
    line-height: 1.5;
    font-weight: 400;
  }

  /* ── UNITS ── */
  .units-section { padding: 20px 0 80px; }

  .unit-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 16px;
    margin-bottom: 20px;
    overflow: hidden;
    transition: box-shadow 0.3s;
    animation: fadeUp 0.5s ease both;
  }

  .unit-card:hover {
    box-shadow: var(--glow);
  }

  .unit-header {
    display: flex;
    align-items: center;
    gap: 16px;
    padding: 20px 24px;
    background: var(--surface2);
    border-bottom: 1px solid var(--border);
    cursor: pointer;
    user-select: none;
  }

  .unit-num {
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    color: var(--bg);
    background: linear-gradient(135deg, var(--accent2), var(--accent));
    border-radius: 8px;
    padding: 4px 10px;
    font-weight: 700;
    white-space: nowrap;
  }

  .unit-title {
    font-size: 16px;
    font-weight: 700;
    letter-spacing: -0.01em;
    flex: 1;
  }

  .unit-arrow {
    color: var(--muted);
    transition: transform 0.3s;
    font-size: 18px;
  }

  .unit-card.open .unit-arrow { transform: rotate(90deg); }

  .unit-body {
    display: none;
    padding: 24px;
  }

  .unit-card.open .unit-body { display: block; }

  .topic-group {
    margin-bottom: 20px;
  }

  .topic-group:last-child { margin-bottom: 0; }

  .topic-heading {
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    color: var(--accent3);
    letter-spacing: 0.1em;
    text-transform: uppercase;
    margin-bottom: 10px;
    padding-bottom: 6px;
    border-bottom: 1px solid var(--border);
  }

  .tags-wrap {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .tag {
    background: rgba(124,58,237,0.1);
    border: 1px solid rgba(124,58,237,0.2);
    border-radius: 6px;
    padding: 4px 10px;
    font-size: 12px;
    color: #a78bfa;
    font-family: 'JetBrains Mono', monospace;
    transition: background 0.2s;
  }

  .tag:hover {
    background: rgba(124,58,237,0.2);
  }

  .tag.green {
    background: rgba(16,185,129,0.08);
    border-color: rgba(16,185,129,0.2);
    color: #6ee7b7;
  }

  .tag.blue {
    background: rgba(0,212,255,0.08);
    border-color: rgba(0,212,255,0.2);
    color: #67e8f9;
  }

  .tag.amber {
    background: rgba(245,158,11,0.08);
    border-color: rgba(245,158,11,0.2);
    color: #fcd34d;
  }

  /* unit color accents */
  .unit-card[data-unit="1"] .unit-num { background: linear-gradient(135deg,#0ea5e9,#38bdf8); }
  .unit-card[data-unit="2"] .unit-num { background: linear-gradient(135deg,#7c3aed,#a78bfa); }
  .unit-card[data-unit="3"] .unit-num { background: linear-gradient(135deg,#10b981,#34d399); color: #0a0c10; }
  .unit-card[data-unit="4"] .unit-num { background: linear-gradient(135deg,#f59e0b,#fbbf24); color: #0a0c10; }
  .unit-card[data-unit="5"] .unit-num { background: linear-gradient(135deg,#ef4444,#f87171); }
  .unit-card[data-unit="6"] .unit-num { background: linear-gradient(135deg,#ec4899,#f472b6); }

  /* footer */
  footer {
    border-top: 1px solid var(--border);
    padding: 24px 0;
    text-align: center;
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    color: var(--muted);
  }

  /* animations */
  @keyframes fadeDown {
    from { opacity:0; transform:translateY(-16px); }
    to   { opacity:1; transform:translateY(0); }
  }
  @keyframes fadeUp {
    from { opacity:0; transform:translateY(16px); }
    to   { opacity:1; transform:translateY(0); }
  }

  .unit-card:nth-child(1) { animation-delay: 0.05s; }
  .unit-card:nth-child(2) { animation-delay: 0.10s; }
  .unit-card:nth-child(3) { animation-delay: 0.15s; }
  .unit-card:nth-child(4) { animation-delay: 0.20s; }
  .unit-card:nth-child(5) { animation-delay: 0.25s; }
  .unit-card:nth-child(6) { animation-delay: 0.30s; }

  /* divider */
  .divider {
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--border), transparent);
    margin: 0;
  }
</style>
</head>
<body>

<div class="container">

  <!-- HERO -->
  <div class="hero">
    <div class="course-badge">INT332 · Session 2025-26</div>
    <h1>DevOps <span>Virtualization</span><br>& Configuration Management</h1>
    <p class="hero-sub">Complete course reference — Units I through VI</p>
    <div class="meta-row">
      <div class="meta-pill">Lectures <span class="val">L:2</span></div>
      <div class="meta-pill">Tutorial <span class="val">T:0</span></div>
      <div class="meta-pill">Practical <span class="val">P:2</span></div>
      <div class="meta-pill">Credits <span class="val">3</span></div>
    </div>
  </div>

  <!-- COURSE OUTCOMES -->
  <div class="section">
    <div class="section-label">Course Outcomes</div>
    <div class="outcomes-grid">
      <div class="outcome-card" style="animation-delay:0.05s">
        <span class="co-badge">CO1</span>
        <p class="outcome-text">Explain DevOps infrastructure concepts including containerization, runtimes, process isolation, namespaces, and resource management mechanisms.</p>
      </div>
      <div class="outcome-card" style="animation-delay:0.10s">
        <span class="co-badge">CO2</span>
        <p class="outcome-text">Apply Docker concepts to build, manage, and distribute container images using networking, storage, and registries.</p>
      </div>
      <div class="outcome-card" style="animation-delay:0.15s">
        <span class="co-badge">CO3</span>
        <p class="outcome-text">Construct microservices applications using Docker Compose with multi-container services and dependency configuration.</p>
      </div>
      <div class="outcome-card" style="animation-delay:0.20s">
        <span class="co-badge">CO4</span>
        <p class="outcome-text">Analyze and implement automated builds using Maven through lifecycle management, dependency control, plugins, and Docker integration.</p>
      </div>
      <div class="outcome-card" style="animation-delay:0.25s">
        <span class="co-badge">CO5</span>
        <p class="outcome-text">Apply Continuous Integration workflows using GitHub Actions for automated builds, testing, image creation, and deployment.</p>
      </div>
      <div class="outcome-card" style="animation-delay:0.30s">
        <span class="co-badge">CO6</span>
        <p class="outcome-text">Develop end-to-end CI/CD pipelines using Jenkins integrating source control, build tools, containers, and deployments.</p>
      </div>
    </div>
  </div>

  <div class="divider"></div>

  <!-- UNITS -->
  <div class="units-section">
    <div class="section-label" style="margin-top:40px">Syllabus Units</div>

    <!-- Unit I -->
    <div class="unit-card open" data-unit="1">
      <div class="unit-header" onclick="toggle(this)">
        <span class="unit-num">UNIT I</span>
        <span class="unit-title">Basics of DevOps Infrastructure</span>
        <span class="unit-arrow">›</span>
      </div>
      <div class="unit-body">
        <div class="topic-group">
          <div class="topic-heading">Containerization Concepts</div>
          <div class="tags-wrap">
            <span class="tag blue">Origin of Containers</span>
            <span class="tag blue">Modern Containerization</span>
            <span class="tag blue">Process Isolation</span>
            <span class="tag blue">Namespaces</span>
            <span class="tag blue">Control Groups (cgroups)</span>
            <span class="tag blue">Resource Limits</span>
          </div>
        </div>
        <div class="topic-group">
          <div class="topic-heading">Docker Fundamentals</div>
          <div class="tags-wrap">
            <span class="tag">Docker Architecture</span>
            <span class="tag">Docker Daemon</span>
            <span class="tag">Docker CLI</span>
            <span class="tag">Docker Hub</span>
            <span class="tag">Docker Registry</span>
            <span class="tag">Container Images & Layers</span>
          </div>
        </div>
        <div class="topic-group">
          <div class="topic-heading">Docker Object Types</div>
          <div class="tags-wrap">
            <span class="tag green">container</span>
            <span class="tag green">image</span>
            <span class="tag green">network</span>
            <span class="tag green">volume</span>
            <span class="tag green">layer</span>
            <span class="tag green">filesystem</span>
          </div>
        </div>
      </div>
    </div>

    <!-- Unit II -->
    <div class="unit-card" data-unit="2">
      <div class="unit-header" onclick="toggle(this)">
        <span class="unit-num">UNIT II</span>
        <span class="unit-title">Image Building & Container Management</span>
        <span class="unit-arrow">›</span>
      </div>
      <div class="unit-body">
        <div class="topic-group">
          <div class="topic-heading">Dockerfile Core Concepts</div>
          <div class="tags-wrap">
            <span class="tag blue">Image Layering</span>
            <span class="tag blue">Build Context</span>
            <span class="tag blue">.dockerignore</span>
            <span class="tag blue">FROM</span>
            <span class="tag blue">RUN</span>
            <span class="tag blue">COPY / ADD</span>
            <span class="tag blue">CMD</span>
            <span class="tag blue">ENTRYPOINT</span>
            <span class="tag blue">WORKDIR</span>
            <span class="tag blue">ENV</span>
            <span class="tag blue">EXPOSE</span>
            <span class="tag blue">VOLUME</span>
          </div>
        </div>
        <div class="topic-group">
          <div class="topic-heading">Image Creation & Management</div>
          <div class="tags-wrap">
            <span class="tag">Tagging & Versioning</span>
            <span class="tag">Inspecting Images</span>
            <span class="tag">History & Layers</span>
            <span class="tag">Docker Build Process</span>
          </div>
        </div>
        <div class="topic-group">
          <div class="topic-heading">Docker Networking</div>
          <div class="tags-wrap">
            <span class="tag green">Bridge Network</span>
            <span class="tag green">Host & Overlay Networks</span>
            <span class="tag green">DNS inside Docker</span>
            <span class="tag green">Linking Containers</span>
            <span class="tag green">Port Mapping</span>
          </div>
        </div>
        <div class="topic-group">
          <div class="topic-heading">Storage & Registries</div>
          <div class="tags-wrap">
            <span class="tag amber">Volumes vs Bind Mounts</span>
            <span class="tag amber">Backing Data on Host</span>
            <span class="tag amber">Copy-on-Write</span>
            <span class="tag amber">Docker Hub</span>
            <span class="tag amber">GHCR</span>
            <span class="tag amber">Private Registries</span>
            <span class="tag amber">Auth & Access Tokens</span>
          </div>
        </div>
      </div>
    </div>

    <!-- Unit III -->
    <div class="unit-card" data-unit="3">
      <div class="unit-header" onclick="toggle(this)">
        <span class="unit-num">UNIT III</span>
        <span class="unit-title">Microservices with Docker Compose</span>
        <span class="unit-arrow">›</span>
      </div>
      <div class="unit-body">
        <div class="topic-group">
          <div class="topic-heading">Microservices Architecture</div>
          <div class="tags-wrap">
            <span class="tag blue">Monolithic vs Microservices</span>
            <span class="tag blue">Scalability</span>
            <span class="tag blue">Isolation & Agility</span>
            <span class="tag blue">API Gateway</span>
          </div>
        </div>
        <div class="topic-group">
          <div class="topic-heading">Docker Compose</div>
          <div class="tags-wrap">
            <span class="tag">YAML Structure</span>
            <span class="tag">docker-compose.yml</span>
            <span class="tag">version / services / volumes / networks</span>
            <span class="tag">Environment Variables</span>
            <span class="tag">Secrets & Configs</span>
            <span class="tag">Build vs Image Fields</span>
            <span class="tag">Service Dependency Ordering</span>
          </div>
        </div>
        <div class="topic-group">
          <div class="topic-heading">Multi-Container Use Cases</div>
          <div class="tags-wrap">
            <span class="tag green">Docker + Backend + Frontend</span>
            <span class="tag green">WordPress + MySQL</span>
            <span class="tag green">Node.js + MongoDB</span>
            <span class="tag green">Java Spring Boot + PostgreSQL</span>
          </div>
        </div>
      </div>
    </div>

    <!-- Unit IV -->
    <div class="unit-card" data-unit="4">
      <div class="unit-header" onclick="toggle(this)">
        <span class="unit-num">UNIT IV</span>
        <span class="unit-title">Maven Build Automation</span>
        <span class="unit-arrow">›</span>
      </div>
      <div class="unit-body">
        <div class="topic-group">
          <div class="topic-heading">Maven Fundamentals</div>
          <div class="tags-wrap">
            <span class="tag blue">Why Build Tools Exist</span>
            <span class="tag blue">POM (Project Object Model)</span>
            <span class="tag blue">Directory Structure</span>
            <span class="tag blue">Parent POM</span>
            <span class="tag blue">Dependency Scope</span>
            <span class="tag blue">Transitive Dependencies</span>
            <span class="tag blue">Version Conflicts & Resolution</span>
          </div>
        </div>
        <div class="topic-group">
          <div class="topic-heading">Build Lifecycle</div>
          <div class="tags-wrap">
            <span class="tag">validate</span>
            <span class="tag">compile</span>
            <span class="tag">test</span>
            <span class="tag">package</span>
            <span class="tag">verify</span>
            <span class="tag">install</span>
            <span class="tag">deploy</span>
          </div>
        </div>
        <div class="topic-group">
          <div class="topic-heading">Plugins & Docker Integration</div>
          <div class="tags-wrap">
            <span class="tag green">Compiler Plugin</span>
            <span class="tag green">Surefire (unit tests)</span>
            <span class="tag green">Shade Plugin (uber jar)</span>
            <span class="tag green">Maven Wrapper (mvnw)</span>
            <span class="tag green">Maven & Docker Integration</span>
            <span class="tag green">Pushing Artifacts to Registries</span>
          </div>
        </div>
      </div>
    </div>

    <!-- Unit V -->
    <div class="unit-card" data-unit="5">
      <div class="unit-header" onclick="toggle(this)">
        <span class="unit-num">UNIT V</span>
        <span class="unit-title">Continuous Integration with GitHub Actions</span>
        <span class="unit-arrow">›</span>
      </div>
      <div class="unit-body">
        <div class="topic-group">
          <div class="topic-heading">Workflow Architecture</div>
          <div class="tags-wrap">
            <span class="tag blue">Workflow Automation</span>
            <span class="tag blue">Events & Triggers</span>
            <span class="tag blue">Directory Structure</span>
            <span class="tag blue">Jobs / Steps / Actions</span>
            <span class="tag blue">Runners</span>
            <span class="tag blue">Matrix Strategies</span>
          </div>
        </div>
        <div class="topic-group">
          <div class="topic-heading">Workflow Triggers</div>
          <div class="tags-wrap">
            <span class="tag">push</span>
            <span class="tag">pull_request</span>
            <span class="tag">schedule</span>
            <span class="tag">manual_workflow</span>
          </div>
        </div>
        <div class="topic-group">
          <div class="topic-heading">Actions & Commands</div>
          <div class="tags-wrap">
            <span class="tag green">Marketplace Actions</span>
            <span class="tag green">Language-Specific Actions</span>
            <span class="tag green">Shell Commands</span>
            <span class="tag green">GitHub-hosted Runners</span>
            <span class="tag green">Self-hosted Runners</span>
            <span class="tag green">Runner Security & Management</span>
          </div>
        </div>
        <div class="topic-group">
          <div class="topic-heading">Docker in CI</div>
          <div class="tags-wrap">
            <span class="tag amber">Build Docker Images in CI</span>
            <span class="tag amber">Caching for Faster Builds</span>
            <span class="tag amber">Multi-job Workflows</span>
            <span class="tag amber">Push to Docker Hub</span>
            <span class="tag amber">Push to GHCR</span>
            <span class="tag amber">Deploy to Servers/Cloud</span>
          </div>
        </div>
      </div>
    </div>

    <!-- Unit VI -->
    <div class="unit-card" data-unit="6">
      <div class="unit-header" onclick="toggle(this)">
        <span class="unit-num">UNIT VI</span>
        <span class="unit-title">CI/CD with Jenkins</span>
        <span class="unit-arrow">›</span>
      </div>
      <div class="unit-body">
        <div class="topic-group">
          <div class="topic-heading">Jenkins Foundations</div>
          <div class="tags-wrap">
            <span class="tag blue">Master/Agent Model</span>
            <span class="tag blue">Installation & UI Overview</span>
            <span class="tag blue">Plugins Management</span>
            <span class="tag blue">Security, Users & Roles</span>
          </div>
        </div>
        <div class="topic-group">
          <div class="topic-heading">Jenkins Pipelines</div>
          <div class="tags-wrap">
            <span class="tag">Freestyle vs Pipeline Jobs</span>
            <span class="tag">Declarative Pipeline Syntax</span>
            <span class="tag">Scripted Pipeline Syntax</span>
            <span class="tag">Jenkinsfile Structure</span>
            <span class="tag">Parameters</span>
            <span class="tag">Environment Variables</span>
            <span class="tag">Multi-branch Pipelines</span>
          </div>
        </div>
        <div class="topic-group">
          <div class="topic-heading">Pipeline Stages</div>
          <div class="tags-wrap">
            <span class="tag green">Checkout (Git)</span>
            <span class="tag green">Build</span>
            <span class="tag green">Test</span>
            <span class="tag green">Package</span>
            <span class="tag green">Managing Artifacts</span>
            <span class="tag green">Post Actions</span>
          </div>
        </div>
        <div class="topic-group">
          <div class="topic-heading">Docker & Maven Integration</div>
          <div class="tags-wrap">
            <span class="tag amber">Building Docker Images via Jenkins</span>
            <span class="tag amber">Docker Inside Jenkins Agents</span>
            <span class="tag amber">Using Docker Plugins</span>
            <span class="tag amber">Publishing to Docker Hub / GHCR</span>
            <span class="tag amber">Jenkins & Maven Builds</span>
            <span class="tag amber">Global Tool Configuration</span>
            <span class="tag amber">Running Maven in Pipelines</span>
          </div>
        </div>
        <div class="topic-group">
          <div class="topic-heading">Advanced CI/CD</div>
          <div class="tags-wrap">
            <span class="tag">Backup & Restore</span>
            <span class="tag">Pipeline Best Practices</span>
            <span class="tag">Code Coverage & Test Reports</span>
            <span class="tag">Deployment Flows (pollSCM, webhook)</span>
            <span class="tag">Pipeline Libraries</span>
            <span class="tag">Jenkins Agents (SSH / SFTP / Container)</span>
            <span class="tag">Deploy to Servers/Cloud</span>
          </div>
        </div>
      </div>
    </div>

  </div>

</div>

<footer>
  <div class="container">
    INT332 · DevOps Virtualization & Configuration Management · Session 2025-26 · Page 1/2
  </div>
</footer>

<script>
  function toggle(header) {
    const card = header.parentElement;
    card.classList.toggle('open');
  }
</script>

</body>
</html>
