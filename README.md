# Git Practice
<hr/>

### Clone
- Clone repository  `git clone <repo_url>`

- Clone single branch  `git clone -b <branch_name> --single-branch git://<repo_url>`

### Git pull

- Pull a branch from remote server to a branch in local  `git pull <remote> <r-branch>:<l-branch>`

- Pull a branch from remote server to the current local branch  `$ git pull <remote_name> <local_branch_name>`

### Git commit

- Commit the change of branch
    ```
    $ git add ...
    $ git commit -m <message>
    $ git push <remote_name> <branch_name>
    ```

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

- Delete a commit (1 - delete only the commit_id) `$ git revert <commit_id>`

- Delete a commit (2 - Delete all newer commit than the commit_id) 
    ```
    $ git reset --hard <commit_id>
    $ git push <remote_name> -f <branch_name>
    ```

### Git push

- To push single tag  `$ git push origin <tag_name>`

- To push all tags  `$ git push --tags`

- Push branch to remote  `$ git push <remote_name> <local_branch_name>`

### Branch

- Show all branch `$ git branch -a`

- Show remote branch `$ git branch -r`

- Show local branch `$ git branch`

- Create new Branch `$ git branch <branch_name>`

- Create branch from commit  `$ git branch branchname <sha1-of-commit>`

- Switch branch  `$ git checkout <branch_name>`

- Create new and checkout  `$ git checkout -b <branch_name>`

- Delete local branch `$ git branch -d <branch_name>`

- Delete remote-tracking branch `$ git branch -d -r <remote_branch_name>`

- Delete remote branch `$ git push -d <branch_to_delete>`

- Force delete branch `$git branch -D <-r> <branch_name>`

### Git stash

- Save all changes of the current branch `$ git stash`

- Show the stashed change history `$ git stash list`

- Show a change  `$ git stash show stash@{<index>}`

- Apply a change `$ git stash apply stash@{<index>}`

- Delete a change `$ git stash drop stash@{<index>}`

- Delete all changes `$ git stash clear`

### Files
- Remove a file  `$ git rm --cached <file_name>`

- Remove a folder in repository without remove on local repository

    `$ git rm --cached -r <folder_name>`

<hr/>

## Commit Message Format

Each commit message consists of a header, a body and a footer. The header has a special format that includes a type, a scope and a subject:

    <type>(<scope>): <subject>
    <BLANK LINE>
    <body>
    <BLANK LINE>
    <footer>

The header is mandatory and the scope of the header is optional. Any line of the commit message cannot be longer 100 characters! This allows the message to be easier to read on GitHub as well as in various git tools.

### Revert

If the commit reverts a previous commit, it should begin with revert:, followed by the header of the reverted commit. In the body it should say: This reverts commit <hash>., where the hash is the SHA of the commit being reverted.

### Type

Must be one of the following:

  - feat: A new feature
  - fix: A bug fix
  - docs: Documentation only changes
  - style: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc)
  - refactor: A code change that neither fixes a bug nor adds a feature
  - perf: A code change that improves performance
  - test: Adding missing or correcting existing tests
  - chore: Changes to the build process or auxiliary tools and libraries such as documentation generation
    
### Scope

The scope could be anything specifying place of the commit change. For example 'database', 'MainActivity', etc... You can use * when the change affects more than a single scope.

### Subject

The subject contains succinct description of the change: 
  - use the imperative, present tense: "change" not "changed" nor "changes"
  - don't capitalize first letter
  - no dot (.) at the end
    
### Body

Just as in the subject, use the imperative, present tense: "change" not "changed" nor "changes". The body should include the motivation for the change and contrast this with previous behavior.

### Footer

  - The footer should contain any information about Breaking Changes and is also the place to reference GitHub issues that this commit closes.
  - Breaking Changes should start with the word BREAKING CHANGE: with a space or two newlines. The rest of the commit message is then used for this.
  - A detailed explanation can be found in this document.
