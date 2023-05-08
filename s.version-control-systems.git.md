---
id: nt0tthyrn13hlj15lyknctl
title: Git
desc: ''
updated: 1683043275084
created: 1681796185376
---
# GIT
Creates a new branch locally then pushes it.
```
git checkout -b $branchname
git push origin $branchname --set-upstream
```






























## WORKFLOW:

### Main branches:
- main > Code available at that time in production
- staging/<version> > Last version available to testers, must be the current version or next to be pushed in production
- develop > Last development work

### Task branches:
Prefixed by:

- feat/<name> for feature work
- fix/<name> for bugfixes
- chore/<name> for codebase maintenance work (dependencies update, tooling, CD/CI...)
- hotfixes/<name> for hotfixes, these are directly pushed

### Release process
1. When I have a satisfying amount of features in develop, push a commit that:

- Increments version number (path, minor, major) and the build numbers if any

2. Create a branch staging/<version> from develop

- That branch will trigger a deployment to beta users
- During the testing period, fix branches (fix/<something>) should be directly merged to that branch. Every push here should increment the build number, if any.
- CHANGELOG.md should be updated if needed.
- Changes must be merged back into develop
- CHANGELOG.md must be merged back into develop

3. Merge the branch staging/<version> in main
4. Delete the staging/<version> branch toavoid push weird stuff to beta users
5. Tag the version v<version number> on main

---

git checkout -b ＜ new-branch ＞
git push --set-upstream origin develop

---

## create a new repository on the command line
echo "# sportsee-front" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M master
git remote add origin https://github.com/jeremyteurterie/sportsee-front.git
git push -u origin master

## push an existing repository from the command line
git remote add origin https://github.com/jeremyteurterie/sportsee-front.git
git branch -M master
git push -u origin master

## import code from another repository
You can initialize this repository with code from a Subversion, Mercurial, or TFS project.