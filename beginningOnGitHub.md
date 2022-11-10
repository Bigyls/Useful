# Init your project on GitHub

### You haven't done anything yet in your project

```bash
git init my_project
```

This will create a "my_project" directory in the current folder.

---

### You have already started your project

Your "my_project" directory therefore already exists, and it already contains files. Go to your directory and run the following command :

```bash
git init
```

---

### Add files to your git

Your directory contains files, you must add them to git so that it can take these files into account :

```bash
git add my_file
```

Or if multiple files :

```bash
git add my_file1 my_file2
```

Or to add all files in the directory :

```bash
git add .
```

---

### Show the status of your git

```bash
git status
```

This will give you the list of files not yet added to your git, and the list of files already added, but not yet updated in your git since their last modification.

---

### Make a commit (like photo/snapshot).

You have modified a file (for example my_file1), then you must make a commit for git to save these modifications :

```bash
git commit my_file1 -m "add function md2html"
```

The -m argument allows you to add a brief comment describing your change. This comment is mandatory; if you don't add the -m argument and its comment, then the nano editor will open for you to add your comment.


It is also possible to commit the whole project

```bash
git commit -m "add function md2html"
```

---

### Get a list of all your commits and their comments

```bash
git log
```

For each commit, the first line corresponds to the sha of the commit.

---

### Revert to an old commit

You have to do a `git log` to know your sha and after :

```bash
git checkout sha_of_old_commit
```

To revert to the last (most recent) commit :

```bash
git checkout master
```

---

### Create a branch

If you want to make a change to one of your files while keeping your last commit intact; you need to create a branch for this :

```bash
git branch name_of_the_branch
```

To find out which branch you are in :

```bash
git branch
```

You will then see your different branches: the master branch (this is the main branch), and your new branch. The asterix in front of master means that you are still in the master branch. It is then necessary to change branch before making your modifications :

```bash
git checkout name_of_the_branch
```

To create a branch by placing yourself directly in this one :

```bash
git checkout -b name_of_the_branch
```

---

### Merge a branch with the master

The changes made in the branch are fine with you. You must then merge your branch and your master. Go to the master branch :

```bash
git checkout master
```

Then :

```bash
git merge name_of_the_branch
```

To delete the branch that is no longer needed :

```bash
git branch -D name_of_the_branch
```

---

### Clone a repository or a gist

```bash
git clone path_of_repository_or_gist path_of_local_directory_to_create
```

---

### Push to github

Link your local git to your github repository (to be done once) :


Create a repository on your github account, then go to your local folder containing your git and your local project. Then enter the following command :

```bash
git remote add origin https://github.com/username/MyProjet.git
```

Make a push (remember to make a commit before !) :

```bash
git push
```

Or :

```bash
git push --set-upstream origin master
```

Or if you have errors :

```bash
git pull --rebase origin main
git push origin main
```

---

### Push to gist

- Create a gist from your github account.
- Clone your local gist
- Place your file in your local git

Then do a commit and then a git push :

```bash
git push git@gist.github.com:<your gist id e4.....>.git
```

---

### Pull from github to your local repo

To pull the latest changes from your remote repository (on github) to your local repository :
Put yourself in your local repository :

```bash
git pull origin master
```

---

### Rebase a branch

The git rebase command **allows you to easily change a series of commits, modifying the history of your repository**. You can reorder, edit, or squash commits together. Typically, you would use git rebase to: Edit previous commit messages. Combine multiple commits into one.

```bash
git stash
git checkout main
git pull
git chekcout feature
git rebase main (OR git rebase -i main, rebase your changes in the current branch to the main branch, OR git merge main)
git status (we always use it after conflict resolution)
```

---

### Cherry pick a commit or multiple commits

**You can cherry-pick a commit on one branch to create a copy of the commit with the same changes on another branch**. If you commit changes to the wrong branch or want to make the same changes to another branch, you can cherry-pick the commit to apply the changes to another branch.

If we want to cherry pick a commit from another branch :

```bash
git checkout branch_name (we switch to the branch to which we want the commit to apply)
git cherry-pick commit_id (if we want to cherry pick one commit, the commit could be from another branch)
git cherry-pick commit_id_1 commit_id_2 (cherry pick two commits)
git cherry-pick commit_id1 ... commit_id_n (cherry pick the commits that are between commit_id_1 and commit_id_n both included)
```

---

### Connect your Shell with GitHub

You will then have to enter your username and password unless you have installed an ssh certificate.
Otherwise, you will need to install gh and launch it with the following commands:

```bash
sudo apt install gh
gh auth login
```

t will then be necessary to select the options GitHub.com => HTTPS => Yes => Paste ann authentication token (token created in Settings => Developer settings => Personal access tokens => Generate token (with all rights and no expiration) ).
Thus, you can perform any actions without entering identifiers.

---

### Enable SSH Authentication

Create an SSH key pair :

```bash
ssh-keygen -t ed25519 -C "<email>@<email>"
```

Retrieve your public key :

```bash
ls ~/.ssh
config  id_rsa  id_rsa.pub  known_hosts

cat ~/.ssh/id_rsa.pub
ssh-rsa AAAAB3Nza.....
```

Add your public key by connecting to github and going to the 'settings' menu then 'SSH and GPG keys'
Enable SSH authentication in an existing repo :

```bash
git remote set-url origin git@github.com:<user name>/<repo name or gist id>.git
```
