<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Cloud Security with AWS IAM

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-security-iam)

**Author:** Bao Luong  
**Email:** baodevops21@gmail.com

---

![Image](http://learn.nextwork.org/stimulated_brown_festive_kaffir_lime/uploads/aws-security-iam_1c864649)

---

## Introducing Today's Project!

In this project, I will demonstrate how to use AWS IAM to controll access and permission settings in our AWS account. I'm doing this project to learn about access permission and cloud seucrity. 

### Tools and concepts

Services I used were Amazon EC2, AWS IAM, and IAM policy simulator.  

Key concepts I learnt include IAM users, groups, account alias, policies, testing permission level of another account, and modifying JSON permission policy. 

### Project reflection

This project took me approximately an hour. The most challenging part was understanding the IAM policy that was written in JSON and it contained multiple statements. It was most rewarding to see permission denied when the intern account was unable to delete any resources or instances in the production instance. The IAM access management worked!

---

## Tags

Tags are organizational tools that let's us label our resources. Tags are helpful for grouping resources, cost allocation and applying policies for all resources of the same tag. 

The tag I’ve used on my EC2 instances is called Env, which stands for environment. The value I’ve assigned for my instances are production and environment. 

![Image](http://learn.nextwork.org/stimulated_brown_festive_kaffir_lime/uploads/aws-security-iam_2e0e5a5d)

---

## IAM Policies

IAM Policies are like rules that determine who can do what in our AWS account. I'm using policies to control who has access to our production env instance. 

### The policy I set up

For this project, I’ve set up a policy using JSON.

I’ve created a policy that allows the policy holder to have permission to have access and work with any instances that are tagged with "development". They can also read any information on any instances but are denied to creating/deleting instances. 

### When creating a JSON policy, you have to define its Effect, Action and Resource.

The Effect, Action, and Resource attributes of a JSON policy means either Allow or Deny - to indicate whether the policy allows or denies a certain action (i.e Effect); ‍a list of the actions that the policy allows or denies (i.e. Action); and which resources does this policy apply to (i.e. Resource). 

---

## My JSON Policy

![Image](http://learn.nextwork.org/stimulated_brown_festive_kaffir_lime/uploads/aws-security-iam_1c864649)

---

## Account Alias

An account alias is a nickname for our AWS account instead of a accountID. 

Creating an account alias took me 15 seconds. Now, my new AWS console sign-in URL is https://baodevops21.signin.aws.amazon.com/console

![Image](http://learn.nextwork.org/stimulated_brown_festive_kaffir_lime/uploads/aws-security-iam_0eb4439b)

---

## IAM Users and User Groups

### Users

IAM users are people or entities that have access/can login to our AWS account.

### User Groups

IAM user groups are like folders that collect IAM users so that apply permission settings at the group level. 

I attached the policy I created to this user group, which means any user created inside this group will automatically get the persmissions attached to our NextWorkDevEnvironmentPolicy IAM policy. 

---

## Logging in as an IAM User

The first way is email sign-in instructions to the user. while the second way is to download a .csv file with the sing on details inside. 

Once I logged in as my IAM user, I noticed that our user is already denied access to panels on the main AWS console dashboard. This was because I only set up permissions to our development EC2 instance, so our intern wouldn't have access to even see anything else. 

![Image](http://learn.nextwork.org/stimulated_brown_festive_kaffir_lime/uploads/aws-security-iam_6f2ab446)

---

## Testing IAM Policies

I tested my JSON IAM policy by attempting to stop both the development and the production instances. 

### Stopping the production instance

When I tried to stop the production instance, but it prompted an error page. This was because our production instance is tagged with the "production" label, which is outside of the scope of our permission policy - interns are only allowed to do things in the development instances. 

![Image](http://learn.nextwork.org/stimulated_brown_festive_kaffir_lime/uploads/aws-security-iam_0e7a9d6a)

---

## Testing IAM Policies

### Stopping the development instance

Next, when I tried to stop the development instance by attempting to stop both the development instances, I successfully saw the instance state change to Stopping and then Starting. This was because the permission policy allows the intern (the network-dev-group) to stop instances.

![Image](http://learn.nextwork.org/stimulated_brown_festive_kaffir_lime/uploads/aws-security-iam_1811801c)

---

## The IAM Policy Simulator

The IAM Policy Simulator is a tool that simulates actions and test permission settings by defining a specifc user/group/role and the action we want to test for. It's useful for saving time when testing permission settings. 

### How I used the simulator

I set up a simulation for testing the permission for whether the dev group can Stopinstances or DeleteTags. The results were denied for both, I had to adjust the scope of the EC2 instances that are tagged with "development". Once the tag was applied the permission was allowed. 

![Image](http://learn.nextwork.org/stimulated_brown_festive_kaffir_lime/uploads/aws-security-iam_069d8a621)

---

---
