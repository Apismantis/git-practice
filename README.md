# Git Practice

### Clone
- Clone repository

`git clone <repo_url>`

- Clone single branch 

`git clone -b <branch_name> --single-branch git://<repo_url>`

### Git pull

- Pull a branch from remote server to a branch in local

`git pull <remote> <r-branch>:<l-branch>`

### Undo commit

- To change the last commit message use --amend

`$ git commit --amend -m "New commit message"`

- Open editor to edit the message

`git commit --amend`

- To undo commit

```
$ git commit -m "Something terribly misguided"              (1)
$ git reset HEAD~                                           (2)
<< edit files as necessary >>                               (3)
$ git add ...                                               (4)
$ git commit -c ORIG_HEAD                                   (5)
```
This is what you want to undo
This leaves your working tree (the state of your files on disk) unchanged but undoes the commit and leaves the changes you committed unstaged (so they'll appear as "Changes not staged for commit" in git status and you'll need to add them again before committing). If you only want to add more changes to the previous commit, or change the commit message, you could use git reset --soft HEAD~ instead, which is like git reset HEAD~ but leaves your existing changes staged.
Make corrections to working tree files.
git add anything that you want to include in your new commit.
Commit the changes, reusing the old commit message. reset copied the old head to .git/ORIG_HEAD; commit with -c ORIG_HEAD will open an editor, which initially contains the log message from the old commit and allows you to edit it. If you do not need to edit the message, you could use the -C option.

### Push tags to git server

- To push single tag

`$ git push origin <tag_name>`

- To push all tags

`$ git push --tags`

### Branch

- Show all branch

`$ git branch -a`

- Show remote branch

`$ git branch -r`

- Create new Branch

`$ git branch <branch_name>`

- Create branch from commit

`$ git branch branchname <sha1-of-commit>`

- Switch branch

`$ git checkout <branch_name>`

- Create new and checkout

`$ git checkout -b <branch_name>`

- Delete branch

`$ git branch -d <branch_name>`

- Pull from branch

`$ git pull <remote_name> <branch_name>`

- Push branch to remote

`$ git push <remote_name> <branch_name>`

### Files
- Remove a file

`$ git rm --cached <file_name>`

- Remove a folder in repository without remove on local repository

`$ git rm --cached -r <folder_name>`
