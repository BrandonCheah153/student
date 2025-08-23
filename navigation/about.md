---
layout: post
title: About
permalink: /about/
comments: true
---

<!-- =========================
     BEACH THEME BACKDROP
========================== -->
<style>
  :root{
    --sky-1:#7fd4ff;
    --sky-2:#ffd3a0;
    --sky-3:#ffafbd;
    --sun:#ffd66b;
    --sand:#f6e0b5;
    --text:#0f223d;
    --card-bg:rgba(255,255,255,0.85);
    --accent:#2fb3ff;
    --shadow:0 10px 30px rgba(0,0,0,.15);
  }
  html,body{
    margin:0; padding:0;
    color:var(--text);
    font-family: ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, "Helvetica Neue", Arial, "Apple Color Emoji","Segoe UI Emoji";
    scroll-behavior:smooth;
    background: linear-gradient(180deg,var(--sand) 0%, #fff 100%);
  }

  /* Animated sky with sun glow */
  .sky {
    position: fixed;
    inset: 0;
    z-index: -3;
    background: linear-gradient(180deg, var(--sky-1), var(--sky-2), var(--sky-3));
    background-size: 100% 200%;
    animation: skyShift 18s ease-in-out infinite alternate;
  }
  @keyframes skyShift {
    0% { background-position: 0% 0%; }
    100% { background-position: 0% 100%; }
  }
  .sun {
    position: fixed;
    top: 8vh; left: 50%;
    width: 20vmin; aspect-ratio: 1/1;
    transform: translateX(-50%);
    border-radius: 50%;
    background: radial-gradient(circle at 50% 50%, var(--sun), rgba(255,214,107,0.0) 60%);
    filter: blur(8px) saturate(110%);
    z-index:-2;
  }

  /* Parallax layers */
  .parallax {
    position: fixed; inset:0; pointer-events:none; z-index:-1;
  }
  .layer {
    position: absolute; inset:0;
    background-repeat: no-repeat;
    background-size: contain;
    opacity:.8;
  }
  /* Clouds (far) */
  .layer.clouds {
    background-image:
      url("{{site.baseurl}}/images/about/cloud-1.svg"),
      url("{{site.baseurl}}/images/about/cloud-2.svg");
    background-position: 10% 12%, 75% 18%;
    opacity:.6;
  }
  /* Gulls (mid) */
  .layer.gulls {
    background-image:
      url("{{site.baseurl}}/images/about/gulls-1.svg"),
      url("{{site.baseurl}}/images/about/gulls-2.svg");
    background-position: 25% 28%, 82% 32%;
    opacity:.7;
  }
  /* Palms (near) */
  .layer.palms {
    background-image:
      url("{{site.baseurl}}/images/about/palm-left.svg"),
      url("{{site.baseurl}}/images/about/palm-right.svg");
    background-position: left bottom, right bottom;
    background-size: 25vmin auto, 28vmin auto;
    opacity:.9;
  }

  /* Global content layout */
  .wrap {
    max-width: 1100px;
    margin: 0 auto;
    padding: 8rem 1.2rem 4rem 1.2rem;
  }

  /* Section headings */
  h2, h3 {
    letter-spacing: .3px;
    text-shadow: 0 1px 0 rgba(255,255,255,.4);
  }

  /* Reusable card */
  .card {
    background: var(--card-bg);
    border-radius: 18px;
    box-shadow: var(--shadow);
    padding: 1.2rem 1.1rem;
    backdrop-filter: blur(6px);
  }

  /* Scroll reveal */
  .reveal {
    opacity:0; transform: translateY(18px) scale(.98);
    transition: opacity .7s ease, transform .7s ease;
  }
  .reveal.in {
    opacity:1; transform: translateY(0) scale(1);
  }

  /* Floating gentle animation for images/icons */
  .float {
    animation: floatY 6s ease-in-out infinite;
  }
  @keyframes floatY {
    0%,100% { transform: translateY(0); }
    50% { transform: translateY(-6px); }
  }

  /* --- Your Flag Grid --- */
  .grid-container {
    display:grid;
    grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
    gap: 14px;
    margin-top: 1rem;
  }
  .grid-item{
    text-align:center;
    background: rgba(255,255,255,.85);
    border-radius: 14px;
    padding:.8rem;
    box-shadow: var(--shadow);
  }
  .grid-item img{
    width:100%; height:100px; object-fit:contain;
    filter: drop-shadow(0 2px 4px rgba(0,0,0,.15));
  }
  .grid-item p{ margin:.35rem 0; }

  /* --- Wave section --- */
  .waves {
    position: relative;
    height: 24vh;
    margin: 8rem 0 2rem 0;
    overflow: hidden;
    border-radius: 16px;
    box-shadow: var(--shadow);
  }
  .waves svg {
    position: absolute; left:0; right:0; bottom:-1px;
    width: 200%; height: 140%;
    animation: waveSlide 10s linear infinite;
  }
  .waves svg.second { animation-duration: 14s; opacity:.5; }
  @keyframes waveSlide{
    0% { transform: translateX(0); }
    100% { transform: translateX(-50%); }
  }

  /* --- Image gallery --- */
  .image-gallery {
    display:flex; flex-wrap:nowrap; overflow-x:auto; gap:12px; padding-bottom: 8px;
  }
  .image-gallery img{
    max-height: 170px; object-fit:cover; border-radius:12px;
    box-shadow: var(--shadow);
    transition: transform .25s ease;
  }
  .image-gallery img:hover{ transform: translateY(-4px) scale(1.02); }

  /* --- Plane stage (kept from your code) --- */
  .plane-stage { height: 220vh; }
  .plane-pin {
    position: sticky; top:0; height: 100vh; overflow:hidden; background:transparent; z-index:2;
  }
  #plane-img {
    position:absolute; left:0; top:0; width: 130px; height:auto; pointer-events:none;
    filter: drop-shadow(0 4px 6px rgba(0,0,0,0.25));
    z-index:3;
  }

  /* Content sections */
  .section { margin: 3rem 0 2rem 0; }
  .chips { display:flex; gap:8px; flex-wrap:wrap; }
  .chip {
    padding:.45rem .7rem; background: #ffffffc7; border-radius: 999px; box-shadow: var(--shadow); font-size:.92rem;
  }

  /* Accessibility: reduce motion */
  @media (prefers-reduced-motion: reduce){
    *{ animation: none !important; transition: none !important; }
    .waves svg { transform: translateX(0) !important; }
  }
