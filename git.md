# GIT

Check Version:
```
git --version
```

Set Config Values:
```
git config --global user.name "John Doe"
git config --global user.email "john@mail.com"
git config --list
```

Get Help:
```
git help config
git config --help
```

Initialize a repo from existing code
```
git init
ls -la // everything that related to our repo
```

Remove git
```
rm -rf .git
```

Get status
```
git status
```

Ignore file
```
touch .gitignore
```

Three stages
working dir => staging area => .git diretory

Add files to staging area
```
git add -A
git add .
```

Remove files from the staging area
```
git reset <optional | file name>
```

View log
```
git log
```

Clonning a git repo
```
git clone <url> <where to clone>
```

View info about the remote repo
```
git remote -v
git branch -a
```

See changes before adding to the statging area
```
git diff
```

Before pushing to the remote repo
```
git pull origin master
git push origin master
```

Branching
```
git branch desired-feature
git checkout desired-feature
```

Push to remote repo
```
git add -A
git commit -m"message"
git push -u origin desired-feature
git branch
```

Merge a branch
```
git checkout master
git pull origin master
git branch --merged // branches that merged so far
git merge desired-feature
git push origin master
```

Delete branch
```
git branch -d desired-feature
git branch -a
git push origin --delete desired-feature // delete the remote repo branch
```
