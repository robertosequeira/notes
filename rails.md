# Rails

## RVM

`\curl -sSL https://get.rvm.io | bash -s stable` - [Install RVM](https://rvm.io/rvm/install)

`rvm list known` - List available ruby versions

`rvm install ree`, `rvm install ruby-2.0.0`, `rvm install 2.0.0` - Install a specific ruby version

https://rvm.io/integration/gnome-terminal - Integrate rvm with gnome terminal

`rvm --default use 2.1.1`- Set default ruby version

`rvm --ruby-version use 2.1.1 --create` - Create .ruby-version file

`rvm --ruby-version use ree@my_app --create` - Create .ruby-version and .ruby-gemset file

`rvm list` - List installed ruby versions

`rvm gemset list` - List gemsets for current ruby version

`rvm list gemsets` - List gemsets across all installed ruby versions

## Rails

`gem install rails -v 3.0.20`, `gem install rails` - Install required rails version

`rails new my_app`, `rails new ~/Desktop/my_app` - Create new rails application

`bundle install` - Install dependencies listed in Gemfile

`rails server` - Start the rails server

`rails generate scaffold Store name:string address:string`

`rails generate scaffold Article name:string description:text price:decimal total_in_shelf:integer total_in_vault:integer store_id:intege`

## Rake

`rake -T` - List available rake tasks

`rake -T db` - List available rake db tasks

`rake db:migrate`
