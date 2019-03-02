# 1. Git initial settings

## 1.1. Configure username and email
```
$ git config --global user.name "Sungjae Cho"
$ git config --global user.email "sungjae.cho.1118@gmail.com"
```
These name and email are not related to the GitHub account.

## 1.2. Set a local GitHub home folder
Set the present working directory as the GitHub home folder 
```
git init
```
# 2. Create a new repository

## 2.1. Make a new repository in GitHub
I made a new repository named as 'git-practice'. Then, I got the repository on 'https://github.com/sungjae-cho/git-practice'.  

## 2.2. Clone the repository on your local directory
```
git clone https://github.com/sungjae-cho/git-practice
```

## 2.3. Make a remote connection between the repository in my GitHub and the local directory
First, change the working directory to the local directory.
```
cd <folder name>
cd git-practice
```
We should make a connection between the repositry in GitHub and the local directory.
```
git remote add <connection name> <repository url in github>
git remote add git-practice https://github.com/sungjae-cho/git-practice
```
We can check what connections exist by typing as follows.
```
git remote -v
```

## 2.4. Push new files into the remote repository.
After you added some files in the local directory, you would like to add the new files into the repository in the GitHub server. 
First, add all new files to the list to commit. '.' means all files in the present working directory. The following command is needed only if there are newly added files.
```
git add <file>
git add .
```
Second, make a commit of all files with a message.
```
git commit -a -m <string message>
git commit -a -m "Something has been updated."
```
Third, push the commit to the remote directory in GitHub.
```
git push <connection name> <user name>
git push git-practice master
```
Once you enter the command, you should type GitHub ID and password to push. Then, you can find that the new files have been added in 'https://github.com/sungjae-cho/git-practice'.

# 3. Update existing files.

## 3.1. Move to the working directory
Change the working directory to the local directory.
```
cd <folder name>
cd git-practice
```

## 3.2. Check the connection with the remote repository in GitHub.
Check what connections exist by typing as follows.
```
git remote -v
```
You can see connection names with their URL.

## 3.3. Push updated files into the remote repository.
Make a commit of all files with a message.
```
git commit -a -m <string message>
git commit -a -m "Something has been updated."
```
Then, push the commit to the remote directory in GitHub.
```
git push <connection name> <user name>
git push git-practice master
```
Once you enter the command, you should type GitHub ID and password to push. Then, you can find that the updated files have been updated in 'https://github.com/sungjae-cho/git-practice'.

# 4. Pull updated files
Update the git directory to the recent one.
```
git pull <remote-name> <branch name>
git pull origin master
```


# 5. Removing a remote
View current remotes.
```
$ git remote -v
origin  https://github.com/OWNER/REPOSITORY.git (fetch)
origin  https://github.com/OWNER/REPOSITORY.git (push)
destination  https://github.com/FORKER/REPOSITORY.git (fetch)
destination  https://github.com/FORKER/REPOSITORY.git (push)
```
Delete the remote 'destination'.
```
$ git remote rm destination
```
Check current remotes.
```
$ git remote -v
origin  https://github.com/OWNER/REPOSITORY.git (fetch)
origin  https://github.com/OWNER/REPOSITORY.git (push)
```

# 6. Delete all uncommitted changes
```bash
$ git reset --hard
```
This throws away all your uncommitted changes. For safety, you should always check that the output of `git status`. [Reference](https://stackoverflow.com/questions/9529078/how-do-i-use-git-reset-hard-head-to-revert-to-a-previous-commit).

# 7. See all the added files that have been changed 

To get just file names, type the following.
```bash
$ git diff --cached --name-only
```

To get detailed information, type the following.
```bash
$ git diff --cached
```

# 8. Move to a particular commit stage

The following command returns the recent commits. `j` is for down scolloing and `k` for up scolling.
```bash
$ git log
```
To see more detailed information about the commit, type the following.
```bash
$ git log --stat
```
Search a particular commit stage where to move over the recent commits.

Type the following to move on to the commit stage. The following command **resets the commit ID as the head**, say, **the last commit ID**.
```bash
$ git reset <commit-id>
```

# 9. See added files 

See files added by the `git ls-files` command.

```bash
git ls-files
```

# 10. See untracked files

```bash
git status -u
```

# 11. Add a commit description to a commit.

[How to commit a change with both “message” and “description” from the command line? [duplicate]](https://stackoverflow.com/questions/16122234/how-to-commit-a-change-with-both-message-and-description-from-the-command-li)

The first way
```bash
git commit -m "Title" -m "Description ..........";
```

The second way
```bash
git commit
```

# 12. Restore a file of a particular commit version

```bash
git checkout <commit_id> <file_path_to_restore>
```
