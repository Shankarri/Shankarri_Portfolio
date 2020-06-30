
#### For external refernce - https://dont-be-afraid-to-commit.readthedocs.io/en/latest/git/commandlinegit.html

## 1. Set up the Git repo in local

 * In order to clone a remote repository you'll want to use the git clone command, which is typically used in this fashion:

```
    $ git clone <repo-url>
```

* This will clone the repository in to your current working directory using the name of the repo as the destination directory. In order to clone it in to a different directory, you can specify one as the second parameter to clone:

``` 
    $ git clone <repo-url> <directory>
```

* An example of this command for a public GitHub repo would look like the following:

```
    $ git clone git@github.com:scottwrobinson/twentyjs.git twentyjs-clone

    Cloning into 'twentyjs-clone'...
    remote: Enumerating objects: 48, done.
    remote: Total 48 (delta 0), reused 0 (delta 0), pack-reused 48
    Receiving objects: 100% (48/48), 9.35 KiB | 0 bytes/s, done.
    Resolving deltas: 100% (22/22), done.

```

## 2. Store your Credentials in Git Repository

* The git config command is used to set Git configuration values on a global or local project level. 

* Define the author name to be used for all commits in the current repository. 

``` 
    $ git config --global user.name <name>
```

* To set your email id to be set globally for all commits in the current repositories.

```
   $ git config --global user.email <your_email@example.com>
```

* To set your password id to be set globally for all commits in the current repositories.

```
   $ git config --global user.password <password>
```

### Another way for globally configuring credentials

* Run the following command to enable credentials storage in your current Git repository - **(recommended)**.

``` 
    $ git config credential.helper store
```

* To enable credentials storage globally **(not recommended)**, run:

```
    $ git config --global credential.helper store
```

* When credentials storage is enabled, the first time you pull or push from the remote Git repository, you will be asked for a username and password, and they will be saved in ~/.git-credentials file.

* During the next communications with the remote Git repository you won’t have to provide the username and password.

* Each credential in ~/.git-credentials file is stored on its own line as a URL like:

``` 
    https://<USERNAME>:<PASSWORD>@github.com
```

## 3.Create a new branch 

* From your terminal window, list the branches on your repository.

```
    $ git branch

    * master
```

* This output indicates there is a single branch, the master and the asterisk indicates it is currently active.

* Create a new feature branch in the repository

```
    $ git branch <feature_branch>
```

* Switch to the feature branch to work on it.

``` 
    $ git checkout <feature_branch>
```

* You can list the branches again with the git branch command.

* To push your newly created branch in the local to the git repository  

```
   $ git push --set-upstream origin <feature_branch>

```

## 4.Commiting code changes to git repo 

* Go to the branch you need to work on and pull the latest changes from the remote Git repository to you local system.

```
    $ git pull
```

* Once the changes are pulled, open your code ediotr and make changes to your local repo.


* Before pushing your changes, get the latest version of the git repo in local. 

```
    $ git pull
```

* If the git repo has a new version ,we might encounter merge issues in the local. 

* Go to the code editor and look into the files structure with file names in different color. Open those files and find the merge changes, then either accept or deny the changes in them.

* Once code is merged, you are now ready to push your changes to remote git repo.

* To push your local changes to the git repository, first check the files that has changes. Enter the below command in your terminal.

```
    $ git status
```

* Enter the below command to add the file/folder to specify the files that need to be pushed to git repository **(recommended)**.

```
    $ git add <folder/file>
```

* Instead of adding each folder/file, you can push all the changes at once also. **(not recommended)**.

```
    $ git add -A
```

* After adding the files, commit those files with a commit message with the below command. Each commit should contain clear and concise commit message so we can backtrack commits if needed.  

```
    $ git commit -m "commit message"
```

* Once the changes are commited, now push the code to the git repo.

```
    $ git push 
```

## 4.Stashing you local code changes  

* Stash command temporarily shelves (or stashes) changes you've made to your working copy so you can work on something else, and then come back and re-apply them later on. 

* Stashing is handy if you need to quickly switch context and work on something else, but you're mid-way through a code change and aren't quite ready to commit.

* Use git status to check the list of files that has changes before stashing them. Use the below command to stash the changes.

```
    $ git stash
```

* At this point you're free to make changes, create new commits, switch branches, and perform any other Git operations; then come back and re-apply your stash when you're ready.

* Note that the stash is local to your Git repository; stashes are not transferred to the server when you push.

* To get your stashed changes back, use the below command. Popping your stash removes the changes from your stash and reapplies them to your working copy.

```
    $  git stash pop
```

* If you no longer need a particlar stash changes,then clear those changes with below command.

```
    $ git stash clear
```

## 5.Merging your current branch with parent branch

Below are the steps to merge two branches in Git

Scenario: You want to merge Branch A to Branch B. You are currently working in Branch B.

1. Stash your changes

2. Pull updated contents for Branch B from Git

3. Resolve merge conflicts if any and push the code. (ideally, you should not get any merge conflict)

4. Checkout Branch A

5. Pull updated contents for Branch A from Git

6. Resolve merge conflicts if any and push the code. (ideally, you should not get any merge conflict)

7. Checkout Branch B

8. Fetch the contents from Branch A

``` 
    $ git fetch origin branchA
```
9. Merge Branch A to Branch B

``` 
    $ git merge origin branchA
```

10. Resolve merge conflicts if any

11. Pop the stashed changes

12. Resolve merge conflicts if any

If you want to know more about 'git merge', you can have a look at https://www.atlassian.com/git/tutorials/using-branches/git-merge.
