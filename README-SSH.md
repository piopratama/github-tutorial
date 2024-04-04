if you have successfully to connect using https you can try to change it to be more secure using ssh.
ssh is a method to use crypthography method securing your transaction.
1. first you need to create pair of key in you machine, private and public key.
you need to secure your private key and share this public key to github repository to identify it is you.
2. to create the key.
```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

change the email with your email associated with github (the email that you use in sign up or login to github web)
3. then you can put the file generated as your desired but common practice in windows is to put it under C:/user/your_username/.ssh
if you have already had the key maybe you need to save it as different file name or remove existing file.

4. then open file generated (file with .pub extension is your public key), copy the content and put it under setting->SSH and GPG Keys of your github account.

5. then if you create a new project use :
```
git init
git remote add origin <use ssh repository link>
```

then add file, commit, and create main branch as we did in README-Basic.md

then to push it we need to provide private key we have. eg.
```
GIT_SSH_COMMAND="ssh -i /path/to/keys/<private key file>" git push origin <branch-name>
```

note:
we will use this private and public key for all repository we are working at, unless we have a reason to have two different ssh key. for example you have two github account.

6. but sometimes annoying to always pass our private key, so we can utilize agent.
```
ssh-add ~/<private key file>
```

next try if it can access github,
```
ssh -T git@github.com
```

7. the problem ssh agent will only remember your private key temporary, when you restart your pc it will forget it.
so how to resolve it ?
we can create "config" file in .ssh directory (C:/user/your_username/.ssh), inside "config" we put:
```
# Github.com server
Host github.com
IdentityFile <private key file>
```

try restart your pc and run 
```
ssh -T git@github.com
```

see if it is success.

8. what about if we have two github account, so you might need to create two pair of key.
one private and public key for your first github account
another is for your second github account, then modify "config" inside .ssh directory to this
```
# GitHub account A
Host github.com-A
    Hostname github.com
    User <username>
    IdentityFile <first private key>

# GitHub account B
Host github.com-B
    Hostname github.com
    User <username>
    IdentityFile <second private key>
```

remember to reside your each public key content to github account associated.
test it using
* ssh -T git@github.com-A
* ssh -T git@github.com-B