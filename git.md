# Git Tips

## Undo last commit

**Before pushing changes, this works:**

```bash 
git reset HEAD~
```

## Compare staged to HEAD

```bash
git diff --cached
```

## Diff between branches

```bash
git diff branch1..branch2
```

## Pushing to pull requested branch on forked project

```bash
$ git checkout -b fork_user-branch_name <sha of fork from master>
$ git pull <forked url> <branch name> <make changes>
$ git push <remote url> <local branch name>:<remote branch name>
```

## List all files tracked in the index

```bash
$ git ls-files <directory>
```

E.g., all files that are IPython notebooks that are being tracked in this repo

```bash
$ git ls-files examples/*.ipynb
```

## Remove file from commit

If a file has been commited erroneously, you can remove it from that commit with
the following steps.  It assumes the last commit was the one to be edited. I
believe that this could be done for 

```bash
$ git reset --soft HEAD~1
$ git reset HEAD /path/to/file
$ git checkout -- /path/to/file
$ git commit -c ORIG_HEAD
$ git push origin <branch_name> -f
```

`ORIG_HEAD` stores the last commit messages, which can be overwritten after
hitting enter for that command. The `-f` flag forces the push to the branch.
