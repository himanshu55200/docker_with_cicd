# Installing Jenkins and Docker on Server

This guide will walk you through the steps for installing Jenkins on

## Prerequisites

Before you begin, you'll need the following:

- An AWS account
- An EC2 instance running Ubuntu Linux
- SSH access to the running Ubuntu Linux server .

Login Your Server

### Update you system

 ```sh
 sudo apt-get update -y
 ```

## [Install Jenkins](https://www.jenkins.io/doc/book/installing/)

### 1. First Install JAVA on the Server

```sh
sudo apt install fontconfig openjdk-17-jre -y
```

### 2. Confirm JAVA has been Installed

```sh
java -version
```

### 3. Add the Jenkins repo using the following command:

```sh
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
```

### 4. Import a key file from Jenkins-CI to enable installation from the package:

```sh
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
```

### 5. Update System

```sh
sudo apt-get update
```

### 6. Install Jenkins:

```sh
sudo apt-get install jenkins -y
```

### 7. Enable the Jenkins service to start at boot:

 ```sh 
sudo systemctl enable jenkins
```

### 8. Start Jenkins as a service:

```sh 
sudo systemctl start jenkins
```

### 9. You can check the status of the Jenkins service using the command:

```sh 
sudo systemctl status jenkins
```

Jenkins will be available on port 8080 of your EC2 instance's public IP address. To access Jenkins, open a web browser
and navigate to `http://[your-ec2-instance-public-ip]:8080`. You will be prompted to enter an initial admin password,
which can be found in the file `/var/lib/jenkins/secrets/initialAdminPassword` on your EC2 instance.

```sh
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

Install Suggested Plugins and after that setup admin.

### 10.command to Stop Jenkins as a service:

```sh
sudo systemctl stop jenkins
```

# [Docker](https://docs.docker.com/engine/install/ubuntu/)

### 1. Update your system

```sh
sudo apt-get update
```

### 2. Install prerequisites and dop setups:

```sh
sudo apt-get install ca-certificates curl
# Install Keys
sudo install -m 0755 -d /etc/apt/keyrings
```

### 3. Add Docker’s official GPG key:

```sh
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
# Give Permission
sudo chmod a+r /etc/apt/keyrings/docker.asc
```

### 4. Set up the stable Docker repository:

```sh
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

```

### 5. Update your package list again:

```sh
sudo apt-get update
```

### 6. Install Docker Engine:

```sh
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y 
```

### 7. To verify that Docker is installed correctly, run the following command to check the version:

```sh
docker --version
```

### 7. Enable the Docker service to start at boot:

 ```sh 
sudo systemctl enable docker
```

### 9. After the installation is complete, start the Docker service using the following command:

```sh
sudo service docker start
```

This should install Docker on your EC2 instance and allow you to start using it.
You can also use the below commands to check if the docker is in active status or not on your machine:

```sh
sudo systemctl is-active docker
```

### To get info about the docker:

```sh
sudo docker info
```

## For Access Docker in Jenkins add your jenkins user to the docker group :

```sh
sudo usermod -aG docker jenkins
```
After that Restart Jenkins
```sh
sudo systemctl restart jenkins

```