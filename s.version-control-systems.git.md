---
id: nt0tthyrn13hlj15lyknctl
title: Git
desc: ''
updated: 1685603429545
created: 1681796185376
---
# GIT
Creates a new branch locally then pushes it.
```
git checkout -b $branchname
git push origin $branchname --set-upstream
```






























# WORKFLOW:
The central repo holds three main branches with an infinite lifetime :
# Production branch :
## - {production} :
We consider origin/production to be the main branch where the source code of HEAD always reflects a production state for everyone.
#
# Master branch :
## - {master} :
We consider origin/master to be the main branch where the source code of HEAD always reflects a production state for local environment.
#
# Develop branch :
## - {develop} :
We consider origin/develop to be the main branch where the source code of HEAD always reflects a state with the latest delivered development changes for the next release.
#
Next to the main branches `production`, `master` and `develop`, my development model uses a variety of supporting branches to aid parallel development, ease tracking of features, prepare for production releases and to assist in quickly fixing live production problems. Unlike the main branches, these branches always have a limited life time, since they will be removed eventually.
# Release branch :
## - {release-***} :

May branch off from: `develop`.

Must merge back into: `develop`, `master` and `production`.

It is exactly at the start of a release branch that the upcoming release gets assigned a version number. So I branch off and give the release branch a name reflecting the new version number :

```
$ git checkout -b release-1.2 develop
Switched to a new branch "release-1.2"
$ ./bump-version.sh 1.2
Files modified successfully, version bumped to 1.2.
$ git commit -a -m "Bumped version number to 1.2"
[release-1.2 74d9424] Bumped version number to 1.2
1 files changed, 1 insertions(+), 1 deletions(-)
```
Bug fixes may be applied in this branch (rather than on the develop branch). Adding large new features here is strictly prohibited.

When the state of the release branch is ready to become a real release, the release branch is merged into `master` and `production`. Then the release branch need to be merged back into `develop`.

```
$ git checkout master
Switched to branch 'master' or 'production'
$ git merge --no-ff release-1.2
Merge made by recursive.
(Summary of changes)
$ git tag -a 1.2
```

To keep the changes made in the release branch, I need to merge those back into `develop`.

```
$ git checkout develop
Switched to branch 'develop'
$ git merge --no-ff release-1.2
Merge made by recursive.
(Summary of changes)
```
# Hotfix branch :
## - {hotfix-***} :

May branch off from: `master` or `production`.

Must merge back into: `develop`, `master` and `production`.

They arise from the necessity to act immediately upon an undesired state of a live production version. When a critical bug in a production version must be resolved immediately.

Hotfix branches are created from the `master` or `production` branch.

```
$ git checkout -b hotfix-1.2.1 master
Switched to a new branch "hotfix-1.2.1"
$ ./bump-version.sh 1.2.1
Files modified successfully, version bumped to 1.2.1.
$ git commit -a -m "Bumped version number to 1.2.1"
[hotfix-1.2.1 41e61bb] Bumped version number to 1.2.1
1 files changed, 1 insertions(+), 1 deletions(-)
```
Then, fix the bug and commit the fix in one or more separate commits.

```
$ git commit -m "Fixed severe production problem"
[hotfix-1.2.1 abbe5d6] Fixed severe production problem
5 files changed, 32 insertions(+), 17 deletions(-)
```

When finished, the bugfix needs to be merged back into master, but also needs to be merged back into develop, in order to safeguard that the bugfix is included in the next release as well.

```
$ git checkout master
Switched to branch 'master'
$ git merge --no-ff hotfix-1.2.1
Merge made by recursive.
(Summary of changes)
$ git tag -a 1.2.1
```
<!-- ### Main branches:
- production > Code available at that time in production.
- master > Code available at that time in local
- release-<version> > Last version available to testers, must be the current version or next to be pushed in production
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
You can initialize this repository with code from a Subversion, Mercurial, or TFS project. -->