### Initialize

gitflow | git
--------|----
`git flow init` | `git init`
 | `git commit --allow-empty -m "Initial commit"`
 | git checkout -b develop

With `gitflow`:
```sh
git flow init
```

With raw `git`:
```
# Make this directory into a git repo
git init 
# Now in `master` branch

# Make an initial commit for the sake of commit tracking (history, branching, etc.)
git commit --allow-empty -m "Initial commit"

# Create a `develop` branch from `master` and then check it out
git checkout -b develop
```


### Connect to the remote repository

With `gitflow` and/or raw `git`:
```sh
# Add the remote repo URL
git remote add origin git@github.com:MYACCOUNT/MYREPO
```


### Create a feature branch


```sh
git flow feature start MYFEATURE
```

git checkout -b MYFEATURE develop  # Create a `MYFEATURE` branch from `develop` and the check it out
```


```sh
git flow feature publish MYFEATURE


git push origin MYFEATURE
```


```sh
git flow feature pull origin MYFEATURE


git pull origin MYFEATURE  # ????
```


```sh
git flow feature finish MYFEATURE


git checkout develop         # Checkout the `develop` branch
git merge --no-ff MYFEATURE  # Merge the `MYFEATURE` branch into `develop`. `--no-ff` creates a merge commit.
git branch -d MYFEATURE      # Delete the `MYFEATURE` branch
git push origin develop      # Push the `develop` branch to remote
```


```sh
git flow release start 1.2.0


git checkout -b release-1.2.0 develop
# (Run some commands to update the version)
git commit -a -m "Bumped version number to 1.2.0"
```


```sh
git flow release publish 1.2.0


git push origin release-1.2.0
```


```sh
git flow release finish 1.2.0


git checkout master
git merge --no-ff release-1.2.0
git branch -d release-1.2.0
git tag -a 1.2.0
```


```sh
git push --tags


git push origin master --tags
```


```sh
git flow hotfix start 1.2.1 [master|develop]


git checkout -b hotfix-1.2.1 [master|develop]
```


```sh
git flow hotfix finish 1.2.1


git checkout develop
git merge --no-ff hotfix-1.2.1
git checkout master
git merge --no-ff hotfix-1.2.1
git branch -d hotfix-1.2.1
git tag -a 1.2.1
```
