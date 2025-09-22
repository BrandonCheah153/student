---
layout: post
title: About
permalink: /about/
---


<div id="about-beach">


 <!-- SKY + SUN. -->
 <div class="sky"></div>
 <div class="sun"></div>


 <!-- OCEAN -->
 <div class="ocean">
   <div class="ocean-fill"></div>
   <div class="wave wave-a"></div>
   <div class="wave wave-b"></div>
 </div>


 <!-- SHORELINE + SAND -->
 <div class="shoreline"></div>
 <div class="sand">
   <div class="crab c1"></div>
   <div class="crab c2"></div>
   <div class="crab c3"></div>
 </div>


 <!-- PARALLAX DECORATIONS -->
 <div class="parallax">
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
   <div class="waves reveal">
     <svg class="w1" viewBox="0 0 1200 300" preserveAspectRatio="none">
       <path d="M0,240 C150,220 300,260 450,240 C600,220 750,180 900,200 C1050,220 1200,210 1200,210 L1200,300 L0,300 Z" fill="#9bd8ff"></path>
     </svg>
     <svg class="w2" viewBox="0 0 1200 300" preserveAspectRatio="none">
       <path d="M0,250 C200,230 300,270 520,250 C680,235 780,190 980,210 C1120,225 1200,220 1200,220 L1200,300 L0,300 Z" fill="#57c5ff"></path>
     </svg>
   </div>


   <!-- Plane -->
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
   </section>


   <!-- Culture -->
   <section class="section reveal card">
     <h3>Culture, Family, and Fun</h3>
     <p>Everything for me, as for many others, revolves around family and goals.</p>
     <ul>
       <li>Born in Escondido (<a href="https://ucsd.edu/" target="_blank">hospital</a>)</li>
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
     </div>
   </section>
 </div>
</div>


