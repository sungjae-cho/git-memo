# Questions
* HEAD?

# How to Use Git and GitHub

**To see the commit log**
```bash
$ git log
```
* The upper one, the newer one.
* You can only see the commit ID, author, date, and commit message for each commit.

**To see which files were changed in each commit**, type the following command.
```bash
$ git log --stat
```
Type `j` for down scrolling, `k` for up scrolling, and `q` for exit.

**To see difference between two commits**
```
$ git diff <commit-id-old> <commit-id-new>
```
If it is easier, you may enter the _first four_ or _more characters_ of the commit ID rather than pasting the entire ID.


**To see the version of Git**
```bash
$ git --version
```
