#  1. What is VCS? and Why it is important?

**VCS** stands for _**Version Control System**_ . It is also known as **Revision Control** or _**Source Code Management**_ . It is the management  of chances to documents, computer programs, websites or other collection information. 

These changes are often identified as numbers or letter code, termed as revision number. Each revision is associated with meta data like timestamp, author(a person who made changes), etc. Revisions can be compared, restored or merged.

**Importance of VCS**:

* _**Version tracking and branching**_

  As each and every change is persisted, it allows you to compare files, identify changes and merge the changes if needed prior to committing the code. It also helps to identify which version is currently in development, QA or production. You can also identify easiily the changes which make or break the code. :)

  You can work on different releases of your software at the same time.

* _**Tagging**_

  A tag is just a snapshot of a project in time. You can tag to refer it back later whenever required.

* _**Restoring Previous Version**_

  You can restore previous version of particular file(s). This feature is very helpful in a situation where you accidental delete code or perform changes which breaks existing code.

* _**Collaboration**_

  In a situation where multiple people are working on a same files or folders at a time was never easy. Using VCS, these people can work simultaneously without worries. VCS later allows merging all the changes to one common revision.

* _**Audit**_

  As metadata for every change in the system is maintained, it becomes very easy to auditor to audit as all the data is readily available.

* _**Easy Integration with IDE and other tools**_

  Many VCS can be integrated with IDE's very easily. This helps developer to use VCS from the same tool they are working on. Saves Time! :)

  

# 2. How to clone a Git repository?

we can use Source tree, Git from the command line, or any client as we like to clone our _**Git repository**_ . These instructions show us how to clone our repository using Git from the terminal.

1. From the repository, click **+** in the global sidebar and select **Clone this repository** under **Get to work**.

2. Copy the clone command (either the SSH format or the HTTPS).
   If you are using the SSH protocol, ensure your public key is in Bitbucket and loaded on the local system to which you are cloning.

3. From a terminal window, change to the local directory where you want to clone your repository.

4. Paste the command you copied from Bitbucket, for example:

   ###### CLONE OVER HTTPS:

   ```
   $ git clone https://username@bitbucket.org/teamsinspace/documentation-tests.git
   ```

   ###### CLONE OVER SSH:

   ```
   $ git clone ssh://git@bitbucket.org:teamsinspace/documentation-tests.git
   ```

If the clone was successful, a new sub-directory appears on your local drive in the directory where you cloned your repository. This directory has the same name as the Bitbucket repository that you cloned. The clone contains the files and metadata that Git requires to maintain the changes you make to the source files.

# 3. How to pull/push to remote repository?

The `git push` command  is used to upload local repository content to a remote repository. Pushing is how you transfer commits from your local repository to a remote repo. It's the counterpart to `git fetch`, but whereas fetching imports commits to local branches, pushing exports commits to remote branches. Remote branches are configured using the `git remote` command. Pushing has the potential to overwrite changes, caution should be taken when pushing.

* ##### Git push usage:

```
git push <remote> <branch>
```

Push the specified branch to <remote>, along with all of the necessary commits and internal objects. This creates a local branch in the destination repository. To prevent you from overwriting commits, Git won’t let you push when it results in a non-fast-forward merge in the destination repository.

```
git push <remote> --force
```

Same as the above command, but force the push even if it results in a non-fast-forward merge. Do not use the `--force` flag unless you’re absolutely sure you know what you’re doing.

```
git push <remote> --all
```

Push all of your local branches to the specified remote.

```
git push <remote> --tags
```

Tags are not automatically pushed when you push a branch or use the `--all` option. The `--tags` flag sends all of your local tags to the remote repository.

* ##### Git push discussion:

`git push` is most commonly used to publish an upload local changes to a central repository. After a local repository has been modified a push is executed to share the modifications with remote team members.

![](C:\Users\Apratim\Downloads\04.svg)



