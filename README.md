# Objective
Store my configuration

# macos
## install brew without root
```console
cd ~
git clone https://github.com/Homebrew/brew homebrew
mkdir ~/usr/local
# installed packaged directory
echo "export HOMEBREW_PREFIX=~/usr/local" >> ~/.zshrc
echo "export PATH=$PATH:~/homebrew/bin:HOMEBREW_PREFIX/bin" >> ~/.zshrc

# the brew items dir
brew --prefix
```
https://superuser.com/a/1689758/1644368

## shellcheck
```console
shellcheck -f diff $file | git apply
```
https://github.com/koalaman/shellcheck/issues/1220#issuecomment-594811243

## install openJDK
```console
# 101 https://sdkman.io/usage
curl -s https://get.sdkman.io | bash
```
`export JAVA_HOME=<jdk_location>`
1. https://www.azul.com/downloads/?package=jdk#download-openjdk
1. https://adoptium.net/index.html
1. https://docs.microsoft.com/en-us/java/openjdk/download
1. https://devblogs.microsoft.com/java/end-of-updates-support-and-availability-of-zulu-for-azure/
## main packages
```console
brew tap muesli/tap && brew tap homebrew/cask-fonts && brew tap ringohub/redis-cli buo/cask-upgrade
brew rm curl && brew install curl-openssl
brew install git coreutils findutils gnu-tar gnu-sed gawk gnutls gnu-indent gnu-getopt grep httpie pwgen tree zopfli mozjpeg duf pyenv tig helm minikube ripgrep jq yq ncdu zlib bzip2 libiconv libzip imap-uw libedit gitmoji redis-cli tfenv kubectl rclone logstalgia gnu-time shellcheck entr z tfenv pwgen
brew install --cask keka iterm2 sublime-text visual-studio-code dbeaver-community sourcetree insomnia postman google-chrome eloston-chromium imageoptim crunch mockoon devtoys bruno

# font
brew install --cask font-go-mono-nerd-font font-jetbrains-mono-nerd-font font-caskaydia-cove-nerd-font font-terminess-ttf-nerd-font font-3270-nerd-font font-blex-mono-nerd-font font-bigblue-terminal-nerd-font font-redhat

# npm
npm i -g @squoosh/cli
npm install -g tldr
npm i -g whistle && w2 start --init

# py
pip install diagrams

# git stat
## reference https://github.com/casperdcl/git-fame
pip install git-fame

# optional
brew install stubby dnsmasq

# for grep
# All commands have been installed with the prefix 'g'.
echo 'export PATH="$(brew --prefix)/opt/libiconv/bin:$PATH"' >> ~/.zshrc
echo 'export PATH="$(brew --prefix)/opt/bzip2/bin:$PATH"' >> ~/.zshrc
echo 'export PATH="$(brew --prefix)/opt/mozjpeg/bin:$PATH"' >> ~/.zshrc
echo 'export PATH="$(brew --prefix)/opt/gnu-getopt/bin:$PATH"' >> ~/.zshrc
echo 'export PATH="$(brew --prefix)/opt/gnu-indent/libexec/gnubin:$PATH"' >> ~/.zshrc
echo 'export PATH="$(brew --prefix)/opt/gnu-sed/libexec/gnubin:$PATH"' >> ~/.zshrc
echo 'export PATH="$(brew --prefix)/opt/coreutils/libexec/gnubin:$PATH"' >> ~/.zshrc
echo 'export PATH="$(brew --prefix)/opt/libiconv/bin:$PATH"' >> ~/.zshrc
echo 'export PATH="$(brew --prefix)/opt/curl/bin:$PATH"' >> ~/.zshrc
echo 'export PATH="$(brew --prefix)/opt/git/bin:$PATH"' >> ~/.zshrc
echo 'MANPATH="$(brew --prefix)/opt/coreutils/libexec/gnuman:$MANPATH"' >> ~/.zshrc

# ref
https://apple.stackexchange.com/questions/69223/how-to-replace-mac-os-x-utilities-with-gnu-core-utilities

# ncdu
ncdu --color=dark
```
## dnssec & dns-over-tls
### quick start
```
https://gist.github.com/uraimo/c651cbf3477994f95d8dbc7c60031697
```
### install
https://dnsprivacy.org/wiki/pages/viewpage.action?pageId=3145812
https://dnsprivacy.org/wiki/display/DP/Configuring+Stubby#ConfiguringStubby-DNSSEC
### config
#### dns list
https://dnsprivacy.org/wiki/display/DP/DNS+Privacy+Test+Servers
#### dnssec config example
1. https://gist.github.com/alanbuxey/8713073e232adfd56198e8cd8ee1258b
1. https://gist.github.com/uraimo/c651cbf3477994f95d8dbc7c60031697
1. https://wiki.archlinux.org/index.php/Stubby
#### get latest cf key
```sh
ref: https://github.com/getdnsapi/stubby/issues/87#issuecomment-377929340

echo | openssl s_client -connect '1.1.1.1:853' 2>/dev/null | openssl x509 -pubkey -noout | openssl pkey -pubin -outform der | openssl dgst -sha256 -binary | openssl enc -base64
od9obscoXQND56/DikypZrJkXGvbQV5Y61QGfcNitHo=

### test
1. https://dnsinstitute.com/documentation/dnssec-guide/ch03s02.html - dnssec
1. https://superuser.com/questions/1532975/how-to-query-for-dns-over-https-dns-over-tls-using-command-line - DoT
1. https://ns1.com/blog/using-dig-trace - using-dig-trace
```console
dnssec
kdig 216.58.208.110 google.com A +dnssec +multiline +tls

