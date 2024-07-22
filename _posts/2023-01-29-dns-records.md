---
layout: post
title: DNS Record Types 
subtitle: Understand the most common record types and how they are used
cover-img: /assets/img/tracy_city.jpeg
thumbnail-img: /assets/img/tracy_city.jpeg
share-img: /assets/img/tracy_city.jpeg
tags: [aws, dns, dns_records]
---

I recently went through the Route 53 section of the study materials for the AWS Certified Solution Architect Associate exam and realized I have never fully understood the different DNS record types. I have made some minor changes to DNS records at work, but admittedly, I didn't completely understand what I was changing. I want to break down the definitions of some of the most common DNS records and what they are used for.

## The SOA Record
The abbreviation SOA stands for "start of authority", and this record contains a lot of important information about the domain. The SOA record contains additional "metadata" fields that have information about who the domain is registered to, the primary server for the zone, retry limits, expiration limits, how many times the SOA record has been edited, etc.

One thing I got confused about when reading more about the is the concept of a 'zone'. A [DNS post](https://www.cloudflare.com/learning/dns/dns-records/dns-soa-record/) on CloudFlare's website describes a zone as "an area of control over a namespace. A zone can include a single domain name, one domain and many subdomains, or many domain names". I think of 'zone' as the area that is being covered by the domain.

## The A Record
The "A" in an A record stands for address. A records are the most commonly used DNS records, and they are used to map the domain name of the website to the IP address of the server hosting the site. You can also setup A records for subdomains to point to other IP addresses. 

## CNAME
CNAME stands for "canonical name". CNAME records are used to map the alias of a domain to another domain name. According to [CloudFlare](https://www.cloudflare.com/learning/dns/dns-records/dns-cname-record/), this is common when a website has subdomains that we want to point back to the root domain for maintenance purposes, etc.

There are a lot more DNS record types out there, but there are the ones I have seen the most and have a great general understanding of now.