The above diagram shows what happens when your local `master` has progressed past the central repository’s `master` and you publish changes by running `git push origin master`. Notice how `git push` is essentially the same as running `git merge master` from inside the remote repository.

## For PULL

The `git pull` command is used to fetch and download content from a remote repository and immediately update the local repository to match that content. Merging remote upstream changes into your local repository is a common task in Git-based collaboration work flows. The `git pull` command is actually a combination of two other commands, `git fetch` followed by `git merge`. In the first stage of operation `git pull` will execute a `git fetch` scoped to the local branch that `HEAD` is pointed at. Once the content is downloaded, `git pull` will enter a merge workflow. A new merge commit will be-created and `HEAD` updated to point at the new commit.

* ##### Git pull usage:

```
git pull <remote>
```

Fetch the specified remote’s copy of the current branch and immediately merge it into the local copy. This is the same as `git fetch <remote>` followed by `git merge origin/<current-branch>`.

```
git pull --no-commit <remote>
```

Similar to the default invocation, fetches the remote content but does not create a new merge commit.

```
git pull --rebase <remote>
```

Same as the previous pull Instead of using `git merge` to integrate the remote branch with the local one, use `git rebase`.

```
git pull --verbose
```

Gives verbose output during a pull which displays the content being downloaded and the merge details.

* ##### Git pull discussion:

You can think of `git pull` as Git's version of `svn update`. It’s an easy way to synchronize your local repository with upstream changes. The following diagram explains each step of the pulling process.

![git pull](C:\Users\Apratim\Downloads\03.svg)



You start out thinking your repository is synchronized, but then `git fetch` reveals that origin's version of master has progressed since you last checked it. Then `git merge` immediately integrates the remote master into the local one.

# 4. How to check the status of the repository?

We use `git ststus` command, to check the current status of the repository.

##### RUN:

```
git status
```

##### RESULT:

```
$ git status
# On branch master
nothing to commit (working directory clean)
```

The command checks the status and reports that there’s nothing to commit, meaning the repository stores the current state of the working directory, and there are no changes to record.

We will use the git status, to keep monitoring the states of both the working directory and the repository.

# 5. How to create and switch to a branch?

Each time you want to commit a bug or a feature, you need to create a branch for it.

To create a new branch there is a `git branch`command.

After you have created a branch, you need to switch in this branch using a `git checkout`command.

But it is also possible to create a new Git branch and switch in this branch using only one `git checkout` command with `-b` option.

Create a new Git branch and checkout:

```
$ git branch <branch_name>
$ git checkout <branch_name>
```

Create a Git branch and checkout in one command:

```
$ git checkout -b <branch_name>
```

# 6. How to connect to a remote a repository?

The `git remote` command is one piece of the broader system which is responsible for syncing changes. Records registered through the `git remote` command are used in conjunction with the `git fetch`, `git push`, and `git pull` commands. These commands all have their own syncing responsibilities which can be explored on the corresponding links.

* ##### Git remote:

The `git remote` command lets you create, view, and delete connections to other repositories. Remote connections are more like bookmarks rather than direct links into other repositories. Instead of providing real-time access to another repository, they serve as convenient names that can be used to reference a not-so-convenient URL.

For example, the following diagram shows two remote connections from your repo into the central repo and another developer’s repo. Instead of referencing them by their full URLs, you can pass the origin and john shortcuts to other Git commands.

![](C:\Users\Apratim\Downloads\01.svg)

```
git remote
```

List the remote connections you have to other repositories.

```
git remote -v
```

Same as the above command, but include the URL of each connection.

Let's check if this worked out ok:

```
$ git remote -v
crash-course-remote   https://github.com/gittower/git-crash-course-remote.git (fetch)
crash-course-remote   https://github.com/gittower/git-crash-course-remote.git (push)
origin   https://github.com/gittower/git-crash-course (fetch)
origin   https://github.com/gittower/git-crash-course (push)
```

