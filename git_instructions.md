# Workin' with git

## Check git is installed and available

First install Visual Studio Code. 
Then check a git version. You should run commmand in terminal: ```git --version```

```
git --version
```

You'll see a version number if git is installed otherwise you'll get an error message.

If it is just not installed download the latest version of git from https://git-scm.com/downloads.

[Download last version of git from git website](https://git-scm.com/downloads).

## Set-up git

You should introduce yourself to git.

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


