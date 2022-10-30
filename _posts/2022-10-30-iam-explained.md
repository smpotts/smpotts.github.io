---
layout: post
title: AWS Identity Access Management (IAM) Explained 
subtitle: Breaking down the different components
cover-img: /assets/img/steamboat.jpeg
thumbnail-img: /assets/img/steamboat.jpeg
share-img: /assets/img/steamboat.jpeg
tags: [aws_iam, permissions]
---

I'm currently studying for the AWS Solutions Architect Associate exam and I realized I didn't understand AWS Identity Access Management (IAM) as well as I thought, despite taking the AWS Cloud Practitioner exam a few years ago. It is really important to have a good understanding of IAM because it is the backbone of security in the AWS cloud. After finally getting a good grasp on the different pieces, I thought what better way to reinforce the things I have learned about IAM than to break down the different components and what they are used for.

## What's IAM?
At a very high level, IAM is a service in the Amazon cloud that is responsible for managing users and services, and their level of access. IAM allows you to create groups, define permissions for the groups, and assign users to groups, so you don't have to manage permissions at the individual level. It also allows you to define permissions for how one AWS service and interact with another through the use of roles.

## The Components of IAM
Here is the breakdown of the different components that make up IAM.

### Users
A user is a physical person who has access to interact with AWS in some capacity. The user should have just enough access to do what they need to do in AWS and nothing more, which AWS calls the "Principal of Least Privilege".

### Groups
Users are assigned to groups based on what their job function/ access levels should be. For instance, "developers" could be a group with users who are developers, and the group would get assigned permissions to allow developers to be able to work in AWS. Then you might have another group called "finance", which pertains to individuals who need access to the AWS billing services and whatnot. 

### Policy Documents
Policies are the thing we use to actually assign the permissions. A policy document is a JSON file that defines the rules of the policy. For example, the policy summary for the AWS managed policy "AmazonS3FullAccess" looks like this:
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:*",
                "s3-object-lambda:*"
            ],
            "Resource": "*"
        }
    ]
}
```
This policy allows full access permissions to S3 and S3 Object Lambda. Policies can be applied to users, groups and roles.

#### Managed Policies
There are hundreds of predefined AWS managed policies for all the different services, that you can use depending on your use cases. You can also create customer managed policies that are more customized policy documents, and then assign the policies to users, groups and roles. 

#### Inline Policies
This is one of the IAM pieces that has tripped me up in the past. Inline policies are assigned at the individual user or group level, meaning there is a 1 to 1 relationship between the policy and the user or group. This means that you cannot apply this policy to other users, groups and roles, it is specifically for the one user/ group it has been assigned to. Typically, these are not recommended.

### Roles
This is the other IAM piece that I have had a hard time conceptualizing because it seems so similar to the other components of IAM and the explanations in the AWS docs feel very prolix. Basically, roles are used to give one part of AWS access to another part of AWS. This makes sense in the case where you want to give one AWS service like EC2 access to another service like AWS MSK. I think the part that is harder to grasp is that users and groups can also be assigned roles, which can be assigned temporarily or permanently. I suppose a use case for roles could be where you have a small subset of developers who are working on a new project and need access to customer data stored in S3. You don't want ALL the developers in the "developers" group to have this level of access, only a subset of users for a fixed amount of time, so you could create a role and assign it to the specific developers who need access.

Understanding these different aspects of IAM and how they relate to each other makes it easier to use IAM cleanly and effectively.

Photo: Steamboat Springs, CO