Note that each remote repository consists of two lines: the first one is the "fetch URL" which is used for reading access. The second one is the "push URL", used when you want to write data to the remote. In many cases, both URLs are the same. However, you can also use this to define different URLs for read and write access (for security and performance reasons).

Also note that you can connect as many remotes to a local repository as you like. In my case, you saw that another remote named "origin" is already present - although we didn't configure this! This was added by Git automatically when we cloned from the remote server (which we did at the beginning of this book). Exactly as with the "master" branch, the name "origin" for this remote is only a naming convention. It's just a normal remote repository like any other.

# 7. How to merge two branch?

`Git merge` will combine multiple sequences of commits into one unified history. In the most frequent use cases, `git merge` is used to combine two branches. The following examples in this document will focus on this branch merging pattern. In these scenarios, `git merge` takes two commit pointers, usually the branch tips, and will find a common base commit between them. Once Git finds a common base commit it will create a new "merge commit" that combines the changes of each queued merge commit sequence.

Say we have a new branch feature that is based off the `master` branch. We now want to merge this feature branch into `master`.

![](C:\Users\Apratim\Downloads\Branch-2.png)



Invoking this command will merge the specified branch feature into the current branch, we'll assume `master`. Git will determine the merge algorithm automatically (discussed below).

![](C:\Users\Apratim\Downloads\Branch-1.png)



Merge commits are unique against other commits in the fact that they have two parent commits. When creating a merge commit Git will attempt to auto magically merge the separate histories for you. If Git encounters a piece of data that is changed in both histories it will be unable to automatically combine them. This scenario is a version control conflict and Git will need user intervention to continue.

There are two main ways Git will merge: Fast Forward and Three way

* ##### Fast Forward Merge:

The code below creates a new branch, adds two commits to it, then integrates it into the main line with a fast-forward merge.

```
# Start a new feature
git checkout -b new-feature master
# Edit some files
git add <file>
git commit -m "Start a feature"
# Edit some files
git add <file>
git commit -m "Finish a feature"
# Merge in the new-feature branch
git checkout master
git merge new-feature
git branch -d new-feature
```

This is a common workflow for short-lived topic branches that are used more as an isolated development than an organizational tool for longer-running features.

Also note that Git should not complain about the `git branch -d`, since new-feature is now accessible from the master branch.

In the event that you require a merge commit during a fast forward merge for record keeping purposes you can execute `git merge` with the `--no-ff`option.

```
git merge --no-ff <branch>
```

This command merges the specified branch into the current branch, but always generates a merge commit (even if it was a fast-forward merge). This is useful for documenting all merges that occur in your repository.

* ##### 3-way merge:

a 3-way merge because `master` progresses while the feature is in-progress. This is a common scenario for large features or when several developers are working on a project simultaneously.

```
Start a new feature
git checkout -b new-feature master
# Edit some files
git add <file>
git commit -m "Start a feature"
# Edit some files
git add <file>
git commit -m "Finish a feature"
# Develop the master branch
git checkout master
# Edit some files
git add <file>
git commit -m "Make some super-stable changes to master"
# Merge in the new-feature branch
git merge new-feature
git branch -d new-feature
```

Note that it’s impossible for Git to perform a fast-forward merge, as there is no way to move `master` up to `new-feature` without backtracking.

For most workflows, `new-feature` would be a much larger feature that took a long time to develop, which would be why new commits would appear on `master` in the meantime. If your feature branch was actually as small as the one in the above example, you would probably be better off rebasing it onto `master` and doing a fast-forward merge. This prevents superfluous merge commits from cluttering up the project history.

# 8. How to resolve merge conflicts?

If the two branches you're trying to merge both changed the same part of the same file, Git won't be able to figure out which version to use. When such a situation occurs, it stops right before the merge commit so that you can resolve the conflicts manually.

