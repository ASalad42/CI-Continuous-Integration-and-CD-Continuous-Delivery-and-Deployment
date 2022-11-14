# CI/CD Pipeline

CI CD is the blueprint to devops strategies and reason for **faster software releases**. CI/CD facilitates an effective process for getting **products to market faster**, continuously delivering code into production, and ensuring an **ongoing flow of new features and bug fixes via the most efficient delivery method.**
- In short, CI is a set of practices performed as developers are writing code, and CD is a set of practices performed after the code is completed.
- The CI/CD pipeline is part of the broader DevOps framework
- **It is the backbone of DevOps practices and automation**, It plays vital, challenging and exciting role in DevOps culture, growing numbers of companies releasing software in minutes with the adoption of CICD practices.

To put it simply, the continuous integration is part of both continuous delivery and continuous deployment. The main difference is the deployment step, in **continuous delivery the deployment is done manually** and in **continuous deployment it happens automatically**
- CI/CD exist to automate the deployments and building of software

Working Diagram:

![image](https://user-images.githubusercontent.com/104793540/187963750-f3c11787-1e12-4fd6-ab3f-927099002c47.png)

## Integral Part of DevOps Lifecycle 

![image](https://user-images.githubusercontent.com/104793540/188126158-d84a579b-2683-482c-8b8a-375f62405ed0.png)

- **Continuous development**
- **Continuous integration**
- Continuous testing
- **Continuous deployment**
- Continuous monitoring
- Continuous feedback
- Continuous operations

### Tools

![image](https://user-images.githubusercontent.com/104793540/188125966-6be213fd-23cf-4847-99e2-fa1de237ee7a.png)

## Continuous Integration (CI)
Developers merge/commit code to master branch multiple times a day, fully automated build and test process which gives feedback within few minutes, by doing so, you avoid the integration hell that usually happens when people wait for release day to merge their changes into the release branch.

CI: Automation 


## Continuous Delivery
Continuous Delivery ensures that you can release new changes to your customers quickly in a sustainable way. This means that on top of having automated your testing, you also have automated your release process and you can deploy your application at any point of time by clicking on a button. **In continuous Delivery the deployment is completed manually.**


## Continuous Deployment 
Continuous Deployment goes one step further than continuous delivery, with this practice, **every change that passes all stages of your production pipeline is released to your customers, there is no human intervention**, and only a failed test will prevent a new change to be deployed to production.

## CI/CD Pipline 

![image](https://user-images.githubusercontent.com/104793540/187894786-00bf110b-5b88-4612-8e1f-fb10a230eec4.png)


### Benifts 
- Faster software releases 
- Reduce cost (less overall manual work due to automation) 
- Fault isolations 
- Robustness (increased test reliability)
- Easier updates 

## Jenkins 


Jenkins is an open-source automation server in which the central build and CI process take place, It is a Java-based program with packages for Windows, macOS, & Linux.
Build automation server > builds your jobs and automates > lots of plugins

![image](https://user-images.githubusercontent.com/104793540/187895244-e8d9c5da-eb4b-471a-b555-6b502e94b0f1.png)

### Setting up
- at dashboard > build new item 
- enter name > freestyle project 
- build now 
- click on #1 date time 
- console out

![image](https://user-images.githubusercontent.com/104793540/187897309-ebd980d2-7090-4d06-95ad-22c0bc4e850c.png)

- can configure on dashboard for specific job
- post build actions

![image](https://user-images.githubusercontent.com/104793540/187898644-a0a51831-18a3-41d4-a9e6-9d65cbe63fbb.png)

#### Linking Github & Jenkins
- generate new ssh key in ssh folder on local host
- add key.pub into github repo under repo settings > deploy key 
- move app folder to same repo 
- add private key to Jenkins 
- github project > project url > http url  
- repository url >ssh url 
- cat privatkey - begin to end - everything in that file copy over 
- credentials same as deploy key name 
- branch main 

## Webhook 
Webhooks are custom HTTP callbacks that you define. They are usually **triggered by an event, such as pushing code to a repository** or when a commit happens. When the event occurs, the source app makes an HTTP request to the URI configured for the webhook. The action to take may be anything. For example, you can use webhooks to:

- **Trigger continuous integration (CI) jobs, update external issue trackers, update a backup mirror, or deploy to your production server.**
- Send a notification to Slack every time a job fails.
- send sns to inform somone 
- Automatically assign labels to merge requests.
- in github > repo settings > webhooks > add
- copy jenkin ip/webhook/


## SSH Github 
- Must go into production environment via ssh (hhtp not secure)
- in working repo > go to settings
- deploy keys section 
- add key (public key created in .ssh folder) (add all contents here)

## SSH Github to Jenkins 
- configure job 
- under Source Code Management > repository url >ssh url
- click add > jenkins > kind: SSH Username with private key
- cat privatkey - begin to end - everything in that file copy over 
- credentials same as deploy key name 

## SSH-AWS-keys from Jenkins to AWS

- configure job 
- under Source Code Management > repository url > ssh url
- click add > jenkins > kind: SSH Username with private key
- cat file.pem aws key - begin to end - everything in that file copy over 
- credentials same as pem key name 
