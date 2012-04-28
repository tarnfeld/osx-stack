# osx-stack

A set of instructions for installing my development stack on OSX (Lion)

## Install the basics

### Dependencies

Make sure you have the latest version of XCode, with the command line tools installed. Also be sure the path to the command line tools is in your `$PATH` variable.

### Homebrew

#### Install homebrew

    /usr/bin/ruby -e "$(/usr/bin/curl -fksSL https://raw.github.com/mxcl/homebrew/master/Library/Contributions/install_homebrew.rb)"

#### Install git

    brew install git git-flow 

#### Update homebrew

    brew update

#### Get the extra homebrew bits

    git clone git://github.com/tarnfeld/homebrew-alt.git /usr/local/LibraryAlt

## Web stack

### Install a few languages / extras

#### PHP (with fpm and mysql)

    brew install /usr/local/LibraryAlt/duplicates/php.rb --with-fpm --with-mysql

#### Node.js, Node Package Manager

    brew install node
    curl http://npmjs.org/install.sh | sh

#### Ruby, Rubygems, RVM

    curl -L get.rvm.io | bash -s stable