The great part of Git's merging process is that it uses the familiar edit/stage/commit workflow to resolve merge conflicts. When you encounter a merge conflict, running the `git status` command shows you which files need to be resolved. For example, if both branches modified the same section of `hello.py`, you would see something like the following:

```
On branch master
Unmerged paths:
(use "git add/rm ..." as appropriate to mark resolution)
both modified: hello.py
```

## How conflicts are presented

When Git encounters a conflict during a merge, It will edit the content of the affected files with visual indicators that mark both sides of the conflicted content. These visual markers are: <<<<<<<, =======, and >>>>>>>. Its helpful to search a project for these indicators during a merge to find where conflicts need to be resolved.

```
here is some content not affected by the conflict
<<<<<<< master
this is conflicted text from master
=======
this is conflicted text from feature branch
>>>>>>> feature branch;
```

Generally the content before the `=======` marker is the receiving branch and the part after is the merging branch.

Once you've identified conflicting sections, you can go in and fix up the merge to your liking. When you're ready to finish the merge, all you have to do is run `git add` on the conflicted file(s) to tell Git they're resolved. Then, you run a normal `git commit` to generate the merge commit. It’s the exact same process as committing an ordinary snapshot, which means it’s easy for normal developers to manage their own merges.

Note that merge conflicts will only occur in the event of a 3-way merge. It’s not possible to have conflicting changes in a fast-forward merge. 

# 9. How to commit changes?

`git commmit`

**The "commit" command is used to save your changes to the local repository.**

Note that you have to explicitly *tell* Git which changes you want to include in a commit *before* running the "git commit" command. This means that a file won't be *automatically* included in the next commit just because it was changed. Instead, you need to use the "git add" command to mark the desired changes for inclusion.

**Important option**:

* `-m` <messages>

  **Sets the commit's message.** Make sure to provide a concise description that helps your teammates (and yourself) understand what happened.

* `-a`

  **Includes all currently changed files in this commit.** Keep in mind, however, that untracked (new) files are not included.

* `--ammend`

  **Rewrites the very last commit** with any currently staged changes and/or a new commit message. Git will rewrite the last commit and effectively replace it with the amended one. Note that such a rewriting of commits should only be performed on commits that have *not* been pushed to a remote repository, yet.

For a basic workflow, you can use the "git add" command to stage changes for the next commit. The actual commit command will then wrap up the mentioned changes in a new commit object:

```
git add index.html css/styles.css
git commit -m "Change titles and styling on homepage"
```

If you have lots of changed files in your working copy - and want all of them included in the next commit - you can make use of the "-a" parameter and thereby omit the "git add" step:

```
git commit -a -m "Change titles and styling on homepage"
```

The "--amend" option comes in handy, for example, when you mistyped the last commit's message or forgot to add a change. The following example will correct the very last commit by overwriting its message and adding another change:

```
git add forgotten-change.js
git commit --amend -m "New commit message"
```

# 10. How to stash changes?

`git stash` temporarily shelves (or *stashes*) changes you've made to your working copy so you can work on something else, and then come back and re-apply them later on. Stashing is handy if you need to quickly switch context and work on something else, but you're mid-way through a code change and aren't quite ready to commit.

