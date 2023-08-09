# Learn Git 🧙‍♂️

#### Purpose

I made this repo in order to strengthen my knowledge of Git. It will not only be a great way to brush up on concepts I already know, but also to learn more advanced topics!

#### _Resources_

- [Official Git Documentation](https://git-scm.com/)
- [The Ultimate Git Course](https://codewithmosh.com/p/the-ultimate-git-course)

#### Table of Contents

1. [Creating Snapshots](#creating_snapshots)
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

A _.gitignore_ file specifies intentionally untracked files that Git should ignore.

- Sometimes a file or directory is already added to your project and cannot simply be ignored by _.gitignore_, in that case we have to remove the file from the staging area and then add it to our ._gitignore_ file.

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

`git restore --source=HEAD~1 file1.js`

### <a id="browsing_history">Browsing History 📖</a>

**Viewing the History**

https://git-scm.com/docs/git-log

`git log`

_Options_
`--oneline`
`--stat`
`--patch`

**Filtering the History**

- Filter by latest commits

`git log -3` - This limits the number of commits to 3, starting with the most recent.
_note: 3 is just used for this example, but can be replaced by any number._

- Filter by author

`git log --author="Geoff` - Limits the commits output to ones with the author header lines that match.
_note: `--author` expects a pattern which will be treated as a regular expression.
So `--author="Geoff"` would also show commits by an author named Geoffrey._

- Filter by date

`git log --before`
`git log --after`

_Examples:_

`git log --after="2020-08-17"`
`git log --after="yesterday"`
`git log --after="one week ago"`

- Filter by subject

`git log --grep="GUI"`

_note: this operation is case sensitive_

- Filter by content

`git log -S"OBJECTIVES"`

`-S` Expects a _string_ and looks for differences that change the number of occurrences of the specified string (i.e. addition/deletion) in a file.

- Filter by range

`git log <commitHash1>...<commitHash2>`
_i.e_ `git log 91f7d40...1ebb7a7`

- Filter by commits that touched certain files

`git log helloWorld.txt`

_sometimes we'll need to seperate our file name from our options ... we can do that like this:_

`git log --oneline -- helloWorld.txt`

_note: if you use this space `--`, you must keep your options together_

_i.e_ `git log --oneline --patch -- helloWorld.txt`

**Formatting the Log Output**

https://git-scm.com/docs/git-log#_pretty_formats

`git log --pretty=format:"%Cblue%an%Creset made commit %h on %cd"`

`%an` - author name
`%H` - commit hash
`%h` - abbreviated commit hash
`%cd` - committer date

`%Cblue%an%Creset` - changes the author name to blue and then resets the color to default

**Aliases**

- we can setup aliases for commands we use frequently

_Creating a custom git log command:_
`git config --global alias.lg "log --pretty=format:'%an committed %h'"`

_Custom command that restores all files in the staging area:_
`git config --global alias.unstage "restore --staged ."`

**Viewing a Commit**

There are two ways to reference a commit:

1. Commit Hash
2. Relative reference to the HEAD

`git show HEAD~2` - 2 commits before the last commit

- We can view the final version of a file in this commit like this:

`git show HEAD~2:testDirectory/test.js`

`git show --name-only` - show only names of changed files

`git show --name-status` - show only names and status of changed files

**Viewing the Changes Across Commits**

`git diff HEAD~2 HEAD` - shows all changes between these commits

`git diff HEAD~2 HEAD test.js` shows only the changes that happened to _test.js_ between these commits.

_Other Examples:_

`git diff HEAD~2 HEAD --name-only`
`git diff HEAD~2 HEAD --name-status`

**Checking Out a Commit**

- To go back to an earlier commit _(move our HEAD pointer)_
  `git checkout <commitHash>`

_Note: When in the 'detached HEAD' state we should not create new commits_

- To show all commits, even if HEAD is behind, we can use the option `-all`
  `git log --oneline --all` 
  
  <br />

- To attach the HEAD pointer to the master branch
  `git checkout master`

**Finding Bugs Using Bisect** 🪲

Start using Bisect - `git bisect start`

Now we need to provide a commit that is bad, and one that is known to be good. This way we can start to narrow down where things went wrong.

`git bisect bad`

`git bisect good <commitHash>`


End our Bisect session, and attach the HEAD back to master - `git bisect reset`

**Find Contributors Using Shortlog**

`git shortlog`

https://git-scm.com/docs/git-shortlog#_options

**Viewing the History of a File**

`git log --oneline --patch file1.txt`

**Restoring a Deleted File**

`git checkout <commitHash> <fileName>`

**Finding the Author of Line Using Blame**

`git blame <fileName>`

**Tagging**

`git tag`

`git tag <tagName> <commitHash>`

- We can checkout a commit by using it's tag instead of it's hash like this:

`git checkout <tagName>`

To view all the tags we have created - `git tag`

There are different types of tags

1. Lightweight tags
	- A reference/ pointer to a particular commit

<br />

2. Annotated tags
	- contain a creation date, the tagger name and e-mail, a tagging message, and an optional GnuPG signature


To create an Annotated tag we use `git tag -a v1.1 -m "Some message"`

`git tag -d <tagName>` - to delete a tag

### <a id="branching">Branching 🌳</a>

**Working with Branches**

`git-branch` - List, create, or delete branches

**Create a new branch**

`git branch <newBranch>`
*ie.* `git branch bugfix`

**List branches**

`git branch`

- Using `git branch` will list branches and show what branch you are currently on. You can also use `git status` to check which branch you are on.

**Switch to a branch**

`git switch <branchName>`

**Renaming a branch**

- We can use the `-m`or `--move` option to move/rename a branch, together with its config and reflog.

`git branch -m <oldName> <newName>`


**Deleting a branch**

- We can use the `-d` or `--delete` option to delete a branch.

*Note: The branch must be fully merged in its upstream branch, or in HEAD if no upstream was set with --track or --set-upstream-to.*

`git branch -d <branchName>`

- `-D` is a shortcut for --delete --force.

**Comparing Branches**

`git log master..bugfix/signup-form`

- this shows the commits which are in `bugfix/signup-form` but are *NOT* in `master`

`git diff master..bugfix/signup-form`

- this shows the differences between `bugfix/signup-form` and `master`

We can make this shorter by just writing `git diff bugfix/signup-form`

- This shows the difference between the current branch *(which is master in our case)* and `bugfix/signup-form`

`git diff --name-status bugfix/signup-form`

- this shows only the files which are changed between the current branch and the `bugfix/signup-form` branch

**Stashing**

Stashing takes the dirty state of your working directory — that is, your modified tracked files and staged changes — and saves it on a stack of unfinished changes that you can reapply at any time (even on a different branch).

`git stash` - Stash the changes in a dirty working directory away

`git stash push -m "New tax rules."`

**View our stashes**

`git stash list`

**Show a stash**

`git stash show <id>`

**Apply stash on our working directory**

`git stash apply <id>`

**Remove a stash**

`git stash drop <id>`

**Merges**

Types of merges:

1. Fast-forward merges *( if branches have not diverged )*
2. 3-way merges *( if branches have diverged )*

**Fast-forward Merges**

**Three-way Merges**

### <a id="collaboration">Collaboration 👥</a>

### <a id="rewriting_history">Rewriting History ✍️</a>
