## Dark mode for my portfolio

My portfolio has been updated quite a bit today. As a result, I wanted to add a dark mode option for the most recent modifications, but I have no idea how to accomplish it more quickly or where to put the dark mode symbol or option.

I then have the wild notion of copying my Webvium force dark mode js and pasting it on my website; by detecting if a user clicks it three times, dark mode will be turned on or off.

This is how my website appears in light mode:

![light mode header](https://cdn.hashnode.com/res/hashnode/image/upload/v1657212086567/yAwlDfXFG.png align="left")

![light mode footer](https://cdn.hashnode.com/res/hashnode/image/upload/v1657212091763/lMk0wzsqH.png align="left")

My website appears as follows when a user triple-clicks to activate the force dark mode:

![dark mode header](https://cdn.hashnode.com/res/hashnode/image/upload/v1657212136688/8TlwSe8pG.png align="left")

![dark mode footer](https://cdn.hashnode.com/res/hashnode/image/upload/v1657212146435/oWNoS3JL0.png align="left")

Even if it's simply a color inversion, it looks cool so far.

I used the following code:

``` JavaScript
window.addEventListener('click', function (evt) {
  if (evt.detail === 3) {
      javascript: (
  function () { 
      var css = 'html {-webkit-filter: invert(100%);' +
                '-moz-filter: invert(100%);' + 
                '-o-filter: invert(100%);' + 
                '-ms-filter: invert(100%);}' +
                'img, iframe, video, canvas, svg, picture {-webkit-filter: invert(100%) !important;' +
                '-moz-filter: invert(100%) !important;' + 
                '-o-filter: invert(100%) !important;' + 
                '-ms-filter: invert(100%) !important;}',
      head = document.getElementsByTagName('head')[0], style = document.createElement('style');
      if (!window.counter) { 
          window.counter = 1;
      } else { 
          window.counter ++;
          if (window.counter % 2 == 0) { 
              var css = 'html {-webkit-filter: invert(0%); -moz-filter: invert(0%); -o-filter: invert(0%); -ms-filter: invert(0%); }' +
                  'img, iframe, video, canvas, svg, picture {-webkit-filter: invert(0%) !important; -moz-filter: invert(0%) !important; -o-filter: invert(0%) !important; -ms-filter: invert(0%) !important;}'
          }
      };
      style.type = 'text/css';
      if (style.styleSheet) {
          style.styleSheet.cssText = css;
      } else {
          style.appendChild(document.createTextNode(css));
      }
      head.appendChild(style);
  }
());
  }
});
```

my website: [https://mrepol742.github.io](https://mrepol742.github.io?utm_source=hashnode)