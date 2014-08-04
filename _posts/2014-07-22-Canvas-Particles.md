---
layout: post.html
title: Canvas Particles
tags: [css,javascript,tutorial,example]
---


Learn to make a simple particle system in HTML5 Canvas and Javascript. 

In this tutorial:
1. Initializing Canvas
2. Dawing circles
3. Simple animation for particle movement using SetInterval
4. Improving the code using RequestAnimationFrame


**1. Initializing Canvas**

Introduced in HTML5, the HTML  ```<canvas>```  element can be used to draw graphics via scripting in JavaScript. The ``` <canvas>```  element isn't supported in some older browsers, but is supported in recent versions of all major browsers. More information can be found on here: [http://caniuse.com/#feat=canvas](http://caniuse.com/#feat=canvas). ```<canvas>``` element requires the closing tag, like so:

    {% codeblock lang:html %}
    <canvas id="myCanvas"></canvas>
    {% endcodeblock %}

This creates a blank canvas for us to use. You can set the with and height at this point:

    {% codeblock lang:html %}
    
    <canvas id="myCanvas" width="500" height="300"> JavaScript Particles Canvas </canvas>
    {% endcodeblock %}
    
If not specified, **width** defaults to **300px** and **height** defaults to **150px**.

Some older versions of browsers do not support the ```<canvas>``` element, we can provide fallback content. We just provide alternate content inside the ```<canvas>``` element. Browsers which don't support ```<canvas>``` will ignore the container and render the fallback content inside it, otehrwise they will render the canvas normally:
    {% codeblock lang:html %}
        
    <canvas id="myCanvas" width="500" height="300"></canvas>
    {% endcodeblock %}

You can even include a different element inside the canvas element:
    {% codeblock lang:html %}
  
    <canvas id="myCanvas" width="500" height="300"><img src="img/example.png" width="500" height="300" alt="Example Image"></canvas>
        {% endcodeblock %}

 Particles.js:
    {% codeblock lang:js %}

        // declare vars
    var ps = [];
    var MAX_NUM = 500;
    var colors = [ '#69D2E7', '#A7DBD8', '#E0E4CC', '#F38630', '#FA6900', '#FF4E50', '#F9D423' ];
    var FPS = 60;
    
    var c=document.getElementById("myCanvas");
    var ctx=c.getContext("2d");
    
    spawn();
    
    
    
    //create the particles
    function spawn() {
      for(var i=0; ps.length < MAX_NUM; i++) {
        ps[i] = { x: Math.random()*window.innerWidth,
                  y: Math.random()*window.innerHeight,
                  r: Math.random()*5,
                  c: colors[Math.floor(Math.random()*colors.length)]
                };                  
       }
    }
    
    function update() {
        for(var i=0; i<ps.length; i++) {
            ps[i].y += 1;
            ps[i].x += -1 + (Math.random() * 3);
            //ps[i].r = Math.random()*5;
        }
    }
    
    function reset() {
        //reset the x and y coordinates if leaves the canvas
        for(var i=0; i<ps.length; i++) {
            //reset if y or coordinate has left the canvas
            if(ps[i].y > c.height) {
                ps[i].y = Math.random()*window.innerHeight;
                ps[i].color = colors[Math.floor(Math.random() * colors.length)];
            }
            //reset if x or coordinate has left the canvas
            if(ps[i].x > c.width || ps[i].x < 0){
              ps[i].x = Math.random()*window.innerWidth;
              ps[i].color = colors[Math.floor(Math.random() * colors.length)];
            }
        }
    }
      
    
    function draw() {
    
      c.width = window.innerWidth;
      c.height = window.innerHeight;
    
      for(var i=0; i<ps.length; i++) {
        ctx.beginPath();
    		ctx.arc( ps[i].x, ps[i].y, ps[i].r, 0, 6);
    		ctx.fillStyle = ps[i].c;
    		ctx.fill(); 
      }
    }
    
    setInterval(function() {
      update();
      draw();
      reset();
    }, 30);
    {% endcodeblock %}

**Some useful resources:**
  1. [MDN - Mozilla Developer Network](https://developer.mozilla.org/en-US/)
  2. [Can I Use...](http://caniuse.com/)
  3. [color.hailpixel.com](http://color.hailpixel.com/)
  4. [StackOverflow](http://stackoverflow.com/)
