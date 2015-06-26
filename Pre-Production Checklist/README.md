# Pre-Production Checklist
* Is it [**responsive**](#responsive)?
* Does is have special features for [**touch devices**](#touch-support)?
* Are [**hit areas**](#hit-areas) appropriately sized?
* Is there a [**noscript fallback**](#noscript-fallback) for old browsers?
* Is all information [**accessible via keyboard**](#keyboard-support)?
* Are there [**visible states**](#visible-states) for focus/hover/selected?
* Are [**alternative selection mechanisms**](#alternative-selection-mechanisms) in place?
* Is there a [**fallback for tooltips**](#tooltip-alternative)?
* Are [**tables**](#table-accessibility) legible and accessible?
* How did it perform on [**PageSpeed**](#pagespeed-evaluation)?
* Is it error-free on [**WAVE**](#wave-evaluation)?

<hr />
##Responsive:
* Test the graphic on as many devices as possible and make sure it flows appropriately and doesn't break out of the viewport.
* Use the viewport meta tag. 
 * ```<meta name="viewport" content="width=device-width, initial-scale=1">```
 * More on sizing content: [Viewport Meta Tag](https://developer.mozilla.org/en-US/docs/Mozilla/Mobile/Viewport_meta_tag) | Mozilla Developers
* Use media queries.
 * ```@media all and (max-width: 768px) {}```
 * More on media queries: [Media Queries for Standard Devices](https://css-tricks.com/snippets/css/media-queries-for-standard-devices/) | CSS Tricks
* More on RWD fundamentals: [Responsive Web Design Basics](https://developers.google.com/web/fundamentals/layouts/rwd-fundamentals/index?hl=en) | Google Developers

<hr>
##Touch Support:
* Some interactives may require specific enhancements for touch devices.
 * Example: Disable hover/click events on a map in favor of a native control like a select box.
* To isolate UI elements and interactions for touch devices, test for mobile **user agent strings** and add a CSS class to the containing element. This way you can use touch-only CSS and JS selectors.

        var touch;
        if (/Android|webOS|iPhone|iPad|iPod|BlackBerry/i.test(navigator.userAgent)) {
            touch = true;
            var wrapper = document.getElementById('interactive-wrapper');
            wrapper.className += ' touch-device';
        }
The above JS snippet tests for the user agent and, if it's a touch device, sets the variable ```touch``` to ```TRUE``` and adds the class ```touch-device``` to the interactive's container. This way you can write touch-only CSS like this:
    
        .touch-device circle {  
          r: 23;
          stroke-width: 8;
        }
    And JS like this:
    
        if (!touch) {
            map.addEventListener( 'mousemove', function(e) {
              var left = e.offsetX===undefined?e.layerX+10:e.offsetX+10;
              var top = e.offsetY===undefined?e.layerY+10:e.offsetY+10;
              if (e.pageX > (window.innerWidth - 300)){
                left = e.offsetX===undefined?e.layerX-tooltip.clientWidth:e.offsetX-tooltip.clientWidth;
              }
              tooltip.style.left = left + 'px';
              tooltip.style.top = top + 'px';
            });
          }
* More on designing for touch: [Fingers, thumbs, and people](http://interactions.acm.org/archive/view/may-june-2015/fingers-thumbs-and-people) | Steven Hoober

<hr>
##Hit Areas:

<hr>
##Noscript Fallback:

<hr>
##Keyboard Support:

<hr>
##Visible States:

<hr>
##Alternative Selection Mechanisms:

<hr>
##Tooltip Alternative:

<hr>
##Table Accessibility:

<hr>
##PageSpeed Evaluation:

<hr>
##WAVE Evaluation:

