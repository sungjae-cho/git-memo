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

# 10. See modified/untracked files

```bash
git status -u
```

## 10.1. See only modified files

```bash
git ls-files -m
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

# 13. Put away local changes and overwrite the local files with the most recent origin/master branch.

```bash
git fetch --all
git reset --hard origin/master
```
* Reference: [How do I force “git pull” to overwrite local files?](https://stackoverflow.com/questions/1125968/how-do-i-force-git-pull-to-overwrite-local-files)
* Explanation: `git fetch` downloads the latest from remote without trying to merge or rebase anything. Then the `git reset` resets the master branch to what you just fetched. The `--hard` option changes all the files in your working tree to match the files in `origin/master`.

# 14. Duplicating a master repository

[Reference](https://help.github.com/en/articles/duplicating-a-repository)

Open Terminal.

Create a bare clone of the repository.

```bash
git clone --bare https://github.com/exampleuser/old-repository.git
```

Mirror-push to the new repository.

```bash
cd old-repository.git
git push --mirror https://github.com/exampleuser/new-repository.git
```

Remove the temporary local repository you created in step 1.

```bash
cd ..
rm -rf old-repository.git
```
# 15. Duplicating a branch repository

[Reference](https://stackoverflow.com/questions/38027834/git-mirror-a-repo-to-specific-branch)

```bash
git clone --single-branch --branch <branch_name> <github_repo_url>
cd <repo_dir>
git remote add <new_remote> <your_repo_url>
git push -u <new_remote>; git push --tags -u <new_remote>
```
"This will gather the entire history leading up to branch_name, but no commits that are not ancestral to it."

# 16. Resetting remote to a certain commit
```bash
git reset --hard <commit-hash>
git push -f origin master
```
[Reference](https://stackoverflow.com/questions/5816688/resetting-remote-to-a-certain-commit)

# 17. How to update a forked repo as its original repo

Add the forked original repo to the remote and call it `upstream`.

```bash
git remote add upstream https://github.com/<original-repo>.git
```

Fetch all branches of remote `upstream`.

```bash
git fetch upstream
```

Rewrite your `master` with upstream’s `master` using `git rebase`.

```bash
git rebase upstream/master
```

Push your updates to your `master`. You may need to force the push with `--force`.
```bash
git push origin master --force
```

[Reference](https://medium.com/@topspinj/how-to-git-rebase-into-a-forked-repo-c9f05e821c8a)

# 18. `git diff`
See what is added and deleted for <new-commit-id> compared with `<old-commit-id>`.
```
git diff <old-commit-id> <new-commit-id>
```
  
See what is added and deleted for the current state compared with `<old-commit-id>`.
```
git diff <old-commit-id>
```

# 19. Hard reset of a single file

```
git checkout HEAD -- my-file.txt
```

`--` basically means: treat every argument after this point as a file name.

[Reference](https://stackoverflow.com/questions/7147270/hard-reset-of-a-single-file)

# 20. `git add` parts of modified lines

```
git add -p # If you do not need to specify some files to commit
git add -p <file_name> # If you want to commit some lines with a particular file
git add -p <file_name> ... <file_name> # If you want to commit some lines with particular files
```

```
           y - stage this hunk
           n - do not stage this hunk
           q - quit; do not stage this hunk nor any of the remaining ones
           a - stage this hunk and all later hunks in the file
           d - do not stage this hunk nor any of the later hunks in the file
           g - select a hunk to go to
           / - search for a hunk matching the given regex
           j - leave this hunk undecided, see next undecided hunk
           J - leave this hunk undecided, see next hunk
           k - leave this hunk undecided, see previous undecided hunk
           K - leave this hunk undecided, see previous hunk
           s - split the current hunk into smaller hunks
           e - manually edit the current hunk
           ? - print help
```
Key controllers: y, n, q, s, and ?.
