# .conf.d
Store my configuration

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
# Reference
[http://depado.markdownblog.com/2015-12-07-setting-up-caddy-server-on-debian](http://depado.markdownblog.com/2015-12-07-setting-up-caddy-server-on-debian)
