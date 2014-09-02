---
layout: post.html
title: Canvas Particles
tags: [css,javascript,tutorial,example]
---


Learning to make a simple particle system in HTML5 Canvas and Javascript. 

In this tutorial I will cover:
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
        

We have now initialized a blank canvas and are ready to draw something. I will cover drawing circles in the next blog post.


**Some useful resources:**
  1. [MDN - Canvas](https://developer.mozilla.org/en-US/docs/Web/HTML/Canvas)
  2. [Can I Use...](http://caniuse.com/)
  4. [StackOverflow](http://stackoverflow.com/)
