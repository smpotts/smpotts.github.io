---
layout: post
title: S3 Tricks and Treats 
subtitle: Even better than Halloween candy 
cover-img: /assets/img/mosaic.jpg
thumbnail-img: /assets/img/pumpkin.jpeg
share-img: /assets/img/mosaic.jpg
tags: [s3, aws]
---

It's Halloween and what better way to spend it than reading about all the great tricks and treats in AWS S3! Here are some cool features and little hacks that can be used to enhance your experience with Amazon S3.

#### 1. S3 can be used to host static website
S3 can be used to host very basic, static websites. This is super simple to configure and has the benefits of being very cost effective and being auto scalable (since S3 scales automatically).

#### 2. You can use versioning as a backup
Versioning allows you to store multiple versions of your S3 buckets. Once you enable versioning on a bucket it can't be removed, it can only be suspended. This is nice because you don't have to worry about losing previous versions of your objects and when you delete an object with versioning enabled, it just puts a delete marker on the file and does not full delete the file until you delete the object with the delete marker.

#### 3. Lifecycle Management can be used to save money on infrequently accessed objects
For objects that you don't anticipate accessing after certain periods of time, you can utilize S3's Lifecycle Management. This couples really well with versioning so that you can move older versions to cheaper storage tiers if you don't anticipate needing them. Lifecycle Management allows you to set up transitions where you define the amount of time you want to wait before transitioning the object, and then which storage tier to move the object to.

#### 4. The more folders and subfolders in our bucket, the better performance we can get
This may seem counterintuitive, but you can actually get better performance on PUTs, COPYs, POSTs and DELETEs when you have more, highly specified folders within a bucket.

#### 5. You can parallelize uploads and downloads
If you run into a case where you need to upload or download large objects from S3, you can use multipart uploads for S3 and byte-range fetches for downloads. Not only does this take less time, but it also makes life easier if there is a failure during the upload/ download because you only need to rerun the part that failed.