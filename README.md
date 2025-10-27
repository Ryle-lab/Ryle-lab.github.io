
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Ryle L. De Hitta | Portfolio</title>
  <meta name="theme-color" content="#0b0f22" />
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&family=Space+Grotesk:wght@500;700&display=swap" rel="stylesheet">
  <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r150/three.min.js"></script>

  <style>
    *{margin:0;padding:0;box-sizing:border-box}
    body{
      overflow:hidden;
      background:#05070f;
      color:#fff;
      font-family:'Space Grotesk',sans-serif;
    }
    canvas#bg3d{
      position:fixed;top:0;left:0;width:100%;height:100%;z-index:-1;
    }
    nav{
      position:fixed;top:0;left:0;width:100%;
      display:flex;justify-content:space-between;align-items:center;
      padding:12px 28px;
      background:rgba(10,15,35,0.6);
      backdrop-filter:blur(12px);
      z-index:99;
    }
    /* Neon animated logo */
    .logo svg text{
      stroke:url(#grad);
      stroke-width:2;
      fill:transparent;
      stroke-dasharray:800;
      stroke-dashoffset:800;
      animation:drawText 3.6s ease forwards,glow 3s ease-in-out infinite 3.6s;
    }
    @keyframes drawText{
      to{stroke-dashoffset:0;fill:url(#grad);}
    }
    @keyframes glow{
      0%,100%{filter:drop-shadow(0 0 6px rgba(124,58,237,0.9));}
      50%{filter:drop-shadow(0 0 20px rgba(99,102,241,1));}
    }
    main{
      text-align:center;
      margin-top:180px;
      animation:fadeInUp 1s ease;
    }
    @keyframes fadeInUp{
      0%{opacity:0;transform:translateY(30px);}
      100%{opacity:1;transform:translateY(0);}
    }
    h1{font-size:3rem;margin-bottom:10px;}
    p{color:#a1a9c4;}
  </style>
</head>
<body>

<!-- 3D Background -->
<canvas id="bg3d"></canvas>

<!-- Navbar -->
<nav>
  <div class="logo">
    <svg width="240" height="60" viewBox="0 0 400 100" xmlns="http://www.w3.org/2000/svg">
      <defs>
        <linearGradient id="grad" x1="0%" y1="0%" x2="100%" y2="100%">
          <stop offset="0%" stop-color="#7c3aed"/>
          <stop offset="100%" stop-color="#4f46e5"/>
        </linearGradient>
      </defs>
      <text x="10" y="70" font-size="48" font-family="Space Grotesk, sans-serif">
        Ryle L. De Hitta
      </text>
    </svg>
  </div>
</nav>

<!-- Hero -->
<main>
  <h1>Welcome,<a href="Ryle_L_De_Hitta_Portfolio.html"> Enter?</a></h1>
  <p>Explore my projects, skills, and creative works.</p>
</main>

<!-- 3D Sci-Fi Grid Background -->
<script>
const scene=new THREE.Scene();
const camera=new THREE.PerspectiveCamera(75,innerWidth/innerHeight,0.1,1000);
const renderer=new THREE.WebGLRenderer({canvas:document.getElementById("bg3d"),antialias:true});
renderer.setSize(innerWidth,innerHeight);
camera.position.set(0,2,6);

// Grid floor
const grid=new THREE.GridHelper(40,40,0x4f46e5,0x1e1b4b);
grid.material.opacity=0.4;grid.material.transparent=true;
scene.add(grid);

// Floating orbs
const orbGeo=new THREE.SphereGeometry(0.12,16,16);
const orbMat=new THREE.MeshBasicMaterial({color:0x8b5cf6});
const orbs=[];
for(let i=0;i<12;i++){
  const orb=new THREE.Mesh(orbGeo,orbMat);
  orb.position.set((Math.random()-0.5)*10,Math.random()*4,(Math.random()-0.5)*10);
  scene.add(orb);orbs.push(orb);
}

// Lighting
const ambient=new THREE.AmbientLight(0x7c3aed,0.4);
const point=new THREE.PointLight(0x6366f1,1.4,20);
point.position.set(0,4,0);
scene.add(ambient,point);

// Mouse movement parallax
document.addEventListener('mousemove',e=>{
  const x=(e.clientX/innerWidth-0.5)*2;
  const y=(e.clientY/innerHeight-0.5)*2;
  camera.position.x=x*2;
  camera.position.y=2-y;
});

// Animate
function animate(){
  requestAnimationFrame(animate);
  grid.rotation.y+=0.001;
  orbs.forEach((o,i)=>{
    o.position.y=Math.sin(Date.now()*0.001+i)*1.5+2;
    o.rotation.y+=0.02;
  });
  renderer.render(scene,camera);
}
animate();

// Resize
addEventListener('resize',()=>{
  camera.aspect=innerWidth/innerHeight;
  camera.updateProjectionMatrix();
  renderer.setSize(innerWidth,innerHeight);
});
</script>

<!-- Self-contained PWA (Service Worker inline) -->
<script>
if('serviceWorker' in navigator){
  const swCode=`
    const CACHE='ryle-portfolio-v3';
    const FILES=['./'];
    self.addEventListener('install',e=>{
      e.waitUntil(caches.open(CACHE).then(c=>c.addAll(FILES)));
    });
    self.addEventListener('fetch',e=>{
      e.respondWith(caches.match(e.request).then(r=>r||fetch(e.request)));
    });
    self.addEventListener('activate',e=>{
      e.waitUntil(caches.keys().then(k=>Promise.all(k.map(n=>n!==CACHE&&caches.delete(n)))));
    });
  `;
  const blob=new Blob([swCode],{type:'application/javascript'});
  const swURL=URL.createObjectURL(blob);
  navigator.serviceWorker.register(swURL).then(()=>console.log('✅ Offline Ready')).catch(console.error);
}
</script>

</body>
</html>