</style>

<div class="sky"></div>
<div class="sun"></div>
<div class="parallax">
  <div class="layer clouds"></div>
  <div class="layer gulls"></div>
  <div class="layer palms"></div>
</div>

<div class="wrap">

  <h2 class="reveal">As a conversation Starter</h2>
  <p class="reveal card">Here are some places I am from. Flags are fetched from Wikipedia Commons.</p>

  <!-- ======= Flag Grid ======= -->
  <div class="reveal">
    <div class="grid-container" id="grid_container"></div>
  </div>

  <!-- ======= Waves Divider ======= -->
  <div class="waves reveal" aria-hidden="true">
    <!-- simple duotone waves; duplicate for parallax feel -->
    <svg class="first" viewBox="0 0 1200 300" preserveAspectRatio="none">
      <path d="M0,240 C150,220 300,260 450,240 C600,220 750,180 900,200 C1050,220 1200,210 1200,210 L1200,300 L0,300 Z" fill="#9bd8ff"></path>
    </svg>
    <svg class="second" viewBox="0 0 1200 300" preserveAspectRatio="none">
      <path d="M0,250 C200,230 300,270 520,250 C680,235 780,190 980,210 C1120,225 1200,220 1200,220 L1200,300 L0,300 Z" fill="#57c5ff"></path>
    </svg>
  </div>

  <!-- ======= Pinned Plane Section (kept) ======= -->
  <section class="plane-stage reveal">
    <div class="plane-pin">
      <img id="plane-img" src="{{site.baseurl}}/images/about/download.png" alt="Plane" class="float">
    </div>
  </section>

  <!-- ======= Journey Section ======= -->
  <section class="section reveal card">
    <h3>Journey through Life</h3>
    <ul>
      <li>🏫 D39 elementary (San Diego, CA)</li>
      <li>🏫 Current senior, Class of 2026</li>
      <li>🎾 Varsity tennis &amp; mentor to middle schoolers</li>
      <li>🤖 Robotics — sensor coding lead</li>
      <li>🗝️ Key Club — community hours</li>
      <li>📚 Homework explainer-in-chief before tests</li>
      <li>📖 Library lunches to finish work</li>
      <li>🎮 Mario Kart with a tight crew after school</li>
    </ul>
    <div class="chips">
      <span class="chip">Curious</span>
      <span class="chip">Builder</span>
      <span class="chip">Team-first</span>
      <span class="chip">Calm under pressure</span>
    </div>
  </section>

  <!-- ======= Culture Section ======= -->
  <section class="section reveal card">
    <h3>Culture, Family, and Fun</h3>
    <p>Everything for me, as for many others, revolves around family and goals.</p>
    <ul>
      <li>Born in Escondido (<a href="https://ucsd.edu/" target="_blank" rel="noopener">hospital</a>)</li>
      <li>Family of four — two parents &amp; one brother</li>
      <li>Gallery below holds snapshots of culture, fun, and memories</li>
    </ul>
  </section>

  <!-- ======= Gallery ======= -->
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

