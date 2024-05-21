# git_task

## Getting Started:

### Initialize Your Environment:

```
Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main)
$ touch test{1..4}.md
git add test1.md && git commit -m "chore: Create initial file"
git add test2.md && git commit -m "chore: Create another file"
git add test3.md && git commit -m "chore: Create third and fourth files"
[main (root-commit) 5cebb83] chore: Create initial file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test1.md
[main 1fef82b] chore: Create another file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test2.md
[main 6e87065] chore: Create third and fourth files
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md
```

## Part 1: Refining Git History (10 Challenges)

### 1.Missing File Fix:

```
Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main)
$ git status
On branch main
Your branch is based on 'origin/main', but the upstream is gone.
  (use "git branch --unset-upstream" to fixup)

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        test4.md

nothing added to commit but untracked files present (use "git add" to track)

Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main)
$ git log
commit 6e8706516c79c2cdf1f8e92ad1cb1837199dbbcc (HEAD -> main)
Author: Angekarara <mbabange2020@gmail.com>
chore: Create third file chore:Create fourth file
Date:   Tue May 21 13:24:55 2024 +0200

    chore: Create third and fourth files

commit 1fef82b30d7ae4b49c0f3f7fff1ce47f8e400892
Author: Angekarara <mbabange2020@gmail.com>
Date:   Tue May 21 13:24:55 2024 +0200

    chore: Create another file

commit 5cebb838a20b0f0ffbca57d5813de81a6dfa322d
Author: Angekarara <mbabange2020@gmail.com>
Date:   Tue May 21 13:24:54 2024 +0200

    chore: Create initial file

Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main)
$ git add test4.md

Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main)
$ git commit --amend
[main ce49105] chore: Create third file chore:Create fourth file
 Date: Tue May 21 13:24:55 2024 +0200
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md
 create mode 100644 test4.md
```

### 2.Editing Commit History:

```
edit 1fef82b chore: Create second file
chore: Create second file

Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main)
$ git rebase -i HEAD~2
Stopped at 1fef82b...  chore: Create second file
You can amend the commit now, with

  git commit --amend

Once you are satisfied with your changes, run

  git rebase --continue

Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main|REBASE 1/2)
$ git commit --amend
[detached HEAD 294e24c] chore: Create second file
 Date: Tue May 21 13:24:55 2024 +0200
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test2.md
```

### 3.Keeping History Tidy - Squashing Commits:

```
Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main|REBASE 1/2)
$ git commit --amend
[detached HEAD 294e24c] chore: Create second file
 Date: Tue May 21 13:24:55 2024 +0200
pick 5cebb83 chore: Create initial file
# This is a combination of 2 commits.
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test2.md

Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main|REBASE 1/2)
$ git rebase -i --root
fatal: It seems that there is already a rebase-merge directory, and
I wonder if you are in the middle of another rebase.  If that is the
case, please try
        git rebase (--continue | --abort | --skip)
If that is not the case, please
        rm -fr ".git/rebase-merge"
and run me again.  I am stopping in case you still have something
valuable there.


Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main|REBASE 1/2)
$ git rebase --continue
Successfully rebased and updated refs/heads/main.

Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main)
$ git rebase -i --root
[detached HEAD df6f4b9]  create initial file/second file
 Date: Tue May 21 13:24:54 2024 +0200
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test1.md
 create mode 100644 test2.md
Successfully rebased and updated refs/heads/main.
```

### 4.Splitting a Commit:

```
$ git rebase -i HEAD~2
fatal: invalid upstream 'HEAD~2'

Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main)
$ git log --oneline
6b96ec2 (HEAD -> main) chore: Create third file chore:Create fourth file
5cebb83 chore: Create initial file

Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main)
$ git rebase -i HEAD~2
fatal: invalid upstream 'HEAD~2'

Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main)
$ git rebase -i HEAD~0
Successfully rebased and updated refs/heads/main.

Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main)
$ git add test3.md

Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main)
$ git commit -m "create third file"
On branch main
Your branch is based on 'origin/main', but the upstream is gone.
  (use "git branch --unset-upstream" to fixup)

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        test2.md

nothing added to commit but untracked files present (use "git add" to track)

Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main)
$ git add test2.md

Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main)
$ git add test3.md

Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main)
$ git commit -m "create third file"
[main d033de7] create third file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test2.md

Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main)
$ git add test4.md

Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main)
$ git commit -m "Create fourth file"
On branch main
Your branch is based on 'origin/main', but the upstream is gone.
  (use "git branch --unset-upstream" to fixup)

nothing to commit, working tree clean

Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main)
$ git branch --unset-upstream

Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main)
$ git commit -m "Create fourth file"
On branch main
nothing to commit, working tree clean

```

