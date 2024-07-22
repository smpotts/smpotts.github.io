---
layout: post
title: Connecting VPCs to other networks and services
subtitle: A quick run through of services that are useful to know about VPCs
cover-img: /assets/img/abq_balloon.jpeg
thumbnail-img: /assets/img/abq_balloon.jpeg
share-img: /assets/img/abq_balloon.jpeg
tags: [aws, vpcs, networking]
---

There are a handful of more complex VPC services that I left out in my previous post about VPCs, so I wanted to run through them to check my understanding.

## Direct Connect
[Direct Connect](https://docs.aws.amazon.com/whitepapers/latest/aws-vpc-connectivity-options/aws-direct-connect.html) allows you to connect your on-prem data center to AWS with a private, stable, and high throughput connection. This is a much better alternative than trying to use VPN which could drop connection or experience latency issues.

## VPC Peering
VPC Peering allows you to create a connection between two of your VPCs using private IP addresses. Having this connection between the two makes it seem like the VPCs are on the same network. You can use peering across different regions and accounts, but the peering connections have to be direct and 1-1. For example, if you have VPCs chained together as such: VPC A <-> VPC B <-> VPC C, VPC A and VPC C will not have a valid connection. 

## PrivateLink
PrivateLink allows you to peer 10s, 100s, or 1000s of VPCs. To paraphrase the [AWS docs](https://docs.aws.amazon.com/vpc/latest/userguide/endpoint-services-overview.html), it also allows for private connectivity between your VPC and other supported AWS services. To enable this you need to create a VPC endpoint in your VPC and point it to the target service and subnet.

### VPC Endpoints
[VPC endpoints](https://docs.aws.amazon.com/whitepapers/latest/aws-privatelink/what-are-vpc-endpoints.html) are powered by PrivateLink, and they allow you to connect your VPC to other AWS services without leaving your private network. They are the piece that is doing the connecting between one thing and another. There are two types of VPC endpoints: interface endpoints and gateway endpoints.

#### Interface Endpoints
According the the [AWS docs](https://docs.aws.amazon.com/whitepapers/latest/aws-privatelink/what-are-vpc-endpoints.html), "an interface endpoint is a collection of one or more elastic network interfaces with a private IP address". Interface endpoints support a variety of AWS services.

#### Gateway Endpoints
Gateway endpoints are a virtual device that you provision, and it only supports DynamoDB and S3.

### PrivateLink vs VPC Peering
From what I understand, VPC Peering is when connecting two VPCs together, where as PrivateLink can peer a VPC to many, many more VPCs, and allow connectivity to AWS services.

## Transit Gateway
Transit Gateway connects VPCs to on-prem networks through a centralized service. It's a way to simpify complex relationships between networking services on-prem and in the cloud, and it allows things to talk to each other directly. 

## VPN Hub
VPN Hub creates a hub and spoke model to connect multiple independent VPNs together through one centralized service. It basically aggregates the VPN connection so they can all talk directly to each other.
