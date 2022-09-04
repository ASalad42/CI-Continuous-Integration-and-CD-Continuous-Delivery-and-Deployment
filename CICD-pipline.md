
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

all my attempts before hand:

![image](https://user-images.githubusercontent.com/104793540/187960161-c74aa057-354e-46d3-8ddb-b8bed17610ee.png)

### Job 2 - Merged to Main 

Have job to merge the develop branch code with the master branch and test against that

![image](https://user-images.githubusercontent.com/104793540/187960543-98dbe58a-685a-43bc-afd5-d78f8df671fe.png)
![image](https://user-images.githubusercontent.com/104793540/187961102-1a9bcf68-8786-401f-9ff1-d379f17e6f3a.png)
![image](https://user-images.githubusercontent.com/104793540/187961330-7525d4e2-7194-4b6d-8407-cbe75e2fa054.png)

so the following was done in dev on local host > pushed > jenkins recieved and tested > then merged with main after success 
![image](https://user-images.githubusercontent.com/104793540/187961463-b53ea776-14ad-4d74-b6fd-76b571367aba.png)

### Job 3 - Continous delivery to AWS EC2

Third job to get code from main branch and deploy on AWS in a running ec2 instance
Create 3rd job in Jenkins: get the code from main branch and copy (scp) to ec2 – run the script  to install node with any other required dependencies  
- ensure job starts after merge is successful > 

![image](https://user-images.githubusercontent.com/104793540/188174868-e58d57fd-f98a-46be-8dc2-e65b08984861.png)

- add contents of pem file into ssh > credentials 
- create new ec2 instance (new feature so cant use ami)
- Create sg – allow Jenkins ip to ssh in as well as any rules required 

![image](https://user-images.githubusercontent.com/104793540/188131869-fb88efc1-8472-419c-a3c7-5d31fe02dee4.png)
![image](https://user-images.githubusercontent.com/104793540/188131968-f3c1d553-b50c-49fb-b1a0-1152ab53c205.png)
![image](https://user-images.githubusercontent.com/104793540/188174560-174d23f1-d3cb-4742-8f2d-661d744c8471.png)

deliverying app into ec2:
- rsync delivers app and evironment folder from workspace into jenkins_app on ec2 via ip
- then ssh into ec2 instance 
- run provision script from env folder 
- npm install 
- npm start

![image](https://user-images.githubusercontent.com/104793540/188202270-c04fb212-5612-4f4c-b672-4bb6478f44f4.png)
![image](https://user-images.githubusercontent.com/104793540/188311451-69af34dc-95fb-416e-b242-5c47ed84289e.png)
![image](https://user-images.githubusercontent.com/104793540/188311508-447c977e-dd4b-4d98-b1b0-3e6eb6486348.png)
![image](https://user-images.githubusercontent.com/104793540/188202311-a4352123-fb01-4bab-a7cb-5318e03a7a19.png)


### Job 4 - Continous deployment to AWS EC2

currently:
![image](https://user-images.githubusercontent.com/104793540/188311962-109f0cd9-ab17-4d23-92f7-1cbd20116a2d.png)


starts the app after successful delivery only: 

![image](https://user-images.githubusercontent.com/104793540/188311933-19ef7aad-8bef-4520-b793-078592c29cc3.png)

### Job 5 - Create DB_HOST=db-ip



### miscellaneous


- First iteration run npm install & npm start manually 
- 4th job launch the app – if 3rd was successful 
- Pm2 kill all - Create a 5th job to create DB_HOST=db-ip
- Npm start 

Sudo Code
```

# ssh into ec2 on aws
# by pass the step where it asks us to confirm the manually 
# scp or rsyn to migrate data from github to ec2
# run provision.sh
#--------------- 
# ssh into your ec2 from localhost to confirm the data has been migrated
# navigate to app folder
# ---------------
# new job to be triggered by above job to launch the app
# npm install

# next job for your db
#pm2 kill all
#db_host
#npm start in the background

# npm start in the background
# nohup node app.js > /dev/null 2>&1 &

```
