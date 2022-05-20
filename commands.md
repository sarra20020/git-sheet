## my cheatsheet git commands

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

- one you have created a new branch, we can switch to it
``` git switch <branch-name>```