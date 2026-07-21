# SDG-OS-WIKI

This repository contains the getting started and general user guide for both the sdg package system and my dotfiles (deployed through sdgpkg).

all of my repositories have been tested on CachyOS, though they should mostly be cross-platform as long as the dependencies are available in your repositories. 

sdgpkg and sdgbuild are both fully functional cross-platform, as is unipkg. 



## What is SDG-OS

SDG-OS and the sdg package system are effectively my dotfiles that got out of hand. It's a way to make it easy to modularly manage your system config in a standardized manner. 

The core of this is sdgpkg, the package manager.

sdgpkg, provided by the SDG-PKG repository, is a wrapper around git that allows you to easily install, update and uninstall packages created in the standard sdg package format. sdgbuild, provided by the SDG-BUILD repository, is a companion tool that helps create these packages.

since the whole system uses git and github as a backend, this allows you to very easily make your own versions of packages. the repository structure is aimed at using multiple small repositories with different priorities, with the intent being that a set of dotfiles can have its own repository (For example, sdgpkg comes with the default repository for my dotfiles.)

an sdgpkg repository can also just be hosted as a file on github, and added with a single command. 

together, sdgpkg and sdgbuild provide the following components:

| package name | features |
| ------------ | -------- |
