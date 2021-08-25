# Git

## Configuration

* Set user data

  ```
  # Global
  $ git config --global user.name 'Roberto Sequeira'
  $ git config --global user.email 'hello@world.com'
  
  # at repo level
  $ git config user.name 'Roberto Sequeira'
  $ git config user.email 'hello@test.com'
  ```
  
* Push only current branch

  `$ git config --global push.default simple`

## Create repo

* Init/Set repository

  ```
  $ git init
  $ git clone git@github.com:robertosequeira/flaming-octo-batman.git
  ```

* Add file/files to repository

  ```
  $ git add index.html
  $ git add "*.html"
  $ git add -A #add all new pending changes
  ```

* Commit changes

  ```
  $ git commit -m "Added home page"
  $ git commit -a -m "Added some files" 
  ```

* Push changes

  ```
  $ git push
  $ git push -u origin master #-u save values origin master as default for next push
  ```
  
* Get from origin

  ```
  $ git pull
  $ git pull origin master
  ```

## Branches 

* Create branch

  ```
  $ git branch test
  $ git checkout -b test #create and checkout branch
  ```

* Switch branch

  `$ git checkout master`
  
* Delete branch

  ```
  $ git branch -d test
  $ git branch -D test # abandon and delete branch even if there pending changes to be merged
  ```
  
## Remote

* Set remote repository

  ```
  $ git remote add origin git@github.com:robertosequeira/flaming-octo-batman.git
  ```

* List remotes

  ```
  $ git remote -v
  $ git remote show
  $ git remote show origin
  ```

## Repo status

* See repository history
  
  `$ git log`

* See repository status (Files added, removed, etc) 

  `$ git status`

## Undo changes

* Undo changes up to a specific commit and push changes

  ```
  $ git reset --hard 1a0a06de757776662e73efc813077225c842f2d8
  $ git push --force
  ```

* Undo current changes

  `$ git checkout -f`

## Start an interactive rebase

The interactive rebase (specified with the flag `-i`) will allow you to interact with several commits to do actions like squash, reorder, reword, etc.

If you need the last **n** commits (where **n** is an integer) then you enter in the command line:

  `$ git rebase -i HEAD~n`

So for example, if you need the last 3 commits you would enter:

  `$ git rebase -i HEAD~3`
  
## Reorder commits

If you want to reoder last 3 commits, then you can [Start an interactive rebase](#start-an-interactive-rebase) and enter in the command line:

  `$ git rebase -i HEAD~3`

After that the command line is going to display information about specified commits:

  ```
  pick 47d0ddc Commit file 3
  pick 4e42d63 Commit file 4
  pick 94c9d8e Commit file 5
  ```

Now to change the order of those commits you only need to change the order of the lines and save the changes. Once you close the file the rebase will continue.

  ```
  pick 47d0ddc Commit file 3
  pick 94c9d8e Commit file 5
  pick 4e42d63 Commit file 4 # THIS COMMIT WAS MOVED TO BE THE LAST ONE
  ```

Take into consideration that the rebase is going to pick the commits in the order they are specified (top-down) so from now on "Commit file 4" is going to be the last commit.

Finally you need to push the changes, if you branch was already published you will have to `git push -f` in order to update the remote with you local changes. If your branch was not publishe then you can `git push`.

## Remove a commit

Using the same approach you can [Start an interactive rebase](#start-an-interactive-rebase) in order to remove a commit. For example:

  `$ git rebase -i HEAD~3`

Now information related to specified commits is going to be displayed

  ```
  pick 47d0ddc Commit file 3
  pick 4e42d63 Commit file 4
  pick 94c9d8e Commit file 5
  ```

You only need to remove the line corresponding to the commit that needs to be removed and save the changes. Once you close the file the rebase will continue.

  ```
  pick 47d0ddc Commit file 3
  pick 94c9d8e Commit file 5
  ```

From now on "Commit file 4" does not exits.

Finally you need to push the changes, if you branch was already published you will have to `git push -f` in order to update the remote with you local changes. If your branch was not publishe then you can `git push`.

## Squash

If you want to squash last 3 commits, then you can [Start an interactive rebase](#start-an-interactive-rebase) and enter in the command line:

  `$ git rebase -i HEAD~3`

Now your are going to see information related to last 3 commits

  ```
  pick 47d0ddc Commit file 3
  pick 4e42d63 Commit file 4
  pick 94c9d8e Commit file 5
  ```

Then with `squash` you have to specify which commits are going to be squashed

  ```
  pick 47d0ddc Commit file 3
  squash 4e42d63 Commit file 4
  squash 94c9d8e Commit file 5
  ```
  
For previous example changes from "Commit file 4" and "Commit file 5" are going to be merged on top of "Commit file 3".

Now you just need to save the changes and once you close the file the rebase will continue.

After git merges all changes the user is going to be able to edit the new commit message. By default all messages from original commits are going to be included in the new commit message.

Finally you need to push the changes, if you branch was already published you will have to `git push -f` in order to update the remote with you local changes. If your branch was not publishe then you can `git push`.

## Reword

If you want to update the commit message for a old commit, then you can [Start an interactive rebase](#start-an-interactive-rebase) and enter in the command line:

  `$ git rebase -i HEAD~3`

Now your are going to see information related to last 3 commits

  ```
  pick 47d0ddc Commit file 3
  pick 4e42d63 Commit file 4
  pick 94c9d8e Commit file 5
  ```

Then using `reword` you have to specify which commits you want to update

  ```
  reword 47d0ddc Commit file 3
  pick 4e42d63 Commit file 4
  pick 94c9d8e Commit file 5
  ```

Once you save the changes and close the file the rebase will continue and you are going to be asked for the new commit message for the commit you marked with `reword`.

Finally you need to push the changes, if you branch was already published you will have to `git push -f` in order to update the remote with you local changes. If your branch was not publishe then you can `git push`.

------

Reference (Reorder, remove, squash): https://git-scm.com/book/es/v2/Git-Tools-Rewriting-History
