To collaborate with other people project, you can try to fork the project in github and it will create copy of the project to your github repository.
1. then you can clone the project so that you have local copy,
```
git clone <project github link> (you can use https or ssh method)
```

2. then create a new branch,
git checkout -b feature/my-new-feature

create branch is always a best practice so that you still have original copy in case you got problem with the project during development

3. normally we want our main local branch up to date with the change of original prject. apply this step:
```
git remote add upstream <upstream_repository_url> (upstream is original project link)
git fetch upstream
git checkout main then git merge upstream/main
git push origin main
```
(this process to keep your main branch in github web up to date with original project. do this daily)

4. then you can working with your branch, then once you finished
you can try to merge with your local main branch (which we always update daily), then push to our github repository main branch

5. if you sure with the change then you can do pull request, this process can be done in your github web to ask the owner of the project to review your code and maybe merge it to their main branch


if you are the project owner, it is better to ask the contributor to pull request to a new branch, then as the project owner you can try to accept your pull request and review it locally, then if you fell all is working fine and agree to merge it and push is are possible.