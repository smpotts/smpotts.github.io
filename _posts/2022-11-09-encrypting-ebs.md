---
layout: post
title: Encrypting an EBS Volume
subtitle: Steps to make an unencrypted volume, encrypted
cover-img: /assets/img/nola_building.jpeg
thumbnail-img: /assets/img/nola_building.jpeg
share-img: /assets/img/nola_building.jpeg
tags: [ebs, aws, ec2, encryption, snapshots]
---

I covered some different features of Amazon Elastic Block Storage (EBS) in the last post, and I lightly touched on the encryption option that you are presented with when creating a new EBS volume. The interesting thing is if you create an EBS volume that is unencrypted, you can't simply go back into the settings and check encrypted. You have to create a snapshot of the unencrypted volume, an encrypted copy of that, create an AMI from the snapshot, and then create a new encrypted instance. As a good exercise in kinetic learning, I'm going to step through how to do that.

### Create an unencrypted volume
The first thing to do is start with an unencrypted EC2 instance and we do that by launching a new instance. We can leave all the settings as is, ignoring the check box for encryption in the Storage section, which will attach an unencrypted EBS volume to our instance.

[![Screen-Shot-2022-11-08-at-7-09-48-PM.png](https://i.postimg.cc/HLfK0mc1/Screen-Shot-2022-11-08-at-7-09-48-PM.png)](https://postimg.cc/Mcmdxhm9)

Navigate to the Volumes tab under Elastic Block Storage, and you will see an unencrypted EBS volume associated with the EC2 instance that was just created.

### Create an unencrypted snapshot of the unencrypted volume
The next thing to do is create a snapshot of the unencrypted EBS volume. To do this, click on the instance and go to Action, then Create snapshot.

[![Screen-Shot-2022-11-08-at-6-45-11-PM.png](https://i.postimg.cc/QN9KzbWN/Screen-Shot-2022-11-08-at-6-45-11-PM.png)](https://postimg.cc/4nG37p5j)

Give the snapshot a name and notice it is unencrypted, and that cannot be changed. Go ahead and create the snapshot.

[![Screen-Shot-2022-11-08-at-6-46-04-PM.png](https://i.postimg.cc/52Nxh4k5/Screen-Shot-2022-11-08-at-6-46-04-PM.png)](https://postimg.cc/WhCLrvVt)

### Copying the unencrypted snapshot
Once the snapshot status is "Completed", we want to go to Actions and click "Copy snapshot".

[![Screen-Shot-2022-11-08-at-7-19-19-PM.png](https://i.postimg.cc/kXg2PPGm/Screen-Shot-2022-11-08-at-7-19-19-PM.png)](https://postimg.cc/BtRS2y2Y)

Now you can see the option to encrypt the copy of the snapshot, so check the Encryption box and we can leave the rest of the encryption details to the default settings.

[![Screen-Shot-2022-11-08-at-7-19-29-PM.png](https://i.postimg.cc/FK5FRMr1/Screen-Shot-2022-11-08-at-7-19-29-PM.png)](https://postimg.cc/VJgPZHbc)

We now have an unencrypted EBS volume and an encrypted copy of the EBS volume.

### Creating an AMI and launching an encrypted EC2 instance
The next step is click on the encrypted snapshot, go to Actions and click "Create image from snapshot".

[![Screen-Shot-2022-11-08-at-7-28-50-PM.png](https://i.postimg.cc/1t1LDS2V/Screen-Shot-2022-11-08-at-7-28-50-PM.png)](https://postimg.cc/rdgnLB8q)

This will create an Amazon Machine Image (AMI), which can then be used to create an EC2 instance. Under AMIs, click on the AMI created from the snapshot and click "Launch Instance from AMI". Choose the same settings as the original EC2 instance and click "Create instance". This creates a new encrypted EC2 instance that is an exact copy of the unencrypted instance.

Photo: New Orleans, LA
