<details>
<summary>Exercise 1: Clone and create new repository </summary>
<br />

- Clone git repository, creating a new local copy and
- Push it to your own GitHub remote repository.

**steps:**
```sh

# clone repository & change into project dir
git clone git@gitlab.com:devops-bootcamp3/git-project.git
cd git-project

# remove remote repo reference and create your own local repository
rm -rf .git
git init
git add .
git commit -m "Initial commit"

# create git repository on GitHub and push your newly created local repository to it
git remote add origin https://github.com/fsiegrist/devops-bootcamp-03-git.git
git push -u origin main

```

</details>

******

<details>
<summary>Exercise 2: .gitignore </summary>
<br />

You see that build folders and editor specific folders are in the repository and decide to ignore it as a best practice.

Ignore .idea folder, .DS_Store, out and build folders

Hint: remove from git cache first

**create .gitignore file with following entries**
```sh
.idea 
.DS_Store
out 
build
```

**remove cached commited files and commit .gitignore file**
```sh
git rm --cached .DS_Store

# -r for directories
git rm -r --cached .idea
git rm -r --cached out
git rm -r --cached build

# commit and push the changes
git add .
git commit -m "remove ignored files"
git push
```

</details>

******

<details>
<summary>Exercise 3: Feature branch </summary>
 <br />

Create a feature branch and change following:

- Upgrade the logstash-logback-encoder version to 6.6
- Add image to the index.html file (url: https://www.careeraddict.com/uploads/article/58721/illustration-group-people-team-meeting.jpg)

You are done with the changes. So:

- Check your changes using "git diff" and
- Commit them if everything is correct. Note: There is a standard in your team to name commits with descriptive text.
- Push your changes to your remote repository.

**steps**
```sh
# create a feature branch
git checkout -b feature/exercise-3

# in build.gradle upgrade the version of the "logstash-logback-encoder" library from '5.2' to '6.6'
compile group: 'net.logstash.logback', name: 'logstash-logback-encoder', version: '6.6'

# in src/main/webapp/index.html add the following image tag:
<img src="https://www.careeraddict.com/uploads/article/58721/illustration-group-people-team-meeting.jpg" width="700" />

# check and commit changes
git diff
git add build.gradle
git commit -m "Upgrade logback library to version 6.6"
git add src/main/webapp/index.html
git commit -m "Add image"

# as this is a new feature branch there is no need to first pull remote changes

# push new feature branch to remote and track the remote branch
git push -u origin feature/exercise-3
```

</details>

******

<details>
<summary>Exercise 4: Bugfix branch </summary>
<br />

You find out there is a bug in your project, so you need to fix it using a new bugfix branch:
- Create a new bugfix branch
- Fix the spelling error in Application.java file

You are done with the changes. So:
- Check your changes using "git diff" and
- Commit them if everything is correct.
- Push your changes to your remote repository.

**steps**
```sh
# create bugfix branch
git checkout -b bugfix/exercise-4

# fix the spelling error in src/main/java/com/Application.java
log.info("Java app started");

# check and commit changes
git diff
git add .
git commit -m "Fix typo"

# as this is a new bugfix branch there is no need to first pull remote changes

# push new bugfix branch to remote and track the remote branch
git push -u origin bugfix/exercise-4
```

</details>

******

<details>
<summary>Exercise 5: Merge request </summary>
<br />

You are done with the feature, now it needs to be tested and deployed. So:
- Merge your feature branch into master (using a merge request)

**steps**
```sh
# merge feature branch into master. Alternatively do the merge from GitHub UI
git checkout main
git merge feature/exercise-3 

# push the merge to remote master
git push
```

</details>

******

<details>
<summary>Exercise 6: Fix Merge conflict </summary>
<br />

You are on the bugfix branch. You notice the logger library version is old, so:
- Update it to version 6.2 (Change the same location in bugfix branch)

Some time went by since you opened your bugfix branch, so you want the up-to-date master state to avoid major conflicts.
- Merge the master branch in your bugfix branch - fix the merge conflict!

**steps**
```sh
# switch to bugfix branch
git checkout bugfix/exercise-4

# in build.gradle upgrade the version of the "logstash-logback-encoder" library from '5.2' to '6.2'
compile group: 'net.logstash.logback', name: 'logstash-logback-encoder', version: '6.2'

# commit change locally
git add .
git commit -m "Upgrade logback library to version 6.2"

# bring bugfix branch uptodate with master branch. Alternatively do the merge from GitHub UI
git merge main

# you will get a merge conflict here for build.gradle file

# fix merge conflict (open build.gradle file and keep master branch version) and when done check the state
git add build.gradle
git merge --continue
git status

# if all fixed, you can commit and push the merge into your bugfix branch
git push

```

</details>

******

<details>
<summary>Exercise 7: Revert commit </summary>
 <br />

**steps**
```sh
# on bugfix branch

# locate index.html in src/main/webapp, line 11 & fix spelling error
<li>Sarah - Full stack devloper</li>

# commit change locally
git add .
git commit -m "Fix spelling error"

# locate index.html in src/main/webapp, line 11 & set image url
<img src="https://3kcz333h8wih3px3rh3vhfv3-wpengine.netdna-ssl.com/wp-content/uploads/2018/10/effective-meetings.jpg" width="" />

# commit change locally
git add .
git commit -m "Set image url"

# push both commits to remote
git push

# revert last commit and push the revertion into remote repo
git revert HEAD
git push

```

</details>

******

<details>
<summary>Exercise 8: Reset commit </summary>
 <br />

**steps**
```sh
# on bugfix branch

# locate index.html in src/main/webapp, line 15 & make change
<li>Bruno - DevOps engineer</li>

# commit change locally
git add .
git commit -m "Adjust employee role description"

# reset the last local commit, meaning move to the previous commit
git reset --hard HEAD~

```

</details>

******

<details>
<summary>Exercise 9: Merge </summary>
 <br />

**steps**
```sh
# merge bugfix branch into master
git checkout master
git merge bugfix/changes

```

</details>

******

<details>
<summary>Exercise 10: Delete Branches </summary>
 <br />

**steps**
```sh
# delete branches remotely via Gitlab UI

# delete branches locally with CLI
git branch -D bugfix/changes
git branch -D feature/changes

```

</details>

******
