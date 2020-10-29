### Start Project

* en: Create a new project to start.
```bash
mkdir project-name # create folder project
cd project-name # enter folder project
```

### Initialize Git

* en: You need install GIT first. Terminal: "sudo apt install git".

```bash
git init # create files git
```

**GitHub**

> You need login on GitHub to create a new repository (+ > new repository).
> Give your repository a name--ideally the same name as your local project.
> The next screen you see will be important, so don't close it.
> Inside click on Code > Clone (url)

### Back Terminal

* en: Create a new file.
```bash
echo '" Title' > README.md
```

* en: Now link your local project with remote project:
```bash
git remote add origin https://github.com/<github_username>/<project_name>.git
git remote -v # show origin 
```

## Global Config

**Configure Global UserName**

```bash
git config --global user.email “youremail@domain.com”
git config --lobal user.name “gitusername“
git config --list # list data
```
* en: To edit file
```bash
nano ~/.gitconfig # edit file
```

* en: Save username for 8h.
```bash
git config --lobal credential.helper ‘cache –timeout=28800’
```

* en: Save username permanently.
```bash
git config --global credential.helper cache
```
 
### Basic Functions

[Basic Functions](https://www.gnial.com.br/gnialhelp/git-and-github-basic-functions/)

### Push Origin Master

* en: Change file or create a new file and send to repositoty:

```bash
git add .
git commit -m "words"
git push origin master # or git push
```

## Branch

### Create Branch

```bash
$ branch checkout -b new_branch_name # no necessary -b if branch exists
$ git status
... add and commit
$ git push origin new_branch_name
```

### Find Branches

* en: On GitHub open repository and find above files a link named BRANCHES.
All branches storages on this page

### Merge Branches

```bash
git checkout master # change to main branch, master branch
git merge new_branch_name
```

* en: Now send files change to repository

```bash
git add .
git commit -m "your commit"
git push origin master
# or
git push
```

### Log

* en: Show pushes
```bash
git log
git log --oneline # short
```

### Delete Branch

* en: After merge with master
```bash
git brash -d new_branch_name
```

### Previous (DANGERS)
[Link](https://marcgg.com/blog/2015/10/18/git-checkout-minus/)
[Link](https://stackoverflow.com/questions/7206801/is-there-any-way-to-git-checkout-previous-branch)

```bash
git checkout @{-1} # back -1 branch history
git checkout -
```
### Previous COMMITS (DANGERS)
[Link](https://stackoverflow.com/questions/3639115/reverting-to-a-specific-commit-based-on-commit-id-with-git

```bash
git log --oneline # show commits
# copy head commit, example: c14809fa or c14809fafb08b9e96ff2879999ba8c807d10fb07
git reset --hard c14809fa # Won't have to type the entire sha, just a little bit will work
# or
git reset --sorf c14809fa # Won't have to type the entire sha, just a little bit will work
```
or
```bash
git log # show commits
# copy head commit, example: c14809fafb08b9e96ff2879999ba8c807d10fb07
git revert --no-commit c14809fa #  Won't have to type the entire sha, just a little bit will work
git commit
```
