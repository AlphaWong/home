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
```

# diff-so-fancy
```bash
# Setting for the new UTF-8 terminal support in Lion
export LC_CTYPE="en_US.UTF-8"
export LC_ALL="en_US.UTF-8"
```

You can customize the user to the one you want. As I said earlier, caddy now doesn't need root privileges to bind to low ports, so any user will do (prefer a user with few rights). Caddy is now ready to be started by supervisor ! Simply add the program into supervisor and enjoy.
```sh
supervisorctl reread
supervisorctl add caddy
supervisorctl start caddy
```

# Reference
[http://depado.markdownblog.com/2015-12-07-setting-up-caddy-server-on-debian](http://depado.markdownblog.com/2015-12-07-setting-up-caddy-server-on-debian)
