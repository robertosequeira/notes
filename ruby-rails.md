# Ruby - Rails

## RVM

* Install RVM(https://rvm.io/rvm/install)

  `\curl -sSL https://get.rvm.io | bash -s stable`

* List available ruby versions

  `rvm list known`

* Install a specific ruby version

```
  rvm install ree
  rvm install ruby-2.0.0
  rvm install 2.0.0
```

* Integrate rvm with gnome terminal (https://rvm.io/integration/gnome-terminal)

* Set default ruby version

  `rvm --default use 2.1.1`

* Create .ruby-version file

  `rvm --ruby-version use 2.1.1 --create`

* Create .ruby-version and .ruby-gemset file

  `rvm --ruby-version use ree@my_app --create`

* List installed ruby versions

  `rvm list`

* List gemsets for current ruby version

  `rvm gemset list`

* List gemsets across all installed ruby versions

  `rvm list gemsets`

## Rails

* Install required rails version
```
  gem install rails
  gem install rails -v 3.0.20
```

* Create new rails application
```
  rails new my_app
  rails new ~/Desktop/my_app
```

* Install dependencies listed in Gemfile

  `bundle install`

* Start rails server

  ```
  rails server
  rails s
  rails s -p 3001
  ```

* Scaffolding

```
  rails generate scaffold Store name:string address:string
  rails generate scaffold Article name:string description:text price:decimal total_in_shelf:integer total_in_vault:integer store_id:intege
```

## Rake

* List available rake tasks

  `rake -T`

* List available rake db tasks

  `rake -T db`

* Execute migrations

  `rake db:migrate`

## Other stuff

* Kill rails dev server

  `kill -9 $(lsof -i tcp:3000 -t)`
