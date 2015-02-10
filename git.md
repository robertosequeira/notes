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
  git add -A (add all new pending changes)
```

* Commit to local repo
```
  git commit -m "Added home page"
  git commit -a -m "Added some files" 
```

* Commit to origin
```
  git push
  git push -u origin master (-u save values origin master as default for next push)
```

* Create branch
```
  git branch test
  git checkout -b test (create and checkout branch)
```

* Delete branch
```
  git branch -d test
  git branch -D test (abandon branch even with pending changes to be merged)
```

* Switch branch
```
  git checkout master
```

* Set remote repository
```
  git remote add origin git@github.com:robertosequeira/flaming-octo-batman.git
  git remote -v
  git remote show
  git remote show origin
```

* See repository history
```
  git log
```

* See repository status (Files added, removed, etc) 
```
  git status
```

* Undo changes up to a specific commit and push changes
```
  git reset --hard 1a0a06de757776662e73efc813077225c842f2d8
  git push --force
```

* Undo current changes
```
  git checkout -f
```