- Git Stash
  - [Stashing your work](https://www.atlassian.com/git/tutorials/saving-changes/git-stash#stashing-your-work)
  - [Re-applying your stashed changes](https://www.atlassian.com/git/tutorials/saving-changes/git-stash#re-applying-your-stashed-changes)
  - [Stashing untracked or ignored files](https://www.atlassian.com/git/tutorials/saving-changes/git-stash#stashing-untracked-or-ignored)
  - [Managing multiple stashes](https://www.atlassian.com/git/tutorials/saving-changes/git-stash#managing-multiple-stashes)
  - [Viewing stash diffs](https://www.atlassian.com/git/tutorials/saving-changes/git-stash#viewing-stash-diffs)
  - [Partial stashes](https://www.atlassian.com/git/tutorials/saving-changes/git-stash#partial-stashes)
  - [Creating a branch from your stash](https://www.atlassian.com/git/tutorials/saving-changes/git-stash#creating-a-branch-from-your-stash)
  - [Cleaning up your stash](https://www.atlassian.com/git/tutorials/saving-changes/git-stash#cleaning-up-your-stash)
  - [How git stash works](https://www.atlassian.com/git/tutorials/saving-changes/git-stash#how-git-stash-works)

## Stashing your work

The `git stash` command takes your uncommitted changes (both staged and unstaged), saves them away for later use, and then reverts them from your working copy. For example:

```
$ git status
On branch master
Changes to be committed:
new file: style.css
Changes not staged for commit:
modified: index.html
$ git stash
Saved working directory and index state WIP on master: 5002d47 our new homepage
HEAD is now at 5002d47 our new homepage
$ git status
On branch master
nothing to commit, working tree clean
```

At this point you're free to make changes, create new commits, switch branches, and perform any other Git operations; then come back and re-apply your stash when you're ready.

Note that the stash is local to your Git repository; stashes are not transferred to the server when you push.

## Re-applying your stashed changes

You can reapply previously stashed changes with `git stash pop`:

```
$ git status
On branch master
nothing to commit, working tree clean
$ git stash pop
On branch master
Changes to be committed:
new file: style.css
Changes not staged for commit:
modified: index.html
Dropped refs/stash@{0} (32b3aa1d185dfe6d57b3c3cc3b32cbf3e380cc6a)
```

*Popping* your stash removes the changes from your stash and reapplies them to your working copy.

Alternatively, you can reapply the changes to your working copy *and* keep them in your stash with `git stash apply`:

```
$ git stash apply
On branch master
Changes to be committed:
new file: style.css
Changes not staged for commit:
modified: index.html
```

This is useful if you want to apply the same stashed changes to multiple branches.

Now that you know the basics of stashing, there is one caveat with `git stash` you need to be aware of: by default Git *won't* stash changes made to untracked or ignored files.

## Stashing untracked or ignored files

By default, running `git stash` will stash:

- changes that have been added to your index (staged changes)
- changes made to files that are currently tracked by Git (unstaged changes)

But it will **not** stash:

- new files in your working copy that have not yet been staged
- files that have been [ignored](https://www.atlassian.com/git/tutorials/gitignore)

So if we add a third file to our example above, but don't stage it (i.e. we don't run `git add`), `git stash` won't stash it.

```
$ script.js
$ git status
On branch master
Changes to be committed:
new file: style.css
Changes not staged for commit:
modified: index.html
Untracked files:
script.js
$ git stash
Saved working directory and index state WIP on master: 5002d47 our new homepage
HEAD is now at 5002d47 our new homepage
$ git status
On branch master
Untracked files:
script.js
```

Adding the `-u` option (or `--include-untracked`) tells `git stash` to also stash your untracked files:

```
$ git status
On branch master
Changes to be committed:
new file: style.css
Changes not staged for commit:
modified: index.html
Untracked files:
script.js
$ git stash -u
Saved working directory and index state WIP on master: 5002d47 our new homepage
HEAD is now at 5002d47 our new homepage
$ git status
On branch master
nothing to commit, working tree clean
```

You can include changes to [ignored](https://www.atlassian.com/git/tutorials/gitignore) files as well by passing the `-a` option (or `--all`) when running `git stash`.





## Managing multiple stashes

You aren't limited to a single stash. You can run `git stash` several times to create multiple stashes, and then use `git stash list` to view them. By default, stashes are identified simply as a "WIP" – work in progress – on top of the branch and commit that you created the stash from. After a while it can be difficult to remember what each stash contains:

```
$ git stash list
stash@{0}: WIP on master: 5002d47 our new homepage
stash@{1}: WIP on master: 5002d47 our new homepage
stash@{2}: WIP on master: 5002d47 our new homepage
```

To provide a bit more context, it's good practice to annotate your stashes with a description, using `git stash save "message"`:

```
$ git stash save "add style to our site"
Saved working directory and index state On master: add style to our site
HEAD is now at 5002d47 our new homepage
$ git stash list
stash@{0}: On master: add style to our site
stash@{1}: WIP on master: 5002d47 our new homepage
stash@{2}: WIP on master: 5002d47 our new homepage
```

By default, `git stash pop` will re-apply the most recently created stash: `stash@{0}`

You can choose which stash to re-apply by passing its identifier as the last argument, for example:

```
$ git stash pop stash@{2}
```

## Viewing stash diffs

You can view a summary of a stash with `git stash show`:

```
$ git stash show
index.html | 1 +
style.css | 3 +++
2 files changed, 4 insertions(+)
```

Or pass the `-p` option (or `--patch`) to view the full diff of a stash:

```
$ git stash show -p
diff --git a/style.css b/style.css
new file mode 100644
index 0000000..d92368b
--- /dev/null
+++ b/style.css
@@ -0,0 +1,3 @@
+* {
+ text-decoration: blink;
+}
diff --git a/index.html b/index.html
index 9daeafb..ebdcbd2 100644
--- a/index.html
+++ b/index.html
@@ -1 +1,2 @@
+<link rel="stylesheet" href="style.css"/>
```

## Partial stashes

You can also choose to stash just a single file, a collection of files, or individual changes from within files. If you pass the `-p` option (or `--patch`) to `git stash`, it will iterate through each changed "hunk" in your working copy and ask whether you wish to stash it:

```
$ git stash -p
diff --git a/style.css b/style.css
new file mode 100644
index 0000000..d92368b
--- /dev/null
+++ b/style.css
@@ -0,0 +1,3 @@
+* {
+ text-decoration: blink;
+}
Stash this hunk [y,n,q,a,d,/,e,?]? y
diff --git a/index.html b/index.html
index 9daeafb..ebdcbd2 100644
--- a/index.html
+++ b/index.html
@@ -1 +1,2 @@
+<link rel="stylesheet" href="style.css"/>
Stash this hunk [y,n,q,a,d,/,e,?]? n
```



You can hit **?** for a full list of hunk commands. Commonly useful ones are:

| **Command** | **Description**                                              |
| ----------- | ------------------------------------------------------------ |
| */*         | search for a hunk by regex                                   |
| *?*         | help                                                         |
| *n*         | don't stash this hunk                                        |
| *q*         | quit (any hunks that have already been selected will be stashed) |
| *s*         | split this hunk into smaller hunks                           |
| *y*         | stash this hunk                                              |

There is no explicit "abort" command, but hitting `CTRL-C`(SIGINT) will abort the stash process.

## Creating a branch from your stash

If the changes on your branch diverge from the changes in your stash, you may run into conflicts when popping or applying your stash. Instead, you can use `git stash branch` to create a new branch to apply your stashed changes to:

```
$ git stash branch add-stylesheet stash@{1}
Switched to a new branch 'add-stylesheet'
On branch add-stylesheet
Changes to be committed:
new file: style.css
Changes not staged for commit:
modified: index.html
Dropped refs/stash@{1} (32b3aa1d185dfe6d57b3c3cc3b32cbf3e380cc6a)
```

This checks out a new branch based on the commit that you created your stash from, and then pops your stashed changes onto it.

## Cleaning up your stash

If you decide you no longer need a particular stash, you can delete it with `git stash drop`:

```
$ git stash drop stash@{1}
Dropped stash@{1} (17e2697fd8251df6163117cb3d58c1f62a5e7cdb)
```

Or you can delete all of your stashes with:

```
$ git stash clear
```

## How git stash works

If you just wanted to know how to use `git stash`, you can stop reading here. But if you're curious about how Git (and `git stash`) works under the hood, read on!

Stashes are actually encoded in your repository as commit objects. The special ref at `.git/refs/stash` points to your most recently created stash, and previously created stashes are referenced by the `stash` ref's reflog. This is why you refer to stashes by `stash@{n}:` you're actually referring to the nth reflog entry for the `stash` ref. Since a stash is just a commit, you can inspect it with `git log`:

```
$ git log --oneline --graph stash@{0}
*-. 953ddde WIP on master: 5002d47 our new homepage
|\ \
| | * 24b35a1 untracked files on master: 5002d47 our new homepage
| * 7023dd4 index on master: 5002d47 our new homepage
|/
* 5002d47 our new homepage
```

Depending on what you stashed, a single `git stash` operation creates either two or three new commits. The commits in the diagram above are:

- `stash@{0}`, a new commit to store the tracked files that were in your working copy when you ran `git stash`

- `stash@{0}`'s first parent, the pre-existing commit that was at HEAD when you ran `git stash`

- `stash@{0}`'s second parent, a new commit representing the index when you ran `git stash`

- ```
  stash@{0}
  ```

  's third parent, a new commit representing untracked files that were in your working copy when you ran

   

  ```
  git stash
  ```

  . This third parent only created if:

  - your working copy actually contained untracked files; and
  - you specified the `--include-untracked` or `--all` option when invoked `git stash`.

How `git stash` encodes your worktree and index as commits:

- Before stashing, your worktree may contain changes to tracked files, untracked files, and ignored files. Some of these changes may also be staged in the index.

  ![Before stashing](https://wac-cdn.atlassian.com/dam/jcr:3a2ede93-1f2d-45ae-9e0b-167cc0362f37/03.2017-12-12-00-28-29.svg)

- Invoking `git stash` encodes any changes to tracked files as two new commits in your DAG: one for unstaged changes, and one for changes staged in the index. The special `refs/stash` ref is updated to point to them.

  ![Git stash](https://wac-cdn.atlassian.com/dam/jcr:35edaf68-e8b1-484e-b5f0-292c532f048a/04.2017-12-12-00-28-29.svg)

- Using the `--include-untracked` option also encodes any changes to untracked files as an additional commit.

  ![Git stash --include-untracked](https://wac-cdn.atlassian.com/dam/jcr:f7dd5493-a98d-449e-ae37-146d6270ccf7/05.2017-12-12-00-28-29.svg)

- Using the `--all` option includes changes to any ignored files alongside changes to untracked files in the same commit.

  ![Git Stash --all](https://wac-cdn.atlassian.com/dam/jcr:446fad60-0ff5-4383-8177-a5fc2813364d/06.2017-12-12-00-28-29.svg)

   

When you run `git stash pop`, the changes from the commits above are used to update your working copy and index, and the stash is shuffled to remove the popped commit. Note that the popped commits aren't immediately deleted, but do become candidates for future garbage collection.



_**References:**_

       1. (https://www.linkedin.com/pulse/what-vcs-version-control-system-7-ways-choose-perfect-nilesh-kanawade)
       2. (https://confluence.atlassian.com/bitbucket/clone-a-repository-223217891.html)
       3. (https://www.atlassian.com/git/tutorials/syncing/git-push)
       4. (https://www.atlassian.com/git/tutorials/syncing/git-pull)
       5. (https://githowto.com/checking_status)
       6. (https://www.shellhacks.com/git-create-new-branch-and-checkout/)
       7. (https://www.atlassian.com/git/tutorials/syncing)
       8. (https://www.git-tower.com/learn/git/ebook/en/command-line/remote-repositories/connecting-remote-repositories)
       9. (https://www.atlassian.com/git/tutorials/using-branches/git-merge)
       10. (https://www.git-tower.com/learn/git/commands/git-commit)
       11. (https://www.atlassian.com/git/tutorials/saving-changes/git-stash#viewing-stash-diffs)