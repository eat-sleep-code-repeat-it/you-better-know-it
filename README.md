# You Better Know It

- [GitHub Help](https://help.github.com/en/github)
- [version control](https://coderefinery.org/lessons/)
- [Git branch design lesson](https://coderefinery.github.io/git-branch-design/)
- [Collaborative distributed version control](https://coderefinery.github.io/git-collaborative/)


We first “stage” the change (git add), then shoot (git commit).
The best commit messages I’ve seen don’t just explain what they’ve changed: they explain why.

```bash
$ git init    # initialize new repository
$ git add <path>    # add files or stage file(s)
$ git add -p <path>    # stages while letting you choose which lines to take
$ git commit  # commit staged file(s)
$ git commit -m "adding ingredients and instructions"
$ git commit -v (will show you the difference in the editor).
$ git status  # see what is going on
$ git log     # see history
$ git log --oneline only shows the first 7 characters of the commit hash and is good to get an overview.
$ git log --stat is nice to show which files have been modified.
$ git branch # show where we are (where HEAD points to) 
$ git diff    # show unstaged/uncommitted modifications
$ git diff --staged    # see **staged** changes
$ git show    # show the change for a specific commit
$ git mv      # move tracked files
$ git rm      # remove tracked files
$ git reset            # unstages staged changes
$ git reset --hard dd4472c   # git reset command is one of the destructive commands in Git, so use with caution.
$ git checkout <path>  # check out the latest staged version ( or committed
                       # version if file has not been staged )
        # git checkout as an operation that brings the working tree to a specific state.
        # The state can be a commit or a branch (pointing to a commit).
$ git checkout <currentbranch>
$ git merge master      # merge changes from master to current branch
$ git merge --abort     # undo the half-finished merge
```

### Recommendation:

* git add every change that improves the code.
* git checkout every change that made things worse.
* git commit as soon as you have created a nice self-contained unit (not too large, not too small).
* Discuss/think about what is too large or too small.

```bash
$ git add file.py                 # checkpoint 1
$ git add file.py                 # checkpoint 2
$ git add another_file.py         # checkpoint 3
$ git add another_file.py         # checkpoint 4
# ... further work on another_file.py ...
$ git diff another_file.py        # diff w.r.t. checkpoint 4
$ git checkout another_file.py    # oops go back to checkpoint 4
$ git commit                      # commit everything that is staged
```

### [Sharing repositories online](https://coderefinery.github.io/git-collaborative/)

A remote is treated the same as a branch, you can also push changes to the remote and pull from the remote.
```bash
$ git remote add origin https://github.com/user/recipe.git
$ git push -u origin master
$ git clone https://github.com/user/recipe.git

$ git log --reverse   #
$ git show b3f33c5d   # display the changeset for the second commit
$ git log --oneline source/wordcount.py  # check the git log of a single file
$ git log --oneline --follow source/wordcount.py
$ git grep -i percentage
$ git blame source/wordcount.py   # fun and useful command to find out when a specific line got introduced and by whom
$ git log --oneline  --grep "word count"   # some keywords from the commit message
$ git log -S test_calculate_word_counts    # find when test_calculate_word_counts  was removed
$ git log/grep/blame/show/bisect is a powerful combination when doing archaeology in a project.
$ git checkout -b <name> <hash> is the recommended mechanism to inspect old code

```

### Frequent situation: interrupted work
  create branches or stash.
  The stash is the first and easiest place to temporarily “stash” things.
```bash
git stash will put working directory and staging area changes away. Your code will be same as last commit.
git stash pop will return to the state you were before. Can give it a list.
git stash list will list the current stashes.
git stash save NAME is like the first, but will give it a name. Useful if it might last a while.
git stash save [-p] [filename] will stash certain files files and/or by patches.
git stash drop will drop the most recent stash (or whichever stash you give).
The stashes form a stack, so you can stash several batches of modifications.
```
### Rebase vs. merge

Advantages and disadvantages
```bash
git rebase makes “merges” producing a linear history.
git merge resolves all conflicts in a single commit
git rebase each commit may need conflict resolution, git rebase may invalidate tests.
git merge preserves chronology of commits and creates explicit merge commits (unless fast-forward).
git rebase can change chronology of commits.

*** When working with others do not rebase commits that other people depend on (history has changed).
Rebasing creates nice linear history without merge commits, but is associated with potential risks.
```
https://dev.to/maxwell_dev/the-git-rebase-introduction-i-wish-id-had
