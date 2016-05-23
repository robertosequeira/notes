# Command line

## Common commands

| Description                         | Command              | Example                      |
| ----------------------------------- |:--------------------:| ---------------------------- |
| list contents                       | ls                   | `$ ls -l`                    |
| make directory                      | mkdir <dirname>      | `$ mkdir workspace`          |
| change directory                    | cd <dirname>         | `$ cd workspace/`            |
| cd one directory up                 |                      | `$ cd ..`                    |
| cd to home directory                |                      | `$ cd ~` or just `$ cd`      |
| cd to path incl. home dir           |                      | `$ cd ~/workspace/`          |
| move file (rename)                  | mv <source> <target> | `$ mv README.rdoc README.md` |
| copy file                           | cp <source> <target> | `$ cp README.rdoc README.md` |
| remove file                         | rm <file>            | `$ rm README.rdoc`           |
| remove empty directory              | rmdir <directory>    | `$ rmdir workspace/`         |
| remove nonempty directory           | rm -rf <directory>   | `$ rm -rf tmp/`              |
| concatenate & display file contents | cat <file>           | `$ cat ~/.ssh/id_rsa.pub`    |

**Source** [Ruby on Rails tutorial](https://www.railstutorial.org/book/)

----


| Description                   | Command                             |
| ----------------------------- | ----------------------------------- |
| Create a symlink              | $ ln -s target link_name            | 
| Print working directory       | $ pwd                               |

## Execute .sh file

* Set execution permission

  `$ chmod 755 clone_repos.sh`

* Execute script

  `$ ./clone_repos.sh`

## Execute commands in the background

- Backup a big DB
  
  ```
  $ nohup pg_dump -v -U postgres my_database > my_database.dump > dump.log & 

  ```

- Copy a local file to a remote server over ssh. 
 
  This command requires ssh keys in order for `user` being allowed to access the server. Otherwhise scp is going to ask for the password and as the process is being executed by `nohup` it's going to fail.

  ```bash
  $ nohup scp -v my_file.txt user@roberto-sequeira.com:~/ &
  ```

- Copy a local file to a remote server over ssh entering user password

  ```bash
  $ scp -v my_file.txt user@roberto-sequeira.com:~/
  $ user@roberto-sequeira.com's password:
  ```
  
  Enter password and then press `Ctrl + z` to pause process
  
  ```
  $ bg
  $ disown
  ```

