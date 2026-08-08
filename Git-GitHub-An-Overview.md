# Git & GitHub : An Overview

![Git-GitHub](https://miro.medium.com/v2/resize:fit:4800/format:webp/1*zDw6rK9fP9DVKET-WPP24g.png)

**Git** is a **Version Control System**, which means, it is a tool which tracks changes in your code, maintains its history, and allows you to revert, compare, and manage different versions of a project.

**GitHub** is a **Cloud-Based Hosting Platform** For Git Repositories, which means, it allows you to store your code online, collaborate with others, and manage projects using features like pull requests, issues, and branches.

---

### GIT TUTORIAL :-

Global Configuration Settings :

These are the initial Configuration Settings where you set up your user information.

```
-> git config --global user.name "<Your Name>"
[set the name / username of the user]

-> git config --global user.email "<youremail@email.com>"
[set the email of the user]

-> git config --global --list
[check / confirm added user information in the list]
```

---

#### Case : Create A Brand‑New Local Project And Upload It To GitHub :

You create a new Local Project, add Git to it, create a GitHub Account and upload your Project to GitHub.

It follows a simple flow — Add => Commit => Push.

```
-> git init
[initialize git in the project]

-> git add <file-1> <file-2> <file-3>
[add files (manually) to staging area]
OR
-> git add .
[add all files to staging area]

-> git commit -m "<Your Commit Message>"
[commit all the staged changes with a message]

-> git remote add origin https://github.com/<your-username>/<your-repository-name>.git
[connect your local project to the github repository]

-> git branch -M main
[rename the current branch to main]
[because git creates master branch by default and github uses main as the default branch name for new repositories]

-> git push -u origin main
[push all your local code / commit on the github repository]
[-u or --set-upstream sets the upstream so that git remembers to upload from your local main branch to the remote repository named origin's main branch]
[after setting upstream initially, later you only have to write :]
-> git push
```

> *NOTE : Before you `git add .`, create a `.gitignore` file. This tells Git which files to never upload (like API keys, system files, or dependency folders). It keeps your repo clean and secure.*

> *For Example :-*

> *`node_modules/` (Trailing Slash) : This means "ignore any folder named `node_modules` anywhere in your project". So if you have `root/node_modules` OR `root/src/frontend/node_modules`, both get ignored.*

> *`/node_modules` (Leading Slash) : The means "only ignore the `node_modules` folder that is exactly at the root level".*

> *`*.env` (With Asterisk In Start): This ignores any file that ends with `.env` (e.g., `.env`, `staging.env`, `production.env`, etc.).*

> *`.env*`* *(With Asterisk In End): This ignores any file that starts with `.env` (e.g., `.env`, `.env.local`, `.env.development`, etc.).*

> *`.env` (Without Asterisk): This ignores only the exact file named `.env`.*

#### Case : Download Project ZIP From GitHub :

If you want to connect and work on a pre-existing GitHub Repository, you can download a ZIP version of it.

But keep in mind that .zip version removes the .git Folder and Commit History of the Project when you extract it. Because of this, Git will no longer recognize it as a Git Repository.

To Re-Connect it with the original GitHub Repository :

```
-> git init

-> git remote add origin https://github.com/<your-username>/<your-repository-name>.git

-> git fetch origin
[download the commit history and branch information from origin (remote repository)]

-> git reset --hard origin/main
[hard reset the local project to match the latest commit history of main branch of origin (remote repository)]
[--hard permanently removes all uncommitted local changes.]

-> git add .

-> git commit -m "<Your Commit Message>"

-> git push -u origin main
```

---

#### Case : Clone GitHub Project To Your Local VS Code :

Another way to connect and work on a pre-existing GitHub Repository (without downloading the ZIP Version of it) is Cloning that Repository to your Local Device. It keeps the Commit History as it is.

```
-> git clone https://github.com/<your-username>/<your-repository-name>.git
[clones the github repository to your local device (including the history) in a new sub-folder]
OR
-> git clone https://github.com/<your-username>/<your-repository-name>.git .
[clones the github repository to your local device (including the history) without creating a new sub-folder]

-> cd <folder-name>
[switch to the newly created sub-folder (if there is any)]

-> git remote -v
[shows all the connected remote repositories]

-> git log --oneline
[list all the commit history of that remotely connected repository in short form with the latest one on top]

-> git status
[tells you git status - all the files that are added, staged or commited... or not!]

-> git add .

-> git commit -m "<Your Commit Message>"

-> git push
```

---

### GITHUB TUTORIAL :-

- Create an account on GitHub.
- Create a new Repository (Folder) and upload all the Code Files.
- You can make your Project live through GitHub Pages (just make sure your index.html should be in the root directory, because it look for that particular file as the default Home Page.)
- You can create Pull Request on Repositories of other Users. Your Pull Request contains your changes on that particular project, that you want them to merge on that project. If they accept it, your changes will be visible. Make sure you make “important” code changes, not just basic “grammatical errors”.
- You can also Fork the Repositories of other Users. This will show their Repository on your Account, but with their Username on top (of course).

---

#### Branches :-

Branches allow Developers to work on different Features separately without affecting the main Codebase.

Common Commands :
```
-> git branch
[show all branches]

-> git branch <branch-name>
[create a new branch]

-> git checkout <branch-name>
OR
-> git switch <branch-name>
[switch to the mentioned branch name]

-> git checkout -b <branch-name>
OR
-> git switch -c <branch-name>
[create and switch to a new branch together]

-> git merge <branch-name>
[merge the mentioned branch name to the current branch]
```

> *The Default “Main” Branch is **main / master** Branch.*

---

#### Merge Conflicts :-

A Merge Conflict happens when Git cannot decide which Code should stay during Code / Branch Merging.

The Merge Conflict looks like this :
```
<<<<<<< HEAD                 [Your local changes (current branch)]
console.log("Old Code");
=======                      [The divider between the two versions]
console.log("New Code");
>>>>>>> [branch-name]        [Changes from the branch being merged]
You must manually choose the correct code.
```

After fixing the conflict, Add => Commit => Push.

How to avoid :
```
-> git checkout main
[checkout to main branch]

-> git pull origin main
[pull all the latest changes to origin branch from main branch]

-> git checkout -b <new-branch>
[create a new branch and start working]
```

---

#### Pull Requests (PRs) :-

A Pull Request is a request you pull to merge your Code / Changes into another GitHub Branch / Repository.

Workflow :

1. Fork or Clone Repository.
2. Create a new Branch.
3. Make changes.
4. Commit and Push changes.
5. Open Pull Request on GitHub.
6. Repository Owner reviews the code.
7. If approved → Changes get merged.

---

#### Forks :-

Forking means creating a Copy of someone else’s GitHub Repository into your own GitHub Account.

It does not affect the original repository.

Workflow :

Click “Fork” on GitHub.
Repository gets copied to your Account.
Clone your Fork locally.
Make changes.
Push changes to your Fork.

---

#### Extra Commands :-

```
-> git restore <file-name>
[re-set a file to the last committed version]

-> git restore --staged <file-name>
[un-stage a file you accidentally added]

-> git reset --soft HEAD~1
[undo your last commit, but keep your changes]

-> git revert commit-hash
[safely undo a public commit without rewriting history]

-> git stash
[if you want to switch branch with an un-committed code]
[it will temporary save your un-committed changes in a shelf]
[change to the other branch and do your work]

-> git stash pop
[restore all your saved changes]

-> git diff
[shows un-staged changes]

-> git diff --staged
[shows staged changes]

-> git diff HEAD
[shows all changes (both staged + un-staged) combined]
```

---

For more reference, check these official documents :

[https://education.github.com/git-cheat-sheet-education.pdf](https://education.github.com/git-cheat-sheet-education.pdf)

[https://git-scm.com/cheat-sheet.pdf](https://git-scm.com/cheat-sheet.pdf)

---

###  AUTHOR - HITARTH PATHAK