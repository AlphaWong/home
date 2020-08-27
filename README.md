# Objective
Store my configuration

# macos
```
brew install httpie
brew install gnu-sed grep
export PATH="/usr/local/opt/grep/libexec/gnubin:/usr/local/opt/gnu-sed/libexec/gnubin:$PATH"
```

# oh my zsh
## theme
https://github.com/juliuscaesar/unicorn

# password generate
```
# 14 is the len of the string
openssl rand -base64 14

brew install pwgen
pwgen -sy 10 1
```

# ssh
```
ssh-keygen -t ed25519 -C "email"
```
# PacAUR
```sh
sudo pacman -S pacaur
```
# Install all of it
```
# core
yay -S zsh neovim docker docker-compose

# tools
https://github.com/cjbassi/gotop

# json
go get -u github.com/simeji/jid/cmd/jid

# utils
yay -S ripgrep docker docker-compose glances fzf-git zopflipng-git mozjpeg tig xdotool ttyrec ttygif ripgrep powershell-bin ctop-bin

# Change shell
`sudo chsh`

# node
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash
npm i -g diff-so-fancy

# whistle
npm install -g whistle
```

# ttf gif (https://github.com/icholy/ttygif)
```
1. Create ttyrec recording

$ ttyrec myrecording

      Hit CTRL-D or type exit when done recording.

2. Convert to gif

$ ttygif myrecording

On OSX optionally you can set a -f flag which will bypass cropping which is needed for terminal apps which aren't full screen. Both standard Terminal and iTerm apps are supported.

$ ttygif myrecording -f
```

# bash-it
```
# Git alias
EDITOR=vim
alias vi="vim"
alias g="git"
alias gss="git status"
alias gp="git push"
alias gc="git commit"
alias ga="git add"
alias gt="git tag"
alias gf="git f"
alias gco="git checkout"
alias gr="git rebase"
alias gup="git pull --rebase"
alias cat="bat"

# k8s
alias kk="kubectl"

# Alias
alias vi=vim
# alias top=glances
# alias cat=ccat
alias fzf="fzf --preview 'cat -n {}'"
alias mi="micro"

export EDITOR='vim' 
export VISUAL='vim'
# export TERM='terminator'

# ttf
# export WINDOWID=$(xdotool getwindowfocus)

# Go
export GOROOT=$HOME/go
export GOPATH=$HOME/works
export PATH=$PATH:$GOROOT/bin:$GOPATH/bin
export GO111MODULE=on

# http server
alias http="python -m SimpleHTTPServer"

# tools
export PATH="/usr/local/opt/mozjpeg/bin:$PATH"
```

# ~/.config/powershell/profile.ps1
https://github.com/PowerShell/PowerShell/blob/master/docs/installation/linux.md#arch-linux
```ps1
Install-Module posh-git -Scope CurrentUser
Install-Module oh-my-posh -Scope CurrentUser
```
```ps1
# Alias list
set-alias vi vim
set-alias g git
set-alias top glances
set-alias gss "g status"

# Env var
$env:GOPATH = "$HOME/works"
$env:GOROOT = "$HOME/go"
$env:Path += "$GOROOT/bin:$GOPATH/bin"

# git
import-module posh-git
import-module oh-my-posh
set-theme Paradox
#
```

# zshrc
```bash
# Fix home end button
bindkey  "^[[H"   beginning-of-line
bindkey  "^[[F"   end-of-line

# Kubectl
if [ $commands[kubectl] ]; then
  source <(kubectl completion zsh)
fi

# Alias
alias vi=vim
alias top=glances
alias cat=ccat
alias open=nautilus
alias fzf=fzf --preview 'cat -n {}'

export EDITOR='vim' 
export VISUAL='vim'
export TERM='terminator'

# ttf
export WINDOWID=$(xdotool getwindowfocus)

# Go
export GOROOT=$HOME/go
export GOPATH=$HOME/works
export PATH=$PATH:$GOROOT/bin:$GOPATH/bin

ZSH_THEME="amuse"
```

# Install font
Reference: http://ehellman.github.io/blog/2013/04/16/manually-install-a-font-in-arch-linux/
```sh
mv font.ttf /usr/share/fonts/
fc-cache -vf
```

# VPN auto start
```
vi ~/.kde4/Autostart
pritunl-client-gtk &
```

# VPN install
```sh
sudo tee -a /etc/pacman.conf << EOF
[pritunl]
Server = https://repo.pritunl.com/stable/pacman
EOF

sudo pacman-key --keyserver hkp://keyserver.ubuntu.com -r 7568D9BB55FF9E5287D586017AE645C0CF8E292A
sudo pacman-key --lsign-key 7568D9BB55FF9E5287D586017AE645C0CF8E292A
sudo pacman -Sy
sudo pacman -S pritunl-client-gtk
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
export EDITOR='vim' 
export VISUAL='vim'
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

# go metalinter
```sh
go get -u gopkg.in/alecthomas/gometalinter.v1
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
# fzf-git
1. `pacaur -S fzf-git`
1. `fzf --preview 'cat -n {}' `

# find cmd
1. `find ~ -name game`
1. https://www.lifewire.com/uses-of-linux-command-find-2201100

# grep cmd
1. grep -nrw source

# cat
1. `cat -n filename.txt`

# Image compress
1. zopflipng-git (png)
   1. install `pacaur -S zopflipng-git`
   1. run `zopflipng -m infile.png outfile.png`
1. https://github.com/mozilla/mozjpeg (jpg)
   1. install `pacaur -S mozjpeg`
   1. run `cjpeg -optimize in.png > out.jpg `
   1. `brew install mozjpeg`
1. cwebp (webp)
1. ```brew install guetzli```
1. https://github.com/chrissimpkins/Crunch
```console
brew cask install crunch
```
# tig
https://github.com/jonas/tig

# htop
https://github.com/hishamhm/htop

# glances
https://github.com/nicolargo/glances

# pip3
```
# Set pip3
export PY_USER_BIN=$(python3 -c 'import site; print(site.USER_BASE + "/bin")')
export PATH=$PY_USER_BIN:$PATH
```

# upterm
https://github.com/railsware/upterm

# Reference
[http://depado.markdownblog.com/2015-12-07-setting-up-caddy-server-on-debian](http://depado.markdownblog.com/2015-12-07-setting-up-caddy-server-on-debian)
