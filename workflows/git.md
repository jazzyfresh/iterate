git
===

a version-control system for your wildest dreams


QuickStart
----------

### TL;DR
```bash
$ git clone <your repo>    # copy the repo to your computer
$ git status               # show me all the new changes
$ git diff                 # see what changed
$ git add .                # tell git that you are going to save all changes
$ git commit -m "your commit message" # save the files as a "commit", or version
$ git push origin master   # send that new version to the remote repo
```

### 1. Go to GitHub.com, create an account
students get unlimited repos for free

### 2. Create a GitHub repo 

make sure to initialize the repo with a REAME, so you can clone it right away.

### 3. Clone the repo
"clone" is a git term that means "copy this git repository in entirety from
an external source to my local file system". In this case, the external source 
is GitHub and the local file system is your computer.

You can see the git clone command the big green button. Hit the clipboard
icon to copy the link. Make sure you are cloning with HTTPS; otherwise you
will have to do some trickery to clone with SSH.

To clone the repo, you type in the following command in your terminal
```bash
$ git clone <the link you just copied from GitHub>
```
For example, to clone my `sassy` repo, I would run this command
```bash
$ git clone https://github.com/jazzyfresh/sassy.git
Cloning into 'sassy'...
remote: Counting objects: 3, done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
Checking connectivity... done.
```

Now you have cloned your very first repo. Try introspecting the file directory.
```bash
$ cd sassy   # change directories means "view this folder", replace "sassy" with the name of your repo

$ ls -la     # ls means "list files in current folder", 
             # -l gives you timestamp and size details
             # -a shows you all the files, even the hidden files that start with "."
total 8
drwxr-xr-x   4 jasminedahilig  staff   136 Apr 22 16:51 .
drwxr-xr-x@ 37 jasminedahilig  staff  1258 Apr 22 16:51 ..
drwxr-xr-x  12 jasminedahilig  staff   408 Apr 22 16:51 .git
-rw-r--r--   1 jasminedahilig  staff     7 Apr 22 16:51 README.md
```

You can see the README.md file that you created automatically on github.
Huh, there is also this strange folder called `.git`. Let's look at that
```bash
$ ls -la .git
total 40
drwxr-xr-x  12 jasminedahilig  staff  408 Apr 22 16:51 .
drwxr-xr-x   4 jasminedahilig  staff  136 Apr 22 16:51 ..
-rw-r--r--   1 jasminedahilig  staff   23 Apr 22 16:51 HEAD
-rwxr--r--   1 jasminedahilig  staff  309 Apr 22 16:51 config
-rw-r--r--   1 jasminedahilig  staff   73 Apr 22 16:51 description
drwxr-xr-x  11 jasminedahilig  staff  374 Apr 22 16:51 hooks
-rw-r--r--   1 jasminedahilig  staff  104 Apr 22 16:51 index
drwxr-xr-x   3 jasminedahilig  staff  102 Apr 22 16:51 info
drwxr-xr-x   4 jasminedahilig  staff  136 Apr 22 16:51 logs
drwxr-xr-x   7 jasminedahilig  staff  238 Apr 22 16:51 objects
-rw-r--r--   1 jasminedahilig  staff  107 Apr 22 16:51 packed-refs
drwxr-xr-x   5 jasminedahilig  staff  170 Apr 22 16:51 refs
```

Whoa that's a lot of stuff... this is the internals of the version control system.
All of this maintains state of your repo at various versions. In general, you 
never want to mess with this directory. That's why it's hidden. But it was fun to
look at it for a second right?

### 4. Okay, let's save your first version
Add some code by saving files in this directory. If you have an existing project,
it's fine to just copy all those files into this directory. In this case,
I added a new markdown file called `new_file.md` and I added some words to the README.

Git can tell that you made a change to the directory. Git can tell 
when you add or remove files, and when you changed files or moved
them around. You can see an overview of changes by running `git status`.
```bash
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        new_file.md

no changes added to commit (use "git add" and/or "git commit -a")
```

You can see what lines changed in existing files by running `git diff`.
```bash
$ git diff
diff --git a/README.md b/README.md
index e1be8da..ba7b794 100644
--- a/README.md
+++ b/README.md
@@ -1 +1,3 @@
-# sassy
\ No newline at end of file
+# sassy
+
+hey there friends
```

Now you're ready to save your first repo version. We call this making a
"commit". This basically takes a snapshot of the whole file directory
and all the files within in, compresses it in a hash, and saves that compressed
version in the `.git` directory. You don't need to worry about all the details,
just know that `git add` prepares files to be saved, and 
`git commit` saves a version.

```bash
$ git add .
# "git add" tells git you're going to save some changes
# "." indicates that you want to save all changes in the current directory
$ git commit -m "my first commit"
[master 0759006] my first commit
 2 files changed, 4 insertions(+), 1 deletion(-)
 create mode 100644 new_file.md  
```

BOOM. You've saved your first repo version and made your first commit.

### 5. Now let's push to GitHub
Because, you know, in case your computer crashes.
Because, you know, cloud. Because, like, open source and stuff.
Ok, sorry, I'll stop now.


If you run `git status` again, you'll see that your branch is ahead of master
by 1 commit.
```bash
$ git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)
nothing to commit, working directory clean
```

Master? Branch? WTH? These are all terms that relate to more advanced
git practices. I will explain this further in another tutorial, but
just get comfortable with thinking that you're making all your changes on
the "master" branch, for now.

Time to send your changes to GitHub. It will ask you for your GitHub
username and password.
```bash
$ git push origin master
# "git push" means "send changes to remote repo"
# "origin" is the shorthand for GitHub, in this case
# "master" is the name of the branch you are currently changing
Username for 'https://github.com': jazzyfresh
Password for 'https://jazzyfresh@github.com':
Counting objects: 4, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (4/4), 334 bytes | 0 bytes/s, done.
Total 4 (delta 0), reused 0 (delta 0)
To https://github.com/jazzyfresh/sassy.git
   ad6e80a..0759006  master -> master
```

BOOM! Check your repo. Your changes will be saved remotely on GitHub.

version control system
----------------------

Version-control is the act of saving data at various points in time,
or after certain changes have been made, ie at different versions.
Usually when we talk about version control, we're talking about saving
files at different versions. A version control system (VCS) is any software
you use to maintain versions of files.

git
---

`git` is an ancient art of version control. It was invented by the great
technomancer Linux Torvalds for maintaining the Linux operating system.
We call a file directory that is version-controlled by `git` a "git repo"
(short for repository). You can make any folder a git repo by running the
command `git init`. 


