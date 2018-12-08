## Setting up nginx

Add new location directives to nginx.conf

```
location ^~ /cycles/static/ {
	alias /home/student/projects/cycles/static/;
}

location ^~ /cycles/ {
	include uwsgi_params;
	uwsgi_pass 127.0.0.1:4305;
}
```

Then make sure you restart the server:

```
sudo systemctl restart nginx.service
```

## The appropriate run command

```
uwsgi --http :4305 --module cycles.wsgi
```



## Add your VM to ALLOWED_HOSTS in cycles/settings.py

This line here:

```
ALLOWED_HOSTS = ['*']
```

Once other people add there will more in the list.
