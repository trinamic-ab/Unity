# Unity

This is branch containing only the source of Unity.
This is maintained using the subtree git command, that way Unity can be included using submodules from this fork.

## How to use this fork

Simply include it as a submodule into a project, 

## How to update this repo

First update the upstream-master branch from the Unity repo :

```
git checkout upstream-master
git pull
```

Then update the unity-src branch with the subtree command :

```
git subtree split --prefix=src \
  --onto unity-src -b unity-src
```

Finally merge or rebase with the master branch :

```
git checkout master
git rebase unity-src
```

## How to set up a subtree repo

This is how I set up this system.

 - First fork the desired repo on github, then clone locally.
 - Create an upstream-master branch that will serve to pull in latest changes to original repo
 - Delete the master branch (you will need to switch the default branch to upstream-master on github)
 
 ```
git checkout upstream-master
git branch -D master
git push origin upstream-master
git push origin :master
 ```
 
 - Create the subtree branch, this takes a long time, upwards of 10 minutes:
 
 ```
git subtree split --prefix=src -b unity-src
git checkout unity-src
 ```
 
 - Finally create and commit the master branch back, and set it as default on github
 
 ```
 git push -u origin master
 ```
 - All your desired changes should be made on the master branch, unity-src is reserved for actual commits on the original repo, and upstream master for pulling changes.
