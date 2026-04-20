<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>EduBridge — AI Student Platform</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
:root {
  --navy: #0B1F4B;
  --blue: #1346A3;
  --sky: #3B82F6;
  --gold: #F59E0B;
  --mint: #10B981;
  --rose: #F43F5E;
  --violet: #8B5CF6;
  --dark: #060E24;
  --card: #0D1B3E;
  --border: rgba(59,130,246,0.18);
  --text: #E2E8F0;
  --muted: #64748B;
  --white: #FFFFFF;
}
*{margin:0;padding:0;box-sizing:border-box}
html{scroll-behavior:smooth}
body{font-family:'DM Sans',sans-serif;background:var(--dark);color:var(--text);min-height:100vh;overflow-x:hidden}

/* ── SCROLLBAR ── */
::-webkit-scrollbar{width:6px}::-webkit-scrollbar-track{background:var(--dark)}::-webkit-scrollbar-thumb{background:var(--blue);border-radius:3px}

/* ── NAV ── */
nav{position:fixed;top:0;left:0;right:0;z-index:100;background:rgba(6,14,36,0.85);backdrop-filter:blur(16px);border-bottom:1px solid var(--border);padding:0 2rem;height:64px;display:flex;align-items:center;justify-content:space-between}
.nav-logo{font-family:'Syne',sans-serif;font-size:1.5rem;font-weight:800;background:linear-gradient(135deg,var(--sky),var(--gold));-webkit-background-clip:text;-webkit-text-fill-color:transparent}
.nav-links{display:flex;gap:1.5rem;align-items:center}
.nav-links a{color:var(--muted);text-decoration:none;font-size:.9rem;font-weight:500;transition:color .2s;cursor:pointer}
.nav-links a:hover,.nav-links a.active{color:var(--sky)}
.btn{padding:.55rem 1.2rem;border-radius:8px;border:none;cursor:pointer;font-family:'DM Sans',sans-serif;font-weight:600;font-size:.88rem;transition:all .2s}
.btn-primary{background:linear-gradient(135deg,var(--sky),var(--blue));color:#fff}
.btn-primary:hover{transform:translateY(-1px);box-shadow:0 4px 20px rgba(59,130,246,.4)}
.btn-outline{background:transparent;border:1px solid var(--border);color:var(--text)}
.btn-outline:hover{border-color:var(--sky);color:var(--sky)}
.btn-gold{background:linear-gradient(135deg,var(--gold),#D97706);color:var(--dark)}
.btn-gold:hover{transform:translateY(-1px);box-shadow:0 4px 20px rgba(245,158,11,.4)}
.btn-sm{padding:.35rem .8rem;font-size:.8rem}

/* ── SECTIONS ── */
.section{display:none;min-height:calc(100vh - 64px);padding:80px 0 2rem}
.section.active{display:block}
.container{max-width:1200px;margin:0 auto;padding:0 2rem}

/* ── HERO ── */
#hero{background:radial-gradient(ellipse at 20% 50%,rgba(19,70,163,.35) 0%,transparent 60%),radial-gradient(ellipse at 80% 20%,rgba(59,130,246,.2) 0%,transparent 50%),var(--dark)}
.hero-inner{display:grid;grid-template-columns:1fr 1fr;gap:4rem;align-items:center;min-height:calc(100vh - 64px)}
.hero-badge{display:inline-flex;align-items:center;gap:.5rem;background:rgba(245,158,11,.12);border:1px solid rgba(245,158,11,.3);color:var(--gold);padding:.35rem .9rem;border-radius:100px;font-size:.8rem;font-weight:600;margin-bottom:1.5rem;animation:fadeIn .6s ease}
.hero-title{font-family:'Syne',sans-serif;font-size:clamp(2.5rem,5vw,4rem);font-weight:800;line-height:1.08;margin-bottom:1.2rem}
.hero-title .accent{background:linear-gradient(135deg,var(--sky),var(--mint));-webkit-background-clip:text;-webkit-text-fill-color:transparent}
.hero-sub{color:var(--muted);font-size:1.1rem;line-height:1.6;margin-bottom:2rem;max-width:480px}
.hero-cta{display:flex;gap:1rem;flex-wrap:wrap}
.hero-stats{display:flex;gap:2rem;margin-top:2.5rem;padding-top:2rem;border-top:1px solid var(--border)}
.hstat{text-align:center}
.hstat-val{font-family:'Syne',sans-serif;font-size:1.6rem;font-weight:700;color:var(--sky)}
.hstat-label{font-size:.78rem;color:var(--muted);margin-top:.2rem}
.hero-visual{display:grid;gap:1rem}
.feature-card{background:var(--card);border:1px solid var(--border);border-radius:16px;padding:1.2rem;display:flex;align-items:center;gap:1rem;animation:slideIn .5s ease forwards;opacity:0}
.feature-card:nth-child(1){animation-delay:.1s}.feature-card:nth-child(2){animation-delay:.2s}.feature-card:nth-child(3){animation-delay:.3s}.feature-card:nth-child(4){animation-delay:.4s}
.fc-icon{width:44px;height:44px;border-radius:12px;display:flex;align-items:center;justify-content:center;font-size:1.3rem;flex-shrink:0}
.fc-title{font-weight:600;font-size:.95rem;color:var(--white)}
.fc-desc{font-size:.8rem;color:var(--muted);margin-top:.2rem}

/* ── CARDS ── */
.card{background:var(--card);border:1px solid var(--border);border-radius:16px;padding:1.5rem}
.card-title{font-family:'Syne',sans-serif;font-size:1.1rem;font-weight:700;margin-bottom:1rem;color:var(--white)}
.section-title{font-family:'Syne',sans-serif;font-size:2rem;font-weight:800;margin-bottom:.5rem}
.section-sub{color:var(--muted);margin-bottom:2rem;font-size:1rem}

/* ── FORM ELEMENTS ── */
.form-group{margin-bottom:1.1rem}
.form-label{display:block;font-size:.82rem;font-weight:600;color:var(--muted);text-transform:uppercase;letter-spacing:.05em;margin-bottom:.45rem}
.form-input,.form-select{width:100%;background:rgba(255,255,255,.04);border:1px solid var(--border);border-radius:10px;padding:.7rem 1rem;color:var(--text);font-family:'DM Sans',sans-serif;font-size:.92rem;outline:none;transition:border-color .2s}
.form-input:focus,.form-select:focus{border-color:var(--sky)}
.form-select option{background:var(--dark)}
.form-grid{display:grid;grid-template-columns:1fr 1fr;gap:1rem}

/* ── RESULT BOX ── */
.result-box{background:linear-gradient(135deg,rgba(19,70,163,.2),rgba(59,130,246,.08));border:1px solid rgba(59,130,246,.3);border-radius:16px;padding:1.5rem;margin-top:1.5rem}
.result-row{display:flex;justify-content:space-between;align-items:center;padding:.65rem 0;border-bottom:1px solid var(--border)}
.result-row:last-child{border-bottom:none}
.result-label{color:var(--muted);font-size:.88rem}
.result-value{font-weight:600;font-size:.95rem;color:var(--white)}
.result-value.green{color:var(--mint)}.result-value.gold{color:var(--gold)}.result-value.blue{color:var(--sky)}

/* ── METER / GAUGE ── */
.meter-wrap{margin:1.2rem 0}
.meter-label{display:flex;justify-content:space-between;margin-bottom:.4rem;font-size:.82rem}
.meter-bar{height:10px;background:rgba(255,255,255,.06);border-radius:100px;overflow:hidden}
.meter-fill{height:100%;border-radius:100px;transition:width 1s ease}

/* ── CHAT ── */
#chat-section{background:var(--dark)}
.chat-layout{display:grid;grid-template-columns:280px 1fr;gap:1.5rem;height:calc(100vh - 130px)}
.chat-sidebar{background:var(--card);border:1px solid var(--border);border-radius:16px;padding:1.2rem;overflow-y:auto}
.chat-main{display:flex;flex-direction:column;background:var(--card);border:1px solid var(--border);border-radius:16px;overflow:hidden}
.chat-header{padding:1rem 1.2rem;border-bottom:1px solid var(--border);display:flex;align-items:center;gap:.75rem}
.ai-avatar{width:40px;height:40px;background:linear-gradient(135deg,var(--sky),var(--violet));border-radius:12px;display:flex;align-items:center;justify-content:center;font-size:1.2rem}
.chat-messages{flex:1;overflow-y:auto;padding:1.2rem;display:flex;flex-direction:column;gap:.9rem}
.msg{max-width:75%;padding:.8rem 1rem;border-radius:14px;font-size:.9rem;line-height:1.5;animation:msgIn .2s ease}
.msg.user{background:linear-gradient(135deg,var(--blue),var(--sky));color:#fff;margin-left:auto;border-bottom-right-radius:4px}
.msg.ai{background:rgba(255,255,255,.06);border:1px solid var(--border);border-bottom-left-radius:4px}
.msg.typing{background:rgba(255,255,255,.04);border:1px solid var(--border);color:var(--muted);font-style:italic}
.chat-input-area{padding:1rem;border-top:1px solid var(--border);display:flex;gap:.75rem}
.chat-input{flex:1;background:rgba(255,255,255,.04);border:1px solid var(--border);border-radius:12px;padding:.7rem 1rem;color:var(--text);font-family:'DM Sans',sans-serif;font-size:.9rem;outline:none;resize:none}
.chat-input:focus{border-color:var(--sky)}
.quick-q{background:rgba(59,130,246,.1);border:1px solid rgba(59,130,246,.2);color:var(--sky);border-radius:8px;padding:.4rem .8rem;font-size:.8rem;cursor:pointer;transition:all .2s;text-align:left;width:100%;margin-bottom:.5rem}
.quick-q:hover{background:rgba(59,130,246,.2)}

/* ── NAVIGATOR ── */
.uni-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(300px,1fr));gap:1.2rem;margin-top:1.5rem}
.uni-card{background:var(--card);border:1px solid var(--border);border-radius:16px;padding:1.3rem;transition:all .25s;cursor:pointer}
.uni-card:hover{border-color:var(--sky);transform:translateY(-2px)}
.uni-flag{font-size:1.6rem;margin-bottom:.6rem}
.uni-name{font-family:'Syne',sans-serif;font-size:1rem;font-weight:700;color:var(--white);margin-bottom:.3rem}
.uni-meta{display:flex;gap:.8rem;flex-wrap:wrap;margin-top:.7rem}
.uni-tag{background:rgba(255,255,255,.05);border:1px solid var(--border);border-radius:6px;padding:.2rem .6rem;font-size:.75rem;color:var(--muted)}
.uni-tag.highlight{background:rgba(59,130,246,.1);border-color:rgba(59,130,246,.25);color:var(--sky)}
.filter-row{display:flex;gap:1rem;flex-wrap:wrap;align-items:flex-end;margin-bottom:1rem}
.filter-row .form-group{margin-bottom:0;min-width:160px}

/* ── TIMELINE ── */
.timeline-list{margin-top:1.5rem}
.tl-item{display:flex;gap:1rem;margin-bottom:1rem;align-items:flex-start}
.tl-dot{width:12px;height:12px;border-radius:50%;flex-shrink:0;margin-top:4px}
.tl-line{width:2px;background:var(--border);flex-shrink:0;margin:4px 5px 0}
.tl-content{background:var(--card);border:1px solid var(--border);border-radius:12px;padding:.8rem 1rem;flex:1}
.tl-date{font-size:.75rem;color:var(--muted);margin-bottom:.2rem}
.tl-task{font-weight:600;font-size:.9rem;color:var(--white)}
.tl-cat{font-size:.75rem;padding:.15rem .5rem;border-radius:4px;margin-top:.3rem;display:inline-block}
.status-done{background:rgba(16,185,129,.12);color:var(--mint)}.status-upcoming{background:rgba(245,158,11,.12);color:var(--gold)}.status-future{background:rgba(100,116,139,.12);color:var(--muted)}

/* ── LOAN ── */
.loan-status-card{border-radius:16px;padding:1.5rem;text-align:center;margin-bottom:1.5rem}
.loan-score{font-family:'Syne',sans-serif;font-size:3.5rem;font-weight:800;line-height:1}
.loan-tier{font-size:1rem;font-weight:600;margin-top:.4rem}

/* ── LEADERBOARD ── */
.lb-row{display:flex;align-items:center;gap:1rem;background:var(--card);border:1px solid var(--border);border-radius:12px;padding:.9rem 1.1rem;margin-bottom:.6rem;transition:all .2s}
.lb-row:hover{border-color:var(--sky)}
.lb-rank{font-family:'Syne',sans-serif;font-size:1.2rem;font-weight:800;width:32px;color:var(--gold)}
.lb-name{flex:1;font-weight:600;font-size:.92rem}
.lb-city{font-size:.78rem;color:var(--muted)}
.lb-xp{font-family:'Syne',sans-serif;font-size:1rem;font-weight:700;color:var(--sky)}
.lb-streak{font-size:.8rem;color:var(--gold)}

/* ── MODAL ── */
.modal-overlay{display:none;position:fixed;inset:0;background:rgba(0,0,0,.7);z-index:200;align-items:center;justify-content:center}
.modal-overlay.open{display:flex}
.modal{background:var(--card);border:1px solid var(--border);border-radius:20px;padding:2rem;width:100%;max-width:480px;max-height:90vh;overflow-y:auto;animation:modalIn .25s ease}
.modal-title{font-family:'Syne',sans-serif;font-size:1.4rem;font-weight:800;margin-bottom:.3rem}
.modal-sub{color:var(--muted);font-size:.88rem;margin-bottom:1.5rem}
.modal-close{float:right;background:none;border:none;color:var(--muted);font-size:1.3rem;cursor:pointer;margin-top:-.3rem}

/* ── DASHBOARD GRID ── */
.dash-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:1.2rem;margin-bottom:1.5rem}
.dash-card{background:var(--card);border:1px solid var(--border);border-radius:16px;padding:1.2rem}
.dash-val{font-family:'Syne',sans-serif;font-size:2rem;font-weight:800;margin-bottom:.2rem}
.dash-label{font-size:.82rem;color:var(--muted)}
.dash-main-grid{display:grid;grid-template-columns:1.5fr 1fr;gap:1.2rem}

/* ── ANIMATIONS ── */
@keyframes fadeIn{from{opacity:0;transform:translateY(10px)}to{opacity:1;transform:translateY(0)}}
@keyframes slideIn{from{opacity:0;transform:translateX(20px)}to{opacity:1;transform:translateX(0)}}
@keyframes msgIn{from{opacity:0;transform:translateY(6px)}to{opacity:1;transform:translateY(0)}}
@keyframes modalIn{from{opacity:0;transform:scale(.96)}to{opacity:1;transform:scale(1)}}
@keyframes pulse{0%,100%{opacity:1}50%{opacity:.5}}

/* ── TOAST ── */
.toast{position:fixed;bottom:2rem;right:2rem;background:var(--card);border:1px solid var(--mint);border-radius:12px;padding:.9rem 1.3rem;font-size:.88rem;color:var(--text);z-index:300;animation:fadeIn .3s ease;display:flex;align-items:center;gap:.7rem}
.toast.error{border-color:var(--rose)}

/* ── NAV USER ── */
.user-chip{display:flex;align-items:center;gap:.6rem;background:rgba(59,130,246,.1);border:1px solid var(--border);border-radius:100px;padding:.3rem .8rem .3rem .5rem;cursor:pointer}
.user-avatar{width:28px;height:28px;background:linear-gradient(135deg,var(--sky),var(--violet));border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:.9rem}
.user-name-chip{font-size:.82rem;font-weight:600}
.xp-badge{font-size:.72rem;color:var(--gold)}

/* ── RESPONSIVE ── */
@media(max-width:768px){
  .hero-inner{grid-template-columns:1fr;gap:2rem}
  .hero-visual{display:none}
  .form-grid{grid-template-columns:1fr}
  .chat-layout{grid-template-columns:1fr}
  .chat-sidebar{display:none}
  .dash-grid{grid-template-columns:1fr 1fr}
  .dash-main-grid{grid-template-columns:1fr}
  nav{padding:0 1rem}
  .nav-links a:not(.nav-cta){display:none}
}
</style>
</head>
<body>

<!-- ── NAV ── -->
<nav>
  <div class="nav-logo">EduBridge</div>
  <div class="nav-links">
    <a onclick="showSection('home')" class="active" id="nav-home">Home</a>
    <a onclick="showSection('navigator')" id="nav-navigator">Universities</a>
    <a onclick="showSection('tools')" id="nav-tools">AI Tools</a>
    <a onclick="showSection('loan')" id="nav-loan">Loan Check</a>
    <a onclick="showSection('chat')" id="nav-chat">AI Mentor</a>
    <a onclick="showSection('timeline')" id="nav-timeline">Timeline</a>
    <a onclick="showSection('leaderboard')" id="nav-leaderboard">Board</a>
  </div>
  <div id="nav-auth-area">
    <button class="btn btn-outline btn-sm" onclick="openModal('login-modal')" style="margin-right:.5rem">Login</button>
    <button class="btn btn-primary btn-sm" onclick="openModal('register-modal')">Get Started</button>
  </div>
</nav>

<!-- ── HOME ── -->
<section class="section active" id="home">
  <div class="container">
    <div class="hero-inner">
      <div>
        <div class="hero-badge">🚀 AI-Powered Study Abroad Platform</div>
        <h1 class="hero-title">Bridge the Gap to Your <span class="accent">Dream University</span></h1>
        <p class="hero-sub">From university discovery to loan approval — EduBridge uses AI to guide every step of your higher education journey. Built for Indian students, powered by Claude AI.</p>
        <div class="hero-cta">
          <button class="btn btn-primary" onclick="openModal('register-modal')">Start Free — It's Fast</button>
          <button class="btn btn-outline" onclick="showSection('tools')">Try AI Tools →</button>
        </div>
        <div class="hero-stats" id="hero-stats">
          <div class="hstat"><div class="hstat-val" id="stat-users">—</div><div class="hstat-label">Students Registered</div></div>
          <div class="hstat"><div class="hstat-val" id="stat-admits">—</div><div class="hstat-label">Admits Helped</div></div>
          <div class="hstat"><div class="hstat-val" id="stat-loans">—</div><div class="hstat-label">Loans Processed</div></div>
        </div>
      </div>
      <div class="hero-visual">
        <div class="feature-card"><div class="fc-icon" style="background:rgba(59,130,246,.15)">🧠</div><div><div class="fc-title">AI Career Navigator</div><div class="fc-desc">LLM-powered university & course matching</div></div></div>
        <div class="feature-card"><div class="fc-icon" style="background:rgba(16,185,129,.15)">📊</div><div><div class="fc-title">ROI Calculator</div><div class="fc-desc">Predict salary vs cost, EMI scenarios</div></div></div>
        <div class="feature-card"><div class="fc-icon" style="background:rgba(245,158,11,.15)">🎯</div><div><div class="fc-title">Admit Predictor</div><div class="fc-desc">ML model with real profile gap analysis</div></div></div>
        <div class="feature-card"><div class="fc-icon" style="background:rgba(139,92,246,.15)">💰</div><div><div class="fc-title">Loan Integration</div><div class="fc-desc">Poonawalla Fincorp — instant eligibility</div></div></div>
      </div>
    </div>
  </div>
</section>

<!-- ── NAVIGATOR ── -->
<section class="section" id="navigator">
  <div class="container">
    <div class="section-title">University Navigator</div>
    <div class="section-sub">Filter and explore universities matching your profile</div>
    <div class="filter-row">
      <div class="form-group"><label class="form-label">Country</label>
        <select class="form-select" id="f-country" onchange="loadUniversities()">
          <option value="all">All Countries</option>
          <option>USA</option><option>UK</option><option>Canada</option><option>Germany</option><option>Australia</option><option>India</option>
        </select>
      </div>
      <div class="form-group"><label class="form-label">Course</label>
        <select class="form-select" id="f-course" onchange="loadUniversities()">
          <option value="all">All Courses</option>
          <option>Computer Science</option><option>MBA</option><option>Data Science</option><option>Engineering</option>
        </select>
      </div>
      <button class="btn btn-primary" onclick="loadUniversities()">Search</button>
    </div>
    <div class="uni-grid" id="uni-grid"></div>
  </div>
</section>

<!-- ── TOOLS ── -->
<section class="section" id="tools">
  <div class="container">
    <div class="section-title">AI-Powered Tools</div>
    <div class="section-sub">Real-time analysis. Predictive insights. Zero guesswork.</div>
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:1.5rem">

      <!-- ROI Calculator -->
      <div class="card">
        <div class="card-title">📊 ROI Calculator</div>
        <div class="form-grid">
          <div class="form-group"><label class="form-label">Country</label>
            <select class="form-select" id="roi-country">
              <option>USA</option><option>UK</option><option>Canada</option><option>Germany</option><option>Australia</option>
            </select>
          </div>
          <div class="form-group"><label class="form-label">Course</label>
            <select class="form-select" id="roi-course">
              <option>Computer Science</option><option>MBA</option><option>Data Science</option><option>Engineering</option>
            </select>
          </div>
          <div class="form-group"><label class="form-label">Tuition/Year (USD)</label>
            <input class="form-input" id="roi-tuition" type="number" value="45000">
          </div>
          <div class="form-group"><label class="form-label">Living Cost/Year (USD)</label>
            <input class="form-input" id="roi-living" type="number" value="15000">
          </div>
          <div class="form-group"><label class="form-label">Duration (Years)</label>
            <input class="form-input" id="roi-duration" type="number" value="2">
          </div>
          <div class="form-group"><label class="form-label">Current Salary (₹/yr)</label>
            <input class="form-input" id="roi-salary" type="number" value="600000">
          </div>
        </div>
        <button class="btn btn-primary" style="width:100%" onclick="calcROI()">Calculate ROI</button>
        <div id="roi-result" style="display:none"></div>
      </div>

      <!-- Admit Predictor -->
      <div class="card">
        <div class="card-title">🎯 Admit Probability Predictor</div>
        <div class="form-grid">
          <div class="form-group"><label class="form-label">GRE Score</label>
            <input class="form-input" id="ap-gre" type="number" value="315" min="260" max="340">
          </div>
          <div class="form-group"><label class="form-label">GPA (out of 4.0)</label>
            <input class="form-input" id="ap-gpa" type="number" value="3.4" step="0.1" min="0" max="4">
          </div>
          <div class="form-group"><label class="form-label">IELTS Score</label>
            <input class="form-input" id="ap-ielts" type="number" value="7.0" step="0.5" min="4" max="9">
          </div>
          <div class="form-group"><label class="form-label">Work Experience (yrs)</label>
            <input class="form-input" id="ap-work" type="number" value="1" min="0">
          </div>
          <div class="form-group"><label class="form-label">Research Papers</label>
            <input class="form-input" id="ap-papers" type="number" value="0" min="0">
          </div>
          <div class="form-group"><label class="form-label">Target Country</label>
            <select class="form-select" id="ap-country">
              <option>USA</option><option>UK</option><option>Canada</option><option>Germany</option>
            </select>
          </div>
        </div>
        <button class="btn btn-gold" style="width:100%" onclick="predictAdmit()">Predict My Chances</button>
        <div id="ap-result" style="display:none"></div>
      </div>
    </div>
  </div>
</section>

<!-- ── LOAN ── -->
<section class="section" id="loan">
  <div class="container">
    <div class="section-title">Loan Eligibility Check</div>
    <div class="section-sub">Powered by Poonawalla Fincorp — instant assessment</div>
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:1.5rem">
      <div class="card">
        <div class="card-title">💰 Your Loan Profile</div>
        <div class="form-grid">
          <div class="form-group"><label class="form-label">Loan Amount (₹)</label>
            <input class="form-input" id="ln-amount" type="number" value="2500000">
          </div>
          <div class="form-group"><label class="form-label">Family Annual Income (₹)</label>
            <input class="form-input" id="ln-income" type="number" value="1000000">
          </div>
          <div class="form-group"><label class="form-label">Co-applicant?</label>
            <select class="form-select" id="ln-coapplicant">
              <option value="yes">Yes (Parent/Guardian)</option>
              <option value="no">No</option>
            </select>
          </div>
          <div class="form-group"><label class="form-label">Collateral Available?</label>
            <select class="form-select" id="ln-collateral">
              <option value="yes">Yes</option>
              <option value="no">No</option>
            </select>
          </div>
          <div class="form-group"><label class="form-label">Admit Letter?</label>
            <select class="form-select" id="ln-admit">
              <option value="yes">Yes, I have it</option>
              <option value="no">Not yet</option>
            </select>
          </div>
          <div class="form-group"><label class="form-label">Target Country</label>
            <select class="form-select" id="ln-country">
              <option>USA</option><option>UK</option><option>Canada</option><option>Germany</option><option>Australia</option><option>India</option>
            </select>
          </div>
        </div>
        <button class="btn btn-gold" style="width:100%" onclick="checkLoan()">Check My Eligibility</button>
      </div>
      <div id="loan-result">
        <div class="card" style="text-align:center;opacity:.5;padding:3rem">
          <div style="font-size:3rem;margin-bottom:1rem">💳</div>
          <div style="color:var(--muted)">Fill in your details and check eligibility</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ── CHAT ── -->
<section class="section" id="chat">
  <div class="container">
    <div class="section-title" style="margin-bottom:1rem">AI Mentor</div>
    <div class="chat-layout">
      <div class="chat-sidebar">
        <div style="font-size:.8rem;font-weight:700;color:var(--muted);text-transform:uppercase;letter-spacing:.08em;margin-bottom:.8rem">Quick Questions</div>
        <button class="quick-q" onclick="sendQuick('What GRE score do I need for top US universities?')">📚 GRE requirements for US</button>
        <button class="quick-q" onclick="sendQuick('How much does an MS in USA cost including living expenses?')">💰 Cost of MS in USA</button>
        <button class="quick-q" onclick="sendQuick('How do I write a strong SOP for Computer Science programs?')">✍️ Writing a strong SOP</button>
        <button class="quick-q" onclick="sendQuick('What are education loan options available in India?')">🏦 Education loan options</button>
        <button class="quick-q" onclick="sendQuick('What is the visa application process for USA student visa?')">🛂 US student visa process</button>
        <button class="quick-q" onclick="sendQuick('What scholarships are available for Indian students abroad?')">🎓 Scholarships for Indians</button>
        <button class="quick-q" onclick="sendQuick('How to choose between USA, Canada and UK for Masters?')">🌍 USA vs Canada vs UK</button>
        <div style="margin-top:1.5rem;padding:1rem;background:rgba(59,130,246,.08);border:1px solid var(--border);border-radius:12px">
          <div style="font-size:.8rem;color:var(--sky);font-weight:600;margin-bottom:.4rem">Your Mentor</div>
          <div style="font-size:.78rem;color:var(--muted)">Powered by Claude AI. Remembers your context within this session.</div>
        </div>
      </div>
      <div class="chat-main">
        <div class="chat-header">
          <div class="ai-avatar">🤖</div>
          <div>
            <div style="font-weight:700;font-size:.95rem">EduBridge AI Mentor</div>
            <div style="font-size:.78rem;color:var(--mint)">● Online — Claude-powered</div>
          </div>
        </div>
        <div class="chat-messages" id="chat-messages">
          <div class="msg ai">👋 Hi! I'm your EduBridge AI Mentor. I can help you with university selection, SOP writing, visa guidance, scholarship search, and education loans. What's on your mind today?</div>
        </div>
        <div class="chat-input-area">
          <textarea class="chat-input" id="chat-input" rows="2" placeholder="Ask anything about your study abroad journey..." onkeydown="chatKeydown(event)"></textarea>
          <button class="btn btn-primary" onclick="sendChat()" style="align-self:flex-end">Send</button>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ── TIMELINE ── -->
<section class="section" id="timeline">
  <div class="container">
    <div class="section-title">Application Timeline Generator</div>
    <div class="section-sub">Get a personalized week-by-week action plan</div>
    <div style="display:grid;grid-template-columns:320px 1fr;gap:1.5rem">
      <div class="card">
        <div class="card-title">⚙️ Configure</div>
        <div class="form-group"><label class="form-label">Target Intake Month</label>
          <select class="form-select" id="tl-month">
            <option value="9">September</option><option value="1">January</option><option value="5">May</option>
          </select>
        </div>
        <div class="form-group"><label class="form-label">Target Year</label>
          <select class="form-select" id="tl-year">
            <option value="2026">2026</option><option value="2027">2027</option>
          </select>
        </div>
        <div class="form-group"><label class="form-label">Current Status</label>
          <select class="form-select" id="tl-status">
            <option>Just exploring</option><option>GRE prep started</option><option>GRE done</option><option>Applications submitted</option>
          </select>
        </div>
        <button class="btn btn-primary" style="width:100%;margin-top:.5rem" onclick="generateTimeline()">Generate My Timeline</button>
      </div>
      <div id="timeline-result">
        <div class="card" style="text-align:center;opacity:.5;padding:3rem">
          <div style="font-size:3rem;margin-bottom:1rem">📅</div>
          <div style="color:var(--muted)">Configure and generate your personalized plan</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ── LEADERBOARD ── -->
<section class="section" id="leaderboard">
  <div class="container">
    <div class="section-title">Student Leaderboard</div>
    <div class="section-sub">Top achievers on EduBridge this month</div>
    <div style="display:grid;grid-template-columns:1fr 320px;gap:1.5rem">
      <div>
        <div id="lb-list"></div>
      </div>
      <div>
        <div class="card">
          <div class="card-title">🏅 Your Progress</div>
          <div id="user-progress">
            <div style="text-align:center;color:var(--muted);font-size:.88rem;padding:1rem">Login to see your stats</div>
          </div>
        </div>
        <div class="card" style="margin-top:1rem">
          <div class="card-title">🎖 Badges</div>
          <div id="badge-list" style="display:flex;flex-wrap:wrap;gap:.5rem;margin-top:.5rem">
            <span style="font-size:1.5rem;opacity:.3" title="Early Bird">🐦</span>
            <span style="font-size:1.5rem;opacity:.3" title="7-Day Streak">🔥</span>
            <span style="font-size:1.5rem;opacity:.3" title="First Loan Check">💳</span>
            <span style="font-size:1.5rem;opacity:.3" title="AI Mentor Chat">🤖</span>
            <span style="font-size:1.5rem;opacity:.3" title="Applied to University">🎓</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ── MODALS ── -->
<div class="modal-overlay" id="login-modal">
  <div class="modal">
    <button class="modal-close" onclick="closeModal('login-modal')">✕</button>
    <div class="modal-title">Welcome Back</div>
    <div class="modal-sub">Enter your email to continue your journey</div>
    <div class="form-group"><label class="form-label">Email</label><input class="form-input" id="login-email" type="email" placeholder="you@example.com"></div>
    <button class="btn btn-primary" style="width:100%" onclick="login()">Continue →</button>
  </div>
</div>

<div class="modal-overlay" id="register-modal">
  <div class="modal">
    <button class="modal-close" onclick="closeModal('register-modal')">✕</button>
    <div class="modal-title">Start Your Journey</div>
    <div class="modal-sub">Create your free EduBridge account</div>
    <div class="form-grid">
      <div class="form-group"><label class="form-label">Full Name</label><input class="form-input" id="reg-name" type="text" placeholder="Priya Sharma"></div>
      <div class="form-group"><label class="form-label">Email</label><input class="form-input" id="reg-email" type="email" placeholder="you@example.com"></div>
      <div class="form-group"><label class="form-label">Phone</label><input class="form-input" id="reg-phone" type="tel" placeholder="+91 9876543210"></div>
      <div class="form-group"><label class="form-label">Target Degree</label>
        <select class="form-select" id="reg-degree">
          <option>MS / MTech</option><option>MBA</option><option>PhD</option><option>MCA</option><option>Other PG</option>
        </select>
      </div>
    </div>
    <div class="form-group"><label class="form-label">Target Country</label>
      <select class="form-select" id="reg-country">
        <option>USA</option><option>UK</option><option>Canada</option><option>Germany</option><option>Australia</option><option>India</option>
      </select>
    </div>
    <button class="btn btn-gold" style="width:100%;margin-top:.5rem" onclick="register()">Create My Account →</button>
  </div>
</div>

<script>
const API = '';  // same origin
let currentUser = null;
let chatSessionId = null;

// ── SECTION NAV ──────────────────────────────────────────────────────────────
function showSection(id) {
  document.querySelectorAll('.section').forEach(s => s.classList.remove('active'));
  document.querySelectorAll('.nav-links a').forEach(a => a.classList.remove('active'));
  document.getElementById(id).classList.add('active');
  const navEl = document.getElementById('nav-' + id);
  if (navEl) navEl.classList.add('active');

  // lazy-load data
  if (id === 'navigator') loadUniversities();
  if (id === 'leaderboard') loadLeaderboard();
}

// ── STATS ──────────────────────────────────────────────────────────────────
async function loadStats() {
  try {
    const r = await fetch(API + '/api/stats');
    const d = await r.json();
    document.getElementById('stat-users').textContent = (d.totalUsers/1000).toFixed(1) + 'K';
    document.getElementById('stat-admits').textContent = (d.admitsHelped/1000).toFixed(1) + 'K';
    document.getElementById('stat-loans').textContent = (d.loansProcessed/1000).toFixed(1) + 'K';
  } catch(e) {
    document.getElementById('stat-users').textContent = '12.8K';
    document.getElementById('stat-admits').textContent = '3.9K';
    document.getElementById('stat-loans').textContent = '4.2K';
  }
}

// ── AUTH ──────────────────────────────────────────────────────────────────────
async function register() {
  const name = document.getElementById('reg-name').value;
  const email = document.getElementById('reg-email').value;
  const phone = document.getElementById('reg-phone').value;
  const targetDegree = document.getElementById('reg-degree').value;
  const targetCountry = document.getElementById('reg-country').value;
  if (!name || !email) return toast('Please enter name and email', 'error');
  try {
    const r = await fetch(API + '/api/auth/register', { method:'POST', headers:{'Content-Type':'application/json'}, body: JSON.stringify({name,email,phone,targetDegree,targetCountry}) });
    const d = await r.json();
    if (d.error) { await loginWithEmail(email); return; }
    setUser(d.user);
    closeModal('register-modal');
    toast('🎉 Welcome to EduBridge, ' + name + '!');
  } catch(e) { toast('Connection error', 'error'); }
}

async function login() {
  const email = document.getElementById('login-email').value;
  if (!email) return toast('Please enter your email', 'error');
  await loginWithEmail(email);
  closeModal('login-modal');
}

async function loginWithEmail(email) {
  try {
    const r = await fetch(API + '/api/auth/login', { method:'POST', headers:{'Content-Type':'application/json'}, body: JSON.stringify({email}) });
    const d = await r.json();
    if (d.user) setUser(d.user);
    toast('👋 Welcome back, ' + d.user.name + '!');
  } catch(e) { toast('Connection error', 'error'); }
}

function setUser(user) {
  currentUser = user;
  document.getElementById('nav-auth-area').innerHTML = `
    <div class="user-chip" onclick="showSection('leaderboard')">
      <div class="user-avatar">👤</div>
      <div>
        <div class="user-name-chip">${user.name.split(' ')[0]}</div>
        <div class="xp-badge">⭐ ${user.xp} XP · 🔥 ${user.streak}</div>
      </div>
    </div>`;
}

// ── UNIVERSITIES ──────────────────────────────────────────────────────────────
const flags = {USA:'🇺🇸',UK:'🇬🇧',Canada:'🇨🇦',Germany:'🇩🇪',Australia:'🇦🇺',India:'🇮🇳'};

async function loadUniversities() {
  const country = document.getElementById('f-country')?.value || 'all';
  const course = document.getElementById('f-course')?.value || 'all';
  const grid = document.getElementById('uni-grid');
  grid.innerHTML = '<div style="color:var(--muted);padding:1rem">Loading...</div>';
  try {
    const r = await fetch(API + `/api/universities?country=${country}&course=${course}`);
    const unis = await r.json();
    grid.innerHTML = unis.map(u => `
      <div class="uni-card">
        <div class="uni-flag">${flags[u.country] || '🌍'}</div>
        <div class="uni-name">${u.name}</div>
        <div style="color:var(--muted);font-size:.82rem">${u.country} · #${u.ranking} Global</div>
        <div class="uni-meta">
          <span class="uni-tag highlight">Avg GRE: ${u.avgGre || 'N/A'}</span>
          <span class="uni-tag">Tuition: $${(u.tuitionUSD/1000).toFixed(0)}K/yr</span>
          <span class="uni-tag">Accept: ${u.acceptRate}%</span>
          <span class="uni-tag" style="color:var(--mint);border-color:rgba(16,185,129,.25)">Avg Salary: $${(u.avgSalary/1000).toFixed(0)}K</span>
          <span class="uni-tag" style="color:var(--gold);border-color:rgba(245,158,11,.25)">Deadline: ${u.deadline}</span>
        </div>
      </div>`).join('');
  } catch(e) { grid.innerHTML = '<div style="color:var(--rose)">Failed to load. Please try again.</div>'; }
}

// ── ROI ──────────────────────────────────────────────────────────────────────
function fmt(n) { return '₹' + (n >= 10000000 ? (n/10000000).toFixed(2)+'Cr' : n >= 100000 ? (n/100000).toFixed(1)+'L' : n.toLocaleString('en-IN')); }

async function calcROI() {
  const body = {
    country: document.getElementById('roi-country').value,
    course: document.getElementById('roi-course').value,
    tuitionUSD: document.getElementById('roi-tuition').value,
    livingUSD: document.getElementById('roi-living').value,
    durationYears: document.getElementById('roi-duration').value,
    currentSalaryINR: document.getElementById('roi-salary').value,
  };
  try {
    const r = await fetch(API + '/api/roi', { method:'POST', headers:{'Content-Type':'application/json'}, body: JSON.stringify(body) });
    const d = await r.json();
    const scoreColor = d.roiScore >= 75 ? 'var(--mint)' : d.roiScore >= 55 ? 'var(--gold)' : 'var(--rose)';
    document.getElementById('roi-result').style.display = 'block';
    document.getElementById('roi-result').innerHTML = `
      <div class="result-box">
        <div style="text-align:center;margin-bottom:1rem">
          <div style="font-family:'Syne',sans-serif;font-size:2.5rem;font-weight:800;color:${scoreColor}">${d.roiScore}/100</div>
          <div style="font-size:.82rem;color:var(--muted)">ROI Score</div>
          <div style="margin-top:.6rem"><div class="meter-bar"><div class="meter-fill" style="width:${d.roiScore}%;background:${scoreColor}"></div></div></div>
        </div>
        <div class="result-row"><span class="result-label">Total Education Cost</span><span class="result-value gold">${fmt(d.totalCostINR)}</span></div>
        <div class="result-row"><span class="result-label">Projected Post-Degree Salary</span><span class="result-value green">${fmt(d.projectedSalaryINR)}/yr</span></div>
        <div class="result-row"><span class="result-label">Salary Hike</span><span class="result-value green">+${d.salaryHike}%</span></div>
        <div class="result-row"><span class="result-label">Investment Payback Period</span><span class="result-value blue">${d.paybackYears} years</span></div>
        <div class="result-row"><span class="result-label">10-Year Net Gain</span><span class="result-value green">${fmt(d.tenYearNetGainINR)}</span></div>
        <div class="result-row"><span class="result-label">Recommended Loan</span><span class="result-value gold">${fmt(d.recommendedLoanINR)}</span></div>
        <div class="result-row"><span class="result-label">Estimated Monthly EMI</span><span class="result-value blue">${fmt(d.emiMonthlyINR)}/mo</span></div>
        <button class="btn btn-gold" style="width:100%;margin-top:1rem" onclick="showSection('loan')">Check Loan Eligibility →</button>
      </div>`;
  } catch(e) { toast('Calculation failed','error'); }
}

// ── ADMIT PREDICTOR ──────────────────────────────────────────────────────────
async function predictAdmit() {
  const body = {
    gre: document.getElementById('ap-gre').value,
    gpa: document.getElementById('ap-gpa').value,
    ielts: document.getElementById('ap-ielts').value,
    workExp: document.getElementById('ap-work').value,
    researchPapers: document.getElementById('ap-papers').value,
    country: document.getElementById('ap-country').value,
  };
  try {
    const r = await fetch(API + '/api/admit-predictor', { method:'POST', headers:{'Content-Type':'application/json'}, body: JSON.stringify(body) });
    const d = await r.json();
    const pColor = d.probability >= 65 ? 'var(--mint)' : d.probability >= 40 ? 'var(--gold)' : 'var(--rose)';
    const gapHtml = d.gaps.map(g => `
      <div style="display:flex;justify-content:space-between;align-items:center;padding:.5rem 0;border-bottom:1px solid var(--border)">
        <div>
          <div style="font-size:.85rem;font-weight:600;color:var(--white)">${g.area}</div>
          <div style="font-size:.75rem;color:var(--muted)">Current: ${g.current} → Target: ${g.target}</div>
        </div>
        <span style="font-size:.72rem;padding:.2rem .55rem;border-radius:4px;background:${g.impact==='High'?'rgba(244,63,94,.12)':g.impact==='Medium'?'rgba(245,158,11,.12)':'rgba(100,116,139,.12)'};color:${g.impact==='High'?'var(--rose)':g.impact==='Medium'?'var(--gold)':'var(--muted)'}">${g.impact}</span>
      </div>`).join('');
    document.getElementById('ap-result').style.display = 'block';
    document.getElementById('ap-result').innerHTML = `
      <div class="result-box">
        <div style="text-align:center;margin-bottom:1rem">
          <div style="font-family:'Syne',sans-serif;font-size:3rem;font-weight:800;color:${pColor}">${d.probability}%</div>
          <div style="font-size:1rem;font-weight:600;color:${pColor}">${d.tier}</div>
          <div style="margin:.6rem 0 0"><div class="meter-bar"><div class="meter-fill" style="width:${d.probability}%;background:${pColor}"></div></div></div>
        </div>
        <div style="font-size:.82rem;font-weight:700;color:var(--muted);margin-bottom:.5rem">PROFILE GAPS TO BRIDGE</div>
        ${gapHtml || '<div style="color:var(--mint);font-size:.85rem;padding:.5rem 0">✅ Strong profile! No major gaps found.</div>'}
      </div>`;
  } catch(e) { toast('Prediction failed','error'); }
}

// ── LOAN ──────────────────────────────────────────────────────────────────────
async function checkLoan() {
  const body = {
    loanAmount: document.getElementById('ln-amount').value,
    familyIncome: document.getElementById('ln-income').value,
    coApplicant: document.getElementById('ln-coapplicant').value,
    collateral: document.getElementById('ln-collateral').value,
    admitLetter: document.getElementById('ln-admit').value,
    country: document.getElementById('ln-country').value,
  };
  try {
    const r = await fetch(API + '/api/loan-eligibility', { method:'POST', headers:{'Content-Type':'application/json'}, body: JSON.stringify(body) });
    const d = await r.json();
    const sColor = d.eligibilityScore >= 70 ? 'var(--mint)' : d.eligibilityScore >= 45 ? 'var(--gold)' : 'var(--rose)';
    const sBg = d.eligibilityScore >= 70 ? 'rgba(16,185,129,.1)' : d.eligibilityScore >= 45 ? 'rgba(245,158,11,.1)' : 'rgba(244,63,94,.1)';
    document.getElementById('loan-result').innerHTML = `
      <div>
        <div class="loan-status-card" style="background:${sBg};border:1px solid ${sColor}40">
          <div class="loan-score" style="color:${sColor}">${d.eligibilityScore}</div>
          <div class="loan-tier" style="color:${sColor}">${d.status}</div>
          <div style="font-size:.8rem;color:var(--muted);margin-top:.4rem">${d.approved ? '✅ Eligible for loan from Poonawalla Fincorp' : '⚠️ Needs additional review'}</div>
        </div>
        <div class="result-box">
          <div class="result-row"><span class="result-label">Interest Rate</span><span class="result-value blue">${d.interestRate}% p.a.</span></div>
          <div class="result-row"><span class="result-label">Monthly EMI (10 yrs)</span><span class="result-value gold">${fmt(d.emi)}</span></div>
          <div class="result-row"><span class="result-label">Processing Fee (~1%)</span><span class="result-value">${fmt(d.processingFee)}</span></div>
          <div class="result-row"><span class="result-label">Repayment Tenure</span><span class="result-value">120 months</span></div>
          ${d.approved ? `<button class="btn btn-gold" style="width:100%;margin-top:1rem" onclick="toast('Loan application initiated! Our team will contact you within 24 hours. 🎉')">Apply Now — Poonawalla Fincorp →</button>` : `<div style="color:var(--muted);font-size:.85rem;margin-top:1rem;padding:.8rem;background:rgba(255,255,255,.03);border-radius:10px">💡 Tip: Adding a co-applicant with income or property collateral can significantly improve your eligibility.</div>`}
        </div>
      </div>`;
  } catch(e) { toast('Check failed','error'); }
}

// ── CHAT ──────────────────────────────────────────────────────────────────────
function chatKeydown(e) { if (e.key === 'Enter' && !e.shiftKey) { e.preventDefault(); sendChat(); } }

async function sendChat() {
  const input = document.getElementById('chat-input');
  const msg = input.value.trim();
  if (!msg) return;
  input.value = '';
  appendMsg(msg, 'user');
  const typing = appendMsg('Thinking...', 'typing');
  try {
    const r = await fetch(API + '/api/chat', {
      method: 'POST',
      headers: {'Content-Type': 'application/json'},
      body: JSON.stringify({ message: msg, sessionId: chatSessionId, userProfile: currentUser })
    });
    const d = await r.json();
    chatSessionId = d.sessionId;
    typing.remove();
    appendMsg(d.reply, 'ai');
  } catch(e) {
    typing.remove();
    appendMsg("I'm having trouble connecting right now. Please try again!", 'ai');
  }
}

function sendQuick(msg) {
  document.getElementById('chat-input').value = msg;
  sendChat();
  if (window.innerWidth < 768) showSection('chat');
}

function appendMsg(text, type) {
  const div = document.createElement('div');
  div.className = 'msg ' + type;
  div.textContent = text;
  const container = document.getElementById('chat-messages');
  container.appendChild(div);
  container.scrollTop = container.scrollHeight;
  return div;
}

// ── TIMELINE ──────────────────────────────────────────────────────────────────
async function generateTimeline() {
  const body = {
    intakeMonth: document.getElementById('tl-month').value,
    intakeYear: document.getElementById('tl-year').value,
    currentStatus: document.getElementById('tl-status').value,
  };
  try {
    const r = await fetch(API + '/api/timeline', { method:'POST', headers:{'Content-Type':'application/json'}, body: JSON.stringify(body) });
    const d = await r.json();
    const catColors = { test:'var(--violet)', research:'var(--sky)', documents:'var(--gold)', writing:'var(--mint)', application:'var(--rose)', finance:'var(--gold)', visa:'var(--sky)', decision:'var(--mint)', logistics:'var(--muted)' };
    const dotColors = { done:'var(--mint)', upcoming:'var(--gold)', future:'var(--border)' };
    document.getElementById('timeline-result').innerHTML = `
      <div class="card">
        <div class="card-title">📅 Your Timeline — ${d.intake} Intake (${d.monthsLeft} months away)</div>
        <div class="timeline-list">
          ${d.timeline.map((item, i) => `
            <div class="tl-item">
              <div style="display:flex;flex-direction:column;align-items:center">
                <div class="tl-dot" style="background:${dotColors[item.status]};margin-top:16px"></div>
                ${i < d.timeline.length-1 ? '<div style="width:2px;flex:1;background:var(--border);margin-top:4px;min-height:24px"></div>' : ''}
              </div>
              <div class="tl-content" style="border-left:3px solid ${dotColors[item.status]}">
                <div class="tl-date">${item.date}</div>
                <div class="tl-task">${item.task}</div>
                <span class="tl-cat" style="background:${catColors[item.category]}18;color:${catColors[item.category]}">${item.category}</span>
                <span class="tl-cat status-${item.status}" style="margin-left:.4rem">${item.status}</span>
              </div>
            </div>`).join('')}
        </div>
      </div>`;
  } catch(e) { toast('Timeline generation failed','error'); }
}

// ── LEADERBOARD ──────────────────────────────────────────────────────────────
async function loadLeaderboard() {
  try {
    const r = await fetch(API + '/api/leaderboard');
    const data = await r.json();
    document.getElementById('lb-list').innerHTML = data.map(u => `
      <div class="lb-row">
        <div class="lb-rank">${u.badge}</div>
        <div>
          <div class="lb-name">${u.name}</div>
          <div class="lb-city">${u.city} · ${u.status}</div>
        </div>
        <div style="text-align:right">
          <div class="lb-xp">${u.xp} XP</div>
          <div class="lb-streak">🔥 ${u.streak} day streak</div>
        </div>
      </div>`).join('');

    if (currentUser) {
      document.getElementById('user-progress').innerHTML = `
        <div style="text-align:center;padding:.5rem 0">
          <div style="font-family:'Syne',sans-serif;font-size:2rem;font-weight:800;color:var(--sky)">${currentUser.xp} XP</div>
          <div style="font-size:.82rem;color:var(--muted)">Level ${currentUser.level}</div>
          <div style="margin-top:.5rem;font-size:.9rem;color:var(--gold)">🔥 ${currentUser.streak} day streak</div>
          <div class="meter-bar" style="margin-top:.8rem"><div class="meter-fill" style="width:${Math.min(100,(currentUser.xp%500)/5)}%;background:var(--sky)"></div></div>
          <div style="font-size:.75rem;color:var(--muted);margin-top:.3rem">${500 - (currentUser.xp%500)} XP to Level ${currentUser.level+1}</div>
        </div>`;
    }
  } catch(e) {}
}

// ── MODAL ──────────────────────────────────────────────────────────────────────
function openModal(id) { document.getElementById(id).classList.add('open'); }
function closeModal(id) { document.getElementById(id).classList.remove('open'); }
document.querySelectorAll('.modal-overlay').forEach(o => o.addEventListener('click', e => { if(e.target === o) o.classList.remove('open'); }));

// ── TOAST ──────────────────────────────────────────────────────────────────────
function toast(msg, type='success') {
  const el = document.createElement('div');
  el.className = 'toast' + (type==='error'?' error':'');
  el.innerHTML = (type==='error'?'❌':'✅') + ' ' + msg;
  document.body.appendChild(el);
  setTimeout(() => el.remove(), 3500);
}

// ── INIT ──────────────────────────────────────────────────────────────────────
loadStats();
</script>
</body>
</html>
