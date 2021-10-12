# Installing OctoPrint on LIMS

These are the instructions for installing OctoPrint directly into the OS on a Raspberry Pi.

For instructions on how to use a container (the preferred method) see these instructions [TBD]


## Install OctoPrint
```
$ sudo apt update
$ sudo apt install -yy python3-pip python3-dev python3-setuptools python3-venv git libyaml-dev build-essential
$ sudo pip install --ignore-install blinker
$ sudo pip install --ignore-install pyserial
$ sudo pip install urllib3==1.21.1
$ sudo mkdir /opt/octoprint && cd /opt/octoprint
$ sudo pip install pip --upgrade
$ sudo pip install --no-cache-dir octoprint
$ sudo usermod -a -G tty pi
$ sudo usermod -a -G dialout pi
```


## Set up OctoPrint to run on boot

```
$ sudo wget https://github.com/OctoPrint/OctoPrint/raw/master/scripts/octoprint.service && sudo mv octoprint.service /etc/systemd/system/octoprint.service
$ sudo nano /etc/systemd/system/octoprint.service
```
Find the following line:
```
ExecStart=/home/pi/OctoPrint/venv/bin/octoprint
```
Modify it to read:

```
ExecStart=/usr/local/bin/octoprint serve
```

Finally enable the service

```
sudo systemctl enable octoprint.service
```
