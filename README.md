## Project Management Board
[![Waffle.io - Columns and their card count](https://badge.waffle.io/StevenTammen/cycles.svg?columns=all)](https://waffle.io/StevenTammen/cycles)

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

## The appropriate screen command

```
screen -S cycles uwsgi --socket 127.0.0.1:4305 \
--venv /home/student/projects/cycles \
--wsgi-file /home/student/projects/cycles/cycles/wsgi.py \
--master
```

## Add your VM to ALLOWED_HOSTS in cycles/settings.py

This line here:

```
ALLOWED_HOSTS = ['172.19.50.192']
```

Once other people add there will more in the list.
