## Create Virtual Environment :
```
python -m venv venv
```

## Activate the Virtual Environment :
### On Linux/macOS:
```
source venv/bin/activate
```
### On Windows:
```
venv\Scripts\activate
```

NOW CREATE YOU DJANGO PROJECT AND TEST IN LOCAL ALL WORKING

## Push Your Project in Git HUB :

### Initialize a Git Repository add all file to git and do first Commit  
```
git init
git add .
git commit -m "Initial commit"
```
### CHANGE YOUR BRANCH NAME 
```
git branch -M master
```

### Add the remote GitHub repository
```
git remote add origin https://github.com/your-username/your-repository-name.git
```

### Push your code in origin 
```
git push -u origin master
```
### If you want change Your  branch
```
git checkout master
```

### Create And checkout in NewBranch
```
git switch -b new-branch
```

## If You want Connect your local machine or server with github using SSH

### 1. Generate SSH key on server or local machine
```shell
ssh-keygen
```
### 2. It will generate Two file private and public key  in same location 
```sh
# this is Private key
~/.ssh/id_rsa
# This is Public key
~/.ssh/id_rsa.pub
```
### 3. Copy public key and paste on the github or any where where you want to connect
```sh
cat ~/.ssh/id_rsa.pub
```
### 4 .Now your server or local machine is connect to Github  
 - Add the SSH key to your GitHub account:
 - Log in to your GitHub account.
 - Go to Settings > SSH and GPG keys > New SSH key.
 - Paste your public key into the "Key" field and give it a title.
 - Click Add SSH key.

### NOW SETUP YOUR SERVER SET JENKINS  WE WILL SEN IN 