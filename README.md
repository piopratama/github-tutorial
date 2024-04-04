To play with git we need to install git in our local machine
1. git can be downloaded from here : https://git-scm.com/
2. install it as usual and test it on your cmd, see if you can try "git version" command

a lot of things we can do with git but let's focus on init a project with git and push it to github
1. create a directory and point our terminal/cmd to the directory let's say we have directory called
"GIT" and inside this directory I create file called README.md. Inside this file we can type anything that we want.
2. then execute "git init" inside project directory
3. go to github and login if you have already had the account, or you can try sign up then follow the process and then login
4. in github (don't get confused git is on your local machine, github is repository online, imagine it like a google drive or onedrive). in github website create repository.
in my case i create repository called github-tutorial

connecting git in our machine to github repository we have just created.
1. go back to our project "GIT" directory with "README.me" file.
2. we need to tell git where to push, utilize this command:
git remote add origin https://github.com/piopratama/github-tutorial.git -> you will get this link in your repository github

note: 
* remember when you use git remote it doesn't affect other project as git remote add is independent
(test it if you like to by executing: "git remote" on two different project)
* remember some setting is global and some is local (project independen). something like user.name and user.email could be global could be local, local config will override global config. keep this in mind.
test this command to see your global config 
```
git config --global --list
```

it will show global setting of git such as : user.name, user.email, and credential.helper.
If you want to set it you can use
```
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
git config --global credential.helper manager
```

credential manager will prompt you and secure your credential, let's say you have proejct A and push to github it will asked for authentication, but if you have another project B to push it will not asking you anymore.

remove --global option if you want to check your local configuration for every different project.

you will also need to check your remote repository in github, are you using https or ssh.
check it by execute "git remote -v".
if you see:
```
origin  https://github.com/piopratama/github-tutorial.git (fetch)
origin  https://github.com/piopratama/github-tutorial.git (push)
```
then it must be https, otherwise could be ssh like this:
```
origin  git@github.com:piopratama/github-tutorial.git (fetch)
origin  git@github.com:piopratama/github-tutorial.git (push)
```

if you are using https then make sure your credential user.name is right and when you push you will be asked password for the first time.

3. let's try to push our project by first add all file in the project using:
```
git add .
git commit -m "your message is here"
git branch -M main
git push --set-upstream origin main
```

you need to specify --set-upstream origin main whenever you add branch on the first time, later on you can just use git push