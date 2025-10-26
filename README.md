
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Ryle L. De Hitta | Portfolio</title>
  <meta name="description" content="Portfolio of Ryle L. De Hitta, BSIT-CPT-1 student and coding enthusiast." />

  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&family=Space+Grotesk:wght@500;700&display=swap" rel="stylesheet">
  <!-- Font Awesome -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.6.0/css/all.min.css" crossorigin="anonymous"/>

  <!-- Three.js + GSAP + ScrollTrigger (one set) -->
  <script src="https://cdn.jsdelivr.net/npm/three@0.150.1/build/three.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>

  <style>
    :root {
      --bg-1:#050811;--bg-2:#0b1121;--card:#101626;--muted:#a1adc6;
      --accent-1:#8b5cf6;--accent-2:#6366f1;--glass:rgba(255,255,255,0.04);
      --radius:14px;--container:1100px;--shadow:0 10px 35px rgba(0,0,0,0.5);
    }
    [data-theme="light"]{
      --bg-1:#f5f6fa;--bg-2:#fff;--card:#fefefe;--muted:#444;
      --glass:rgba(0,0,0,0.04);--shadow:0 4px 15px rgba(0,0,0,0.1);
      color:#111;
    }
    *{box-sizing:border-box;margin:0;padding:0}
    html,body{height:100%}
    body{
      font-family:'Inter',sans-serif;background:radial-gradient(circle at 20% 30%,var(--bg-2) 0%,var(--bg-1)100%);
      color:#e6eef8;line-height:1.6;overflow-x:hidden;position:relative;
    }
    body[data-theme="light"]{color:#111;}
    canvas#particles, canvas#bg-3d{position:fixed;top:0;left:0;width:100%;height:100%;pointer-events:none;z-index:-2}
    a{text-decoration:none;color:inherit}

    @keyframes fadeInUp{0%{opacity:0;transform:translateY(12px)}100%{opacity:1;transform:translateY(0)}}

    nav{
      position:sticky;top:0;z-index:100;backdrop-filter:blur(14px);
      background:rgba(15,18,34,0.6);border-bottom:1px solid rgba(255,255,255,0.05);
      display:flex;justify-content:space-between;align-items:center;padding:12px 24px;max-width:var(--container);margin:0 auto;
    }
    [data-theme="light"] nav{background:rgba(255,255,255,0.88);}
    .logo{font-family:'Space Grotesk',sans-serif;font-size:1.15rem;font-weight:700;
      background:linear-gradient(90deg,var(--accent-1),var(--accent-2));
      -webkit-background-clip:text;-webkit-text-fill-color:transparent}
    .nav-links{display:flex;gap:14px;align-items:center}
    .nav-links a{font-weight:600;font-size:.95rem;color:var(--muted);padding:8px 10px;border-radius:8px;transition:.22s}
    .nav-links a:hover{background:rgba(255,255,255,0.04);color:#fff;transform:translateY(-2px)}
    .nav-toggle{display:none;background:transparent;border:0;color:var(--muted);font-size:1.2rem}
    .theme-toggle{background:none;border:0;color:var(--muted);font-size:1.1rem;cursor:pointer;padding:6px;border-radius:8px}

    .page {
      max-width:var(--container);margin:0 auto;padding:28px;
    }

    .hero{display:flex;align-items:center;justify-content:space-between;gap:32px;padding:60px 0 48px;animation:fadeInUp .8s ease;}
    .hero-left h1{font-family:'Space Grotesk',sans-serif;font-size:2.2rem;margin-bottom:8px;color:#fff}
    [data-theme="light"] .hero-left h1{color:#111;}
    .hero-left p{color:var(--muted);max-width:520px;margin:0}
    .hero-cta{margin-top:18px;display:flex;gap:12px;flex-wrap:wrap}
    .btn{display:inline-flex;align-items:center;gap:10px;font-weight:700;font-size:.95rem;border-radius:10px;padding:10px 14px;cursor:pointer;transition:.22s;border:0}
    .btn-primary{background:linear-gradient(90deg,var(--accent-1),var(--accent-2));color:#fff;box-shadow:0 6px 20px rgba(99,102,241,0.14)}
    .btn-outline{background:transparent;color:var(--muted);border:1px solid rgba(255,255,255,0.06)}
    .btn:hover{transform:translateY(-3px);box-shadow:0 12px 30px rgba(99,102,241,0.18)}
    .hero-right{flex:0 0 180px;display:flex;justify-content:center}
    .profile{width:180px;height:180px;border-radius:50%;overflow:hidden;border:3px solid rgba(255,255,255,0.06);background:linear-gradient(180deg,rgba(255,255,255,0.03),rgba(255,255,255,0.01));box-shadow:var(--shadow);transition:.35s}
    .profile:hover{transform:scale(1.03)}
    .profile img{width:100%;height:100%;object-fit:cover;display:block}

    section{padding:56px 0;animation:fadeInUp .8s ease}
    h2{font-family:'Space Grotesk',sans-serif;font-size:1.6rem;margin-bottom:18px;text-align:center;color:#fff}

    .about-grid{display:flex;flex-wrap:wrap;gap:20px;justify-content:center}
    .about-card{background:var(--glass);border:1px solid rgba(255,255,255,0.04);border-radius:12px;padding:20px;max-width:520px;box-shadow:var(--shadow)}

    .projects-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:20px;align-items:start}
    .proj-card{position:relative;overflow:hidden;border-radius:12px;background:var(--card);transition:transform .28s,box-shadow .28s;box-shadow:var(--shadow)}
    .proj-card img{width:100%;height:160px;object-fit:cover;filter:brightness(.85);transition:transform .35s,filter .35s}
    .proj-info{padding:14px}
    .proj-card:hover img{transform:scale(1.06);filter:brightness(1)}
    .proj-card:hover{transform:translateY(-6px);box-shadow:0 14px 40px rgba(99,102,241,0.18)}

    .skills-list{max-width:640px;margin:0 auto;display:grid;gap:12px}
    .skill{display:block}
    .skill span{display:flex;justify-content:space-between;color:var(--muted);font-weight:600;margin-bottom:6px}
    .bar{background:rgba(255,255,255,0.05);border-radius:999px;height:10px;overflow:hidden}
    .fill{height:100%;background:linear-gradient(90deg,var(--accent-1),var(--accent-2));border-radius:999px;width:0;animation:fillAnim 1.8s ease forwards}
    @keyframes fillAnim{from{width:0}}

    /* Contact form */
    form.contact{max-width:640px;margin:0 auto;background:var(--glass);border:1px solid rgba(255,255,255,0.04);padding:20px;border-radius:12px;box-shadow:var(--shadow)}
    form.contact input, form.contact textarea{width:100%;padding:10px;margin-bottom:12px;border-radius:8px;border:1px solid rgba(255,255,255,0.06);background:rgba(255,255,255,0.02);color:inherit}

    footer{padding:28px 0;text-align:center;color:var(--muted);font-size:.95rem}

    /* Logo reveal + 3D bg styles */
    #bg-3d{z-index:-3}
    .logo-reveal{position:fixed;top:50%;left:50%;transform:translate(-50%,-50%);font-size:2.4rem;font-weight:800;color:var(--accent-1);letter-spacing:1px;text-shadow:0 0 18px rgba(139,92,246,0.9);opacity:0;z-index:200;pointer-events:none}
    .intro-overlay{position:fixed;inset:0;display:grid;place-items:center;background:linear-gradient(180deg,rgba(2,6,23,0.92),rgba(2,6,23,0.75));backdrop-filter:blur(6px);z-index:199}
    .intro-hidden{opacity:0;visibility:hidden;pointer-events:none}

    /* 3D tilt safety */
    .tilt-safe{transform-style:preserve-3d;will-change:transform;transition:transform .25s ease}

    @media(max-width:880px){
      .nav-links{display:none}
      .nav-toggle{display:block}
      .hero{flex-direction:column;align-items:center;text-align:center}
      .hero-right{order:-1;margin-bottom:18px}
      .profile{width:140px;height:140px}
      canvas#bg-3d{display:none}
    }
  </style>
</head>
<body data-theme="dark">
  <!-- 3D background canvas (rotating geometric shapes) -->
  <canvas id="bg-3d" aria-hidden="true"></canvas>
  <!-- lightweight particle canvas (2D dots) -->
  <canvas id="particles" aria-hidden="true"></canvas>

  <!-- Logo reveal (will animate) -->
  <div class="logo-reveal" id="logoReveal">Ryle L. De Hitta</div>

  <nav class="page" role="navigation" aria-label="Main navigation">
    <div class="logo">Ryle L. De Hitta</div>
    <div class="nav-links" id="navLinks">
      <a class="nav-link" href="#home">Home</a>
      <a class="nav-link" href="#about">About</a>
      <a class="nav-link" href="#projects">Projects</a>
      <a class="nav-link" href="#skills">Skills</a>
      <a class="nav-link" href="#contact">Contact</a>
    </div>
    <div style="display:flex;gap:8px;align-items:center">
      <button class="theme-toggle" id="themeToggle" aria-label="Toggle theme"><i class="fa-solid fa-sun"></i></button>
      <button class="nav-toggle" id="navToggle" aria-label="Toggle menu" aria-expanded="false"><i class="fa-solid fa-bars"></i></button>
    </div>
  </nav>

  <main class="page" id="home">
    <section class="hero" id="heroSection">
      <div class="hero-left">
        <h1>Curious Mind. Code Crafter. Innovator.</h1>
        <p>Hey, I’m <strong>Ryle L. De Hitta</strong> — a BSIT-CPT-1 student and coding enthusiast passionate about building modern, AI-driven, and tech-inspired experiences.</p>
        <div class="hero-cta">
          <a class="btn btn-primary" href="#projects"><i class="fa-solid fa-rocket"></i> Explore Projects</a>
          <a class="btn btn-outline" href="#contact"><i class="fa-solid fa-paper-plane"></i> Contact</a>
        </div>
      </div>
      <div class="hero-right">
        <div class="profile" role="img" aria-label="Profile image">
          <img src="IMG_20250814_092221.jpg" alt="Profile" onerror="this.src='https://via.placeholder.com/400x400.png?text=Profile';">
        </div>
      </div>
    </section>
    <section id="about">
      <h2>About Me</h2>
      <div class="about-grid">
        <div class="about-card">
          <h3 style="color:var(--accent-2)">Who I Am</h3>
          <p>I'm <strong>Ryle L. De Hitta</strong>, a BSIT-CPT-1 student passionate about coding, design, and technology.</p>
        </div>
        <div class="about-card">
          <h3 style="color:var(--accent-2)">What Drives Me</h3>
          <p>I love challenges — whether it’s solving a tough bug or building something new. My goal: impactful, creative tech solutions.</p>
        </div>
      </div>
    </section>
    <section id="projects">
      <h2>Projects</h2>
      <div class="projects-grid">
        <article class="proj-card tilt-safe">
          <img src="IMG_20251016_170758.png" alt="AnimeInfo" onerror="this.src='https://via.placeholder.com/800x450.png?text=Project+1';">
          <div class="proj-info"><h3>AnimeInfo</h3><p>AI-powered anime search & community curation — React, Node.js, AI</p></div>
        </article>
        <article class="proj-card tilt-safe">
          <img src="IMG_20251008_073722.jpg" alt="Logic and Switching Theory" onerror="this.src='https://via.placeholder.com/800x450.png?text=Project+2';">
          <div class="proj-info"><h3>Logic & Switching Theory</h3><p>OR-gates activity and visual demos.</p></div>
        </article>
        <article class="proj-card tilt-safe">
          <img src="Screenshot_20251022_194013_22e4250240c136c826b8a3b1264b092d.jpg" alt="MLBB Highlights" onerror="this.src='https://via.placeholder.com/800x450.png?text=Project+3';">
          <div class="proj-info"><h3>MLBB Highlights</h3><p>Mobile Legends gameplay highlights — editing & showcase.</p></div>
        </article>
      </div>
    </section
    <section id="skills">
      <h2>Skills</h2>
      <div class="skills-list">
        <div class="skill"><span>HTML <strong>95%</strong></span><div class="bar"><div class="fill" style="width:95%"></div></div></div>
        <div class="skill"><span>CSS <strong>90%</strong></span><div class="bar"><div class="fill" style="width:90%"></div></div></div>
        <div class="skill"><span>JavaScript <strong>75%</strong></span><div class="bar"><div class="fill" style="width:75%"></div></div></div>
        <div class="skill"><span>Python <strong>70%</strong></span><div class="bar"><div class="fill" style="width:70%"></div></div></div>
        <div class="skill"><span>React <strong>60%</strong></span><div class="bar"><div class="fill" style="width:60%"></div></div></div>
      </div>
    </section>
    <section id="contact">
      <h2>Contact Me</h2>
      <form class="contact" id="contactForm" novalidate>
        <input name="name" type="text" placeholder="Your Name" required>
        <input name="email" type="email" placeholder="Your Email" required>
        <textarea name="message" rows="5" placeholder="Your Message" required></textarea>
        <button class="btn btn-primary" type="submit">Send Message</button>
        <div id="formStatus" style="margin-top:10px;color:var(--muted);font-size:.95rem"></div>
      </form>
    </section>


  <footer>© 2025 Ryle L. De Hitta. Crafted with ❤️ and creativity.</footer>

  <!-- Intro overlay (accessible, dismissible) -->
  <div class="intro-overlay" id="introOverlay" aria-hidden="false">
    <div style="text-align:center;color:#fff">
      <h1 style="font-family:'Space Grotesk',sans-serif;margin-bottom:8px;font-size:2.4rem">Welcome — Ryle L. De Hitta</h1>
      <p style="color:rgba(230,238,248,0.9);max-width:70vw;margin:0 auto 12px">Curious mind • Community builder • Code crafter</p>
      <div style="display:flex;gap:10px;justify-content:center;margin-top:12px">
        <button id="enterBtn" class="btn btn-primary">Enter Portfolio</button>
        <button id="skipBtn" class="btn btn-outline">Skip</button>
      </div>
    </div>
  </div>

  <script>
  // ---------- NAV & THEME ----------
  const navToggle = document.getElementById('navToggle');
  const navLinks = document.getElementById('navLinks');
  navToggle && navToggle.addEventListener('click', () => {
    const expanded = navToggle.getAttribute('aria-expanded') === 'true';
    navToggle.setAttribute('aria-expanded', String(!expanded));
    navLinks.style.display = navLinks.style.display === 'flex' ? 'none' : 'flex';
  });

  const themeToggle = document.getElementById('themeToggle');
  const body = document.body;
  function setTheme(t){
    body.setAttribute('data-theme', t);
    themeToggle.innerHTML = t === 'dark' ? '<i class="fa-solid fa-sun"></i>' : '<i class="fa-solid fa-moon"></i>';
    try{localStorage.setItem('site-theme', t);}catch(e){}
  }
  const saved = (localStorage.getItem('site-theme') || 'dark');
  setTheme(saved);
  themeToggle.addEventListener('click', ()=> setTheme(body.getAttribute('data-theme') === 'dark' ? 'light' : 'dark'));

  // ---------- PARTICLES (2D lightweight) ----------
  const canvas = document.getElementById('particles');
  const ctx = canvas.getContext('2d');
  let parts = [];
  function resizeParticles(){ canvas.width = innerWidth; canvas.height = innerHeight; }
  window.addEventListener('resize', resizeParticles);
  resizeParticles();
  for(let i=0;i<80;i++){
    parts.push({x:Math.random()*canvas.width,y:Math.random()*canvas.height,r:Math.random()*1.8+0.2,dx:(Math.random()-0.5)*0.6,dy:(Math.random()-0.5)*0.6});
  }
  function drawParticles(){
    ctx.clearRect(0,0,canvas.width,canvas.height);
    ctx.fillStyle = 'rgba(255,255,255,0.06)';
    parts.forEach(p=>{
      ctx.beginPath();ctx.arc(p.x,p.y,p.r,0,Math.PI*2);ctx.fill();
      p.x+=p.dx; p.y+=p.dy;
      if(p.x<0||p.x>canvas.width) p.dx *= -1;
      if(p.y<0||p.y>canvas.height) p.dy *= -1;
    });
    requestAnimationFrame(drawParticles);
  }
  drawParticles();

  // ---------- THREE.JS: Rotating cubes background (performance-conscious) ----------
  (function(){
    if(window.innerWidth < 760) return; // disable heavy canvas on small screens
    const canvas3 = document.getElementById('bg-3d');
    const renderer = new THREE.WebGLRenderer({ canvas: canvas3, alpha:true, antialias:true });
    renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));
    renderer.setSize(window.innerWidth, window.innerHeight);
    const scene = new THREE.Scene();
    const camera = new THREE.PerspectiveCamera(60, innerWidth/innerHeight, 0.1, 1000);
    camera.position.z = 6;

    const light = new THREE.PointLight(0x8a63ff, 1.6, 60);
    light.position.set(6,6,6);
    scene.add(light);
    scene.add(new THREE.AmbientLight(0x222233,0.6));

    const geometry = new THREE.BoxGeometry(1,1,1);
    const material = new THREE.MeshStandardMaterial({ color:0x8a63ff, emissive:0x120022, metalness:0.6, roughness:0.3 });
    const cubes = [];
    const count = 24;
    for(let i=0;i<count;i++){
      const m = new THREE.Mesh(geometry, material);
      m.position.set((Math.random()-0.5)*12, (Math.random()-0.5)*8, (Math.random()-0.5)*12);
      const s = Math.random()*0.6+0.3;
      m.scale.set(s,s,s);
      m.rotation.set(Math.random()*Math.PI, Math.random()*Math.PI, Math.random()*Math.PI);
      scene.add(m);
      cubes.push(m);
    }

    function render(){
      requestAnimationFrame(render);
      cubes.forEach((c, idx) => {
        c.rotation.x += 0.0015 + (idx%5)*0.0002;
        c.rotation.y += 0.002 + (idx%7)*0.0002;
      });
      renderer.render(scene, camera);
    }
    render();

    window.addEventListener('resize', ()=>{
      renderer.setSize(window.innerWidth, window.innerHeight);
      camera.aspect = window.innerWidth / window.innerHeight;
      camera.updateProjectionMatrix();
    });
  })();

  // ---------- GSAP: Logo reveal + Intro overlay handling ----------
  gsap.registerPlugin(ScrollTrigger);
  const logo = document.getElementById('logoReveal');
  const intro = document.getElementById('introOverlay');
  const enterBtn = document.getElementById('enterBtn');
  const skipBtn = document.getElementById('skipBtn');

  // show logo (small quick animation) then hide; respect reduced motion
  const reduce = window.matchMedia('(prefers-reduced-motion: reduce)').matches;
  if(!reduce){
    gsap.fromTo(logo, {opacity:0, scale:0.9, y:10}, {opacity:1, scale:1.05, y:0, duration:1, ease:"power2.out"});
    gsap.to(logo, {opacity:0, y:-80, delay:2.2, duration:1.1, ease:"power2.in"});
  } else {
    logo.style.opacity = 0;
  }

  // Intro overlay: auto dismiss or click
  function dismissIntro(){
    if(!intro) return;
    intro.classList.add('intro-hidden');
    intro.setAttribute('aria-hidden','true');
    try{document.documentElement.style.overflow='';document.body.style.overflow='';}catch(e){}
  }
  enterBtn && enterBtn.addEventListener('click', dismissIntro);
  skipBtn && skipBtn.addEventListener('click', dismissIntro);
  // auto-dismiss after short time, shorter on mobile or reduced motion
  const introTimeout = reduce || window.innerWidth < 520 ? 600 : 3000;
  setTimeout(dismissIntro, introTimeout);

  // ---------- 3D tilt on hover for project cards & buttons ----------
  function applyTilt(selector){
    const els = document.querySelectorAll(selector);
    els.forEach(el=>{
      let rect;
      el.addEventListener('mousemove', (e)=>{
        rect = el.getBoundingClientRect();
        const x = (e.clientX - rect.left) / rect.width;
        const y = (e.clientY - rect.top) / rect.height;
        const rotateY = (x - 0.5) * 8;
        const rotateX = (0.5 - y) * 6;
        el.style.transform = `translateZ(0) rotateX(${rotateX}deg) rotateY(${rotateY}deg) scale(1.02)`;
      });
      el.addEventListener('mouseleave', ()=>{ el.style.transform = 'translateZ(0) rotateX(0deg) rotateY(0deg) scale(1)'; el.style.transition='transform .28s ease'; });
    });
  }
  applyTilt('.proj-card');
  applyTilt('.btn');

  // ---------- GSAP: Entrance animations & Part 6 (scroll 3D) ----------
  gsap.utils.toArray('section, .hero-left, .proj-card, .skills-list').forEach((el, i)=>{
    gsap.fromTo(el, {opacity:0, y:30}, {opacity:1, y:0, duration:0.8, delay: i*0.06, ease:"power2.out"});
  });

  // Scroll-triggered depth
  if(!reduce && window.innerWidth >= 760){
    gsap.to('#bg-3d', {
      scrollTrigger: { scrub: 0.8 },
      scale: 1.07,
      opacity: 0.95,
      ease: 'none'
    });

    document.querySelectorAll('section').forEach((sec)=>{
      gsap.fromTo(sec, {opacity:0, y:60, z:-150}, {
        opacity:1, y:0, z:0, duration:1.1, ease:'power3.out',
        scrollTrigger: { trigger: sec, start: 'top 80%', end: 'bottom 60%', toggleActions: 'play none none reverse' }
      });
    });
  }

  // ------- Contact form mailto fallback ----------
  const form = document.getElementById('contactForm');
  const status = document.getElementById('formStatus');
  form && form.addEventListener('submit', (e)=>{
    e.preventDefault();
    const fd = new FormData(form);
    const name = fd.get('name')||'';
    const email = fd.get('email')||'';
    const message = fd.get('message')||'';
    const subject = encodeURIComponent('Portfolio contact from ' + name);
    const body = encodeURIComponent(`Email: ${email}\n\n${message}`);
    const recipient = 'youremail@example.com';
    window.location.href = `mailto:${recipient}?subject=${subject}&body=${body}`;
    status.textContent = 'Opening your mail client...';
    setTimeout(()=> status.textContent = 'If your mail client did not open, copy this message and email directly.',2500);
  });

  // ---------- Accessibility: reduce motion & keyboard ----------
  if(reduce){
    document.querySelectorAll('.fill').forEach(el => el.style.transition='none');
  }

  // ensure nav links smooth scroll
  document.querySelectorAll('a[href^="#"]').forEach(a=>{
    a.addEventListener('click', function(e){
      const target = document.querySelector(this.getAttribute('href'));
      if(target){
        e.preventDefault();
        target.scrollIntoView({behavior:'smooth',block:'start'});
      }
    });
  });

  // Set copyright year
  document.addEventListener('DOMContentLoaded', ()=> {
    const footer = document.querySelector('footer');
    footer && (footer.innerHTML = `© ${new Date().getFullYear()} Ryle L. De Hitta. Crafted with ❤️ and creativity.`);
  });
  </script>
  <!-- ------------- 3D Background: Customizable (replace previous Three.js code) ------------- -->
<style>
  /* Controls UI */
  #bg-controls {
    position: fixed;
    right: 14px;
    bottom: 18px;
    z-index: 220;
    background: rgba(6,8,18,0.6);
    border: 1px solid rgba(255,255,255,0.04);
    backdrop-filter: blur(6px);
    padding: 10px;
    border-radius: 12px;
    color: #e6eef8;
    font-family: Inter, sans-serif;
    font-size: 13px;
    box-shadow: 0 10px 30px rgba(3,6,23,0.6);
    min-width: 180px;
  }
  #bg-controls h4{margin:0 0 8px 0;font-size:13px}
  .bg-btn {display:block;width:100%;margin:6px 0;padding:8px;border-radius:8px;background:transparent;border:1px solid rgba(255,255,255,0.03);color:var(--muted);cursor:pointer;text-align:left}
  .bg-btn.active {background:linear-gradient(90deg,var(--accent-1),var(--accent-2));color:#fff;border:0}
  #bg-quality {width:100%;margin-top:8px}
  #bg-controls small{display:block;color:rgba(255,255,255,0.6);margin-top:6px}
  #bg-upload{display:block;margin-top:8px;width:100%}
  /* hide on small screens */
  @media (max-width:760px) { #bg-controls { display:none; } }
</style>

<div id="bg-controls" aria-hidden="false" role="region" aria-label="Background controls">
  <h4>Background</h4>
  <button class="bg-btn" data-preset="cubes" id="btn-cubes">🧊 Rotating Cubes</button>
  <button class="bg-btn" data-preset="spheres" id="btn-spheres">⚪ Floating Spheres</button>
  <button class="bg-btn" data-preset="grid" id="btn-grid">🔷 Wireframe Grid</button>

  <label style="margin-top:8px;font-size:12px">Performance</label>
  <input id="bg-quality" type="range" min="0.25" max="1" step="0.25" value="1" />
  <small>Quality (lower for smoother on slow devices)</small>

  <label style="margin-top:6px;font-size:12px">Use your own image</label>
  <input id="bg-upload" type="file" accept="image/*" />
  <small>Image will be used as a distant background plane</small>
</div>

<script>
/*
  Customizable 3D background using three.js
  - Presets: cubes, spheres, grid
  - Upload an image to use as distant background
  - Quality slider (0.25 - 1)
  - Auto-disable on mobile (width < 760)
*/

(function(){
  // Safety / capability checks
  if (!window.THREE) {
    console.warn('Three.js not found — 3D background disabled.');
    return;
  }

  const canvas = document.getElementById('bg-3d');
  if (!canvas) {
    console.warn('Canvas #bg-3d not found — 3D background disabled.');
    return;
  }

  // Mobile fallback: don't init heavy scene on small screens
  const MOBILE_BREAKPOINT = 760;
  const isMobile = window.innerWidth < MOBILE_BREAKPOINT || navigator.userAgent.match(/Mobi|Android/i);
  if (isMobile) {
    // Hide canvas visually
    canvas.style.display = 'none';
    console.info('Mobile device detected — 3D background disabled for performance.');
    return;
  }

  // Basic three.js setup
  const renderer = new THREE.WebGLRenderer({ canvas: canvas, alpha: true, antialias: true });
  const DPR = Math.min( window.devicePixelRatio || 1, 2 );
  renderer.setPixelRatio(DPR);
  renderer.setSize(window.innerWidth, window.innerHeight);
  renderer.domElement.style.pointerEvents = 'none'; // clicks pass through
  renderer.domElement.style.zIndex = -3;

  const scene = new THREE.Scene();
  const camera = new THREE.PerspectiveCamera(60, window.innerWidth/window.innerHeight, 0.1, 1000);
  camera.position.z = 6;

  // Environment lighting
  const ambient = new THREE.AmbientLight(0x222233, 0.6);
  scene.add(ambient);
  const point = new THREE.PointLight(0x8a63ff, 1.4);
  point.position.set(6, 6, 6);
  scene.add(point);

  // Global state
  let state = {
    preset: 'cubes',
    quality: 1,
    userBgTexture: null
  };

  // Scene objects holders
  let objects = [];
  let planeBg = null;

  // Utility: dispose meshes and geometries
  function clearObjects(){
    objects.forEach(obj=>{
      if(obj.geometry) obj.geometry.dispose();
      if(obj.material){
        if (obj.material.map) obj.material.map.dispose();
        obj.material.dispose();
      }
      scene.remove(obj);
    });
    objects = [];
  }
  function removePlaneBg(){
    if (planeBg) {
      if (planeBg.geometry) planeBg.geometry.dispose();
      if (planeBg.material) {
        if (planeBg.material.map) planeBg.material.map.dispose();
        planeBg.material.dispose();
      }
      scene.remove(planeBg);
      planeBg = null;
    }
  }

  // Preset builders
  function buildCubes(count=24){
    clearObjects();
    const geo = new THREE.BoxGeometry(1,1,1);
    const mat = new THREE.MeshStandardMaterial({ color: 0x8a63ff, emissive: 0x120022, metalness: 0.6, roughness: 0.3 });
    for(let i=0;i<count;i++){
      const m = new THREE.Mesh(geo.clone(), mat.clone());
      m.position.set((Math.random()-0.5)*12, (Math.random()-0.5)*6, (Math.random()-0.5)*12);
      const s = Math.random()*0.7 + 0.25;
      m.scale.set(s,s,s);
      m.rotation.set(Math.random()*Math.PI, Math.random()*Math.PI, Math.random()*Math.PI);
      scene.add(m);
      objects.push(m);
    }
  }

  function buildSpheres(count=180){
    clearObjects();
    // small moving spheres (particles-like but real meshes)
    const geo = new THREE.SphereGeometry(0.08, 12, 12);
    const mat = new THREE.MeshStandardMaterial({ color: 0xc8caff, emissive: 0x1a1630, metalness: 0.1, roughness: 0.5 });
    for(let i=0;i<count;i++){
      const m = new THREE.Mesh(geo.clone(), mat.clone());
      m.position.set((Math.random()-0.5)*12, (Math.random()-0.5)*8, (Math.random()-0.5)*12);
      const s = Math.random()*0.9 + 0.2;
      m.scale.setScalar(s);
      scene.add(m);
      objects.push(m);
      // give each one a random velocity (store on object)
      m.userData.vel = { x:(Math.random()-0.5)*0.002, y:(Math.random()-0.5)*0.002, z:(Math.random()-0.5)*0.002 };
    }
  }

  function buildGrid(size=18, step=1.4){
    clearObjects();
    // Wireframe grid made of lines (cheap)
    const material = new THREE.LineBasicMaterial({ color: 0x7a6df6, opacity: 0.9, transparent: true });
    const group = new THREE.Group();
    for(let y=-4;y<=4;y++){
      const points = [];
      for(let x=-8;x<=8;x++){
        points.push(new THREE.Vector3(x*step, y*step*0.45, Math.sin(x+y)*0.4));
      }
      const geom = new THREE.BufferGeometry().setFromPoints(points);
      const line = new THREE.Line(geom, material);
      group.add(line);
      objects.push(line);
      scene.add(line);
    }
    // add a rotating pivot for subtle motion
    objects.push(group);
    // no need to keep separate variable
  }

  // Apply state (rebuild scene for preset)
  function applyPreset(){
    removePlaneBg();
    const q = state.quality;
    if(state.preset === 'cubes'){
      const count = Math.round(24 * q);
      buildCubes(Math.max(8, count));
    } else if(state.preset === 'spheres'){
      const count = Math.round(180 * q);
      buildSpheres(Math.max(40, count));
    } else if(state.preset === 'grid'){
      buildGrid();
    }
  }

  // Add plane background image if user provided
  function setBackgroundImage(imgUrl){
    removePlaneBg();
    if(!imgUrl) return;
    const texLoader = new THREE.TextureLoader();
    texLoader.load(imgUrl, (tex)=>{
      const geom = new THREE.PlaneGeometry(40, 22);
      const mat = new THREE.MeshBasicMaterial({ map: tex, toneMapped: false });
      planeBg = new THREE.Mesh(geom, mat);
      planeBg.position.set(0,0,-20); // far back
      scene.add(planeBg);
    }, undefined, (err)=>{ console.warn('bg image load error', err); });
  }

  // Animation loop (optimized)
  let last = performance.now();
  function animate(now){
    const dt = (now - last) * 0.001;
    last = now;
    // rotate/animate objects lightly
    objects.forEach((o, idx)=>{
      if (state.preset === 'cubes'){
        o.rotation.x += 0.0015 + (idx%5)*0.0003;
        o.rotation.y += 0.002 + (idx%7)*0.00025;
      } else if(state.preset === 'spheres'){
        // move spheres by velocity
        if(o.userData && o.userData.vel){
          o.position.x += o.userData.vel.x * (1 + dt*60);
          o.position.y += o.userData.vel.y * (1 + dt*60);
          o.position.z += o.userData.vel.z * (1 + dt*60);
          // bounce bounds
          if(o.position.x < -12 || o.position.x > 12) o.userData.vel.x *= -1;
          if(o.position.y < -8 || o.position.y > 8) o.userData.vel.y *= -1;
          if(o.position.z < -12 || o.position.z > 12) o.userData.vel.z *= -1;
        }
      } else if(state.preset === 'grid'){
        // gently rotate whole group if group present
        // some items may be groups (Three.Group)
        if (o.type === 'Group') {
          o.rotation.z += 0.0008;
          o.rotation.x += 0.0003;
        }
      }
    });

    // subtle camera bob (slow)
    camera.position.x = Math.sin(now*0.0004) * 0.12;
    camera.position.y = Math.sin(now*0.0007) * 0.08;

    renderer.render(scene, camera);
    requestAnimationFrame(animate);
  }

  // Controls & UI wiring
  const btnCubes = document.getElementById('btn-cubes');
  const btnSpheres = document.getElementById('btn-spheres');
  const btnGrid = document.getElementById('btn-grid');
  const qSlider = document.getElementById('bg-quality');
  const upload = document.getElementById('bg-upload');

  function setActiveButton(id){
    [btnCubes,btnSpheres,btnGrid].forEach(b=>b.classList.remove('active'));
    const el = document.getElementById(id);
    el && el.classList.add('active');
  }

  btnCubes.addEventListener('click', ()=> { state.preset='cubes'; setActiveButton('btn-cubes'); applyPreset(); });
  btnSpheres.addEventListener('click', ()=> { state.preset='spheres'; setActiveButton('btn-spheres'); applyPreset(); });
  btnGrid.addEventListener('click', ()=> { state.preset='grid'; setActiveButton('btn-grid'); applyPreset(); });

  qSlider.addEventListener('input', (e)=> {
    state.quality = parseFloat(e.target.value);
    // adjust renderer pixel ratio for quality
    renderer.setPixelRatio(Math.max(0.6, Math.min(DPR * state.quality, 2)));
    applyPreset();
  });

  upload.addEventListener('change', (e)=>{
    const f = e.target.files && e.target.files[0];
    if(!f) return;
    const url = URL.createObjectURL(f);
    state.userBgTexture = url;
    setBackgroundImage(url);
  });

  // initialize default
  setActiveButton('btn-cubes');
  applyPreset();

  // Start animation loop
  requestAnimationFrame(animate);

  // Resize handler
  window.addEventListener('resize', ()=>{
    renderer.setSize(window.innerWidth, window.innerHeight);
    camera.aspect = window.innerWidth / window.innerHeight;
    camera.updateProjectionMatrix();
    // mobile auto-disable at runtime
    if(window.innerWidth < MOBILE_BREAKPOINT){
      renderer.domElement.style.display = 'none';
    } else {
      renderer.domElement.style.display = '';
    }
  });

  // expose for debugging (optional)
  window._bg3d = {
    scene, camera, renderer, state, applyPreset, setBackgroundImage
  };

})();
</script>
<!-- ------------- end 3D background code ------------- -->
<!-- ===== Galaxy 3D Environment (replace previous 3D code) ===== -->
<style>
  /* Minimal controls UI (desktop only) */
  #bg-controls { position: fixed; right: 14px; bottom: 18px; z-index: 240;
    background: rgba(6,8,18,0.6); border:1px solid rgba(255,255,255,0.03);
    backdrop-filter: blur(6px); padding:10px; border-radius:12px; color:#e6eef8;
    font-family: Inter, sans-serif; font-size:13px; box-shadow:0 10px 30px rgba(3,6,23,0.6); min-width:180px;
  }
  #bg-controls h4{margin:0 0 8px 0;font-size:13px}
  .bg-row{display:flex;gap:6px}
  .bg-btn{flex:1;padding:8px;border-radius:8px;background:transparent;border:1px solid rgba(255,255,255,0.03);color:var(--muted);cursor:pointer}
  .bg-btn.active{background:linear-gradient(90deg,var(--accent-1),var(--accent-2));color:#fff;border:0}
  #bg-quality{width:100%;margin-top:8px}
  #bg-upload{display:block;margin-top:8px;width:100%}
  #bg-controls small{display:block;color:rgba(255,255,255,0.6);margin-top:6px}
  @media (max-width:760px){ #bg-controls{display:none} canvas#bg-3d{display:none} }
</style>

<div id="bg-controls" aria-hidden="false" role="region" aria-label="Background controls">
  <h4>Background • Galaxy</h4>
  <div style="margin-bottom:6px">Preset</div>
  <div class="bg-row">
    <button class="bg-btn active" id="preset-galaxy">Galaxy</button>
    <button class="bg-btn" id="preset-minimal">Minimal</button>
  </div>
  <label style="margin-top:8px;font-size:12px">Quality</label>
  <input id="bg-quality" type="range" min="0.25" max="1" step="0.25" value="1" />
  <label style="margin-top:8px;font-size:12px">Upload nebula image</label>
  <input id="bg-upload" type="file" accept="image/*" />
  <small>Image used as distant nebula plane. (Optional)</small>
</div>

<script>
/* Galaxy environment for #bg-3d canvas
   - layered nebula planes (canvas textures) + performant stars (Points)
   - gentle parallax & camera motion
   - mobile auto-disable
   Paste under body, replace any old Three.js background code.
*/
(function(){
  if (!window.THREE) { console.warn('Three.js required. Include it before this script.'); return; }
  const canvas = document.getElementById('bg-3d');
  if (!canvas) { console.warn('#bg-3d canvas not found — add <canvas id="bg-3d"></canvas> to your HTML'); return; }

  // Mobile safety
  const MOBILE_BREAKPOINT = 760;
  const isMobile = window.innerWidth < MOBILE_BREAKPOINT || /Mobi|Android/i.test(navigator.userAgent);
  if (isMobile) {
    canvas.style.display = 'none';
    console.info('Mobile detected — galaxy background disabled for performance.');
    return;
  }

  // Renderer
  const renderer = new THREE.WebGLRenderer({ canvas: canvas, alpha: true, antialias: true });
  renderer.setPixelRatio(Math.min(window.devicePixelRatio || 1, 2));
  renderer.setSize(window.innerWidth, window.innerHeight);
  renderer.domElement.style.zIndex = -3;
  renderer.domElement.style.pointerEvents = 'none';

  // Scene & Camera
  const scene = new THREE.Scene();
  const camera = new THREE.PerspectiveCamera(60, window.innerWidth/window.innerHeight, 0.1, 1000);
  camera.position.z = 6;

  // Lights
  const amb = new THREE.AmbientLight(0xaaaaaa, 0.35);
  scene.add(amb);
  const key = new THREE.PointLight(0xc5b8ff, 1.2, 80);
  key.position.set(5, 6, 4);
  scene.add(key);

  // ---------- Nebula planes (canvas textures) ----------
  // helper: create blurred radial gradient canvas texture
  function makeNebulaCanvas(w=1024,h=512, colorStops){
    const c = document.createElement('canvas');
    c.width = w; c.height = h;
    const ctx = c.getContext('2d');
    // clear
    ctx.clearRect(0,0,w,h);
    // draw multiple radial gradients
    colorStops.forEach(cs => {
      const grd = ctx.createRadialGradient(cs.x*w, cs.y*h, 0, cs.x*w, cs.y*h, Math.max(w,h)*cs.radius);
      grd.addColorStop(0, cs.colorInner);
      grd.addColorStop(0.25, cs.colorMid);
      grd.addColorStop(1, 'rgba(0,0,0,0)');
      ctx.globalCompositeOperation = 'lighter';
      ctx.fillStyle = grd;
      ctx.beginPath();
      ctx.rect(0,0,w,h);
      ctx.fill();
    });
    return c;
  }

  // default nebula color layers
  const defaultNebulaLayers = [
    [{ x:0.25,y:0.4, radius:0.9, colorInner:'rgba(150,120,255,0.9)', colorMid:'rgba(120,90,220,0.25)'},
     { x:0.7,y:0.5, radius:0.8, colorInner:'rgba(200,150,255,0.6)', colorMid:'rgba(120,80,220,0.15)'}],
    [{ x:0.5,y:0.3, radius:1.0, colorInner:'rgba(255,200,180,0.4)', colorMid:'rgba(200,140,255,0.08)'}]
  ];

  // create nebula planes and add to scene
  let nebulaPlanes = [];
  function createNebulaPlanes(layers=defaultNebulaLayers){
    // remove old
    nebulaPlanes.forEach(p=>{
      if(p.material.map) p.material.map.dispose();
      p.geometry.dispose();
      p.material.dispose();
      scene.remove(p);
    });
    nebulaPlanes = [];
    const depths = [-16, -14, -12];
    layers.forEach((layerSet, idx) => {
      // build canvas combining gradients
      const canvasTex = makeNebulaCanvas(2048,1024, layerSet);
      const tex = new THREE.CanvasTexture(canvasTex);
      tex.needsUpdate = true;
      const mat = new THREE.MeshBasicMaterial({ map: tex, transparent: true, opacity: 0.85, blending: THREE.AdditiveBlending, depthWrite:false });
      const geo = new THREE.PlaneGeometry(48, 24);
      const mesh = new THREE.Mesh(geo, mat);
      mesh.position.set(0, 0.5 - idx*0.15, depths[idx] || -10 - idx*2);
      mesh.rotation.y = 0.03 * (idx%2 ? 1 : -1);
      mesh.scale.set(1.3,1.3,1);
      scene.add(mesh);
      nebulaPlanes.push(mesh);
    });
  }

  createNebulaPlanes();

  // ---------- Star field (Points) ----------
  let stars;
  function createStars(count=2500, radius=80){
    if (stars) {
      stars.geometry.dispose();
      stars.material.dispose();
      scene.remove(stars);
      stars = null;
    }
    const positions = new Float32Array(count*3);
    for (let i=0;i<count;i++){
      const phi = Math.acos(2*Math.random()-1);
      const theta = 2*Math.PI*Math.random();
      const r = THREE.MathUtils.lerp(40, radius, Math.random());
      const x = r * Math.sin(phi) * Math.cos(theta);
      const y = r * Math.sin(phi) * Math.sin(theta);
      const z = r * Math.cos(phi);
      positions[i*3] = x;
      positions[i*3+1] = y;
      positions[i*3+2] = z;
    }
    const geo = new THREE.BufferGeometry();
    geo.setAttribute('position', new THREE.BufferAttribute(positions, 3));
    const mat = new THREE.PointsMaterial({ color: 0xffffff, size: 0.06, transparent:true, opacity:0.9, sizeAttenuation:true });
    stars = new THREE.Points(geo, mat);
    scene.add(stars);
  }
  createStars(2500, 90);

  // ---------- Soft glowing sphere (dynamic light) ----------
  const glowGeo = new THREE.SphereGeometry(1.2, 32, 32);
  const glowMat = new THREE.MeshStandardMaterial({ color: 0xcab8ff, emissive: 0x4b2bff, emissiveIntensity: 0.9, metalness: 0.1, roughness: 0.6 });
  const glowSphere = new THREE.Mesh(glowGeo, glowMat);
  glowSphere.position.set(-2.8, 1.6, -6);
  scene.add(glowSphere);

  // ---------- Camera & mouse parallax ----------
  const mouse = { x:0, y:0 };
  window.addEventListener('mousemove', (e)=>{
    mouse.x = (e.clientX / window.innerWidth) * 2 - 1;
    mouse.y = (e.clientY / window.innerHeight) * 2 - 1;
  });

  // ---------- Animation loop (optimized) ----------
  let last = performance.now();
  function animate(now){
    const dt = (now - last) * 0.001;
    last = now;
    // subtle rotations
    stars.rotation.y += 0.0006;
    glowSphere.rotation.y += 0.0009;
    nebulaPlanes.forEach((p, i)=> {
      p.rotation.z += 0.0004 * (i+1);
    });
    // camera parallax
    camera.position.x += (mouse.x * 0.8 - camera.position.x) * 0.06;
    camera.position.y += (-mouse.y * 0.5 - camera.position.y) * 0.06;
    camera.lookAt(0,0,0);
    renderer.render(scene, camera);
    requestAnimationFrame(animate);
  }
  requestAnimationFrame(animate);

  // ---------- UI & controls wiring ----------
  const btnGalaxy = document.getElementById('preset-galaxy');
  const btnMinimal = document.getElementById('preset-minimal');
  const qSlider = document.getElementById('bg-quality');
  const upload = document.getElementById('bg-upload');

  function setActive(btn){
    [btnGalaxy, btnMinimal].forEach(b=>b.classList.remove('active'));
    btn && btn.classList.add('active');
  }

  btnGalaxy.addEventListener('click', ()=>{
    setActive(btnGalaxy);
    // default rich galaxy
    createNebulaPlanes(defaultNebulaLayers);
    createStars(Math.round(2500 * parseFloat(qSlider.value)), 90);
    glowSphere.visible = true;
  });

  btnMinimal.addEventListener('click', ()=>{
    setActive(btnMinimal);
    // minimal: fewer stars, dim nebula
    createNebulaPlanes([[{x:0.5,y:0.45,radius:0.9,colorInner:'rgba(160,150,255,0.35)',colorMid:'rgba(100,90,200,0.06)'}]]);
    createStars(Math.round(700 * parseFloat(qSlider.value)), 60);
    glowSphere.visible = false;
  });

  qSlider.addEventListener('input', (e)=>{
    const q = parseFloat(e.target.value);
    const starCount = btnMinimal.classList.contains('active') ? Math.round(700*q) : Math.round(2500*q);
    createStars(starCount, 90);
    renderer.setPixelRatio(Math.min(window.devicePixelRatio || 1, 2) * q);
  });

  upload.addEventListener('change', (ev)=>{
    const f = ev.target.files && ev.target.files[0];
    if (!f) return;
    const url = URL.createObjectURL(f);
    // create texture and replace nebula planes with one plane using the image
    removeNebulaPlanesAndUseImage(url);
  });

  function removeNebulaPlanesAndUseImage(url){
    // remove existing planes
    nebulaPlanes.forEach(p=>{
      if(p.material.map) p.material.map.dispose();
      if(p.geometry) p.geometry.dispose();
      if(p.material) p.material.dispose();
      scene.remove(p);
    });
    nebulaPlanes = [];
    // create textured plane
    const loader = new THREE.TextureLoader();
    loader.load(url, tex=>{
      const geo = new THREE.PlaneGeometry(60, 34);
      const mat = new THREE.MeshBasicMaterial({ map: tex, transparent: true, opacity: 0.95, depthWrite:false });
      const plane = new THREE.Mesh(geo, mat);
      plane.position.set(0,0,-18);
      plane.rotation.y = 0.03;
      scene.add(plane);
      nebulaPlanes.push(plane);
    }, undefined, err=>{ console.warn('bg image load error', err); });
  }

  // helper to clean nebula previous resources (used by upload)
  function disposeNebula(){
    nebulaPlanes.forEach(p=>{
      if(p.material && p.material.map) p.material.map.dispose();
      if(p.material) p.material.dispose();
      if(p.geometry) p.geometry.dispose();
      scene.remove(p);
    });
    nebulaPlanes = [];
  }

  // Responsive
  window.addEventListener('resize', ()=>{
    renderer.setSize(window.innerWidth, window.innerHeight);
    camera.aspect = window.innerWidth / window.innerHeight;
    camera.updateProjectionMatrix();
  });

  // expose for debugging
  window._galaxyBg = { scene, camera, renderer, createNebulaPlanes, createStars, disposeNebula };

  // initial state
  setActive(btnGalaxy);
  // set quality initial based on slider
  qSlider.dispatchEvent(new Event('input'));
})();
</script>
<!-- ===== end Galaxy 3D Environment ===== -->

