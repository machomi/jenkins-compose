
### 1. Start Jenkins stack


    docker compose up -d


### 2. Read Jenkins admin password

    docker compose logs jenkins-master

### 3. Finish jenkins initial setup

Login to http://localhost:8080 with password provided. 

Install suggested plugins. Finish wizard.

### 4. Create new node

Go to http://localhost:8080/manage/computer/createItem

Fill up form:

    Name: jenkins-slave
    Remote root directory: /home/jenkins/agent

and save.

### 5. Read jenkins slave secret

Go to http://localhost:8080/manage/computer/jenkins-slave/ 

Read and note secret value.

### 6. Set JENKINS_SECRET

Set secret from previous step as env JENKINS_SECRET in docker compose jenkins-slave.

### 7. Restart container with jenkins slave.

The easiest way is to run again:

    docker compose up -d

Check if node is connected.

You can easliy adjust jenkins slave building your own docker image from jenkins/inbound-agent. You can as many nodes as needed.