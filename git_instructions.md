![git logo](git_logo.png "git logo")

> # Workin' with git

> ## Check git is installed and available

First install Visual Studio Code. 
Then check a git version. You should run commmand ```git --version``` in the terminal. 

```
git --version
```

You'll see a version number if git is installed otherwise you'll get an error message.

If it's just not installed download the latest version of git from https://git-scm.com/downloads or install it from [PowerShell](https://github.com/PowerShell/PowerShell/releases/download/v7.2.1/PowerShell-7.2.1-win-x64.msi) via winget command.

[Download the latest version of git from official git website](https://git-scm.com/downloads "Another linkt to git downloads").

> ## Set-up git

First read at least three first chapters [The Book of Git](https://git-scm.com/book/ru/v2 "Free version of Pro Git book") >:D

You should introduce yourself to git. Enter your name and an email.

```
git config --global user.name «Your name in english»
git config --global user.email ваша_почта@example.com
```

To check setting run

```
git config --list
```

Create a folder for git repository on your PC. Open it in Visual Studio Code and run command to initialize git.

```
git init
```

After that git creates an empty git repository with a .git directory, subdirectories & template files. And intial branch without commits will be created.

> ## Basic git commands

Only a few commands are needed for the basic use case of git for maintaining the history of changes.

This command ```git add``` add file content to the index. It updates the index using content found in the working tree and prepares the content for the subsequent commit. The index holds a snapshot of the content of the working tree, but not a whole file. An it contains changes made on the last commit.
```
git add your_file.md
```
 
This command record changes to the repository. It takes all data added with ```git add``` and saves a snapshot in git internal database and makes it the last point in your branch.
```
git commit -m "Your_commit_comment"
```

If you wanna to commit whithout add you should run command with an option ```-a```.
```
git commit -a -m "Your_commit_comment"
```
The next command show you the working tree status.

```
git status
```

This command ```git diff``` show you difference between the working tree and the index or a tree.
Show difference between you working copy & the index.
```
git diff
```
Show difference between the index & the last commit.
```
git diff --staged
```
Show difference between any last commits in branches.
```
git diff master another_branch
```

The command `git checkout` move pointer HEAD to a different branch. Also ypu can restore a historic version of a specific file. Use this command to switch between commmits or branches. See other feature below.
```
git checkout
```



Use this command ```git log``` to show commit history.
```
git log
```
Use it with option to show it like a tree in graphical mode.
```
git log --graph
```
A typical output of ```git log --graph``` looks like this:

![git log --graph output](git_log_graph.png "git log --graph")



> ## Ignore files

If you want to exclude files from tracking by git you should create ```.gitignore``` file and fill it with filenames or file masks. Like this ```*.jpg```.

> ## Create branches

To create branch and switch to it:
```
git chechout -b new_branch_name
```
Branch is a simple movable pointer to the one of the commits. Usuaally the latest in a chain of commits. The main branch in git is ```master```.
To create new branch run: 
```
git branch branch_name
```
To switch between branches run:
```
git checkout branch_name
```
> ## Merge branches
To merge two or more development histories use `git merge` command. The merge will be provided with an actual branch you are in and a branch you selected:
```
git merge branch_name
```

You can also create new branch and switch to it with `git switch` command. But be warned about this command. It is experimental and its behavior may change. 
```
git switch -c new_branch_name
```
Use `--no-commit` to perform merge with stop before commit. It is used to inspect and tweak the merge result befor committing.

Warning: Running git merge with non-trivial uncommitted changes is discouraged: while possible, it may leave you in a state that is hard to back out of in the case of a conflict.
> ## Solve conflicts
There are two types of conflicts: 
* Git fails to start the merge. 
* Git fails during the merge.

Git will fail to start merge if there are pending changes in the working directory or staging area of the current project. You should commit pending changes and try again.

Git will fail during the merge because of conflict of contents in files which it merge. It indicates a conflict between the current local branch and the branch being merged.
When conflict occurs you can resolve it by accepting current changes, incoming changes, both changes or compare it.

You can abort process of merging and restore the state before it.
```
git merge --abort
```


> ## Delete branches
Use `git branch` with the option`-d` to delete branches.
```
git branch -d local_branch_name
```

Use the command below to delete branch when it contains commits that not fully merged into local branches. Please be careful with the capital dee "-D" option. 

```
git branch -D local_branch_name
```
To show only remote repositories use options `-r` or `--remotes`:
```
git branch -r
```
To delete a remote branch use `git push` command:
``` 
git push origin --delete remote_branch_name
```

> ## Branching & switching between commits
You can temporarily switch between commits to revise it by using `git checkout commit_number`. This command updates the HEAD to point to either the specified branch or commit. When the HEAD points to a branch it is okay, but when you point to commit Git switches to detached HEAD state. This warning is important because all of your work that you are doing in this state is detached from the rest of development. If you continue to commit changes in this state there would be no branch to get back to it. So develop only in branch but not in the detached HEAD state.

If you want to get back to actual state use for example `git checkout master`.

You can switch to commit and continue work from it use `git checkout -b new_branch_name commit_number`

> ## Working with a remote repositories

Git allows collaboration with others developers via distributed collaboration model. All developers got their own copy of the repository and they work with it. Users typically share a bunch of commits. Git allows sharing entire branches between repositories.  

Use `git remote` to create, delete and review connections to other remote repositories. Remote repositories in git are like bookmarks and do not give you a real-time connection to it.

Use `git remote` or `git remote -v ` to view available remote connections.

Use the command below to add connections. "Name" is a convenient tag to your remote repository. You can also add it by configuring `/.git/config` file.
```
git remote add name URL
```
Use `git remote rm name` command to delete connection.


