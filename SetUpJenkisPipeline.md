# Setup Jenkins Pipeline

### 1. Create Your First Freestyle Project Job

- In Jenkins, create a new Freestyle project.

### 2. Configure GitHub Repository

- Under the "GitHub Project" section, enter your Git repository URL.

### 3. Enable Source Code Management with Git

- In the "Source Code Management" section, select Git.
- Add your GitHub repository URL and credentials.

### 4. Build Steps

- In the "Build" section, add an Execute Shell build step.
- Add the following commands to build and run your Docker container:
    ```shell
    docker build . -t myimage
    docker run -d --name mycontainer -p 8000:8000 myimage
    ```

## 5. Enable Continuous Integration

- Install the GitHub Integration Plugin from Jenkins Plugin Manager.
- Go to your GitHub repository settings, and under the Webhooks section, add a new webhook with the following URL:

```sh 
http://<jenkins-server-ip>:<port>/github-webhook/
```

Example:

```sh
http://35.244.39.134:8080/github-webhook/
```









 