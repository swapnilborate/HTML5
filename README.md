# HTML5
HTML 5 documentation

What is initial scale, user-scalable, minimum-scale, maximum-scale attribute in meta tag?

I was going through the source code of a website and found this piece of code.

<meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=1.0, minimum-scale=1.0, maximum-scale=1.0">

They are viewport meta tags, and is most applicable on mobile browsers.

width=device-width

This means, we are telling to the browser “my website adapts to your device width”.

initial-scale

This defines the scale of the website, This parameter sets the initial zoom level, which means 1 CSS pixel is equal to 1 viewport pixel. This parameter help when you're changing orientation, or preventing default zooming. Without this parameter, responsive site won't work.

maximum-scale
Maximum-scale defines the maximum zoom. When you access the website, top priority is maximum-scale=1, and it won’t allow the user to zoom.

minimum-scale
Minimum-scale defines the minimum zoom. This works the same as above, but it defines the minimum scale. This is useful, when maximum-scale is large, and you want to set minimum-scale.

user-scalable
User-scalable assigned to 1.0 means the website is allowing the user to zoom in or zoom out.

But if you assign it to user-scalable=no, it means the website is not allowing the user to zoom in or zoom out.

user-scalable:

user-scalable=yes (default) to allow the user to zoom in or zoom out on the web page;

user-scalable=no to prevent the user from zooming in or zooming out.

you can get more detail infomation by reading the following articles, hope it helpful for you!

https://i.stack.imgur.com/bAzG0.png
