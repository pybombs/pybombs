# Base image
FROM debian:buster
WORKDIR /pybombs

# Minimal package installation
RUN apt-get update -qq -y
# ruamel will get installed by setup.py via pip, but this just makes the
# process smoother
RUN apt-get install -qq -y python3-pip
RUN apt-get install -qq -y python3-ruamel.yaml

# Install PyBOMBS using setuptools
COPY PyBOMBS*.tar.gz /pybombs
RUN tar zxf *.tar.gz
RUN cd * && python3 setup.py install -q

# Install something
RUN mkdir /prefix
RUN cd /prefix
RUN pybombs -v auto-config
RUN pybombs -v recipes add-defaults
RUN pybombs -v prefix init -a default default
RUN pybombs install gr-osmosdr

