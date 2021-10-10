FROM balenalib/raspberrypi400-64-debian

RUN apt-get upgrade
RUN apt-get update
RUN apt-get install -yy python3-pip python3-dev python3-setuptools python3-venv git libyaml-dev build-essential
RUN pip install pip --upgrade
RUN pip install --no-cache-dir octoprint

# octopi defaults to running on port 5000.  Remap when you run if you wish
EXPOSE 5000

# octoprint doesn't like running as root, so create a user
RUN useradd -ms /bin/bash pi

USER pi
WORKDIR /home/pi