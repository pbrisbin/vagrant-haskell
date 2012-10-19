A vagrant box for working on Haskell projects.

## Background

A fork of puffnfresh's [bitbucket][] project which was based largely off 
John Bender's [blog post][] and [project][].

[bitbucket]: https://bitbucket.org/puffnfresh/vagrant-haskell-heroku
[blog post]: http://johnbender.us/2011/03/05/snap-setup-from-scratch-the-vagrant-way/
[project]:   https://github.com/johnbender/snap-skeleton

## Changes

* Added apt recipe to get things working
* Default shared directory (see Usage)

## Planned changes

* Automate cabal update
* Remove heroku toolbelt (do that stuff in the host OS)
* Networking settings for viewing yesod apps from host OS

## Usage

From within your haskell project directory:

~~~ { .bash }
# Add this project as a submodule
$ git submodule add https://github.com/pbrisbin/vagrant-haskell ./vm
$ git submodule update --init

# Enter the submodule, bring up the VM, and SSH in
$ cd ./vm
$ vagrant up
$ vagrant ssh

# Within the VM update cabal (not strictly necessary, but a good idea)
[guest]$ cabal update
[guest]$ cabal install cabal-install

# Navigate to the shared sources and build your project
[guest]$ cd /app
[guest]$ cabal install
~~~
