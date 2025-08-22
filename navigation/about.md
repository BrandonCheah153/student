---
layout: post
title: About
permalink: /about/
comments: true
---

## As a conversation Starter

Here are some places I am from.

<comment>
Flags are made using Wikipedia images
</comment>

<style>
    /* Style looks pretty compact, 
       - grid-container and grid-item are referenced the code 
    */
    .grid-container {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(150px, 1fr)); /* Dynamic columns */
        gap: 10px;
    }
    .grid-item {
        text-align: center;
    }
    .grid-item img {
        width: 100%;
        height: 100px; /* Fixed height for uniformity */
        object-fit: contain; /* Ensure the image fits within the fixed height */
    }
    .grid-item p {
        margin: 5px 0; /* Add some margin for spacing */
    }

    .image-gallery {
        display: flex;
        flex-wrap: nowrap;
        overflow-x: auto;
        gap: 10px;
        }

    .image-gallery img {
        max-height: 150px;
        object-fit: cover;
        border-radius: 5px;
    }
    
</style>

<!-- This grid_container class is used by CSS styling and the id is used by JavaScript connection -->
<div class="grid-container" id="grid_container">
    <!-- content will be added here by JavaScript -->
</div>

<script>
    // 1. Make a connection to the HTML container defined in the HTML div
    var container = document.getElementById("grid_container"); // This container connects to the HTML div

    // 2. Define a JavaScript object for our http source and our data rows for the Living in the World grid
    var http_source = "https://upload.wikimedia.org/wikipedia/commons/";
    var living_in_the_world = [
        {"flag": "0/01/Flag_of_California.svg", "greeting": "Hey", "description": "California - since birth"},
        {"flag": "2/21/Flag_of_Vietnam.svg", "greeting": "CHÀO", "description": "ethnic background"},
        {"flag": "c/c3/Flag_of_France.svg", "greeting": "Salut", "description": "ethnic background"},
        {"flag": "9/9f/Flag_of_Indonesia.svg", "greeting": "Hai", "description": "ethnic background"},
    ];

    // 3a. Consider how to update style count for size of container
    // The grid-template-columns has been defined as dynamic with auto-fill and minmax

    // 3b. Build grid items inside of our container for each row of data
    for (const location of living_in_the_world) {
        // Create a "div" with "class grid-item" for each row
        var gridItem = document.createElement("div");
        gridItem.className = "grid-item";  // This class name connects the gridItem to the CSS style elements
        // Add "img" HTML tag for the flag
        var img = document.createElement("img");
        img.src = http_source + location.flag; // concatenate the source and flag
        img.alt = location.flag + " Flag"; // add alt text for accessibility

        // Add "p" HTML tag for the description
        var description = document.createElement("p");
        description.textContent = location.description; // extract the description

        // Add "p" HTML tag for the greeting
        var greeting = document.createElement("p");
        greeting.textContent = location.greeting;  // extract the greeting

        // Append img and p HTML tags to the grid item DIV
        gridItem.appendChild(img);
        gridItem.appendChild(description);
        gridItem.appendChild(greeting);

        // Append the grid item DIV to the container DIV
        container.appendChild(gridItem);
    }
</script>

<!-- Pinned Plane Section -->
<section class="plane-stage">
  <div class="plane-pin">
    <!-- use the one you actually have: download.jpg OR download.png -->
    <img id="plane-img" src="{{site.baseurl}}/images/about/download.png" alt="Plane">
  </div>
</section>

<style>
  .plane-stage {
    height: 200vh;        /* length of the “paused” section */
  }
  .plane-pin {
    position: sticky;
    top: 0;
    height: 100vh;        /* full screen while pinned */
    overflow: hidden;     /* hides edges as plane exits */
    background: transparent;
    z-index: 1;
  }
  #plane-img {
    position: absolute;   /* positioned inside the pinned box */
    left: 0;
    top: 0;
    width: 120px;         /* tweak size as you like */
    height: auto;
    pointer-events: none;
    filter: drop-shadow(0 4px 6px rgba(0,0,0,0.25)); /* no blur for sharpness */
    z-index: 2;
  }
</style>

<!-- Plane Scroll Script (targets plane-img only) -->
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

    // Progress 0..1 while the pinned section is active
    var passed = -rect.top;
    var p = clamp(passed / scrollable, 0, 1);

    // Flight path (viewport units keep it aligned to screen)
    var x = 2 + 96 * p;                        // 2vw -> ~98vw
    var y = 22 + (-8 * Math.sin(p * Math.PI)); // lower baseline + bob
    var rot = -8 + 16 * p;

    plane.style.transform =
      'translate(' + x + 'vw,' + y + 'vh) rotate(' + rot + 'deg)';
  }

  updatePlane();
  window.addEventListener('scroll', updatePlane, {passive:true});
  window.addEventListener('resize', updatePlane);
})();
</script>



### Journey through Life

Here is what I did at those places

- 🏫 I went to D39 elementary school in San Diego California.
- 🏫 Middle and High School in San Diego California, curent senior and graduating class of 2026.
- 🎓 Plays varsity tennis but also helps coach middle school kids.
- On the robotics team, usually in charge of coding the sensors.
- Attends Key Club meetings but mostly for the community service hours.
- Always the one who explains homework problems to friends right before the test.
- Eats lunch in the library sometimes to finish work.
- Has a small but close group of friends who play Mario Kart after school.

### Culture, Family, and Fun

Everything for me, as for many others, revolves around family and goals.

- My momma told me that I was born in escondido [hospital](https://ucsd.edu/)
- My family is pretty big as I have two parents and 1 brother. 
- The gallery of pics has some of my family, fun, culture and memories.

<comment>
Gallery of Pics, scroll to the right for more ...
</comment>
<div class="image-gallery">
  <img src="{{site.baseurl}}/images/dog.png" alt="Image 1">
  <img src="{{site.baseurl}}/images/about/earings.png" alt="Image 2">
  <img src="{{site.baseurl}}/images/about/grapes.png" alt="Image 3">
  <img src="{{site.baseurl}}/images/about/griaffe.png" alt="Image 4">
  <img src="{{site.baseurl}}/images/about/parrot.png" alt="Image 5">
  <img src="{{site.baseurl}}/images/about/lora_fam.jpg" alt="Image 6">
  <img src="{{site.baseurl}}/images/about/lora_fam2.jpg" alt="Image 7">
  <img src="{{site.baseurl}}/images/about/pj_party.jpg" alt="Image 8">
  <img src="{{site.baseurl}}/images/about/trent_family.png" alt="Image 9">
  <img src="{{site.baseurl}}/images/about/claire.jpg" alt="Image 10">
  <img src="{{site.baseurl}}/images/about/grandkids.jpg" alt="Image 11">
  <img src="{{site.baseurl}}/images/about/farm.jpg" alt="Image 12">
</div>
