# Git Quick Guide 

## Configs
```bash
# config global user（config file is located in ~/.gitconfig）
git config --global user.name "username"
git config --global user.email "email"

# config local user （config file is located in .git/config）
git config [--local] user.name "username"  
git config [--local] user.email "email" 
git config --list # list current setting

# store password
git config --global credential.helper store
```

## Clone from remote
```bash
# Clone
git clone $HTTPS
# Clone(Specified branch)
git clone -b $BRANCH $HTTPS
# Use checkout to clone other branches you need
git branch -r           # See branches on remote
# Create a branch copied from remote branch
git checkout -b $BRANCH origin/$BRANCH 
# Switch to new branch
git checkout $BRANCH
```

## Track & Untrack
```bash
# Track files
git add --all
git add *.cpp
# Untrack files
git rm --cached $FILE
# By ignore file
gedit .git/config
    # insert at core section
    excludefiles=.gitignore
    
gedit .gitignore
    # add files you do not need
    *.[ao]
    *~
    *.out   
```

## Upload local branch
```bash
git pull origin master:master
git checkout pi
# Merge master branch and solve conflicts
git merge master 
git pull origin pi:pi
```

## Others
```bash
# =============Roll back===============
git reset --hard HEAD^
git reset --hard HEAD~2
git reflog
git reset --hard HEAD@{1}

# ===============Tag=================
git tag # show all
git tag -a v1.01 # add 
git tag -d v1.01 # delete
git push origin [tagname] # upload one tag
git push origin --tags # upload all local versions
```
