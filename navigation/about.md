---
layout: post
title: About
permalink: /about/
comments: true
---

<div id="about-beach">

  <!-- LAYERED BACKGROUND: sky, sun, water, shoreline, sand -->
  <div class="sky" aria-hidden="true"></div>
  <div class="sun" aria-hidden="true"></div>

  <!-- Ocean band behind content -->
  <div class="ocean" aria-hidden="true">
    <div class="ocean-fill"></div>
    <!-- two moving wave crests for parallax feel -->
    <div class="wave wave-a"></div>
    <div class="wave wave-b"></div>
  </div>

  <!-- Shoreline foam band -->
  <div class="shoreline" aria-hidden="true"></div>

  <!-- Sand band at the very back with moving grain pattern -->
  <div class="sand" aria-hidden="true">
    <!-- crabs -->
    <div class="crab c1"></div>
    <div class="crab c2"></div>
    <div class="crab c3"></div>
  </div>

  <!-- Parallax overlays (inline SVG data URIs) -->
  <div class="parallax" aria-hidden="true">
    <div class="layer clouds"></div>
    <div class="layer gulls"></div>
    <div class="layer palms palm-left"></div>
    <div class="layer palms palm-right"></div>
  </div>

  <div class="wrap">
    <h2 class="reveal">As a conversation Starter</h2>
    <p class="reveal card">Here are some places I am from. Flags are fetched from Wikipedia Commons.</p>

    <!-- Flag Grid -->
    <div class="reveal">
      <div class="grid-container" id="grid_container"></div>
    </div>

    <!-- Waves Divider -->
    <div class="waves reveal" aria-hidden="true">
      <svg class="w1" viewBox="0 0 1200 300" preserveAspectRatio="none">
        <path d="M0,240 C150,220 300,260 450,240 C600,220 750,180 900,200 C1050,220 1200,210 1200,210 L1200,300 L0,300 Z" fill="#9bd8ff"></path>
      </svg>
      <svg class="w2" viewBox="0 0 1200 300" preserveAspectRatio="none">
        <path d="M0,250 C200,230 300,270 520,250 C680,235 780,190 980,210 C1120,225 1200,220 1200,220 L1200,300 L0,300 Z" fill="#57c5ff"></path>
      </svg>
    </div>

    <!-- Pinned Plane -->
    <section class="plane-stage reveal">
      <div class="plane-pin">
        <img id="plane-img" src="{{site.baseurl}}/images/about/download.png" alt="Plane" class="float">
      </div>
    </section>

    <!-- Journey -->
    <section class="section reveal card">
      <h3>Journey through Life</h3>
      <ul>
        <li>🏫 D39 elementary (San Diego, CA)</li>
        <li>🏫 Current senior, Class of 2026</li>
        <li>🎾 Varsity tennis & mentor</li>
        <li>🤖 Robotics — sensor coding lead</li>
        <li>🗝️ Key Club — community hours</li>
        <li>📚 Homework explainer before tests</li>
        <li>📖 Library lunches to finish work</li>
        <li>🎮 Mario Kart with a tight crew</li>
      </ul>
      <div class="chips">
        <span class="chip">Curious</span><span class="chip">Builder</span>
        <span class="chip">Team-first</span><span class="chip">Calm</span>
      </div>
    </section>

    <!-- Culture -->
    <section class="section reveal card">
      <h3>Culture, Family, and Fun</h3>
      <p>Everything for me, as for many others, revolves around family and goals.</p>
      <ul>
        <li>Born in Escondido (<a href="https://ucsd.edu/" target="_blank" rel="noopener">hospital</a>)</li>
        <li>Family of four — two parents &amp; one brother</li>
        <li>Gallery below holds snapshots of culture, fun, and memories</li>
      </ul>
    </section>

    <!-- Gallery -->
    <section class="section reveal">
      <div class="image-gallery">
        <img src="{{site.baseurl}}/images/dog.png" alt="Dog" class="float">
        <img src="{{site.baseurl}}/images/about/earings.png" alt="Earings" class="float">
        <img src="{{site.baseurl}}/images/about/grapes.png" alt="Grapes" class="float">
        <img src="{{site.baseurl}}/images/about/griaffe.png" alt="Giraffe" class="float">
        <img src="{{site.baseurl}}/images/about/parrot.png" alt="Parrot" class="float">
        <img src="{{site.baseurl}}/images/about/lora_fam.jpg" alt="Family 1" class="float">
        <img src="{{site.baseurl}}/images/about/lora_fam2.jpg" alt="Family 2" class="float">
        <img src="{{site.baseurl}}/images/about/pj_party.jpg" alt="Party" class="float">
        <img src="{{site.baseurl}}/images/about/trent_family.png" alt="Family 3" class="float">
        <img src="{{site.baseurl}}/images/about/claire.jpg" alt="Claire" class="float">
        <img src="{{site.baseurl}}/images/about/grandkids.jpg" alt="Grandkids" class="float">
        <img src="{{site.baseurl}}/images/about/farm.jpg" alt="Farm" class="float">
      </div>
    </section>
  </div>