### 5.Advanced Squashing:

```
pick 6b96ec2 chore: Create third file chore:Create fourth file
# This is a combination of 2 commits.
nothing to commit, working tree clean
On branch main
nothing to commit, working tree clean

```

### 6.Dropping a Commit:

```
Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main)
$ git add unwanted.txt

Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main)
$ git commit -m "unwanted commit"
[main 6f5b4d3] unwanted commit
 1 file changed, 1 insertion(+)
 create mode 100644 unwanted.txt
Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main)
$ git reset --hard HEAD~1
HEAD is now at ece690b Create third and fouth files chore: Create third file chore:Create fourth file

Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main)
$ git log
commit ece690b1464547a29262bc993a3ecaf2d76aba67 (HEAD -> main)
Author: Angekarara <mbabange2020@gmail.com>
Date:   Tue May 21 13:24:55 2024 +0200

    Create third and fouth files
    chore: Create third file chore:Create fourth file

    create third file

commit 5cebb838a20b0f0ffbca57d5813de81a6dfa322d
Author: Angekarara <mbabange2020@gmail.com>
Date:   Tue May 21 13:24:54 2024 +0200

    chore: Create initial file

Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main)
$ git reset --hard 5cebb838a20b0f0ffbca57d5813de81a6dfa322d
HEAD is now at 5cebb83 chore: Create initial file
```

### 7.Reordering Commits:

```
$ git log
commit 6f5b4d3654353124742a74651ebc71fe93acb6f3 (HEAD -> main, origin/main)
Author: Angekarara <mbabange2020@gmail.com>
Date:   Tue May 21 14:44:55 2024 +0200

    unwanted commit

commit ece690b1464547a29262bc993a3ecaf2d76aba67
Author: Angekarara <mbabange2020@gmail.com>
Date:   Tue May 21 13:24:55 2024 +0200

    Create third and fouth files
    chore: Create third file chore:Create fourth file

    create third file

commit 5cebb838a20b0f0ffbca57d5813de81a6dfa322d
Author: Angekarara <mbabange2020@gmail.com>
Date:   Tue May 21 13:24:54 2024 +0200

    chore: Create initial file

Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main)
$ git rebase -i HEAD~3
fatal: invalid upstream 'HEAD~3'

Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main)
$ git rebase -i HEAD~2
Successfully rebased and updated refs/heads/main.

```

### 8.Cherry-Picking Commits:

```
Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (ft/branch)
$ git checkout main
Switched to branch 'main'
Your branch and 'origin/main' have diverged,
and have 2 and 2 different commits each, respectively.
  (use "git pull" if you want to integrate the remote branch with yours)

Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main)
$ git log ft/branch
commit 8bb14196c1cf7772f3a1ad90be9cf3495a223704 (origin/ft/branch, ft/branch)
Author: Angekarara <mbabange2020@gmail.com>
Date:   Tue May 21 15:13:45 2024 +0200

    readme file

commit 4fde62514d54398974d819f30d5f5ecf6360330a
Author: Angekarara <mbabange2020@gmail.com>
Date:   Tue May 21 15:09:06 2024 +0200

    Implemented test 5

commit abf68aa31ab5a94dd97b380fb8fa522afbca9712 (HEAD -> main)
Author: Angekarara <mbabange2020@gmail.com>

Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main)
$ git cherry-pick 4fde62514d54398974d819f30d5f5ecf6360330a
[main 5665c2b] Implemented test 5
 Date: Tue May 21 15:09:06 2024 +0200
 1 file changed, 1 insertion(+)
 create mode 100644 test5.md
```
### 9. Visualizing Commit History (Bonus):
```
Ange Karara Mbabazi@DESKTOP-Q5MA0LI MINGW64 ~/git_task (main)
$ git log --graph
*   commit 6a5e3f38ca6771bfdbd2b895115a5e6b653e7511 (HEAD -> main)
|\  Merge: 5665c2b 5fec1ee
| | Author: Angekarara <mbabange2020@gmail.com>
| | Date:   Tue May 21 15:37:10 2024 +0200
| |
| |     Merge branch 'main' of https://github.com/Angekarara/git_task
| |
| *   commit 5fec1ee9692ba9a2396cabb9dd9dab557f93bead (origin/main)
| |\  Merge: 6f5b4d3 8bb1419
| | | Author: Angekarara <99403587+Angekarara@users.noreply.github.com>
| | | Date:   Tue May 21 15:36:29 2024 +0200
| | |
| | |     Merge pull request #1 from Angekarara/ft/branch
| | |
:
```

