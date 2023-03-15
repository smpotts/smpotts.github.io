---
layout: post
title: A comprehensive overview of VPCs
subtitle: The basic components, and their relationships
cover-img: /assets/img/taos.jpg
thumbnail-img: /assets/img/taos.jpg
share-img: /assets/img/taos.jpg
tags: [aws, vpcs, networking]
---

One of the hardest pieces of AWS to digest for me is the VPC/ Networking section. I didn't take any Networking classes in college, and I don't have a ton of experience working on networking in different jobs I've had so far which makes it more challenging. I've had to go through the VPC section of the [A Cloud Guru](https://acloudguru.com/) course I'm taking to study for the AWS Solutions Architect Associate exam twice, and after the second pass, I wanted to go over the high level VPC components and how they fit together.

## VPCs
The virtual private cloud (VPC), is the outer most, all encompassing part of the networking architecture in the cloud. It is deployed in a single region, and as A Cloud Guru refers to it, "like a virtual data center in the cloud". It's logically isolated from the rest of the cloud, and it gives you full control over the network.

When you create a VPC, it gives you three things: a main Route table, a main Network ACL, and a security group. I'm going to dive a little deeper into each one.

### Route Tables (also referred to as the Router)
Paraphrasing from the [AWS site](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Route_Tables.html) on VPC Routing tables, a route table contains a set of rules for how it should route traffic. 

### Network ACLs
The next component we encounter in the VPC after the Route table is the Network ACL. The AWS docs have a great diagram on [this](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html) page describing Network ACLs. To paraphrase the docs again, the Network ACLs define the inbound and outbound rules for a subnet.

### Security Groups
Security groups are basically virtual firewalls, and they contain a list of inbound and outbound traffic rules. To paraphrase, the [AWS docs](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html) define a security group as a way to control traffic to and from resources.

### Subnets
According to the [AWS docs](https://docs.aws.amazon.com/vpc/latest/userguide/configure-subnets.html), as subnet "is a range of IP addresses in your VPC. You can launch AWS resources into your subnets." I've been thinking about subnets as isolated sub-sections of the cloud that we can put resources inside, which I guess is still valid. I think I've conceptualized it this way because we often have a public subnet where things that need to communicate with the outside internet would live. Then the private internet would house things like the backend database, that we do not want to be reachable by the internet. Another thing to note is that subnets are only associated with one availability zone.

#### CIDR Blocks
When I first read about the CIDR block range it completely blew my mind, and it made no sense, but the more I mull it over, the more I get it. Subnets are creating these "sub-sections" of the cloud (to continue with the analogy I've been thinking of) by defining IP address ranges. The way we define an IP address range is with CIDR blocks.

#### Security Groups in Subnets
From what I've gathered, subnets usually have a security group inside them. There may be scenarios where that's not necessary, but that's what I've seen so far. I think this is because resources like EC2 instances are typically deployed in the subnet, and they also need to be associated with a security group.

### Internet Gateways
The next component of the VPC is the Internet Gateway which is the mechanism that allows the VPC to access the public internet. This association is set up through the Route table to the public subnet.

### NAT Gateways
NAT (Network Address Translation) Gateways allow the private subnets within the VPC to access the public internet and other resources outside the subnet, without allowing access in from the internet. This requires configuration in the Route table to provide additional access. NAT Gateways are not associated with security groups, and they need to be deployed in the public subnet. 

There are several other important services within the VPC/ Networking orbit, but these are the core components I've come across and how they relate to each other.

Photo: outside of Taos, NM