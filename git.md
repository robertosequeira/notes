# Git

* Init/Set repository

  ```
  git init
  git clone git@github.com:robertosequeira/flaming-octo-batman.git
  ```

* Get from origin

  ```
  git pull
  git pull origin master
  ```

* Add file/files to repository

  ```
  git add index.html
  git add "*.html"
  git add -A #add all new pending changes
  ```

* Commit changes

  ```
  git commit -m "Added home page"
  git commit -a -m "Added some files" 
  ```

* Push changes

  ```
  git push
  git push -u origin master #-u save values origin master as default for next push
  ```

## Branches 

* Create branch

  ```
  git branch test
  git checkout -b test #create and checkout branch
  ```

* Switch branch

  `git checkout master`
  
* Delete branch

  ```
  git branch -d test
  git branch -D test # abandon and delete branch even if there pending changes to be merged
  ```
  
## Remote

* Set remote repository

  `git remote add origin git@github.com:robertosequeira/flaming-octo-batman.git`
  
* List remotes

  ```
  git remote -v
  git remote show
  git remote show origin
  ```

## Repo status

* See repository history
  
  `git log`

* See repository status (Files added, removed, etc) 

  `git status`

## Undo changes

* Undo changes up to a specific commit and push changes

  ```
  git reset --hard 1a0a06de757776662e73efc813077225c842f2d8
  git push --force
  ```

* Undo current changes

  `git checkout -f`
  
## Reorder commits

Lets say you want to reoder last 3 commits so you enter at the command line:

  `git rebase -i HEAD~3`

After that the command line is going to display information about specified commits:

  ```
  pick 47d0ddc Commit file 3
  pick 4e42d63 Commit file 4
  pick 94c9d8e Commit file 5
  ```

Now to change the order of those commits you only need to change the order of the lines. Take into consideration that the rebase is going to pick the commits in the order they are specified (top-down) so from now "Commit file 4" is going to be the last commit.

  ```
  pick 47d0ddc Commit file 3
  pick 94c9d8e Commit file 5
  pick 4e42d63 Commit file 4
  ```

## Remove a commit

Same approach can be used to remove a commit

  `git rebase -i HEAD~3`

Now information related to specified commits is going to be displayed

  ```
  pick 47d0ddc Commit file 3
  pick 4e42d63 Commit file 4
  pick 94c9d8e Commit file 5
  ```

Finally you only need to remove the line corresponding to the commit that needs to be removed and save the changes.

  ```
  pick 47d0ddc Commit file 3
  pick 94c9d8e Commit file 5
  ```

From now "Commit file 4" does not exits

# Squash

Lets say you want to squash last 3 commits so you enter at the command line:

  `git rebase -i HEAD~3`

Now your are going to see information related to last 3 commits

  ```
  pick 47d0ddc Commit file 3
  pick 4e42d63 Commit file 4
  pick 94c9d8e Commit file 5
  ```

Now you have to specify which commits are going to be squashed

  ```
  pick 47d0ddc Commit file 3
  squash 4e42d63 Commit file 4
  squash 94c9d8e Commit file 5
  ```

For previous example changes from "Commit file 4" and "Commit file 5" are going to be merged on top of "Commit file 3".
After git merge all changes the user is going to be able to edit the new commit message. By default all messages from original commits are going to be included in the new commit message.

Reference (Reorder, remove, squash): https://git-scm.com/book/es/v2/Git-Tools-Rewriting-History
  
  
  
