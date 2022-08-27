---
layout: post
title: Subdomain Takeovers for Kindergarteners
subtitle: A few things I learned about DNS, Subdomains and Subdomain Takeovers 
cover-img: /assets/img/alaska.jpeg
thumbnail-img: /assets/img/alaska.jpeg
share-img: /assets/img/alaska.jpeg
tags: [dns, subdomain_takeovers]
---

I recently learned about the risk of subdomain takeovers and found the issue both fascinating and terrifying. I haven't done a ton of network related work in my career, so it's something I'm actively trying to learn more about and get experience with. I still have a lot more to research on subdomain takeovers, but I wanted to briefly touch on some things that I learned while diving into this issue further.

### DNS 101
DNS stands for Domain Name System, and it's basically the translation between the human readable URL that we type into the browser like "www.google.com", and the IP addresses on the backend that serve up content for the website. A domain name has a few different components:
1. Top-level domains: using "www.google.com" as the example, the top-level domain refers to the extension part of the URL, in this case ".com"
2. Second-level domains: this is the unique name part of the URL, so for this example it would be "google"
3. Subdomains: I learned that "www" is actually a subdomain. On other sites you might see a URL that has "shop" or "blog" for the subdomain instead of "www"

### Subdomains
A subdomain is a way to separate or organize content within a domain. It could be used to have a separate section for a blog or an online shop. A good example of this is how Github Pages uses subdomains to allow users to host static websites on the Github domain. Github's domain is "www.github.com", but users can utilize a subdomain and host their own site as "username.github.io".

### Subdomain Takeovers
Like I said I'm not a networking expert, but here is the general concept of a subdomain takeover. Say I have a domain like "www.shelbylikescoffee.com" (just throwing something out there, it's not a real website!) and then I wanted to create a subdomain "shop.shelbylikescoffee.com" where people could buy cool merch. Maybe I create the online store, but then take it down, or forget to do anything with it at all, but the subdomain exists, and it's reachable. With a subdomain takeover, a hacker could utilize this subdomain and server malicious content to it, meanwhile, users think they are still using my website because technically they still are. Given the potential for this type of attack, it's really important to remove subdomains that are not being used.

I find this topic very intriguing, and I plan on doing more research about subdomain takeovers and learn more about prevention methods.


