# You Better Know It

- [version control](https://coderefinery.org/lessons/)
- [GitHub Help](https://help.github.com/en/github)

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
$ git diff    # show unstaged/uncommitted modifications
$ git diff --staged    # see **staged** changes
$ git show    # show the change for a specific commit
$ git mv      # move tracked files
$ git rm      # remove tracked files
$ git reset            # unstages staged changes
$ git checkout <path>  # check out the latest staged version ( or committed
                       # version if file has not been staged )
```

