# Git and GitHub

GitHub - a cloud based service to manage Git repositories (Microsoft)

Git - opensource VCS

Perhaps one of the easiest approaches is to create a new Repository on GitHub and then **<mark>clone</mark>** the repository by copying the SSH link

![](file:///E:/Brainscape/GIT/new%20RepoClone.png)

* then at the commandline on your local PC
* in your chosen folder
* assuming git has been installed


```bash
leste@AQUARIUS MINGW64 ~/IdeaProjects
$ git clone git@github.com:ldeeley/GitHubPracticeMarkTwo.git
Cloning into 'GitHubPracticeMarkTwo'...
warning: You appear to have cloned an empty repository.

leste@AQUARIUS MINGW64 ~/IdeaProjects
$
```

You have now created a local GIT repository. This is essentially a directory which GIT track. Move into the folder and list the contents

```bash
leste@AQUARIUS MINGW64 ~/IdeaProjects
$ cd GitHubPracticeMarkTwo

leste@AQUARIUS MINGW64 ~/IdeaProjects/GitHubPracticeMarkTwo (main)
$ ls -al
total 12
drwxr-xr-x 1 leste 197609 0 Apr  5 09:18 ./
drwxr-xr-x 1 leste 197609 0 Apr  5 09:18 ../
drwxr-xr-x 1 leste 197609 0 Apr  5 09:18 .git/
```

(main) refers to the branch
there is nothing being tracked by GIT at this stage

using IDE, add a file (GitPractice.java) in this folder

```bash
leste@AQUARIUS MINGW64 ~/IdeaProjects/GitHubPracticeMarkTwo (main)
$ ls
GitPractice.java

leste@AQUARIUS MINGW64 ~/IdeaProjects/GitHubPracticeMarkTwo (main)
$ git status
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .idea/
        GitPractice.java

nothing added to commit but untracked files present (use "git add" to track)

leste@AQUARIUS MINGW64 ~/IdeaProjects/GitHubPracticeMarkTwo (main)
$
```

the file is still not tracked by GIT until it is <mark>added</mark>

```bash
leste@AQUARIUS MINGW64 ~/IdeaProjects/GitHubPracticeMarkTwo (main)
$ git add GitPractice.java
warning: in the working copy of 'GitPractice.java', CRLF will be replaced by LF the next time Git touches it

leste@AQUARIUS MINGW64 ~/IdeaProjects/GitHubPracticeMarkTwo (main)
$ git status
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   GitPractice.java

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .idea/


leste@AQUARIUS MINGW64 ~/IdeaProjects/GitHubPracticeMarkTwo (main)
$
```
so the above shows that a file GitPractice.java has been added and is being tracked by GIT but another file .idea is NOT being tracked by GIT. This is from the IDE and don't want this, so that's fine.

finally, commit the file to GIT. Need to add a COMMIT message !


```bash
leste@AQUARIUS MINGW64 ~/IdeaProjects/GitHubPracticeMarkTwo (main)
$ git commit -m "Init commit of GitPractice.java" .
warning: in the working copy of 'GitPractice.java', CRLF will be replaced by LF the next time Git touches it
[main (root-commit) a68c4d1] Init commit of GitPractice.java
 1 file changed, 7 insertions(+)
 create mode 100644 GitPractice.java

leste@AQUARIUS MINGW64 ~/IdeaProjects/GitHubPracticeMarkTwo (main)
$ git status
On branch main
Your branch is based on 'origin/main', but the upstream is gone.
  (use "git branch --unset-upstream" to fixup)

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .idea/

nothing added to commit but untracked files present (use "git add" to track)

leste@AQUARIUS MINGW64 ~/IdeaProjects/GitHubPracticeMarkTwo (main)
$
```

* the untracked directory is from the IDE and can be ignored using .gitignore
* the file is now being tracked by GIT - LOCALLY - GitHub does not have these changes yet.

Now to synch the changes with GitHub i.e PUSH the LOCAL changes up to GitHub repository

```bash
leste@AQUARIUS MINGW64 ~/IdeaProjects/GitHubPracticeMarkTwo (main)
$ git push -u origin main
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 337 bytes | 168.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To github.com:ldeeley/GitHubPracticeMarkTwo.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.

leste@AQUARIUS MINGW64 ~/IdeaProjects/GitHubPracticeMarkTwo (main)
$
```

Now, do the following to the GitPractice.java

* modify the file
* check the status
```bash
leste@AQUARIUS MINGW64 ~/IdeaProjects/GitHubPracticeMarkTwo (main)
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   GitPractice.java

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .idea/

no changes added to commit (use "git add" and/or "git commit -a")

leste@AQUARIUS MINGW64 ~/IdeaProjects/GitHubPracticeMarkTwo (main)
$
```

so, Git indicates that GitPractice.java has been modified but the those changes needs to be added to staging (Step1) and then commit (Step2) and ultimately push (Step3) to remote GitHub
add the modified file to staging
commit the file

```bash
leste@AQUARIUS MINGW64 ~/IdeaProjects/GitHubPracticeMarkTwo (main)
$ git add .
warning: in the working copy of 'GitPractice.java', CRLF will be replaced by LF the next time Git touches it
warning: in the working copy of '.idea/GitHubPracticeMarkTwo.iml', CRLF will be replaced by LF the next time Git touches it
warning: in the working copy of '.idea/misc.xml', CRLF will be replaced by LF the next time Git touches it
warning: in the working copy of '.idea/workspace.xml', CRLF will be replaced by LF the next time Git touches it

leste@AQUARIUS MINGW64 ~/IdeaProjects/GitHubPracticeMarkTwo (main)
$ git commit -m "modified file" GitPractice.java
warning: in the working copy of 'GitPractice.java', CRLF will be replaced by LF the next time Git touches it
[main fc53948] modified file
 1 file changed, 1 insertion(+)

leste@AQUARIUS MINGW64 ~/IdeaProjects/GitHubPracticeMarkTwo (main)
$
```
finally, need to push the amended file up to GitHub (Step 3)

```bash
leste@AQUARIUS MINGW64 ~/IdeaProjects/GitHubPracticeMarkTwo (main)
$ git push -u origin main
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 296 bytes | 296.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To github.com:ldeeley/GitHubPracticeMarkTwo.git
   a68c4d1..fc53948  main -> main
branch 'main' set up to track 'origin/main'.

leste@AQUARIUS MINGW64 ~/IdeaProjects/GitHubPracticeMarkTwo (main)
$
```
the commits can now be seen on the main branch in the remote repo ldeeley/GitHubPracticeMarkTwo

![](file:///E:/Brainscape/GIT/two%20commits.png)

Let's create a new branch to develop a seperate part of the project

```bash
leste@AQUARIUS MINGW64 ~/IdeaProjects/GitHubPracticeMarkTwo (main)
$ git branch
* main

leste@AQUARIUS MINGW64 ~/IdeaProjects/GitHubPracticeMarkTwo (main)
$
```
the above shows that at the moment there is only one branch main and the asterisk * shows that this is the current branch

```bash
leste@AQUARIUS MINGW64 ~/IdeaProjects/GitHubPracticeMarkTwo (main)
$ git checkout -b bellsnwhistles
Switched to a new branch 'bellsnwhistles'

leste@AQUARIUS MINGW64 ~/IdeaProjects/GitHubPracticeMarkTwo (bellsnwhistles)
$ git branch
* bellsnwhistles
  main

leste@AQUARIUS MINGW64 ~/IdeaProjects/GitHubPracticeMarkTwo (bellsnwhistles)
$
```
the above creates a new branch called 'bellsnwhistles' and switches to it - note the asterisk