</div>

<style>
  /* THEME VARS + SCOPE */
  #about-beach {
    --sky1:#7fd4ff; --sky2:#ffd3a0; --sky3:#ffafbd; --sun:#ffd66b;
    --water1:#66c9ff; --water2:#43b5ff; --foam:#ffffff;
    --sand:#f4e3b4; --sand-dots:#d5bf8a;
    --text:#0f223d; --card:rgba(255,255,255,.88); --shadow:0 10px 30px rgba(0,0,0,.15);
    color:var(--text);
    font-family: ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, Arial;
    position: relative;
  }
  #about-beach .wrap{ max-width:1100px; margin:0 auto; padding:8rem 1.2rem 4rem; }
  #about-beach .card{ background:var(--card); border-radius:18px; box-shadow:var(--shadow); padding:1.1rem; backdrop-filter: blur(6px); }
  #about-beach .reveal{ opacity:0; transform:translateY(18px) scale(.98); transition:opacity .7s ease, transform .7s ease; }
  #about-beach .reveal.in{ opacity:1; transform:none; }
  #about-beach .float{ animation: floatY 6s ease-in-out infinite; }
  @keyframes floatY{ 50%{ transform: translateY(-6px); } }

  /* SKY + SUN (animated gradient) */
  #about-beach .sky{ position:fixed; inset:0; z-index:-5; background:linear-gradient(180deg,var(--sky1),var(--sky2),var(--sky3)); background-size:100% 200%; animation: skyShift 16s ease-in-out infinite alternate; }
  @keyframes skyShift{ to{ background-position:0 100%; } }
  #about-beach .sun{ position:fixed; top:7vh; left:50%; width:22vmin; aspect-ratio:1/1; transform:translateX(-50%); border-radius:50%; background: radial-gradient(circle at 50% 50%, var(--sun), rgba(255,214,107,0) 60%); filter: blur(8px); z-index:-4; }

  /* OCEAN BAND (moves horizontally) */
  #about-beach .ocean{ position:fixed; left:0; right:0; top:35vh; height:38vh; z-index:-3; overflow:hidden; }
  #about-beach .ocean-fill{
    position:absolute; inset:0;
    background: linear-gradient(180deg, var(--water1) 0%, var(--water2) 60%, #2fa6f9 100%);
    transform: translateZ(0);
  }
  #about-beach .wave{
    position:absolute; left:-50%; width:200%; height:120%;
    bottom:-4vh; opacity:.75; background-repeat: repeat-x; background-size: 1200px 160px;
    animation: waveSlide 12s linear infinite;
  }
  #about-beach .wave-a{ background-image:url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="1200" height="160"><path d="M0 80 C60 40 120 120 180 80 C240 40 300 120 360 80 C420 40 480 120 540 80 C600 40 660 120 720 80 C780 40 840 120 900 80 C960 40 1020 120 1080 80 C1140 40 1200 120 1260 80 L1260 160 L0 160 Z" fill="%23ffffff" opacity="0.7"/></svg>'); }
  #about-beach .wave-b{ bottom:-2vh; opacity:.5; animation-duration: 18s; background-image:url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="1200" height="160"><path d="M0 90 C70 50 140 130 210 90 C280 50 350 130 420 90 C490 50 560 130 630 90 C700 50 770 130 840 90 C910 50 980 130 1050 90 C1120 50 1190 130 1260 90 L1260 160 L0 160 Z" fill="%23ffffff" opacity="0.5"/></svg>'); }
  @keyframes waveSlide{ to{ transform: translateX(-50%); } }

  /* SHORELINE FOAM (moves slowly) */
  #about-beach .shoreline{
    position:fixed; left:0; right:0; top:72vh; height:4vh; z-index:-2;
    background: radial-gradient(ellipse at 50% 0%, var(--foam) 0%, rgba(255,255,255,.6) 60%, rgba(255,255,255,0) 80%);
    filter: blur(2px);
    animation: foamPulse 5s ease-in-out infinite alternate;
  }
  @keyframes foamPulse{ to{ transform: translateY(.4vh); opacity:.95; } }

  /* SAND (with drifting grain texture) */
  #about-beach .sand{
    position:fixed; left:0; right:0; bottom:0; height:28vh; z-index:-1;
    background: var(--sand);
    overflow:hidden;
  }
  #about-beach .sand::before{
    content:""; position:absolute; inset:-20% -20% 0 -20%;
    background-image:
      radial-gradient(2px 2px at 20% 30%, var(--sand-dots) 30%, transparent 31%),
      radial-gradient(2px 2px at 70% 60%, var(--sand-dots) 30%, transparent 31%),
      radial-gradient(2px 2px at 40% 80%, var(--sand-dots) 30%, transparent 31%),
      radial-gradient(2px 2px at 85% 20%, var(--sand-dots) 30%, transparent 31%);
    background-size: 320px 220px;
    opacity:.5;
    animation: sandDrift 22s linear infinite;
  }
  @keyframes sandDrift{ to{ transform: translateX(-20%); } }

  /* CRABS (CSS + inline SVG) */
  #about-beach .crab{
    position:absolute; bottom: 6vh; width: 48px; height: 32px;
    background-repeat:no-repeat; background-size: contain;
    background-image: url('data:image/svg+xml;utf8, \
      <svg xmlns="http://www.w3.org/2000/svg" width="96" height="64" viewBox="0 0 96 64"> \
        <ellipse cx="48" cy="40" rx="22" ry="14" fill="%23e5553f"/> \
        <circle cx="38" cy="28" r="5" fill="%23e5553f"/> \
        <circle cx="58" cy="28" r="5" fill="%23e5553f"/> \
        <circle cx="38" cy="26" r="2" fill="%230f223d"/> \
        <circle cx="58" cy="26" r="2" fill="%230f223d"/> \
        <path d="M28 40 q-10 -8 0 -16" stroke="%23e5553f" stroke-width="4" fill="none" stroke-linecap="round"/> \
        <path d="M68 40 q10 -8 0 -16" stroke="%23e5553f" stroke-width="4" fill="none" stroke-linecap="round"/> \
        <g stroke="%230f223d" stroke-linecap="round"> \
          <path d="M40 52 l-6 8"/><path d="M46 52 l-2 10"/><path d="M52 52 l2 10"/><path d="M58 52 l6 8"/> \
        </g> \
      </svg>');
    animation: crabWalk 14s linear infinite, crabBob 1.8s ease-in-out infinite;
    will-change: transform;
  }
  #about-beach .crab.c1{ left: -60px; animation-duration: 18s, 1.8s; animation-delay: 0s, 0s; }
  #about-beach .crab.c2{ left: -60px; bottom: 8vh; animation-duration: 22s, 2.1s; animation-delay: 4s, .2s; transform: scale(.9); opacity:.9; }
  #about-beach .crab.c3{ left: -60px; bottom: 5vh; animation-duration: 26s, 1.9s; animation-delay: 8s, .1s; transform: scale(.8); opacity:.8; }
  @keyframes crabWalk{ to{ transform: translateX(calc(100vw + 120px)); } }
  @keyframes crabBob{ 50%{ transform: translateY(-2px); } }

  /* PARALLAX ART */
  #about-beach .parallax{ position:fixed; inset:0; pointer-events:none; z-index:-1; }
  #about-beach .layer{ position:absolute; inset:0; background-repeat:no-repeat; background-size: contain; }
  #about-beach .clouds{
    opacity:.6; background-position: 10% 12%, 75% 18%;
    background-image:
      url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="360" height="140"><g fill="%23fff" opacity=".9"><ellipse cx="80" cy="70" rx="70" ry="40"/><ellipse cx="140" cy="65" rx="60" ry="35"/><ellipse cx="200" cy="75" rx="70" ry="40"/></g></svg>'),
      url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="280" height="120"><g fill="%23fff" opacity=".85"><ellipse cx="60" cy="60" rx="55" ry="30"/><ellipse cx="120" cy="55" rx="50" ry="28"/><ellipse cx="180" cy="65" rx="55" ry="30"/></g></svg>');
  }
  #about-beach .gulls{
    opacity:.7; background-position: 25% 28%, 82% 32%;
    background-image:
      url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="160" height="80"><path d="M5 40 Q30 10 55 40 M55 40 Q80 10 105 40" stroke="%230f223d" stroke-width="3" fill="none" stroke-linecap="round"/></svg>'),
      url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="160" height="80"><path d="M10 50 Q35 20 60 50 M60 50 Q85 20 110 50" stroke="%230f223d" stroke-width="3" fill="none" stroke-linecap="round"/></svg>');
  }
  #about-beach .palms{
    background-size: 28vmin auto;
    transform-origin: bottom center;
    animation: palmSway 5.5s ease-in-out infinite alternate;
    opacity:.9;
  }
  #about-beach .palm-left{
    background-position: 2% 100%;
    background-image:url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 140 220"><path d="M70 220 L70 120" stroke="%230f223d" stroke-width="10"/><path d="M70 120 C25 105 15 90 10 80 C45 85 60 92 70 100 C80 90 95 85 130 80 C120 92 110 110 70 120Z" fill="%230f223d"/></svg>');
  }
  #about-beach .palm-right{
    background-position: 98% 100%;
    background-image:url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 140 220"><path d="M70 220 L70 120" stroke="%230f223d" stroke-width="10"/><path d="M70 120 C25 105 15 90 10 80 C45 85 60 92 70 100 C80 90 95 85 130 80 C120 92 110 110 70 120Z" fill="%230f223d"/></svg>');
  }
  @keyframes palmSway{ to{ transform: rotate(2.4deg); } }

  /* Waves divider + Gallery (kept from previous) */
  #about-beach .waves{ position:relative; height:24vh; margin:8rem 0 2rem; overflow:hidden; border-radius:16px; box-shadow:var(--shadow); }
  #about-beach .waves svg{ position:absolute; left:0; right:0; bottom:-1px; width:200%; height:140%; }
  #about-beach .waves .w1{ animation: waveSlide 10s linear infinite; }
  #about-beach .waves .w2{ animation: waveSlide 14s linear infinite; opacity:.5; }

  #about-beach .grid-container{ display:grid; grid-template-columns: repeat(auto-fill, minmax(160px,1fr)); gap:14px; margin-top:1rem; }
  #about-beach .grid-item{ text-align:center; background:#ffffffd9; border-radius:14px; padding:.8rem; box-shadow:var(--shadow); }
  #about-beach .grid-item img{ width:100%; height:100px; object-fit:contain; filter: drop-shadow(0 2px 4px rgba(0,0,0,.15)); }
  #about-beach .grid-item p{ margin:.35rem 0; }

  #about-beach .image-gallery{ display:flex; gap:12px; overflow-x:auto; padding-bottom:8px; }
  #about-beach .image-gallery img{ max-height:170px; object-fit:cover; border-radius:12px; box-shadow:var(--shadow); transition:transform .25s ease; }
  #about-beach .image-gallery img:hover{ transform: translateY(-4px) scale(1.02); }

  /* Plane */
  #about-beach .plane-stage{ height:230vh; }
  #about-beach .plane-pin{ position:sticky; top:0; height:100vh; overflow:hidden; z-index:3; }
  #about-beach #plane-img{ position:absolute; left:0; top:0; width:130px; height:auto; pointer-events:none; filter: drop-shadow(0 4px 6px rgba(0,0,0,.25)); }

  /* Accessibility */
  @media (prefers-reduced-motion: reduce){
    #about-beach *{ animation:none !important; transition:none !important; }
  }
