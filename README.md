### Start Project

* en: Create a new project to start
```bash
mkdir project-name
cd project-name
```

### Initialize Git

You need install git first. Terminal: "sudo apt install git".

```bash
git init
```

**GitHub**

> You need login on GitHub e create repository (button plus named new repository).
> Give your repository a name--ideally the same name as your local project.
> The next screen you see will be important, so don't close it.
> Inside click on Code > Clone (url)

### Back Terminal

* en: Create a new file
```bash
echo '" Title' > README.md
```

* en: Now link your local project with remote project:
```bash
git remote add origin https://github.com/<github_username>/<project_name>.git
git remote -v # show origin 
```

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

* en: Save username for 8h
```bash
git config --lobal credential.helper ‘cache –timeout=28800’
```

* en: Save username permanently
```bash
git config --global credential.helper cache
```
 
### Basic Functions

[Basic Functions](https://www.gnial.com.br/gnialhelp/git-and-github-basic-functions/)

### Push Origin Master

* Change file or create a new file and send to repositoty:

```bash
git add .
git commit -m "words"
git push origin master # or git push
```




