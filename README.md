# osx-stack

A set of instructions for installing my development stack on OSX (Lion). You may also need root for some of these commands! **Run all of these commnds from the root of this repository**.

## Install the basics

Make sure you have the latest version of XCode, with the command line tools installed. Also be sure the path to the command line tools is in your `$PATH` variable.

### Install homebrew

    /usr/bin/ruby -e "$(/usr/bin/curl -fksSL https://raw.github.com/mxcl/homebrew/master/Library/Contributions/install_homebrew.rb)"

### Install git

    brew install git git-flow

### Update homebrew

    brew update

### Get the extra homebrew library

    git clone git://github.com/tarnfeld/homebrew-alt.git /usr/local/LibraryAlt

## Databases

### MongoDB

Soon

### Riak

Soon

### MySQL

    brew install mysql \
    && sudo mkdir -p /Library/LaunchAgents \
    && sudo cp LaunchAgents/homebrew.mxcl.mysql.plist /Library/LaunchAgents/ \
    && sudo launchctl load /Library/LaunchAgents/homebrew.mxcl.mysql.plist \
    && sudo mysql_install_db --verbose --user=`whoami` --basedir="$(brew --prefix mysql)" --datadir=/usr/local/var/mysql --tmpdir=/tmp

### Redis

    brew install redis \
    && sudo mkdir -p /Library/LaunchAgents \
    && sudo cp LaunchAgents/homebrew.mxcl.redis.plist /Library/LaunchAgents/ \
    && sudo launchctl load /Library/LaunchAgents/homebrew.mxcl.redis.plist

### Memcached

    brew install memcached \
    && sudo mkdir -p /Library/LaunchDaemons \
    && sudo cp LaunchDaemons/homebrew.mxcl.memcached.plist /Library/LaunchDaemons/ \
    && sudo launchctl load /Library/LaunchDaemons/homebrew.mxcl.memcached.plist

## Web stack

### PHP (with fpm, mysql and other extensions)

    brew install /usr/local/LibraryAlt/duplicates/php.rb --with-fpm --with-mysql \
    && brew install gearman-php memcached-php mongo-php xdebug-php xcache-php redis-php imagick-php
    && cp Config/php.ini /usr/local/etc/php.ini \
    && cp Config/php-fpm.conf /usr/local/etc/php-fpm.conf \
    && sudo mkdir -p /Library/LaunchDaemons \
    && sudo cp LaunchDaemons/org.php-fpm.plist /Library/LaunchDaemons/ \
    && sudo launchctl load /Library/LaunchDaemons/org.php-fpm.plist

### PHP XDebug (if you don't install it from above)

    brew tap josegonzalez/php \
    && brew install josegonzalez/php/xdebug-php

Make sure you add the following to your php ini (usually `/usr/local/etc/php.ini`)

    zend_extension="/usr/local/Cellar/xdebug-php/2.1.3/xdebug.so"

### PHPUnit

    sudo pear config-set auto_discover 1 \
    && sudo pear install pear.phpunit.de/PHPUnit

Make sure you have the following in your path

    /usr/local/Cellar/php/5.3.10/bin

### NGINX

    brew install nginx \
    && sudo mkdir -p /Library/LaunchDaemons \
    && sudo cp -r Config/nginx /usr/local/etc/nginx \
    && sudo cp LaunchDaemons/homebrew.mxcl.nginx.plist /Library/LaunchDaemons/ \
    && sudo launchctl load /Library/LaunchDaemons/homebrew.mxcl.nginx.plist

### Apache

Run the following commands to configure apache (the version that comes preinstalled). **Don't forget to enable web sharing!**

    sudo cp Config/apache/includes.conf /etc/apache2/other/ \
    && sudo cp Config/apache/php.conf /etc/apache2/other/ \
    && sudo cp Config/apache/directory.conf /etc/apache2/other/ \
    && sudo cp Config/php.ini /etc/php.ini \
    && sudo apachectl restart

### Node.js (and npm)

    brew install node \
    && curl http://npmjs.org/install.sh | sh

### Rubygems

    git clone git://github.com/rubygems/rubygems.git /tmp/rubygems \
    && OLD_PATH=`pwd` \
    && cd /tmp/rubygems \
    && sudo ruby setup.rb \
    && cd .. \
    && rm -rf rubygems \
    && cd $OLD_PATH

### RVM

    curl -L get.rvm.io | bash -s stable \
    && source ~/.rvm/scripts/'rvm' \
  	&& rvm install 1.9.3 \

Make sure you add the following to your bash profile (usually `~/.profile`)

    source ~/.rvm/scripts/'rvm'

## Tools

### Teleport

    gem install teleport

