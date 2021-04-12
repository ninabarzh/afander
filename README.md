# Afander,  the Youngling

Just for having fun learning and using locally for internet site analyses.

- [x] Yay! You're on Rails!
- [ ] Now the scraper and various analyses and wiring it all into a single page.

- [Afander,  the Youngling](#afander--the-youngling)
  - [Yay! You're on Rails!](#yay-youre-on-rails)
    - [Install Ruby Version Manager (RVM)](#install-ruby-version-manager-rvm)
    - [Use latest Ruby version](#use-latest-ruby-version)
    - [Install latest node](#install-latest-node)
    - [Install other dependencies](#install-other-dependencies)
    - [Set up latest ruby gems](#set-up-latest-ruby-gems)
    - [Install Ruby on Rails](#install-ruby-on-rails)
    - [Install database and create role](#install-database-and-create-role)
    - [Set up Rails application](#set-up-rails-application)
    - [Configure database](#configure-database)
    - [Install yarn](#install-yarn)
    - [Launch Puma Rails Web Server](#launch-puma-rails-web-server)
  - [Scraping](#scraping)
    - [Install Kimurai gem](#install-kimurai-gem)
    - [Install headless browsers](#install-headless-browsers)
  - [Problems or Suggestions](#problems-or-suggestions)
  - [Contributing](#contributing)


## Yay! You're on Rails!

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

    $ sudo apt install -y nodejs

    $ node -v

### Install other dependencies

If you don't have them already, you'll also have to install 

    $ sudo apt install gcc g++ make

### Set up latest ruby gems

    $ gem update --system

    $ gem -v

### Install Ruby on Rails

Install [Ruby on Rails](https://rubygems.org/gems/rails/versions)

    $ gem install rails -v 6.1.3.1

    $ rails -v

### Install database and create role

Postgres:

    $ sudo apt install postgresql postgresql-contrib libpq-dev -y

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

    $ rails s -b localhost -p 80

## Scraping

### Install Kimurai gem

    $ gem install kimurai

### Install headless browsers

Install x virtual framebuffer. It performs all graphical operations in virtual memory without showing any screen output.

    $ sudo apt install -q -y xvfb

[Selenium](https://www.selenium.dev/documentation/en/):

    § gem install selenium-webdriver

If not have yet, install chrome, firefox and phantom with drivers. Check and install the driver versions needed for [firefox](https://github.com/mozilla/geckodriver/releases/) and for [chrome](https://sites.google.com/a/chromium.org/chromedriver/downloads) (in my case version 89). For firefox I just used the latest geckodriver. All versions located here http://phantomjs.org/download.html

Firefox

    $ apt install firefox-esr

    $ wget https://github.com/mozilla/geckodriver/releases/download/v0.29.1/geckodriver-v0.29.1-linux64.tar.gz

    $ sudo tar -xvzf geckodriver-v0.29.1-linux64.tar.gz -C /usr/local/bin

Chrome

    $ sudo wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb

    $ sudo apt install ./google-chrome-stable_current_amd64.deb

    $ wget https://chromedriver.storage.googleapis.com/89.0.4389.23/chromedriver_linux64.zip

    $ sudo unzip chromedriver_linux64.zip -d /usr/local/bin

    $ sudo chown root:root /usr/local/bin/chromedriver

    $ sudo chmod +x /usr/local/bin/chromedriver

Phantom

    $ sudo apt install -q -y chrpath libxft-dev libfreetype6 libfreetype6-dev libfontconfig1 libfontconfig1-dev

    $ wget https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-2.1.1-linux-x86_64.tar.bz2

    $ tar -xvjf phantomjs-2.1.1-linux-x86_64.tar.bz2

    $ sudo mv phantomjs-2.1.1-linux-x86_64 /usr/local/lib

    $ sudo ln -s /usr/local/lib/phantomjs-2.1.1-linux-x86_64/bin/phantomjs /usr/local/bin

## Problems or Suggestions

[Open an issue here](https://github.com/tymyrddin/afander/issues)

## Contributing

This project welcomes contributions and suggestions.