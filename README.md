# .conf.d
Store my configuration

# diff-so-fancy
```bash
# Setting for the new UTF-8 terminal support in Lion
export LC_CTYPE="en_US.UTF-8"
export LC_ALL="en_US.UTF-8"
```


# Supervisor configuration
In this guide I'll assume you have a functionning supervisor installation. It will allow us to execute caddy as a daemon. First of all we'll edit the /etc/supervisor/supervisord.conf and add this line under the [supervisord] section :

```
minfds=4096
```

Why is that ? In a production environment, caddy will complain that the number of open file descriptor is too low. The reason is that supervisor's default value is too low (1024, instead of 4096 as recommended by caddy). Now let's add a new program to our supervisor configuration. Create the file <code>/etc/supervisord/conf.d/caddy.conf</code>:

```
[program:caddy]
directory=/etc/caddy/
command=/etc/caddy/caddy -conf="/etc/caddy/Caddyfile"
user=www-data
autostart=true
autorestart=true
stdout_logfile=/var/log/supervisor/caddy_stdout.log
stderr_logfile=/var/log/supervisor/caddy_stderr.log
```

You can customize the user to the one you want. As I said earlier, caddy now doesn't need root privileges to bind to low ports, so any user will do (prefer a user with few rights). Caddy is now ready to be started by supervisor ! Simply add the program into supervisor and enjoy.
```sh
supervisorctl reread
supervisorctl add caddy
supervisorctl start caddy
```

# Reference
[http://depado.markdownblog.com/2015-12-07-setting-up-caddy-server-on-debian](http://depado.markdownblog.com/2015-12-07-setting-up-caddy-server-on-debian)
