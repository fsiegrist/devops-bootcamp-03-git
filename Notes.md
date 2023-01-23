## Notes on the videos
<br />

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

</details>

******