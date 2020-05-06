
# Jenkins Automated Test and merging to Production
In this project i tried to automate everything development to production level in simple webserver.
Steps that followed

 1. Git local and github repo
 2. create 3 jobs (main_server, testing, merge) as follows
 3. Add hooks given below
 4. Commit from any branch either master or dev1 respectivly it will run job( ie if master commit then main_server will bulid and if dev1 commit then test will build)
 5. Run merge Job after testing either using bash script or using url or manually building

## Post- commit Hook 

#!/bin/bash

echo "git push after commit "

if [ `git rev-parse --abbrev-ref HEAD` == "dev1" ];
then
git push -u origin dev1
curl --user "admin:redhat" http://192.168.43.243:8080//job/test/build?token=[add token here]
if [ `git rev-parse --abbrev-ref HEAD` == "master" ];
then
git push -u origin master
curl --user "admin:redhat" http://192.168.43.243:8080//job/main_server/build?token=[add token here]

fi

## Main_server Jenkins setup

![main_server 1](https://github.com/narayanhari/jenkins_automate_project_description/blob/master/main_server1.png)

![main_server2](https://github.com/narayanhari/jenkins_automate_project_description/blob/master/main_server2.png)

![main_server3](https://github.com/narayanhari/jenkins_automate_project_description/blob/master/main_server3.png)

## Test  Jenkins Setup
![test1](https://github.com/narayanhari/jenkins_automate_project_description/blob/master/test1.png)

![test2](https://github.com/narayanhari/jenkins_automate_project_description/blob/master/test2.png)

![test3](https://github.com/narayanhari/jenkins_automate_project_description/blob/master/test3.png)

## Merge Jenkins Setup
![merge1](https://github.com/narayanhari/jenkins_automate_project_description/blob/master/merge1.png)

![merge2](https://github.com/narayanhari/jenkins_automate_project_description/blob/master/merge2.png)
