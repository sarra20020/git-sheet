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

- combine two branch, move to the destination branch and then use the following cmd
``` git merge <branch-name>```
    > A fast-forward merge can occur when there is a linear path from the current branch tip to the target branch.
    > In the event that you require a merge commit during a fast forward merge for record keeping purposes you can execute git merge with the --no-ffoption. ```git merge --no-ff <branch-name>```

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
