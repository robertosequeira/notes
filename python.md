# Python

* Restore pip exec for a specific python version (Mint, ?)
  ```
  $ sudo python -m pip install --upgrade --force-reinstall pip
  $ sudo python2.7 -m pip install --upgrade --force-reinstall pip
  $ sudo python3 -m pip install --upgrade --force-reinstall pip
  ```

* Creating a virtual env

  ```
  $ cd ~/project_directory
  $ virtualenv virtualenvname
  $ source virtualenvname/bin/activate
  $ pip install -r requirements.txt
  ```
