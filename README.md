# CI CD Pipeline

CI CD is the blueprint to devops strategies and reason for **faster software releases**. CI/CD facilitates an effective process for getting **products to market faster**, continuously delivering code into production, and ensuring an **ongoing flow of new features and bug fixes via the most efficient delivery method.**
- In short, CI is a set of practices performed as developers are writing code, and CD is a set of practices performed after the code is completed.
- The CI/CD pipeline is part of the broader DevOps framework
- **It is the backbone of DevOps practices and automation**, It plays vital, challenging and exciting role in DevOps culture, growing numbers of companies releasing software in minutes with the adoption of CICD practices.

To put it simply, the continuous integration is part of both continuous delivery and continuous deployment. The main difference is the deployment step, in **continuous delivery the deployment is done manually** and in **continuous deployment it happens automatically**
- CI/CD exist to automate the deployments and building of software

![image](https://user-images.githubusercontent.com/104793540/187893411-61138c31-ad8b-461e-b7fa-65d00c963587.png)

## Continuous Integration (CI)
Developers merge/commit code to master branch multiple times a day, fully automated build and test process which gives feedback within few minutes, by doing so, you avoid the integration hell that usually happens when people wait for release day to merge their changes into the release branch.

## Continuous Delivery
Continuous Delivery ensures that you can release new changes to your customers quickly in a sustainable way. This means that on top of having automated your testing, you also have automated your release process and you can deploy your application at any point of time by clicking on a button. **In continuous Delivery the deployment is completed manually.**


## Continuous Deployment 
Continuous Deployment goes one step further than continuous delivery, with this practice, **every change that passes all stages of your production pipeline is released to your customers, there is no human intervention**, and only a failed test will prevent a new change to be deployed to production.

## Jenkins 

Jenkins is an open-source automation server in which the central build and CI process take place, It is a Java-based program with packages for Windows, macOS, & Linux.


## Webhook 
Webhooks are custom HTTP callbacks that you define. They are usually **triggered by an event, such as pushing code to a repository** or when a commit happens. When the event occurs, the source app makes an HTTP request to the URI configured for the webhook. The action to take may be anything. For example, you can use webhooks to:

- **Trigger continuous integration (CI) jobs, update external issue trackers, update a backup mirror, or deploy to your production server.**
- Send a notification to Slack every time a job fails.
- send sns to inform somone 
- Automatically assign labels to merge requests.


## SSH Github 
To production env via ssh (hhtp not secure)



## SSH Github to Jenkins 


## SSH-AWS-keys from Jenkins to AWS
