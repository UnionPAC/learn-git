# Learn Git 🧙‍♂️

#### Purpose

I made this repo in order to strengthen my knowledge of Git. It will not only be a great way to brush up on concepts I already know, but also to learn more advanced topics!

#### _Resources_

- [Official Git Documentation](https://git-scm.com/)
- [The Ultimate Git Course](https://codewithmosh.com/p/the-ultimate-git-course)

#### Table of Contents

1. [Creating Snapshots](#creating-snapshots)
2. [Browsing History](#browsing_history)
3. [Branching](#branching)
4. [Collaboration](#collaboration)
5. [Rewriting History](#rewriting_history)

### Introduction to Git

**wtf is Git?** 🤔

Git is a Version Control System that tracks changes made to a codebase over time in a database called a **repository**.

### <a id="creating_snapshots">Creating Snapshots 📸</a>

**Initializing a new Git repo**
`git init`: creates an empty Git repository or reinitialize an existing one

**Staging Files**
`git status`: shows the working tree status

**Committing Changes**
`git commit`: records changes to the repository

```
git commit [-a | --interactive | --patch] [-s] [-v] [-u<mode>] [--amend]
	   [--dry-run] [(-c | -C | --squash) <commit> | --fixup
[(amend|reword):]<commit>)]
	   [-F <file> | -m <msg>] [--reset-author] [--allow-empty]
	   [--allow-empty-message] [--no-verify] [-e] [--author=<author>]
	   [--date=<date>] [--cleanup=<mode>] [--[no-]status]
	   [-i | -o] [--pathspec-from-file=<file> [--pathspec-file-nul]]
	   [(--trailer <token>[(=|:)<value>])…​] [-S[<keyid>]]
	   [--] [<pathspec>…​]
```

> https://git-scm.com/docs/git-commit

**Committing Best Practices**

- Commits shouldn't be too big or too small
- Commit often
- As you reach a state you want to record **THEN** make a commit
- Make meaningful commit messages

**Skipping the Staging Area**
`git commit -am "enter commit message here"`

**Removing Files**

`git rm`: Remove files from the working tree and from the index
`git rm file1.txt`

**Renaming or Moving Files**

`git mv`: Move or rename a file, a directory, or a symlink
`git mv file1.txt main.js`

**Ignoring Files**

A *.gitignore* file specifies intentionally untracked files that Git should ignore.

- Sometimes a file or directory is already added to your project and cannot simply be ignored by *.gitignore*, in that case we have to remove the file from the staging area and then add it to our .*gitignore* file.

👇

**Git rm Options**
`--cached` Use this option to unstage and remove paths only from the index (staging area). Working tree files, whether modified or not, will be left alone.

`-r` Allow recursive removal when a leading directory name is given.

**Short Status**

`git status -s`: Shows a short format of the working tree status

**View Staged and Unstaged Changes**

`git diff`: Show changes between the working tree and the index or a tree, changes between the index and a tree, changes between two trees, changes resulting from a merge, changes between two blob objects, or changes between two files on disk.

`git diff --staged`

**Viewing History**

`git log`: Show commit logs

`git log --oneline`
`git log --oneline --reverse`

**Viewing a Commit**

`git show`: Shows one or more objects (blobs, trees, tags and commits).

`git show HEAD~1`

`git ls-tree`: List the contents of a tree object

**Unstaging Files**

`git restore`: Restore specified paths in the working tree with some contents from a restore source. If a path is tracked but does not exist in the restore source, it will be removed to match the source.

`git restore .`
`git restore file1.js`

**Discarding Local Changes**

`git clean`: Remove untracked files from the working tree

**Restoring a File to an Earlier Version**

**Creating Snapshots with VSCode**

**Creating Snapshots with GitKraken**

### <a id="browsing_history">Browsing History 📖</a>

### <a id="branching">Branching 🌳</a>

### <a id="collaboration">Collaboration 👥</a>

### <a id="rewriting_history">Rewriting History ✍️</a>
