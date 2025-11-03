<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Portfolio — Clone inspirado</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;800&display=swap" rel="stylesheet">
  <style>
    :root{
      --bg1:#0f1720;
      --bg2:#071026;
      --accent:#66b2ff;
      --white:#ffffff;
      --glass: rgba(255,255,255,0.04);
    }
    *{box-sizing:border-box}
    html,body{height:100%;margin:0;font-family:'Inter',system-ui,Segoe UI,Arial;}

    /* animated gradient background */
    .bg {
      position:fixed;inset:0;z-index:-2;overflow:hidden;
      background: radial-gradient(600px 400px at 10% 10%, rgba(102,178,255,0.06), transparent 10%),
                  radial-gradient(500px 350px at 90% 80%, rgba(255,255,255,0.03), transparent 10%),
                  linear-gradient(120deg,var(--bg1),var(--bg2));
      animation: bgShift 12s linear infinite;
    }
    @keyframes bgShift{
      0%{background-position:0% 0%,0% 0%,0% 0%}
      50%{background-position:10% 20%,20% 40%,100% 100%}
      100%{background-position:0% 0%,0% 0%,0% 0%}
    }

    /* subtle moving lines */
    .grid-lines{position:fixed;inset:0;opacity:0.06;z-index:-1;background-image:linear-gradient(transparent 24px, rgba(255,255,255,0.02) 25px),linear-gradient(90deg, transparent 24px, rgba(255,255,255,0.02) 25px);background-size:100% 25px,25px 100%;animation: linesMove 40s linear infinite}
    @keyframes linesMove{from{background-position:0 0,0 0}to{background-position:400px 0,0 400px}}

    .wrap{min-height:100vh;display:flex;align-items:center;justify-content:center;padding:48px}
    .card{width:100%;max-width:980px;padding:40px;border-radius:14px;background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));box-shadow:0 8px 30px rgba(2,6,23,0.6);backdrop-filter: blur(6px);border:1px solid rgba(255,255,255,0.04)}

    .top{display:flex;gap:28px;align-items:center}
    .avatar{flex:0 0 120px;height:120px;border-radius:14px;background:linear-gradient(135deg,var(--accent),#9de1ff);box-shadow:0 6px 30px rgba(102,178,255,0.12);display:flex;align-items:center;justify-content:center;color:var(--white);font-weight:800;font-size:28px}

    .intro{flex:1}
    .name{font-weight:800;font-size:28px;color:var(--white);margin:0 0 8px}
    .typewriter{font-family:monospace;color:var(--white);font-size:18px;white-space:nowrap;overflow:hidden;border-right:3px solid rgba(255,255,255,0.12);width:100%;max-width:720px}

    /* typewriter effect (JS-driven for better control) */
    .blinking-cursor{display:inline-block;width:10px;margin-left:6px;animation: blink 1s steps(2) infinite}
    @keyframes blink{50%{opacity:0}}

    /* action buttons */
    .actions{margin-top:18px;display:flex;gap:12px}
    .btn{padding:10px 16px;border-radius:10px;border:1px solid rgba(102,178,255,0.12);background:transparent;color:var(--white);cursor:pointer;font-weight:600}
    .btn.primary{background:linear-gradient(90deg, rgba(102,178,255,0.12), rgba(102,178,255,0.06));box-shadow:0 6px 24px rgba(102,178,255,0.06)}

    /* skills area */
    .skills{margin-top:28px}
    .skill{margin-bottom:14px}
    .skill .label{display:flex;justify-content:space-between;font-size:13px;color:rgba(255,255,255,0.7);margin-bottom:6px}
    .bar{height:12px;background:rgba(255,255,255,0.06);border-radius:999px;overflow:hidden}
    .bar .fill{height:100%;width:0%;border-radius:999px;background:linear-gradient(90deg,var(--accent),#cfeeff);box-shadow:0 8px 20px rgba(102,178,255,0.12);transition:width 1.2s cubic-bezier(.2,.9,.2,1)}

    /* glow headings */
    h2{color:var(--white);text-shadow:0 6px 30px rgba(102,178,255,0.06);}

    /* responsive tweaks */
    @media (max-width:720px){
      .card{padding:20px}
      .avatar{flex-basis:80px;height:80px;font-size:20px}
      .name{font-size:20px}
      .typewriter{font-size:15px}
    }
  </style>
</head>
<body>
  <div class="bg"></div>
  <div class="grid-lines"></div>

  <div class="wrap">
    <div class="card">
      <div class="top">
        <div class="avatar">NC</div>
        <div class="intro">
          <p class="name">Nahuel Cappa</p>
          <div class="typewriter" id="typewriter"></div>
          <div class="actions">
            <button class="btn primary" id="btn-portfolio">Ver portfolio</button>
            <button class="btn" id="btn-contact">Contactar</button>
          </div>

          <div class="skills" id="skills">
            <h2>Conocimientos</h2>
            <div class="skill">
              <div class="label"><span>Flutter</span><span>90%</span></div>
              <div class="bar"><div class="fill" data-fill="90%"></div></div>
            </div>
            <div class="skill">
              <div class="label"><span>Dart</span><span>85%</span></div>
              <div class="bar"><div class="fill" data-fill="85%"></div></div>
            </div>
            <div class="skill">
              <div class="label"><span>HTML/CSS</span><span>80%</span></div>
              <div class="bar"><div class="fill" data-fill="80%"></div></div>
            </div>
            <div class="skill">
              <div class="label"><span>JavaScript</span><span>70%</span></div>
              <div class="bar"><div class="fill" data-fill="70%"></div></div>
            </div>
          </div>

        </div>
      </div>
    </div>
  </div>

  <script>
    // Typewriter text frames (you can edit these)
    const lines = [
      'Desarrollador Flutter · UI/UX · Apps y Web',
      'Creo interfaces limpias y performantes',
      'Open to collaborate — GitHub & Freelance'
    ];

    const el = document.getElementById('typewriter');
    let line = 0, pos = 0, adding = true, pause = 0;

    function tick(){
      if(pause>0){ pause--; setTimeout(tick,60); return; }
      const current = lines[line];
      if(adding){
        pos++;
        el.textContent = current.slice(0,pos);
        if(pos===current.length){ adding=false; pause=30; }
      } else {
        pos--;
        el.textContent = current.slice(0,pos);
        if(pos===0){ adding=true; line=(line+1)%lines.length; }
      }
      // keep cursor
      if(!document.getElementById('cursor')){
        const c = document.createElement('span'); c.id='cursor'; c.className='blinking-cursor'; c.textContent='▌'; el.appendChild(c);
      }
      setTimeout(tick,40);
    }
    tick();

    // animate skill bars when visible
    function animateSkills(){
      document.querySelectorAll('.fill').forEach(el=>{
        const val = el.getAttribute('data-fill')||'0%';
        el.style.width = val;
      });
    }

    // intersection observer to trigger once
    const obs = new IntersectionObserver((entries, o)=>{
      entries.forEach(e=>{ if(e.isIntersecting) { animateSkills(); o.disconnect(); } });
    },{threshold:0.4});
    obs.observe(document.getElementById('skills'));

    // Buttons (example behavior)
    document.getElementById('btn-portfolio').addEventListener('click', ()=>{
      window.open('https://github.com/','_blank');
    });
    document.getElementById('btn-contact').addEventListener('click', ()=>{
      window.open('mailto:nahuel@example.com');
    });
  </script>
</body>
</html>
