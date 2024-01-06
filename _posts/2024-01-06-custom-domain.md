---
layout: post
title: Configuring a custom domain with Github pages 
subtitle: Switching from the Github subdomain to a custom domain in roughly an hour
cover-img: /assets/img/balboa2.jpg
thumbnail-img: /assets/img/balboa2.jpg
share-img: /assets/img/balboa2.jpg
tags: [tech, dns, github_pages]
---

I've been wanting to purchase a custom domain name for my personal website since I first started it, but I wasn't totally sure where I wanted to register it or what I wanted to call it, plus I was a little intimidated by the thought of having to get deep into world of DNS to set it up. The truth is, configuring my website in Github Pages to use the new domain name I purchased on Namecheap was actually quite simple once I got all the pieces together.

I chose Namecheap because I had seen it recommended in a blog post on best domain names for 2023 a few months ago. It was also a DNS provider that we considered at eSpark when Google discontinued Google Domains. As much as I wanted to think of something creative and catchy, I chose to use my name as the second-level domain. I chose the standard ".com" domain because it was cheapest, and it also seemed a more appropriate than using ".dev" or ".org". I explicitly decided not to use ".io" for reasons laid out in [this](https://www.beep.blog/io/) blog post that I read on HackerNews last year. After I bought the new domain name, I went to the URL I purchased, and it displayed a message that the URL had recently been purchased (by me!).

Once I purchased the domain name I went into the Settings tab of my Github repo for my personal website and looked for where to put my new domain name. I quickly saw the "Custom domain" section and eagerly put my new domain name in the text box. I knew there would have to be some sort of configuration between Namecheap and Github, but I was hoping to get a useful error message with details about what to do next. This is the error message I got back:

[![Screenshot-2024-01-06-at-08-50-12.png](https://i.postimg.cc/C130NpFT/Screenshot-2024-01-06-at-08-50-12.png)](https://postimg.cc/YGzTrVGb)

I started looking on StackOverflow to see what the CNAME configuration should be to get Namecheap to verify that I own the domain name and allow Github Pages to route to it. I found a really helpful GitHub Gist [post](https://gist.github.com/notTag/4a60598d018124c9ac4a7b1f3e2bac9a) that got me most of the way there with one minor issues, the IP addresses listed for the A records are out of date. The post links to an article on the Namecheap website, which has the updated GitHub IP addresses that are needed for the A records. After I got that configured I went back to GitHub Pages and I thought I had everything setup correctly, but I was still seeing the error above, but this time I was also seeing a new message about TLS certificate provisioning:

[![Screenshot-2024-01-06-at-09-01-52.png](https://i.postimg.cc/FHNTLCXP/Screenshot-2024-01-06-at-09-01-52.png)](https://postimg.cc/crk7qmHY)

The TLS certificate is a certificate proving that a person or business owns a domain, so I knew I was getting closer. I went on StackOverflow to try to figure out if anything else was missing, and someone commented about how it sometimes takes time for DNS changes to propogate. I verified that my GitHub pages website was now being hosted on my domain, just not on HTTPS yet. I waited for a bit and went back to check that the TLS certificate verification was complete. Once that was done (about 30 minutes), I refreshed the page, and the DNS error I was seeing before was resolved:

[![Screenshot-2024-01-06-at-09-18-37.png](https://i.postimg.cc/QCPHrykj/Screenshot-2024-01-06-at-09-18-37.png)](https://postimg.cc/YL6p68sP)

After the TLS cert was verified, I was able to recheck the "Enforce HTTPS" checkbox again. I reloaded my webpage, and this time it was on HTTPS. Everything looks good and the whole process was quick and (mostly) painless.