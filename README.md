copy master to test

# Guacamole recipe

Used in teaching Git.

https://coderefinery.github.io/git-intro/10-archeology/

## useful commands for day 2

### Inspecting history

* git grep sometext

* git annotate somefile --- git annotate R/session.R | grep "No links matched that expression"

git grep "No links matched that expression"
git annotate R/session.R     (find has for the sentence 'no links matched that expression')

aboved two commands can be replaced by :

git annotate R/session.R | grep "No links matched that expression"

* git checkout -b branchname somehash
 create new branch which is named branchname with somehash and switch to it.
 when you want to delete branchname, you need to 
 ```
 git checkout -b meusum abc123
 git checkout master
 git branch -d museum
 ```

### finding out when something broken ```git bisect```

```
git bisect start
git bisect good f0ea950  # this is a commit that worked
git bisect bad master    # last commit is broken
python get_pi.py      # now compile and/or run
  # after that decide whether
git bisect good
  # or
git bisect bad
python get_pi.py     # now compile and/or run 
  # after that decide whether
git bisect good
  # or
git bisect bad
  # iterate until commit is found

```

repeat aboved process until :

```
Bisecting: 0 revisions left to test after this (roughly 0 steps)
```

```
git log --oneline | tail -n 1
```
finding the first commit

## git graph

git config --global alias.graph "log --all --graph --decorate --oneline"

## default settings

git config --global core.editor vim

git config --global core.quotepath false  # 修正中文乱码问题