<!-- =========================
     YOUR ORIGINAL JS (Flags)
========================== -->
<script>
  (function(){
    var container = document.getElementById("grid_container");
    var http_source = "https://upload.wikimedia.org/wikipedia/commons/";
    var living_in_the_world = [
      {"flag": "0/01/Flag_of_California.svg", "greeting": "Hey", "description": "California - since birth"},
      {"flag": "2/21/Flag_of_Vietnam.svg", "greeting": "CHÀO", "description": "ethnic background"},
      {"flag": "c/c3/Flag_of_France.svg", "greeting": "Salut", "description": "ethnic background"},
      {"flag": "9/9f/Flag_of_Indonesia.svg", "greeting": "Hai", "description": "ethnic background"},
    ];
    for (const location of living_in_the_world) {
      var gridItem = document.createElement("div");
      gridItem.className = "grid-item reveal";
      var img = document.createElement("img");
      img.src = http_source + location.flag;
      img.alt = location.flag + " Flag";
      var description = document.createElement("p");
      description.textContent = location.description;
      var greeting = document.createElement("p");
      greeting.textContent = location.greeting;
      gridItem.appendChild(img);
      gridItem.appendChild(description);
      gridItem.appendChild(greeting);
      container.appendChild(gridItem);
    }
  })();
</script>

<!-- =========================
     PLANE SCROLL SCRIPT
========================== -->
<script>
(function(){
  var plane = document.getElementById('plane-img');
  var stage = document.querySelector('.plane-stage');
  if(!plane || !stage) return;

  function clamp(v, lo, hi){ return Math.max(lo, Math.min(hi, v)); }

  function updatePlane(){
    var rect = stage.getBoundingClientRect();
    var viewportH = window.innerHeight || document.documentElement.clientHeight;
    var stageHeight = stage.offsetHeight;
    var scrollable = Math.max(1, stageHeight - viewportH);
    var passed = -rect.top;
    var p = clamp(passed / scrollable, 0, 1);

    var x = 2 + 96 * p;
    var y = 20 + (-10 * Math.sin(p * Math.PI));
    var rot = -10 + 20 * p;

    plane.style.transform = 'translate(' + x + 'vw,' + y + 'vh) rotate(' + rot + 'deg)';
  }

  updatePlane();
  window.addEventListener('scroll', updatePlane, {passive:true});
  window.addEventListener('resize', updatePlane);
})();
</script>

<!-- =========================
     PARALLAX + REVEAL ENGINE
========================== -->
<script>
(function(){
  // Parallax on scroll: different speeds per layer
  var clouds = document.querySelector('.layer.clouds');
  var gulls = document.querySelector('.layer.gulls');
  var palms = document.querySelector('.layer.palms');

  function parallax(){
    var y = window.scrollY || window.pageYOffset;
    if (clouds) clouds.style.transform = 'translateY(' + (y * 0.12) + 'px)';
    if (gulls)  gulls.style.transform  = 'translateY(' + (y * 0.2)  + 'px)';
    if (palms)  palms.style.transform  = 'translateY(' + (y * 0.35) + 'px)';
    raf = requestAnimationFrame(parallax);
  }
  var raf = requestAnimationFrame(parallax);

  // Scroll reveal
  var reveals = Array.from(document.querySelectorAll('.reveal'));
  var io = new IntersectionObserver((entries)=>{
    entries.forEach(e=>{
      if(e.isIntersecting){
        e.target.classList.add('in');
        io.unobserve(e.target);
      }
    });
  },{
    root:null, rootMargin:'0px 0px -5% 0px', threshold:0.1
  });
  reveals.forEach(el=> io.observe(el));

  // Respect prefers-reduced-motion
  if (window.matchMedia('(prefers-reduced-motion: reduce)').matches) {
    cancelAnimationFrame(raf);
    if (clouds) clouds.style.transform = '';
    if (gulls)  gulls.style.transform  = '';
    if (palms)  palms.style.transform  = '';
    reveals.forEach(el=>el.classList.add('in'));
  }
})();
</script>
