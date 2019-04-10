# Mission:  Build a node application with with a restful API

# Note:  A problem we have to overcome has been the .bash_profile vs .bashrc
on Macs.  I found the following excerpt on this issue.

When a user logs in to a system, the user’s work environment is determined by
the initialization files. These initialization files are defined by the
user’s startup shell, which can vary depending on the release.  
They are called .bashrc and or .bash_profile if they do not exist you can
create them with touch .bashrc or .bash_profile

Many linux systems use the .bashrc file to initialize the users environment,  
but Mac OS is an exception and will use .bash_profile unless you alias it from
the .bashrc initialize file which is a
recommendation.  We are not going to do that for now maybe down the line.

### Begin with creating a new directory in your projects folder on your desktop called team_seguin_demo1 then at your terminal run

- ```git clone git@github.com:seguin-util/team_seguin_demo1.git```
- Now open the new folder by typing ```atom .```
- This will show all files in the folder including the ***steps_new2.md*** file with all the instructions on how to complete this exercise.

### Step 1a
- Verify if brew is installed with ```brew --version```
- if installed move to step 1b
- else run ```/usr/bin/ruby -e "$(curl -fsSL \
  https://raw.githubusercontent.com/Homebrew/install/master/install)"```

- Homebrew known as brew installs the stuff you need that Apple
(or your Linux system) didn’t.

### Step 1b
- Verify your dependencies with ```nvm --version```
- if exist
- then move to step 2
- else run  ```brew install nvm```
- nvm allows you to install multiple versions of node

![nvm is a node version manager allowing you to install multiple versions of
node](/Users/jsaldana/Desktop/InternProjects/loopback_Demo1/
  nvm_explain_image.png "nvm allows you to install multiple versions of node")


### Step 2
- check if nvm is working run:
```command -v nvm```
- should echo nvm

#### Note:  In your startup script, e.g. ~/.bashrc, ~/.profile, ~/.zshrc, you’ll need to add this:

``` export NVM_DIR="$HOME/.nvm" [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"```

### Step 3
- install a new version of Node.js
- please install node version 8.6 with ```nvm install 8.6.0```

### Step 4
``` npm install -g loopback-cli```
- Check version of loopback
```lb -v```
- ***What is lookback?*** LoopBack is a highly-extensible, open-source Node.js
framework that enables you to create dynamic end-to-end REST APIs.

### Step 5
Create a new LoopBack Application - at terminal run: ```lb```
- lb will present you with a command line options to build a new node
application
- ***name:  team_seguin > dir: team_seguin > version: 3.x > application
type: api-server > should say Im all done running npm install for you.***

### Step 6
- verify everything is running properly - at terminal run:  ```node .``` > now open up in a browser ```http://localhost:3000/explorer``` explore your new node api interface built for you with just a few commands.

### Step 7

- if everything is going as expected than do your first commit to your github account.
- ***Git Workflow to add your own code***

- ***Note*** Your local repository consist of ```3 main trees maintained by git```.
The first one is your working directory, second is the index acts as staging
area, lastly is head which points to the last commit you made.
- ***Note: use the the && as a pipe between commands to run all at once***
- from your team_seguin directory run ```git add .``` &&
```git commit -m -a "My first commit on team_seguin all is running as expected"``` && ```git push -u origin master```

### Step 8
- To sign up as a new user, click to unfold the ```POST /Users endpoint```.
In the ```‘Credentials’ parameter paste a new json object```

- ```
  {
  "email":"user1@email.com",
  "password":"passw0rd",
  "username":"user1"
}```

- The Response Body should return a new id.
```
{     
  "username": "user1",   
  "email": "user1@email.com",   
  "id": 1
}```

### Step 9
- Then to login click and unfold the ```POST /Users/login endpoint```,
in the ```‘Credentials’ parameter paste the json object with the email and
password properties```

- ```
{
  "username":"user1",
  "password":"passw0rd"
}
```

### Step 10

- The Response Body should return an ```id value that is the access token```, which you use to authenticate other API requests.

- ```{   
"id": "cwotd42A6VxOrWbFEN1EQigITKA1RnFHGWAKUz",   
"ttl": 1209600,   
"created": "2017-09-20T21:03:59.305Z",   
"userId": 1
}
```

### Step 11

- Copy the access_token value and paste the value in the top right of the
Loopback explorer, and ```press the ‘Set access token’ button```.
In a regular API request, you would add a URL parameter ‘?access_token=..’

### step 12
- Go to PUT /Users/{id}, and in the parameters enter for ‘id’ the userId,
in this case ‘1’, and for ‘data’ enter

```
{
  "username": "user1",
  "email": "user1@email.com",
  "password" : "passw0rd",
  "firstname": "john",
  "lastname": "doe"
}
```
- Press the ‘Try it out!’ button. You will see, you were allowed to make
updates to the user, but only because you are the authenticated owner of user 1.

### Done! Great Job Jordyn and Elilita your first api server.