kdig -d @1.1.1.1 +tls-ca +tls-host=cloudflare-dns.com +dnssec example.com

http://en.conn.internet.nl/connection/
http://www.dnssec-tools.org/
http://dnssec.vs.uni-due.de/

DoT
https://www.cloudflare.com/ssl/encrypted-sni/
```

# php
```console
phpbrew install 8.0.2 +default +dbs +curl
```

# oh my zsh
## theme
https://github.com/juliuscaesar/unicorn
## prompt
1. https://github.com/starship/starship
1. https://github.com/sindresorhus/pure
1. https://dev.to/abdfnx/oh-my-zsh-powerlevel10k-cool-terminal-1no0
## font
1. https://github.com/ryanoasis/nerd-fonts
### command
```console
brew cask install font-go-mono-nerd-font
```

# password generate
```
# 14 is the len of the string
openssl rand -base64 14

brew install pwgen
pwgen -sBy 10 1
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

# .zshrc
```console
# theme
ZSH_THEME=""
autoload -U promptinit; promptinit
prompt pure

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
# alias cat="bat"

# k8s
alias kk="kubectl"

# show all fonts
alias show_fonts='system_profiler -json SPFontsDataType | grep \"family | sort | uniq'

# Alias
alias vi=vim
# alias top=glances
# alias cat=ccat
alias fzf="fzf --preview 'cat -n {}'"
alias mi="micro"
alias composer="composer.phar"
alias gg="gitmoji"

export EDITOR='vim' 
export VISUAL='vim'
# export TERM='terminator'

# ttf
# export WINDOWID=$(xdotool getwindowfocus)

# Go
export GOPATH=$HOME/works
export GOENV_ROOT="$HOME/.goenv"
eval "$(goenv init -)"
export PATH="$GOENV_ROOT/bin:$PATH"
export PATH=$PATH:$GOROOT/bin:$GOPATH/bin

# py
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init --path)"

# tf
export PATH="$HOME/.tfenv/bin:$PATH"

# php
[[ -e ~/.phpbrew/bashrc ]] && source ~/.phpbrew/bashrc

# http server
alias http="python -m SimpleHTTPServer"

# tools
export PATH="/usr/local/opt/mozjpeg/bin:$PATH"

# local
export LC_CTYPE=en_US.UTF-8
export LC_ALL=en_US.UTF-8
export LANG=en_US.UTF-8

# gnu-coreutils
# All commands have been installed with the prefix 'g'.
export PATH="$(brew --prefix)/opt/libiconv/bin:$PATH"
export PATH="$(brew --prefix)/opt/bzip2/bin:$PATH"
export PATH="$(brew --prefix)/opt/mozjpeg/bin:$PATH"
export PATH="$(brew --prefix)/opt/gnu-getopt/bin:$PATH"
export PATH="$(brew --prefix)/opt/gnu-indent/libexec/gnubin:$PATH"
export PATH="$(brew --prefix)/opt/gnu-sed/libexec/gnubin:$PATH"
export PATH="$(brew --prefix)/opt/coreutils/libexec/gnubin:$PATH"
export PATH="$(brew --prefix)/opt/libiconv/bin:$PATH"
export PATH="$(brew --prefix)/opt/bzip2/bin:$PATH"
export PATH="$(brew --prefix)/opt/curl/bin:$PATH"
export PATH="$(brew --prefix)/opt/git/bin:$PATH"
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

# vim colors
```sh
curl -o ~/.vim/colors/desert256.vim https://raw.githubusercontent.com/brafales/vim-desert256/refs/heads/master/colors/desert256.vim
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
   1. `ls ./*.jpg|xargs -I@ cjpeg -quality 10 -outfile ./out/@ @` to loop all
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
