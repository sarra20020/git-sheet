# My cheatsheet git commands

- configure default editor for commit messages
```git config --global core.editor "code --wait"```

- get the status on the recent dir 
``` git status ```

- get all commits existing in the current dir
``` git log ``` or to format ```git log --oneline```

- stage a file in a the current dir
``` git add <file_name> ```

- stage all files in the current  dir
``` git add .```

- amend the previous commit message
```git commit --amend ``` 
- shortcut for staging and committing
``` git commit -a -m"message" ```
- list all branches existing in the current directory (CD)
``` git branch ```
### branching
- create a new branch
``` git branch <branch-name>```
    > will not swith to the created branch.

- once you have created a new branch, we can switch to it
``` git switch <branch-name>``` or  ``` git checkout <branch-name>```
    > to create a branch and switch on it ``` git switch -c <branch-name>``` or  ``` git checkout -b <branch-name>```

- delete a branch
``` git branch -D <branch-name>```
    > we have to be into another branch while trying to delete a branch
 - rename a branch
 ``` git branch -m <branch-name>```
    > we should be within the branch we want to rename

- push the new created  local branch with his content 
    ```git push --set-upstream origin <branch_name>```
### merging
- combine two branch, move to the destination branch and then use the following cmd
``` git merge <branch-name>```
    > A fast-forward merge can occur when there is a linear path from the current branch tip to the target branch.
    > In the event that you require a merge commit during a fast forward merge for record keeping purposes you can execute git merge with the --no-ffoption. ```git merge --no-ff <branch-name>```
### diff
- view changes between commits, branches, files , our working dir ...   etc itshow the difference between new changes and the last commit 
    ``` git diff ``` without additionnal options, it will list all hte changes in our working dir  that are Not staged for the next commit

    > `git diff --staged` or `git diff --cached` will only list the changes that are staged, and to view for a particular field we can add the specific <file_name> in option as `git diff HEAD [file_name]` or compare two files `git diff [file_name_1] [file_name_2]`

- `git diff branch1..branch2` || `git diff branch1 branch2` will list the changes between the tips of branch1 and branch2 

    > `git diff commit1..commit2` || `git diff commit1 commit2` to compare two commits , provide git diff with the commit hashes of the commits in question (i.e git diff 4eb57y 5oyeij) the order matter

    > `git diff HEAD ` lists all changes in the working tree since your last commit 

- ### Stashing 
    > Git provide an easy way of stashing these uncommited changes so that we can return to them later, without having to make unnecessary  commit 
    - ` git stash` or ` git stash save`  put stuff in the stash (running this command will take all uncommited changes (stages or unstaged) and stash them , reverting the changes in your working copy )
    - ` git stash pop` remove the most recently stashed changes in your stash and re-apply them your working copy
    - `git stash apply` to apply whatever is stashed away , without removing it from the stash .This can be useful if you want to apply stashed changes to multiple branches
    - `git stash list` display all existing stashes, Git assume you want to apply the most recent stash when you run `git stash apply` , but you can also specify a particular stash like `git stash apply stash@{id}`
    - `git stash drop stash@{id}` to delete a particular stash 
    - `git stash clear` will clear all stashes

### Checkout and Time travelling

- `git checkout <commit-hash>` will detach the head and point it to this particular commit 
    > `git switch <branch_name>` will re-atach our head to branch name
- `cat .git/HEAD` see the commit our head is referring to
- ` git checkout HEAD <file_name>` or ` git checkout -- <file_name> ` will discard new changes added to the file name and will back to whatever it looked like in your last commit a.k.a where HEAD is still referencing 
- `git restore <file_name>` is a new git Git brand command that helps wit un doing operations.Its restore using HEAD as the default source , but we can change that using the `--source ` option 
- `git restore --source HEAD~2 <file(s)_name>` or `git restore --source <commit-hash> <file(s)_name>` will restore file(s) prior to the last 2 second commit
- If you have accidentally added  file to your stagging area with `git add`  and you don't wish to include it to the next commit ,we can use ` git restore` as well to remove it from the staging area ---> `git restore --staged <file_name>`
- `git reset`
    > Regular reset : `git reset <commit-hash>` will reset the repo back to a specific commit without changing files content
    > Hard reset : `git reset --hard <commit-hash>` (`git reset --hard HEAD~1` for the 1st commit ahead of HEAD) will delete the  specific commit and associated changes
- `git revert ` similar to `git reset` it creates a brand new commit which reverses/undos the changes from a commit 
    > `git revert` or `git reset` : If we want to reverse  some commits that other people already have on their machines , we should use *revert* if not shared yet we should use *reset*(and no one will ever know)


## GitHub
 - Definition :  *GitHub* is a hosting platform for git         repositories , meanwhile *Git* is a version control software that runs locally on your machine, no account, no internet needed to use git.

 - `git clone` is a git  *not github* command to fetch a remote repo to local file

 ### configuring SSH keys (ref docs: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

 -  first of all we need to veriry if there's existing ssh keys
 so we tap the command `ls -al ~/.ssh`
 - if no ssh keys available you can generate a new one :
    > open a terminal
    > `ssh-keygen -t ed25519 -C "your_email@example.com"`
    > Note: If you are using a legacy system that doesn't support the Ed25519 algorithm, use: `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`
- Start the ssh-agent in the background
    > `eval "$(ssh-agent -s)"`
- Check if your ~/.ssh/config file exists in the default location
    > open ~/.ssh/config or cd ~/.ssh/config if the file doesn't exist we could create a new one with `touch ~/.ssh/config`
    > follow the docs for more details.
 ### viewing remotes
 - `git remote or git remote -v` will list any existing remotes that we can run in our dir
 > this command command will display nothing in case no remote repos is present in the current dir
 > `git remote add <name> <url>` to add a new remote ex: *git remote add origin https;//github.com/blah/repo.git*
 > **Origin** is a conventional Git remote name, can be changed
 > `git remote rename <old> <new> ` to rename a remote
 > `git remote remove <name>` will delete a remotes
 > `git branch -r` to view remote branches our repository knows about

 ### Pushing your work 
 - **`git push <remote> <branch>`** ex : *git push origin main*
 - Before pushin we can rename our default branch to whatever we want like `git branch -M <name>`


    