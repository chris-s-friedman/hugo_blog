---
title: "Dotfiles"
date: 2021-09-07T20:41:05-04:00
draft: false
type: "post"
slug: "dotfiles"
tags:
  - dotfiles
---

If there's a single tool I made, that I am most greatful for having in my toolbelt, i'd say it is my collection of dotfiles. I am frequently booting up new cloud computing instances, so being able to automate - and quickly execute - my setup allows me to have a more enjoyable dev experience.

{{% note %}}
Disclaimer: Below i'll talk about my dotfiles and the way _that I_ organize them, but dotfiles are a very personal tool that should be suited to the individual's needs, desires, and preferences. That said, my dotfiles are <a href="https://github.com/chris-s-friedman/dotfiles" target="_blank">here</a>
{{% /note %}}

## Individual Dotfiles

Currently, my dotfiles are split into the following seperate files:

- `.alias` for all my aliases
- `.exports` for all my exports.
- `.functions.sh` for my own helpful functions
- `.gitconfig` for my gitconfig. useful to be able to have my development environment be the same between machines.
- `.p10k.zsh` is my <a href="https://github.com/romkatv/powerlevel10k" target="_blank">powerlevel10k</a> theme. I love this theme and how it's organized. Still need to automate making sure that nerdfonts get installed.
- `.vimrc` for my vim configurations
- `.zshrc` for my zsh configuration
- `Brewfile` is my brewfile to automate installing programs, apps and tools with brew as well as from the mac app store. I initially created my brewfile following these <a href="https://openfolder.sh/macos-migrations-with-brewfile" target="_blank">instructions</a>, but basically, the brewfile can be created and updated with `brew bundle dump`.

## Setup Scripts

When setting up a new machine - for personal use, work, or perhaps a cloud compute instance such as an ec2 - i can use the setup scripts I have to get my dotfiles in place and being used.

1. Clone my dotfiles `git clone https://github.com/chris-s-friedman/dotfiles.git`
2. cd into my dotfile repo `cd dotfiles`
3. I haven't automated this yet - but if zsh isn't installed, install zsh `sudo apt-get install git zsh`
4. set zsh to be default shell and install <a href="https://ohmyz.sh/" target="_blank">oh-my-zsh</a> `sh system/set_shell.sh`
5. do the rest of the setup, like copying over the dotfiles, setting up oh-my-zsh addons, and installing other apps, programs, and tools `sh system/setup.sh`

Once that script finished, I'm usually good to go and ready to start working!
