# Afander,  the Youngling

Just for having fun learning and using locally for site analysis.

## Installation

### Install Ruby Version Manager (RVM)

    $ gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 
    gpg: key 105BD0E739499BDB: public key "Piotr Kuczynski <piotr.kuczynski@gmail.com>" imported
    gpg: key 3804BB82D39DC0E3: public key "Michal Papis (RVM signing) <mpapis@gmail.com>" imported
    gpg: Total number processed: 2
    gpg:               imported: 2

    $ curl -sSL https://get.rvm.io | bash -s stable --ruby

    $ source /home/[username]/.rvm/scripts/rvm

    $ rvm --version
    rvm 1.29.12 (latest) by Michal Papis, Piotr Kuczynski, Wayne E. Seguin [https://rvm.io]

### Use latest Ruby version

    $ rvm list known

    $ rvm --default use ruby-3.0.0
    Using /home/[user]/.rvm/gems/ruby-3.0.0

### Install latest node

    $ curl -sL https://deb.nodesource.com/setup_15.x | sudo bash -

    $ sudo apt-get install -y nodejs

    $ node -v

### Install other dependencies

If you don't have them already, you'll also have to install 

    $ sudo apt-get install gcc g++ make

### Set up latest ruby gems

    $ gem update --system

    $ gem -v

### Install Ruby on Rails

Install [Ruby on Rails](https://rubygems.org/gems/rails/versions)

    $ gem install rails -v 6.1.3.1

    $ rails -v

### Install database and create role

Postgres:

    $ sudo apt-get install postgresql postgresql-contrib libpq-dev -y

    $ sudo systemctl start postgresql

    $ sudo systemctl enable postgresql

    $ dpkg --status postgresql

Log in as sudo on PostgreSQL

    $ sudo -u postgres psql

Change the postgres password

    postgress=# \password postgres

Create role

    postgress=# create role afander with createdb login password 'whateverpassword';

Check

    postgress=# \du

Leave with Ctrl-Z

### Set up Rails application

    $ rails new afander -d postgresql

Correct the gemfile and

    $ bundle install

### Configure database

In the config directory find file database.yml and configure development and test (two spaces in front of each line!)

    development:
      <<: *default
      database: afander_development
      username: afander
      password: [whateverpasswordyouchose]
      host: localhost
      port: 5432

    test:
      <<: *default
      database: afander_test
      username: afander
      password: [whateverpasswordyouchose]
      host: localhost
      port: 5432

Create the database

    $ rails db:setup
    Created database 'afander_development'
    Created database 'afander_test'
    ...

Migrate the database

    $ rails db:migrate

### Install yarn

Install yarn if you don't already have it

    $ curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -

    $ echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list

    $ sudo apt-get update

    $ sudo apt install --no-install-recommends yarn

### Launch Puma Rails Web Server

    $ rails webpacker:install

And try to resolve all dependencies with yarn.

Launch

    $ rails s -b localhost -p 8080

Yay! You're on Rails!

Now the crawler, indexer, query (ranking) and wiring.
 