# Learn to use Git Terminal by example

If you are used to work with GUI tool and want to learn the basics of working using the terminal, keep on reading.

## Start Project

* en: Create a new project to start.
```bash
mkdir project-name # create folder project
cd project-name # enter folder project
```

## Initialize Git

* en: You need install GIT first. Terminal: "sudo apt install git".

```bash
git init # create files git
```

**GitHub**

> You need login on GitHub to create a new repository (+ > new repository).
> Give your repository a name--ideally the same name as your local project.
> The next screen you see will be important, so don't close it.
> Inside click on Code > Clone (url)

## Back Terminal

* en: Create a new file.
```bash
echo '# Title' > README.md
```

* en: Now link your local project with remote project (repository):
```bash
git remote add origin https://github.com/<github_username>/<repository_name>.git
git remote -v # show origin 
```

# Token

* Settings **>** Developer settings **> New personal access token**
** Save your private token

# Global Config

**Configure Global UserName**

```bash
git config --global user.email “youremail@domain.com”
git config --global user.name “gitusername“
git config --list # list data
```
* en: To edit file
```bash
nano ~/.gitconfig # edit file
```

* en: Save username for 8h.
```bash
git config --global credential.helper ‘cache –timeout=28800’
```

* en: Save username permanently.
```bash
git config --global credential.helper cache
```
 
## Basic Functions