</style>

<script>
  // Build flags
  (function(){
    var container = document.querySelector("#about-beach #grid_container");
    if(!container) return;
    var http = "https://upload.wikimedia.org/wikipedia/commons/";
    var flags = [
      {"flag":"0/01/Flag_of_California.svg","greeting":"Hey","description":"California - since birth"},
      {"flag":"2/21/Flag_of_Vietnam.svg","greeting":"CHÀO","description":"ethnic background"},
      {"flag":"c/c3/Flag_of_France.svg","greeting":"Salut","description":"ethnic background"},
      {"flag":"9/9f/Flag_of_Indonesia.svg","greeting":"Hai","description":"ethnic background"},
    ];
    for (const f of flags){
      var item = document.createElement("div"); item.className="grid-item reveal";
      var img = document.createElement("img"); img.src = http + f.flag; img.alt = f.flag + " Flag";
      var d = document.createElement("p"); d.textContent = f.description;
      var g = document.createElement("p"); g.textContent = f.greeting;
      item.appendChild(img); item.appendChild(d); item.appendChild(g); container.appendChild(item);
    }
  })();

  // Plane scroll — robust version (works with fast scroll & short pages)
  (function(){
    var plane = document.querySelector("#about-beach #plane-img");
    var stage = document.querySelector("#about-beach .plane-stage");
    if(!plane || !stage) return;

    var ticking = false;
    var clamp = (v,lo,hi)=>Math.max(lo,Math.min(hi,v));

    function compute(){
      var rect = stage.getBoundingClientRect();
      var vh = window.innerHeight || document.documentElement.clientHeight;
      var scrollable = Math.max(1, stage.offsetHeight - vh);
      var p = clamp((-rect.top)/scrollable, 0, 1);

      // nice arc with slight bob + bank
      var x = 2 + 96*p;
      var y = 22 + (-9*Math.sin(p*Math.PI));
      var rot = -8 + 16*p;

      plane.style.transform = 'translate3d('+x+'vw,'+y+'vh,0) rotate('+rot+'deg)';
      ticking = false;
    }

    function request(){
      if(!ticking){ ticking = true; requestAnimationFrame(compute); }
    }

    // Update on load/scroll/resize
    addEventListener('scroll', request, {passive:true});
    addEventListener('resize', request);
    addEventListener('load', request);
    // If the stage enters/exits viewport, recompute
    if ('IntersectionObserver' in window){
      var io = new IntersectionObserver(()=>request());
      io.observe(stage);
    }
    request();
  })();

  // Parallax drift + Scroll reveal
  (function(){
    var root = document.getElementById('about-beach');
    if(!root) return;
    var clouds = root.querySelector('.clouds');
    var gulls  = root.querySelector('.gulls');
    var palmL  = root.querySelector('.palm-left');
    var palmR  = root.querySelector('.palm-right');

    var raf;
    function parallax(){
      var y = window.scrollY || window.pageYOffset;
      if (clouds) clouds.style.transform = 'translateY('+(y*0.12)+'px)';
      if (gulls)  gulls.style.transform  = 'translateY('+(y*0.18)+'px)';
      if (palmL)  palmL.style.transform  = 'translateY('+(y*0.28)+'px) rotate(2deg)';
      if (palmR)  palmR.style.transform  = 'translateY('+(y*0.28)+'px) rotate(-2deg)';
      raf = requestAnimationFrame(parallax);
    }
    raf = requestAnimationFrame(parallax);

    var io = new IntersectionObserver((entries)=>{
      entries.forEach(e=>{
        if(e.isIntersecting){ e.target.classList.add('in'); io.unobserve(e.target); }
      });
    },{ threshold:0.12, rootMargin:'0px 0px -5% 0px' });
    root.querySelectorAll('.reveal').forEach(el=> io.observe(el));

    if (matchMedia('(prefers-reduced-motion: reduce)').matches) {
      cancelAnimationFrame(raf);
      [clouds,gulls,palmL,palmR].forEach(el=>{ if(el) el.style.transform=''; });
      root.querySelectorAll('.reveal').forEach(el=> el.classList.add('in'));
    }
  })();
</script>
