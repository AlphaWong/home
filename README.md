# Objective
Store my configuration

# ssh
```
ssh-keygen -t ed25519 -C "email"
```
# PacAUR
```sh
sudo pacman -S pacaur
```
# zshrc
```bash
# Alias
alias vi=nvim
alias top=htop
alias cat=ccat
alias open=nautilus

export EDITOR='nvim' 
export VISUAL='nvim'
export TERM='terminator'

# Go
export GOROOT=$HOME/go
export GOPATH=$HOME/works
export PATH=$PATH:$GOROOT/bin:$GOPATH/bin

ZSH_THEME="amuse"
```

# gcin
```bash
# ~/.xprofile 
# http://hyperrate.com/thread.php?tid=31637
# https://manjaro-zh.blogspot.hk/2015/05/manjaro-linux-gcin.html

export GTK_IM_MODULE=gcin
export QT_IM_MODULE=gcin
export XMODIFIERS="@im=gcin"
gcin &
```

# Set default editor
```sh
export EDITOR='nvim' 
export VISUAL='nvim'
```

# neovim config
```sh
ln -s ~/.vimrc ~/.config/nvim/init.vim
```

# vim Vundle
```sh
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
```
Install Plugins:
```sh
# Launch vim and run
:PluginInstall
:GoInstallBinaries
```

# vim tree
https://github.com/scrooloose/nerdtree

# vim reference
https://github.com/google/vim-codefmt

```
brew install macvim --with-lua

# If you haven't launched Xcode after updating it, do so now. Xcode will ask for permission to install additional components. 
# Let it install those components. Once that is done, try the MacVim build again.
```
```
# use brew vim if present
/usr/local/bin/vim --version > /dev/null 2>&1
BREW_VIM_INSTALLED=$?

if [ $BREW_VIM_INSTALLED -eq 0 ]; then
   alias vi="/usr/local/bin/vim"
fi
```

# diff-so-fancy
Installation
```sh
npm i -g diff-so-fancy
```

```bash
# Setting for the new UTF-8 terminal support in Lion
export LC_CTYPE="en_US.UTF-8"
export LC_ALL="en_US.UTF-8"
```

# ccat
```sh
go get -u github.com/jingweno/ccat
```
It's recommended to alias ccat to cat:
```sh
alias cat=ccat
```

# tldr
Installation
```sh
npm install -g tldr
```
# the fuck
on-my-zsh
```bash
plugins=(git bundler osx rake ruby thefuck)
```

# Image compress
1. zopflipng-git (png)
   1. install `pacaur -S zopflipng-git`
   1. run `zopflipng -m infile.png outfile.png`
1. https://github.com/mozilla/mozjpeg (jpg)
   1. install `pacaur -S mozjpeg`
   1. run `cjpeg -optimize in.png > out.jpg `
1. cwebp (webp)

# tig
https://github.com/jonas/tig

# htop
https://github.com/hishamhm/htop

# glances
https://github.com/nicolargo/glances

# upterm
https://github.com/railsware/upterm

# Reference
[http://depado.markdownblog.com/2015-12-07-setting-up-caddy-server-on-debian](http://depado.markdownblog.com/2015-12-07-setting-up-caddy-server-on-debian)