[Basic Functions](https://www.gnial.com.br/gnialhelp/git-and-github-basic-functions/)

## Push Origin Master

* en: Change file or create a new file and send to repositoty:

```bash
git add .
git commit -m "words"
git push origin master # or git push
```

### Change Branch Name
```bash
# go to branch
git old-branch-name
# rename your current branch
# -m --force
git branch -m new-branch-name
# list all branchs
git status -a
# change remote branch too
git branch -m :old-branch-name new-branch-name
# finaly remote upstream (-set-upstream-to define future push and sync branchs)
# pt-BR: finalmente define upstream remoto (-set-upstream-to define onde os próximos push 
# devem ser enviados, mantendo a branch local e remota em sincronia)
git push origin -u new-branch-name
```

```bash
git remote -v
```
[Ref](https://devconnected.com/how-to-change-branch-name-on-git/#:~:text=Change%20Branch%20Name.%20In%20order%20to%20change%20a,to%20the%20branch%20that%20you%20want%20to%20rename.)


# Branch

## Create Branch

```bash
# option 1
git branch new-branch-name
git checkout new-branch-name
# option 2
git checkout -b new-branch-name 
# no necessary -b if branch exists
```
[Ref](https://www.freecodecamp.org/portuguese/news/tutorial-de-git-checkout-remote-branch/)

## Staus / Push

```bash
# status
git status
# ... add and commit
git push origin new-branch-name
```

## Merge Branches

```bash
# change to master or master branch
git checkout master
# merge master <- new-branch-name
git merge new-branch-name
```

* en: Now send changed files to repository master
```bash
git add .
git commit -m "merge commit"
git push origin master
# or
git push
```

## Find Branches

* en: On GitHub open repository and find above files a link named BRANCHES. All branches storages on this page
```bash
# to list brachs localy
git branch
# list too remote branchs
git branch -a
```

## Log

* en: Show pushes
```bash
git log
git log --oneline # short
git log --all --decorate --oneline --graph # nice | highlight
# to remember flags: "A DOG"
# A --all
# D --decorate
# O --oneline
# G --graph
```

## Delete Branch

* en: After merge with master
```bash
git brash -d new_branch_name
```
## Alias | Shotcuts Commands

* en: Create alias
```bash
# to create shotcut "dog"
# command "log --all --decorate --oneline --graph"
git config --global alias.dog "log --all --decorate --oneline --graph"
```
* en: Remove alias
```bash
git config --global --unset alias.dog
```

## Fork Original

* en: Send your files to origin fork repository
```bash
git push --set-upstream origin master
```

## Previous Commits and Branchs

> pt: Qual a diferença entre RESET e REVERT?
> * **RESET** - Aponta para uma COMMIT e apaga tudo que foi criado ou alterado após essa commit específica. Perdendo todo seu histórico. 
> * 1,2,[3],4,5 -> 1,2,3
> * **REVERT** - Reverte uma COMMIT específica, as alterações dessa commit escolhida será revertida mas o histórico posterior mantido. 
> * 1,2,[3],4,5 -> 1,2,4,5

#### 1 of 4 ) Previous Branch @{-1}

[Link](https://marcgg.com/blog/2015/10/18/git-checkout-minus/)
[Link](https://stackoverflow.com/questions/7206801/is-there-any-way-to-git-checkout-previous-branch)

```bash
git checkout @{-1} # back -1 branch history
git checkout -
```
#### 2 of 4 ) Previous Commit RESET | REVERT

[Link](https://stackoverflow.com/questions/3639115/reverting-to-a-specific-commit-based-on-commit-id-with-git)

**RESET**

```bash
git log --oneline # show commits
# copy head commit, example: c14809fa or c14809fafb08b9e96ff2879999ba8c807d10fb07
# Won't have to type the entire sha, just a little bit will work
git reset --sorf c14809fa 
git reset --mixed c14809fa 
git reset --hard c14809fa
git reset --hard HEAD~1 # previous 1 back
git reset --hard HEAD~2 # previous 2 back
git commit
```

**REVERT**

# This will revert the last commit:
```bash
git revert HEAD
```
Or
```bash
git log --oneline # show commits
git revert c14809fa
git revert c14809fa 0d1d7fc32  # 2 commits
git revert c14809fa..0d1d7fc32 # range commits
# flags
git revert c14809fa --no-edit # no open file revert
git revert c14809fa --no-commit # no commit this revert
# final
git commit
```
Revert error: go back
```bash
git revert --abort
```

#### 3 of 4 ) Hard delete unpublished commits

If, on the other hand, you want to really get rid of everything you've done since then, there are two possibilities. One, if you haven't published any of these commits, simply reset:

**Bad idea**

```bash
# This will destroy any local modifications.
# Don't do it if you have uncommitted work you want to keep.
git reset --hard 0d1d7fc32
git commit

**Better idea**

# Alternatively, if there's work to keep:
git stash
git reset --hard 0d1d7fc32
git stash pop
# This saves the modifications, then reapplies that patch after resetting.
# You could get merge conflicts, if you've modified things which were
# changed since the commit you reset to.
```

#### 4 of 4 ) Undo published commits with new commits

On the other hand, if you've published the work, you probably don't want to reset the branch, since that's effectively rewriting history. In that case, you could indeed revert the commits. With Git, revert has a very specific meaning: create a commit with the reverse patch to cancel it out. This way you don't rewrite any history.

```bash
# This will create three separate revert commits:
git revert a867b4af 25eee4ca 0766c053

# It also takes ranges. This will revert the last two commits:
git revert HEAD~2..HEAD

#Similarly, you can revert a range of commits using commit hashes (non inclusive of first hash):
git revert 0d1d7fc..a867b4a

# Reverting a merge commit
git revert -m 1 <merge_commit_sha>

# To get just one, you could use `rebase -i` to squash them afterwards
# Or, you could do it manually (be sure to do this at top level of the repo)
# get your index and work tree into the desired state, without changing HEAD:
git checkout 0d1d7fc32 .

# Then commit. Be sure and write a good message describing what you just did
git commit
```

## Error
#### --set-upstream origin master
fatal: The current branch master has no upstream branch.
To push the current branch and set the remote as upstream, use
```git
git push --set-upstream origin master
```
#### Soluction 
[stackoverflow](https://stackoverflow.com/questions/23401652/fatal-the-current-branch-master-has-no-upstream-branch)
[stackoverflow](https://stackoverflow.com/a/17096880/6309)
```bash
git push -u origin master
# or 
git push -u origin --all
# or
git config --global push.default current
```
