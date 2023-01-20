## Prerequisites

### Virtual Environment

Install the python3-venv package:

```
apt-get install python3-venv  
```

Create directory for the virtual environment:

```
mkdir djangoenv
```

Create the virtual environment:

```
cd djangoenv
python3 -m venv djangoenv  
```

Activate the virtual environment:

```
source djangoenv/bin/activate  
```


## Installation

```
sudo apt-get update
pip install django  
```

## Startup

Start Daphne like this:

```
daphne dashboard.asgi:application
```

## Enhancements

* [ ] create a virtual python environment for the app to run inside
* [ ] create a systemd service to start the app on boot

## Start as a Service

Create a service file like this:

```
[Unit]
Description=My Daphne Service
After=network.target

[Service]
Type=simple
User=wwwrunn
WorkingDirectory=/srv/myapp
ExecStart=/path/to/my/virtualenv/bin/python /path/to/daphne -b 0.0.0.0 -p 8001 myproject.asgi:application
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

Save it in `/etc/systemd/system/myapp.service` and make the system aware of it:

```
sudo systemctl daemon-reload
```

Start the service

```
sudo systemctl start daphne.service
```

Make it run on reboot

```
sudo systemctl enable daphne.service
```