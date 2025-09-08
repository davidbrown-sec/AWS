
# Cloud Security with AWS IAM


**Author:** David Brown  
**Email:** rundcxl@gmail.com

---

![Image](http://learn.nextwork.org/thankful_red_mysterious_otter/uploads/aws-security-iam_1c864649)

---

## Introducing Today's Project!

In this project, I demonstrate how to use AWS Identity and Access Management (IAM) to control access and manage permission settings within an AWS account. The goal of this project is to build a strong foundation in AWS cloud security by learning the fundamentals of authentication, authorization, and least-privilege access.

### Tools and concepts

The services I used in this project were Amazon EC2 and AWS IAM. Key concepts I learned include IAM users, policies, user groups, and account aliases. I also gained hands-on experience with the IAM Policy Simulator and a deeper understanding of how JSON IAM policies work.

### Project reflection

his project took me approximately 1.5 hours including demo time. The most challenging part was understanding IAM policies written in JSON, but the most rewarding part was seeing everything come together and the policy working as intended.

---

## Tags

AWS resource tags are used to organize, secure, and manage cloud resources. Tags are key–value pairs that can identify ownership, environment, or cost center, making it easier to track usage and expenses. I also learned how tags can be applied in IAM policies to enforce least-privilege access, helping strengthen governance, automation, and overall cloud security.

I used a tag called ENV (short for Environment) on my EC2 instances. The values I assigned were Production and Development, allowing me to clearly separate and manage resources based on their environment.

![Image](http://learn.nextwork.org/thankful_red_mysterious_otter/uploads/aws-security-iam_2e0e5a5d)

---

## IAM Policies

IAM policies are rules that define who can do what within an AWS account. In this project, I used policies to control access to the production environment instance, ensuring only authorized users could interact with it.

### The policy I set up

For this project, I’ve set up a policy using json.

I created a policy that grants the policyholder full permissions on any instance tagged with “development”. The policy also allows them to view information about any instance, but explicitly denies them the ability to create or delete tags on any instance.

### When creating a JSON policy, you have to define its Effect, Action and Resource.

In a JSON IAM policy, the Effect, Action, and Resource attributes define the policy’s behavior:
	•	Effect specifies whether the policy allows or denies the action.
	•	Action defines what operations the policy permits or restricts (e.g., ec2:StartInstances).
	•	Resource identifies the specific AWS resource(s) the policy applies to.


---

## My JSON Policy

![Image](http://learn.nextwork.org/thankful_red_mysterious_otter/uploads/aws-security-iam_1c864649)

---

## Account Alias

An account alias is simply a nickname for my AWS account ID. Instead of using the long numeric ID, I can now log in and reference the account by its alias.

Creating an account alias took me less than 30 seconds and was a simple configuration in the IAM dashboard. My new AWS console sign-in URL now uses the alias instead of the numeric account ID, making it easier to remember and access.

![Image](http://learn.nextwork.org/thankful_red_mysterious_otter/uploads/aws-security-iam_0eb4439b)

---

## IAM Users and User Groups

### Users

IAM users are individual people or entities that can log in to and access your AWS account.

### User Groups

IAM user groups are like folders that organize IAM users, allowing you to apply permission settings at the group level instead of configuring each user individually.
 user groups are...

I attached the policy I created to this user group, which means any user added to the group will automatically inherit the permissions defined in the IAM policy.

---

## Logging in as an IAM User

The first option is to email sign-in instructions directly to the user. The second option is to download a CSV file that contains the user’s login details.

Once I logged in as my IAM user, I noticed that my user is already denied access to panels on the mainAWS console dashoboard. This was because we only set up pewrmissions to our developmeent EC2 instance, so my user wouldnt have access to even see anything else. 

![Image](http://learn.nextwork.org/thankful_red_mysterious_otter/uploads/aws-security-iam_6f2ab446)

---

## Testing IAM Policies

I tested my JSON IAM policy by attempting to stop both the development and production instances.

### Stopping the production instance

When I tried to stop the production instance, I received an error. This happened because the instance is tagged with the Production label, and my user is not allowed to modify resources with that tag.


![Image](http://learn.nextwork.org/thankful_red_mysterious_otter/uploads/aws-security-iam_0e7a9d6a)

---

## Testing IAM Policies

### Stopping the development instance

Next, when I tried to stop the development instance, the state successfully changed from Stopping to Stopped. This worked because the IAM policy attached to the nextwork-dev-group allows users in that group to stop development instances.

![Image](http://learn.nextwork.org/thankful_red_mysterious_otter/uploads/aws-security-iam_1811801c)

---

## The IAM Policy Simulator

The IAM Policy Simulator is a tool that allows you to simulate actions and test permission settings by selecting a specific user, group, or role and the actions you want to evaluate. It’s useful because it saves time and avoids disrupting live operations.

### How I used the simulator

I set up a simulation to check whether my dev user group had permission to StopInstances or DeleteTags. The initial results were denied for both actions. To fix this, I adjusted the policy scope so that it only applied to EC2 instances tagged with Development. After supplying that tag condition, the permissions were successfully allowed.

![Image](http://learn.nextwork.org/thankful_red_mysterious_otter/uploads/aws-security-iam_069d8a621)

---

---
