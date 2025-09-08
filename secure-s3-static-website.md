

# Host a Website on Amazon S3



**Author:** David Brown  
**Email:** engr.davidb@gmail.com  

---

![Image](http://learn.nextwork.org/thankful_red_mysterious_otter/uploads/aws-host-a-website-on-s3_5d4474f9)

---

## Introducing Today's Project!

In this project, I used **Amazon S3 (Simple Storage Service)** to host a static website.

### Tools and Concepts
Services I used included Amazon S3. Key concepts I learned include:  
- Bucket policies  
- Uploading static website files  
- **index.html**  
- Bucket endpoint URLs  
- ACLs (Access Control Lists) and how they control access to bucket objects  

### Project Reflection
This project took me approximately **1 hour**. The most challenging part was resolving the **403 Forbidden error**. The most rewarding part was seeing my website work successfully.  

---

## How I Set Up an S3 Bucket

Creating an S3 bucket took me **less than 2 minutes**. The prompts were straightforward and easy to follow.  

The Region I picked for my S3 bucket was **N. California**, because it is the closest region to me. It is best practice to pick the closest region because it reduces latency (time to retrieve data) and lowers costs.  

S3 bucket names are **globally unique**! This means no two Amazon S3 buckets in the entire world can share the same name, regardless of region or account ID.  

![Image](http://learn.nextwork.org/thankful_red_mysterious_otter/uploads/aws-host-a-website-on-s3_ba6d42ad)

---

## Upload Website Files to S3

### index.html and Image Assets
I uploaded two files to my S3 bucket:  
- An **index.html** file (this determines the structure of the website)  
- A folder of **images and assets**  

Both are necessary: index.html defines the website’s structure, while the assets folder supplies the images and content displayed on the site.  

![Image](http://learn.nextwork.org/thankful_red_mysterious_otter/uploads/aws-host-a-website-on-s3_a265af88)

---

## Static Website Hosting on S3

Website hosting means placing website files on a web server, which is designed to turn those files into a website people can visit.  

To enable static website hosting in my S3 bucket, I went into the **Properties** tab, enabled static website hosting, and labeled **index.html** as my index document.  

An **ACL (Access Control List)** is a way to configure permissions inside a bucket. I enabled ACLs so that I could control access to my website files later.  

![Image](http://learn.nextwork.org/thankful_red_mysterious_otter/uploads/aws-host-a-website-on-s3_c22c54c0)

---

## Bucket Endpoints

Once static website hosting is enabled, S3 generates a **bucket endpoint URL**, which is the public link to your hosted website.  

When I first visited the bucket endpoint URL, I saw a **403 Forbidden error**.  
The reason: objects in a bucket are private by default. Even though I disabled *Block Public Access*, the website files themselves were still private. I needed to update their access settings separately to make them public.  

![Image](http://learn.nextwork.org/thankful_red_mysterious_otter/uploads/aws-host-a-website-on-s3_22ce4daf)

---

## Success!

To resolve the **403 Forbidden error**, I updated the access settings of the files inside my bucket. Using ACLs, I made my bucket’s files public. Once I checked the bucket endpoint, I could verify that my website was working correctly.  

![Image](http://learn.nextwork.org/thankful_red_mysterious_otter/uploads/aws-host-a-website-on-s3_5d4474f9)

---

## Bucket Policies

An alternative to ACLs are **bucket policies**, which define rules for what actions are (or aren’t) allowed.  

The benefit of using bucket policies is greater control of permissions across the entire bucket, while ACLs are useful for controlling access to individual objects.  

For example, my bucket policy denies everyone the ability to delete the **index.html** file. I tested this by trying to delete it and received a “Permission Denied” error, proving the policy worked.  

![Image](http://learn.nextwork.org/thankful_red_mysterious_otter/uploads/aws-host-a-website-on-s3_sm2sm2sm)
