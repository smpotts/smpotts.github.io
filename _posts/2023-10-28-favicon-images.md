---
layout: post
title: Adding images to browser tabs with Favicon
subtitle: How I got this work on my site without favicon generators
cover-img: /assets/img/skeleton_tennis.jpeg
thumbnail-img: /assets/img/skeleton_tennis.jpeg
share-img: /assets/img/skeleton_tennis.jpeg
tags: [tech, favicon]
---

When I first got my website running I was annoyed that I didn't have an image to show on the browser tabs, but I had bigger things to tackle so I pushed that aside as something I would figure out later. Over a year later, I finally got to a point where I was interested in figuring this out, so I timeboxed my efforts to one hour. This first thing I did was I went to Dean Attali's GitHub repo where I cloned his open source [Beautiful Jekyll project](https://github.com/daattali/beautiful-jekyll) to use as a base for my website. I went to his website and saw his browser image is just an image with his initials. I thought maybe this could be something that he made configurable in the code, so I searched his repository for "DA". There wasn't anything in the source code that provided any evidence this was configurable.

I started Googling this and found a lot of people talking on StackOverflow about [Favicon](https://en.wikipedia.org/wiki/Favicon). Favicon is the name of the small image that appears in the tab on your browser. From [this](https://stackoverflow.com/questions/11488960/how-do-i-put-my-websites-logo-to-be-the-icon-image-in-browser-tabs) StackOverflow post, I learned about free third party sites that will help you generate a favicon image. I tried a couple, and I had the best luck generating an image that looked reasonable with [Real Favicon Generator](https://realfavicongenerator.net/). I learned through trial and error that it's best to edit the image you want and make sure it's a perfect square before you try to upload it, or else the tool will try to pad the side of the image to make a square, and it looks bad. Also, the StackOverflow post I read recommended exporting the file as a PNG, so I did that before uploading the image to make things easier.

After the image generated from Read Favicon Generator, it returned instructions for installing the favicon. 

[![Screenshot-2023-10-28-at-1-01-33-PM.png](https://i.postimg.cc/8zfHhD2p/Screenshot-2023-10-28-at-1-01-33-PM.png)](https://postimg.cc/rDcxT6y3)

I was really confused why it had to be this complicated because the StackOverflow post mentioned that you could just add the image in the header tag. I decided I would try to add the image without the help of a generator, so copied the square image that I used to upload to Real Favicon Generator, and I put it in the root folder of my project, at the same level as the `index.html` file. Then I found the HTML file in my project that contains the header code that is applied to each page on the website, and I added this:
```
<link rel="shortcut icon" type="image/x-icon" href="/avatar-favicon.png" />
```
This was sufficient to get a favicon image added to each of my browser tabs, and doing this without the use of a favicon generator was much cleaner and simpler.