# SDG-OS-WIKI

This repository contains the getting started and general user guide for both the sdg package system and my dotfiles (deployed through sdgpkg).

all of my repositories have been tested on CachyOS, though they should mostly be cross-platform as long as the dependencies are available in your repositories. 

sdgpkg and sdgbuild are both fully functional cross-platform, as is unipkg. 



## What is SDG-OS

SDG-OS and the sdg package system are effectively my dotfiles that got out of hand. It's a way to make it easy to modularly manage your system config in a standardized manner. 

The core of this is sdgpkg, the package manager.

`sdgpkg`, provided by the SDG-PKG repository, is a wrapper around git that allows you to easily install, update and uninstall packages created in the standard sdg package format. `sdgbuild`, provided by the SDG-BUILD repository, is a companion tool that helps create these packages.

Since the whole system uses git and github as a backend, this allows you to very easily make your own versions of packages. The repository structure is aimed at using multiple small repositories with different priorities, with the intent being that a set of dotfiles can have its own repository (For example, sdgpkg comes with the default repository for my dotfiles.)

An sdgpkg repository can also just be hosted as a file on github, and added with a single command. 

Together, sdgpkg and sdgbuild provide the following components:

| package name | main command | features |
| ------------ | ------------ | -------- |
| sdgos-meta | - | metapackage that installs all of my dotfiles, this package effectively gets you a clone of my setup |
| unipkg | unipkg | universal package management wrapper that makes it a lot easier for sdgpkg to install dependencies, since unipkg will call whichever package manager you have installed dynamically |
| sdg-mango | - | my core mangoWM, DankMaterialShell and Matugen configs. depends on sdg-term |
| sdg-term | - | my ghostty and zsh configs, including optional integration with various other sdg packages |
| sdg-docs | sdgdocs | interactive modular documentation viewer, every package comes with documentation, call sdgdocs from the terminal to view all the different available documentation topics and their related docs. 
| sdg-tips | sdgtip | modular tips system, every package comes with tips. integrates with sdg-term to show you a tip on initial terminal launch. | 
| sdg-mango-helpers | dmsbars/manlayout/mangoconf | provides various helpers for mangoWM including a line-by-line config explainer (`mangoconf view`) and an RGB daemon for corsair keyboard auto-theming |
| sdg-util | tldrtui/git-projects/colortui/reference | provides various utility scripts |
| sdg-fetch | sdgfetch | cli fastfetch wrapper with configuration TUI, various selectable logo's and configs and a quick way to convert an image to a fastfetch ASCII |
| sdg-themes | sdgtheme | auto-theming system for my mango config. handles colors, DMS config, borders and optionally fonts and sdgfetch config, includes a CLI for easily cloning the current theme to a new user theme as well as edit the current theme |
| sdg-vox | sdgvox | configurable voice control system with a GUI, includes custom wakewords and various triggered actions |
| sdg-glyphs | sdgglyphs | highly configurable glyph/symbol-based input and control system | 
| sdg-wayshell | wayshell | core daemon components allowing any command to be used as a dynamic shel component |
| sdg-wayshell-conf | - | default configurations for wayshell providing volume and brightness sliders, a screenshot system and pinable bottom bar modules showing performance impact of your focused application as well as elevated applications
| sdg-pkg | sdgpkg | package manager with simple repositories and branching capabilities | 
| sdg-build | sdgbuild | build system for creating your own packages, handling updates/branching and locally building packages | 


## getting started


To get started, you'll want to clone and bootstrap sdgpkg:
```sh
git clone https://github.com/SDG-Den/SDG-PKG
cd SDG-PKG
./bootstrap.sh
```

From there, you can choose how much of my dotfiles you want to install.

To install everything, just run the following command:
```
sdgpkg install sdgos-meta
```

`sdgpkg` will ask you to approve every install script, Simply press `y` to approve the installation of each component. 

This will *not* provide you with sdgbuild. 


To get a minimal functional install:
```sh
sdgpkg install sdg-mango # this will also install sdg-term
sdgpkg install sdg-docs # recommended
```

Keep in mind some binds will not work as their dependencies are missing. 



If you don't want to use my mango setup, and are just looking to use one of the specific components, just install that component:
```sh
sdgpkg install sdg-fetch
```


## updating

`sdgpkg` comes with a single command to upgrade all your packages: `sdgpkg upgrade`. 

You can also use `sdgpkg` through `unipkg`, which will also handle your other package managers. 

A full system update using unipkg would look like this: `unipkg update all && unipkg upgrade all`

updates will not replace your config files, installs and builds will.


## uninstalling 

to uninstall a package, you can run `sdgpkg uninstall <package name>`, note that this keeps your config files in place and does not uninstall any dependencies. 


## building locally

if you want to install a package without using sdgpkg, you can either use the build.sh script or run `sdgbuild build` in the root of the repository. This will not install dependencies and will overwrite configs. 

