---
layout: base
title: Background with Object
description: Use JavaScript to have an in motion background.
sprite: images/platformer/sprites/flyinglabubu.png
background: images/platformer/backgrounds/labubu.jpg
permalink: /background
---

<canvas id="world"></canvas>

<script>
  const canvas = document.getElementById("world");
  const ctx = canvas.getContext('2d');
  const backgroundImg = new Image();
  const spriteImg = new Image();
  backgroundImg.src = '{{page.background}}'; //Background Image
  spriteImg.src = '{{page.sprite}}'; //Player Image

//Track when both images finish loading
  let imagesLoaded = 0;
  backgroundImg.onload = function() {
    imagesLoaded++;
    startGameWorld();
  };
  spriteImg.onload = function() {
    imagesLoaded++;
    startGameWorld();
  };
/* This block Starts the Game
 * It. checks for all images being loaded beofre placing it on the website
*/
// Core game logic
  function startGameWorld() {
    if (imagesLoaded < 2) return; // Delays start until everything is laoded
// Base class for anything drawn on the canvas
    class GameObject {
      constructor(image, width, height, x = 0, y = 0, speedRatio = 0) {
        this.image = image;
        this.width = width;
        this.height = height;
        this.x = x;
        this.y = y;
        this.speedRatio = speedRatio;
        this.speed = GameWorld.gameSpeed * this.speedRatio;
      }
      update() {} //Empty by default, subclasses override
      draw(ctx) {
        ctx.drawImage(this.image, this.x, this.y, this.width, this.height);
      }
    }
//Background object(scrolls horizontally forever)
    class Background extends GameObject {
      constructor(image, gameWorld) {
        // Fill entire canvas
        super(image, gameWorld.width, gameWorld.height, 0, 0, 0.1);
      }
      update() {
        this.x = (this.x - this.speed) % this.width; //Wrap Background
      }
      draw(ctx) {
        //Draw two copies side by side so it loops seamlessly
        ctx.drawImage(this.image, this.x, this.y, this.width, this.height);
        ctx.drawImage(this.image, this.x + this.width, this.y, this.width, this.height);
      }
    }
// Player object (bobs up and down on a sin wave)
    class Player extends GameObject {
      constructor(image, gameWorld) {
        const width = image.naturalWidth / 2; //Scale down sprite
        const height = image.naturalHeight / 2;
        const x = (gameWorld.width - width) / 2; //Center horizotally
        const y = (gameWorld.height - height) / 2; // Center vertically
        super(image, width, height, x, y);
        this.baseY = y;
        this.frame = 0;
      }
      update() {
        this.y = this.baseY + Math.sin(this.frame * 0.05) * 20;
        this.frame++;
      }
    }
// Math and moving images
    class GameWorld {
      static gameSpeed = 5;
      constructor(backgroundImg, spriteImg) {
        this.canvas = document.getElementById("world");
        this.ctx = this.canvas.getContext('2d');
        this.width = window.innerWidth;
        this.height = window.innerHeight;
        this.canvas.width = this.width;
        this.canvas.height = this.height;
        this.canvas.style.width = `${this.width}px`;
        this.canvas.style.height = `${this.height}px`;
        this.canvas.style.position = 'absolute';
        this.canvas.style.left = `0px`;
        this.canvas.style.top = `${(window.innerHeight - this.height) / 2}px`;

        this.objects = [
         new Background(backgroundImg, this),
         new Player(spriteImg, this)
        ];
      }
      gameLoop() {
        this.ctx.clearRect(0, 0, this.width, this.height);
        for (const obj of this.objects) {
          obj.update();
          obj.draw(this.ctx);
        }
        requestAnimationFrame(this.gameLoop.bind(this));
      }
      start() {
        this.gameLoop();
      }
    }

    const world = new GameWorld(backgroundImg, spriteImg);
    world.start();
  }
