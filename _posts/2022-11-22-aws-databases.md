---
layout: post
title: Fighting analysis paralysis with AWS database services
subtitle: A starting point for choosing a service that fits your use case
cover-img: /assets/img/watch_hill_boats.jpg
thumbnail-img: /assets/img/watch_hill_boats.jpg
share-img: /assets/img/watch_hill_boats.jpg
tags: [databases, aws]
---

AWS offers a wide variety of database services that can feel overwhelming when you are trying to find a service that best suits your use case. I can attest to this because there have been times when I'm looking for a database service to support one of my projects or just looking to see what other options are out there, and I feel completely overwhelmed and confused by the choices. In this post I'm going to lay out many of the database services that Amazon supports, as well as when to use them.

## Knowing your data
In order to choose a database service that best supports your application needs, you have to have an idea of what the data will look like and how they will relate to one another. Here are some different directions to start in depending on what types of data you're working with:
* analytics / big data : this is probably best suited for a columnar data store like Redshift
* transactional data : this could be something like an online shop where we are storing order data, and this would probably be best for a relational data store
* semi-structured/ unstructured data : if the structure of the data is unpredictable, it would probably make the most sense to choose a NoSQL database
* time series data : if you have a device getting constant temperature readings for instance, then you'll likely want to go with a time series data store
* relationship data : graph databases could be really useful for maintaining relationships between objects

These are just a handful of use cases and scenarios, but the point is you need to have a general understanding of what the data will look like and what you're planning to do with them before deciding on which database service to use.

## Relational (OLTP) databases
Traditionally, relational databases are used for transaction type data, which is really just recording data from something that happened at a point in time, like an online purchase. We want the queries that we write against this type of data to be relatively simple and straightforward because it's a lot more costly to write analytical queries on relational databases. For relational databases, Amazon provides a service called RDS, which allows you to provision a database with one of six different database engine types:
* Amazon Aurora
* MySQL
* MariaDB
* PostgreSQL
* Oracle
* Microsoft SQL Server

You can also choose the engine version you want. One of the best features with using RDS is the option to deploy the database instance into multiple availability zones. You'll see this in the "Availability and durability" section when creating a new database. If you choose this option, AWS will create an exact copy of your database in another availability zone, and handle the replication and fail over for you in the case of an emergency. It's important to note that multi-AZ database instances do not increase performance, they're just for disaster recovery. You can't even run things off the secondary instance if the primary is active.

### Amazon Aurora
I wanted to highlight Amazon Aurora, which is Amazon's proprietary database, and it's a MySQL and PostgreSQL compatible database engine. When you go to create an Aurora database instance, you have to select whether you want your instance to use the MySQL or PostgreSQL compatible database engine. Aurora gets much better performance than the native MySQL or PostgreSQL database engines at a lower price point. Aurora has automatic backups by default, and it automatically stores 2 copies of your data across 3 different availability zones, so 6 copies in total! It also provides other features like snapshots, replication, and autoscaling.

#### Aurora Serverless
Aurora Serverless is the autoscaling feature that you can enable on your Aurora instance upon creation. Basically it allows your instance to auto scale on demand when there spikes in the workload.

## Analytics (OLAP) databases
Columnar databases like Amazon Redshift are typically the best option for analytics and data warehousing. Redshift is capable of processing large, complex queries and storing large quantities of data. I'm not going to spend too much time on Redshift because I intend to dive into it deeper in another post.

## NoSQL databases
As I mentioned above, NoSQL databases are good when the data are either unstructured or semi-structured. Amazon has a couple different options for NoSQL databases. 

### DynamoDB
The first and most obvious choice is DynamoDB. Similar to Aurora, DynamoDB is Amazon's proprietary, fully managed, NoSQL database. The data in the tables are stored across 3 different data centers, and it supports eventual consistency reads, which means that the data will be consistent across all copies of the table usually within a second or less.

#### DynamoDB Transactions
Another interesting feature of DynamoDB are these things called "DynamoDB Transactions", basically allowing you to group SQL transaction statements together and execute them in one transaction such that they are either all successful, or the whole transaction is rolled back. This is often used when there are "ACID" requirements i.e. the data must be atomic, consistent, isolated and durable.

#### DynamoDB DAX
Amazon offers an enhancement to DynamoDB called "DynamoDB DAX". DAX is an in-memory cache that sits between your application and your DynamoDB instance to reduce request time and improve performance.

### MongoDB via Amazon DocumentDB
Another way to use NoSQL on AWS would be to use MongoDB through the Amazon DocumentDB service. This allows you to run MongoDB workloads on AWS, without having to manage the service or worry about things like backups and operational overhead. This is definitely not as sleek as DynamoDB, so I would definitely opt for using that if possible.

## More obscure choices
There are a couple more services that have pretty specific use cases, that would also work depending on what kind of data you have and what you're looking to do with it.

### Apache Cassandra workloads with AWS Keyspaces
Keyspaces is used for running Apache Cassandra workloads. This is typically used for big data services, and you only pay for what you use.

### Creating Graph databases in AWS Neptune
Neptune is Amazon's fully managed Graph database that allows you to structure and maintain connections between objects.

### Maintaining ledger databases in AWS Quantum Ledger Database (QLDB)
These are Amazon's fully managed ledger databases that are immutable, meaning once data has been written to the database, it cannot be modified. These databases provide a transaction log, and they are often used in projects that have a lot of regulatory requirements like cryptocurrencies.

### Time series data with AWS Timestream
This is a fully managed, serverless data store in AWS that allows you to easily store and analyze time series data. It provides auto scaling capabilities, and the data are always encrypted.

There are even more services that interact with data on AWS, and no doubt they will continue to add more, but this is a good starting point for what database services are available on AWS.

Photo: Watch Hill, RI