<style>
 /* === High contrast text & transparent background === */
 #about-beach,
 #about-beach .wrap { position: relative; z-index: 10; color: #0b1a2b; }
 #about-beach h2, #about-beach h3 { color: #08213a; text-shadow:0 1px 0 rgba(255,255,255,.6); }
 #about-beach a { color:#0a4fb3; text-decoration:underline; }
 #about-beach a:hover { text-decoration-thickness:2px; }
 #about-beach .post, #about-beach .page, #about-beach .container,
 #about-beach .post-content, #about-beach .entry { background:transparent!important; }


 /* === Background layers with correct z-index === */
 #about-beach .sky{position:fixed;inset:0;z-index:1;background:linear-gradient(180deg,#7fd4ff,#ffd3a0,#ffafbd);background-size:100% 200%;animation:skyShift 16s ease-in-out infinite alternate;}
 @keyframes skyShift{to{background-position:0 100%;}}
 #about-beach .sun{position:fixed;top:7vh;left:50%;width:22vmin;aspect-ratio:1/1;transform:translateX(-50%);border-radius:50%;background:radial-gradient(circle,#ffd66b,rgba(255,214,107,0) 60%);filter:blur(8px);z-index:2;}


 #about-beach .ocean{position:fixed;left:0;right:0;top:35vh;height:38vh;z-index:3;overflow:hidden;}
 #about-beach .ocean-fill{position:absolute;inset:0;background:linear-gradient(180deg,#66c9ff 0%,#43b5ff 60%,#2fa6f9 100%);}
 #about-beach .wave{position:absolute;left:-50%;width:200%;height:120%;bottom:-4vh;opacity:.75;background-repeat:repeat-x;background-size:1200px 160px;animation:waveSlide 12s linear infinite;}
 #about-beach .wave-a{background-image:url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="1200" height="160"><path d="M0 80 C60 40 120 120 180 80 C240 40 300 120 360 80 C420 40 480 120 540 80 C600 40 660 120 720 80 C780 40 840 120 900 80 C960 40 1020 120 1080 80 C1140 40 1200 120 1260 80 L1260 160 L0 160 Z" fill="%23ffffff" opacity="0.7"/></svg>');}
 #about-beach .wave-b{bottom:-2vh;opacity:.5;animation-duration:18s;background-image:url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="1200" height="160"><path d="M0 90 C70 50 140 130 210 90 C280 50 350 130 420 90 C490 50 560 130 630 90 C700 50 770 130 840 90 C910 50 980 130 1050 90 C1120 50 1190 130 1260 90 L1260 160 L0 160 Z" fill="%23ffffff" opacity="0.5"/></svg>');}
 @keyframes waveSlide{to{transform:translateX(-50%);}}


 #about-beach .shoreline{position:fixed;left:0;right:0;top:72vh;height:4vh;z-index:4;background:radial-gradient(ellipse at 50% 0%,#fff 0%,rgba(255,255,255,.6) 60%,transparent 80%);filter:blur(2px);}


 #about-beach .sand{position:fixed;left:0;right:0;bottom:0;height:28vh;z-index:5;background:#f4e3b4;overflow:hidden;}
 #about-beach .sand::before{content:"";position:absolute;inset:-20% -20% 0 -20%;background-image:radial-gradient(2px 2px at 20% 30%,#d5bf8a 30%,transparent 31%),radial-gradient(2px 2px at 70% 60%,#d5bf8a 30%,transparent 31%);background-size:320px 220px;opacity:.5;animation:sandDrift 22s linear infinite;}
 @keyframes sandDrift{to{transform:translateX(-20%);}}


 .crab{position:absolute;bottom:6vh;width:48px;height:32px;background-repeat:no-repeat;background-size:contain;background-image:url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="96" height="64"><ellipse cx="48" cy="40" rx="22" ry="14" fill="%23e5553f"/><circle cx="38" cy="28" r="5" fill="%23e5553f"/><circle cx="58" cy="28" r="5" fill="%23e5553f"/><circle cx="38" cy="26" r="2"/><circle cx="58" cy="26" r="2"/><path d="M28 40 q-10 -8 0 -16" stroke="%23e5553f" stroke-width="4" fill="none"/><path d="M68 40 q10 -8 0 -16" stroke="%23e5553f" stroke-width="4" fill="none"/></svg>');animation:crabWalk 18s linear infinite;}
 .c1{left:-60px;} .c2{left:-60px;bottom:8vh;animation-duration:22s;} .c3{left:-60px;bottom:5vh;animation-duration:26s;}
 @keyframes crabWalk{to{transform:translateX(calc(100vw + 120px));}}


 #about-beach .parallax{position:fixed;inset:0;z-index:6;pointer-events:none;}
 #about-beach .clouds{background-image:url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="360" height="140"><ellipse cx="80" cy="70" rx="70" ry="40" fill="%23fff"/></svg>');background-position:10% 14%;opacity:.6;}
 #about-beach .gulls{background-image:url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="160" height="80"><path d="M5 40 Q30 10 55 40 M55 40 Q80 10 105 40" stroke="%230f223d" stroke-width="3" fill="none"/></svg>');background-position:25% 28%;opacity:.7;}
 #about-beach .palms{background-size:28vmin auto;opacity:.9;}


 .waves{position:relative;height:24vh;margin:8rem 0 2rem;overflow:hidden;border-radius:16px;box-shadow:var(--shadow);}
 .waves svg{position:absolute;left:0;right:0;bottom:-1px;width:200%;height:140%;}
 .waves .w1{animation:waveSlide 10s linear infinite;}
 .waves .w2{animation:waveSlide 14s linear infinite;opacity:.5;}


 .grid-container{display:grid;grid-template-columns:repeat(auto-fill,minmax(160px,1fr));gap:14px;margin-top:1rem;}
 .grid-item{background:#ffffffd9;border-radius:14px;padding:.8rem;text-align:center;}
 .grid-item img{width:100%;height:100px;object-fit:contain;}


 .image-gallery{display:flex;gap:12px;overflow-x:auto;}
 .image-gallery img{max-height:170px;border-radius:12px;box-shadow:var(--shadow);}


 .plane-stage{height:230vh;}
 .plane-pin{position:sticky;top:0;height:100vh;z-index:12;}
 #plane-img{position:absolute;left:0;top:0;width:130px;filter:drop-shadow(0 4px 6px rgba(0,0,0,.25));}
</style>


<script>
 // Build flags
 (function(){
   var container=document.querySelector("#grid_container");
   var http="https://upload.wikimedia.org/wikipedia/commons/";
   var flags=[{"flag":"0/01/Flag_of_California.svg","greeting":"Hey","description":"California - since birth"},{"flag":"2/21/Flag_of_Vietnam.svg","greeting":"CHÀO","description":"ethnic background"},{"flag":"c/c3/Flag_of_France.svg","greeting":"Salut","description":"ethnic background"},{"flag":"9/9f/Flag_of_Indonesia.svg","greeting":"Hai","description":"ethnic background"}];
   for(const f of flags){var item=document.createElement("div");item.className="grid-item";var img=document.createElement("img");img.src=http+f.flag;var d=document.createElement("p");d.textContent=f.description;var g=document.createElement("p");g.textContent=f.greeting;item.appendChild(img);item.appendChild(d);item.appendChild(g);container.appendChild(item);}
 })();


 // Plane animation
 (function(){
   var plane=document.querySelector("#plane-img");
   var stage=document.querySelector(".plane-stage");
   if(!plane||!stage)return;
   function clamp(v,lo,hi){return Math.max(lo,Math.min(hi,v));}
   function update(){
     var rect=stage.getBoundingClientRect();
     var vh=window.innerHeight;
     var scrollable=Math.max(1,stage.offsetHeight-vh);
     var p=clamp((-rect.top)/scrollable,0,1);
     var x=2+96*p, y=22+(-9*Math.sin(p*Math.PI)), rot=-8+16*p;
     plane.style.transform='translate('+x+'vw,'+y+'vh) rotate('+rot+'deg)';
   }
   update();window.addEventListener('scroll',update,{passive:true});window.addEventListener('resize',update);
 })();
</script>


