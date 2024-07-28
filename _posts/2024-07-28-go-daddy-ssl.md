---
layout: post
title: Setting up SSL for GoDaddy hosted WordPress with CloudFlare
subtitle: Creating SSL certificates for a GoDaddy hosted WordPress site
cover-img: /assets/img/fireworks.jpg
thumbnail-img: /assets/img/fireworks.jpg
share-img: /assets/img/fireworks.jpg
tags: [tech, ssl, wordpress, godaddy] 
---

The only experience I have with setting up a website is my experience setting up this website using GitHub Pages. There are a lot of features that GitHub gives you right out of the box if you use GitHub Pages, one of which being the checkbox to enforce HTTPS when you set up the site. Given how easy GitHub makes things, I figured that was the case for most web hosting sites like GoDaddy, especially because they are paid services. I was recently asked to help a friend configure SSL certificates on her website so the would enforce HTTPS, and given my experience with GitHub Pages, I thought this would be a simple checkbox in the site configuration of GoDaddy. I was shocked to see GoDaddy charges a recurring annual fee to provide managed SSL on websites with upfront costs starting at $209. I figured there had to be a more cost-effective alternative, so I set out to see what else we could do. This documents the process of using CloudFlare to create SSL certificates, applying the certificates to GoDaddy, and then tinkering with WordPress settings to enforce HTTPS.

I searched on Google to see whether anyone else had encountered and documented this issue, and sure enough I found [this](https://caweem.com/blog/how-to-install-cloudflare-ssl-on-godaddy/) blog post, which covers the majority of the initial setup. I learned from this blog post I could set up a CloudFlare account for the website hosted on GoDaddy on the free-tier, and generate/ manage the SSL certificates through CloudFlare. The majority of the setup from the blog was pretty straightforward, and mainly covers generating the SSL certificates and applying them to GoDaddy. Once this part was complete I put "https://" in front of the domain name of the website and tried it. The webpage was able to load, but I received a browser error from Firefox saying the page contained "mixed content". Mixed content is where the page is trying to load certain assets that have HTTPS content and others that have HTTP content. This means that the page is only partially encrypted, and it may *look* secure, but it isn't.

I went back to Google and ChatGPT to try to figure out how I could get rid of the mixed content issue. One of the first things I discovered is that the GoDaddy managed WordPress site is set up to point to HTTP by default if it was initally configured that way. To change this:
1. Go to Settings
2. Click General
3. Edit the WordPress Address (URL) and Site Address (URL) fields to have "https" in the URL 

WordPress uses these URLs to generate URLs for images, so this needs to be changed when HTTPS is enforced. This was definitely a necessary step, but it still didn't resolve the SSL issues, so I installed the "Really Simple SSL" WordPress plugin thanks to advice from Stack Overflow. I enabled the plugin to enforce SSL and I also enabled `.htaccess` to redirect HTTP to HTTPS. After clearing my cache and refreshing, the mixed content errors that were loading with the page before went away. That is until I scrolled to the bottom of the page and loaded more images from the grid of photos on the webpage. For some reason when the page was prompted to load more images, the mixed content error came back. 

When I inspected the content the pages was trying to render, I could see an assortment of images with "http" and "https" URLs, which was clearly the issue. I found a highly regarded WordPress plugin called "Better Search Replace" that does string search and replaces across different WordPress database tables. I found 7 instances of the database still pointing to "http", and replaced those with "https". After making this database updating, clearing my cache, and refreshing, the mixed content errors went away for good.

It's worth mentioning that the Links tab on the WordPress admin panel also had hardcoded URLs to different things on the WordPress site like "Support" and "Documentation", which I updated just in case, but I wasn't entirely sure what they were related to. Ultimately it was worth a small headache to get SSL setup manually for WordPress, and avoid playing GoDaddy hundreds of dollars for a relatively simple task.
