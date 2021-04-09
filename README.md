# Afander,  the Youngling

Just for learning and having fun.

## Installation

Download and install Ruby Version Manager (RVM):

    $ gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 
    gpg: key 105BD0E739499BDB: public key "Piotr Kuczynski <piotr.kuczynski@gmail.com>" imported
    gpg: key 3804BB82D39DC0E3: public key "Michal Papis (RVM signing) <mpapis@gmail.com>" imported
    gpg: Total number processed: 2
    gpg:               imported: 2

    $ curl -sSL https://get.rvm.io | bash -s stable --ruby

    $ source /home/[username]/.rvm/scripts/rvm

    $ rvm --version
    rvm 1.29.12 (latest) by Michal Papis, Piotr Kuczynski, Wayne E. Seguin [https://rvm.io]

Use latest Ruby version
    $ rvm list known

    $ rvm --default use ruby-3.0.0
    Using /home/[user]/.rvm/gems/ruby-3.0.0

Install latest node

    $ curl -sL https://deb.nodesource.com/setup_15.x | sudo bash -

    $ sudo apt-get install -y nodejs

    $ node -v

If you don't have them already, you'll also have to install 

    $ sudo apt-get install gcc g++ make

Set up latest ruby gems

    $ gem update --system

    $ gem -v

Install [Ruby on Rails](https://rubygems.org/gems/rails/versions)

    $ gem install rails -v 6.1.3.1

    $ rails -v

