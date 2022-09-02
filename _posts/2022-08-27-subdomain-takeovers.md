---
layout: post
title: Subdomains 101 and Subdomain Takeovers
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
Here is the general concept of a subdomain takeover. Say for example, I have a domain like "www.shelbylikescoffee.com", and then I create a subdomain "shop.shelbylikescoffee.com" where I have a separate section of the website specifically for selling merchandise. Then after some time I decide I don't want the online store, and I take down the hosted content but, forget to remove the subdomain DNS entry. Leaving the subdomain accessible and not having hosted content, makes my site vulnerable to a type of cyber attack called a "subdomain takeover". With a subdomain takeover, a hacker could take control over this subdomain and serve their own, malicious content to it, while the users think they are still accessing content related to my site. Given the potential for this type of attack, it's really important to stay on top of the subdomain DNS entries associated with your site and remove any that are not being used.

Photo: Fairbanks, AK