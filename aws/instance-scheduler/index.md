---
author:
    name: Paradox
    avatar: /paradox.jpg
    email: s.samarthkulkarni@gmail.com
    link: https://github.com/ParadoxInfinite/
date: 2022-10-19T01:40
categories: [aws, ec2, guides, instance-scheduler]
title: Instance Scheduler
description: Guide to setup Instance scheduler to schedule your EC2 hours
image: /imgs/aws.jpg
---
# Instance Scheduler

![](/imgs/aws-instance-scheduler.png)

<br/>
Setting up AWS Instance Scheduler to save EC2 instance costs for your dev/uat servers.
<br/><br/>

## Use Case
When you have EC2 instances which are running when not needed (outside of work hours, on holidays, etc.) and billing you for it, Instance Scheduler will help you cut down on these costs by reducing the uptime of the server instance by shutting it down with a schedule but also conveniently bringing it back when needed (as scheduled).

## Instructions

!!!danger Disclaimer
This guide is correct and up to date only as of the publishing date. AWS have the rights to change features regarding this or change the pricing on their platform. I am not responsible for their actions, use the guide mainly as a reference but check their website and documentation for the updated details.
!!!

!!! Special Thanks
THanks to DeshDeepakDhobi (DD) for his guide over on [Medium](https://medium.com/@deshdeepakdhobi/aws-instance-scheduler-start-stop-ec2-and-rds-instances-automatically-641cfe4786ac) which I used as a base to this guide. Some of the details seem a bit confusing and incomplete on his guide as well as the screenshots are a bit outdated, thus this new guide.
!!!

### Set up Instance Scheduler in CloudFormation
>>>Head over to the [AWS Instance Scheduler Page](https://aws.amazon.com/solutions/implementations/instance-scheduler/) and click on the `Launch in the AWS Console` option.
!!!warning Region Check
Ensure you're on the correct region or you will end up creating the job in the wrong region.
!!!
On that page, you could change any options you want, but we'll keep the defaults and click Next.
>>>In `Specify Stack Details` page, give your CloudFormation Stack a name like `dev-server-scheduler`, and your Instance Scheduler a tag name like `dev-scheduler`. Set the default time zone to your time zone, this would help you avoid converting times later.
- `Frequency` depends on what you would schedule your timtings as. If you're doing something like 08:00 to 18:00, then I think a 60 minute frequency is good enough.
- You could enable CloudWatch logs and metrics if you need. Do add `Started tags` and `Stopped tags`, this would help you differentiate between Manual starts of the instance vs Instance Scheduler's.<br/><br/>

>>>In `Configure stack options` page, I decided to keep everything default, you could add a role, if you already have or need something specific, for CloudFormation to use, but it'll create it's own role if you keep it empty.
>>>In the next page, just verify details and acknowledge the role creation for CloudFormation and it'll start creation of your CloudFormation Stack.
>>>Wait till the status turns to `CREATE_COMPLETE` like in the image. ![](/imgs/aws-instance-scheduler-status.png)
>>>

### DynamoDB Setup
>>>Head over to DynamoDB and click on the `Tables` option in the left sidebar.
>>>In the list, find the table which as `ConfigTable` in the name. Open that table and click on the `Explore table items` button.
>>>In the table, you'll find multiple `period` and `schedules`. We'll use the `seattle-office-hours` schedule and `office-hours` period for our purpose.
>>>Change the options inside the `office-hours` period as per the image, you can edit the timings and weekdays as you need.<br/>![|700](/imgs/aws-instance-scheduler-dynamo-db-period.png)
>>>Change the options inside the `seattle-office-hours` schedule as per the image, while changing the name, description, and timezone as you need.<br/>![|700](/imgs/aws-instance-scheduler-dynamo-db-schedule.png)
>>>

### EC2 Tags
>>>Once this is done, head over to EC2 and inside your instance, go to `Actions > Instance Settings > Manage Tags`.
>>>You'll need to add a couple of tags here as per the image, but ensure to change the names as per your setup from previous steps.
![](/imgs/aws-instance-scheduler-ec2-tags.png)
Note: The tag key should be the same name as the CloudFormation Stack for the instance scheduler. The tag key for my setup is `dev-scheduler`
>>>Save the tags.
>>>

### Testing
>>>Just check the instance state outside work hours to ensure it is stopped and during the next day, your instance starts up automatically.
>>>As the instance is stopping, some of your services might not boot up automatically upon restart of the instance, add them to your startup script. This would depend for each of the service you want to start. Some services might give you a startup script/command, so do check them out.
>>>

Enjoy saving $$$, cheers!

![|350](/imgs/congration.jpg)