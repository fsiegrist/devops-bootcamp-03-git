## Notes on the videos
<br />

<details>
<summary>Video: Concept of Branches</summary>
<br />

Pull and track a remote branch:
`git checkout -b feature/branch --track origin/feature/branch`

Bind an existing local branch to a remote branch (track remote branch):
`git branch -u origin/<remote-branch> <local-branch>`

Detach a existing local branch from a tracked remote branch (stop tracking remote branch):
`git branch --unset-upstream`

Push an track a new local branch:
`git push -u origin <branch-name>`

Push an already tracked branch:
`git push origin <branch-name>`

List all local branches:
`git branch`

List all remote branches:
`git branch -r`

List all branches (local and remote):
`git branch -a`

Update branches (and delete references to no longer existing remote branches):
`git fetch --prune`

</details>

*****

<details>
<summary>Video: Deleting Branches</summary>
<br />

Delete a local branch:
`git branch -d <branch-name>`

Delete a remote branch:
`git push origin -d <branch-name>`

</details>

*****

<details>
<summary>Video: Gitignore</summary>
<br />

When you want git to ignore a file or directory, you can add it to .gitignore. But if that file or directory is already tracked by git (i.e. it is already part of a commit and has been pushed to the remote repository), you have to remove it from the git cache and push that change to delete it also on the remote repository.

```sh
git rm --cached .DS_Store
git rm -r --cached .idea
git rm -r --cached node_modules
git push
```

Find out which .gitignore entry is responsible for a certain file being ignored?
`git check-ignore -v <path/to/file>`

</details>

******