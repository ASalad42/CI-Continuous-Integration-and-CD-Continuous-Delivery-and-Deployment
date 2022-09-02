# CI/CD Pipeline

CI CD is the blueprint to devops strategies and reason for **faster software releases**. CI/CD facilitates an effective process for getting **products to market faster**, continuously delivering code into production, and ensuring an **ongoing flow of new features and bug fixes via the most efficient delivery method.**
- In short, CI is a set of practices performed as developers are writing code, and CD is a set of practices performed after the code is completed.
- The CI/CD pipeline is part of the broader DevOps framework
- **It is the backbone of DevOps practices and automation**, It plays vital, challenging and exciting role in DevOps culture, growing numbers of companies releasing software in minutes with the adoption of CICD practices.

To put it simply, the continuous integration is part of both continuous delivery and continuous deployment. The main difference is the deployment step, in **continuous delivery the deployment is done manually** and in **continuous deployment it happens automatically**
- CI/CD exist to automate the deployments and building of software

![image](https://user-images.githubusercontent.com/104793540/187963750-f3c11787-1e12-4fd6-ab3f-927099002c47.png)

## Continuous Integration (CI)
Developers merge/commit code to master branch multiple times a day, fully automated build and test process which gives feedback within few minutes, by doing so, you avoid the integration hell that usually happens when people wait for release day to merge their changes into the release branch.

## Continuous Delivery
Continuous Delivery ensures that you can release new changes to your customers quickly in a sustainable way. This means that on top of having automated your testing, you also have automated your release process and you can deploy your application at any point of time by clicking on a button. **In continuous Delivery the deployment is completed manually.**


## Continuous Deployment 
Continuous Deployment goes one step further than continuous delivery, with this practice, **every change that passes all stages of your production pipeline is released to your customers, there is no human intervention**, and only a failed test will prevent a new change to be deployed to production.

## Pipline 

![image](https://user-images.githubusercontent.com/104793540/187894786-00bf110b-5b88-4612-8e1f-fb10a230eec4.png)

## Jenkins 

Jenkins is an open-source automation server in which the central build and CI process take place, It is a Java-based program with packages for Windows, macOS, & Linux.

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
To production env via ssh (hhtp not secure)
## SSH Github to Jenkins 
## SSH-AWS-keys from Jenkins to AWS


## CICD Activity

![image](https://user-images.githubusercontent.com/104793540/188112377-d4a52873-4ade-4e77-ba55-7b3336b36935.png)

 ### Configure your job to checkout code from the develop branch rather than the master branch
 
![image](https://user-images.githubusercontent.com/104793540/187959113-ea43616b-d45a-4c85-8fc2-63a91ffa73b0.png)
![image](https://user-images.githubusercontent.com/104793540/187959157-9686174a-9824-46a8-bb30-9434e4126ff9.png)
![image](https://user-images.githubusercontent.com/104793540/187959212-fd0c378d-96f9-40bf-ad7b-f8a18d753d39.png)
![image](https://user-images.githubusercontent.com/104793540/187959281-fda4d5a5-fc0d-4001-a35f-281519b0efdb.png)
![image](https://user-images.githubusercontent.com/104793540/187959440-2980d45d-4b77-4f93-9c2a-c0e21bb736d1.png)

#### local host:
- view all branches with git branch 
- create new branch with git branch name 
- better is git checkout -b name to	Create a new branch and switch to it
- git checkout command and specify the name of the branch you want to switch to.
- remove branch with git branch -d name

https://github.com/joshnh/Git-Commands

#### debugging:
- new deploy keys - uses eng122 public
- jenkins uses private key for eng122
- ssh agent for 122 and eng122
- http://18.133.180.208:8080/github-webhook/

![image](https://user-images.githubusercontent.com/104793540/187960069-e6bb5d89-10f8-45ab-ad27-f423270d8925.png)
![image](https://user-images.githubusercontent.com/104793540/187959002-a5cda70d-7229-4354-a11e-1b2398c1f5d4.png)

all my attemts before hand:

![image](https://user-images.githubusercontent.com/104793540/187960161-c74aa057-354e-46d3-8ddb-b8bed17610ee.png)

### Have job merge the develop branch code with the master branch and test against that

![image](https://user-images.githubusercontent.com/104793540/187960543-98dbe58a-685a-43bc-afd5-d78f8df671fe.png)
![image](https://user-images.githubusercontent.com/104793540/187961102-1a9bcf68-8786-401f-9ff1-d379f17e6f3a.png)
![image](https://user-images.githubusercontent.com/104793540/187961330-7525d4e2-7194-4b6d-8407-cbe75e2fa054.png)

so the following was done in dev on local host > pushed > jenkins recieved and tested > then merged with main after success 
![image](https://user-images.githubusercontent.com/104793540/187961463-b53ea776-14ad-4d74-b6fd-76b571367aba.png)

### create 3rd job to get code from main and deploy on AWS in a running ec2 instance

- add contents of pem file into ssh > credentials 
- create new ec2 instance (new feature so cant use ami)
- Create sg – allow Jenkins ip to ssh in as well as any rules required 

![image](https://user-images.githubusercontent.com/104793540/188116470-6a777581-2647-4cfd-8b53-f69c17a74f67.png)


- Create 3rd job in Jenkins: get the code from main branch and copy (scp) to ec2 – run the script  to install node with any other required dependencies  
- 3rd job only triggered 
- First iteration run npm install & npm start manually 
- 4th job launch the app – if 3rd was successful 
- Pm2 kill all - Create a 5th job to create DB_HOST=db-ip
- Npm start 

