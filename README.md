# osx-stack

A set of instructions for installing my development stack on OSX (Lion)

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

## Web stack

### PHP (with fpm and mysql)

    brew install /usr/local/LibraryAlt/duplicates/php.rb --with-fpm --with-mysql

### Node.js, Node Package Manager

    brew install node \
    && curl http://npmjs.org/install.sh | sh

### Rubygems

    git clone git://github.com/rubygems/rubygems.git ~/rubygems \
    && cd ~/rubygems \
    && sudo ruby setup.rb \
    && cd .. \
    && rm -rf rubygems

### RVM

    curl -L get.rvm.io | bash -s stable \
    && source ~/.rvm/scripts/'rvm' \
  	&& rvm install 1.9.3 \

Make sure you add the following to your bash profile (usually `~/.profile`).

    source ~/.rvm/scripts/'rvm'
