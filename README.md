shadowsocks
===========

[![PyPI version]][PyPI]
[![Build Status]][Travis CI]

A fast tunnel proxy that helps you bypass firewalls.

Features:
- TCP & UDP support
- User management API
- TCP Fast Open
- Workers and graceful restart
- Destination IP blacklist

Server
------

### Install

Debian / Ubuntu:

    apt-get install python-pip
    pip install git+https://github.com/developmentmachine/shadowsocks.git@master

CentOS:

    yum install python-setuptools && easy_install pip
    pip install git+https://github.com/developmentmachine/shadowsocks.git@master

For CentOS 7, if you need AEAD ciphers, you need install libsodium
```
dnf install libsodium python34-pip
pip3 install  git+https://github.com/developmentmachine/shadowsocks.git@master
```
Termux:

    pkg install python git
    pip install git+https://github.com/developmentmachine/shadowsocks.git@master

**Note:** If Python is upgraded (e.g., in Termux or your system), you must uninstall and reinstall the package:

    pip uninstall shadowsocks
    pip install git+https://github.com/developmentmachine/shadowsocks.git@master

Linux distributions with [snap](http://snapcraft.io/):

    snap install shadowsocks

Windows:

See [Install Shadowsocks Server on Windows](https://github.com/developmentmachine/shadowsocks/wiki/Install-Shadowsocks-Server-on-Windows).

### Usage

    ssserver -p 443 -k password -m aes-256-cfb

To run in the background:

    sudo ssserver -p 443 -k password -m aes-256-cfb --user nobody -d start

To stop:

    sudo ssserver -d stop

To check the log:

    sudo less /var/log/shadowsocks.log

Check all the options via `-h`. You can also use a [Configuration] file
instead.

If you installed the [snap](http://snapcraft.io/) package, you have to prefix the commands with `shadowsocks.`,
like this:

    shadowsocks.ssserver -p 443 -k password -m aes-256-cfb
    
### Usage with Config File

[Create configuration file and run](https://github.com/developmentmachine/shadowsocks/wiki/Configuration-via-Config-File)

```json
{
    "server":"0.0.0.0",
    "server_port":10086,
    "local_address":"127.0.0.1",
    "local_port":1080,
    "password":"123456",
    "timeout":300,
    "method":"aes-256-cfb",
    "fast_open":false
}
```

To start:

    ssserver -c /etc/shadowsocks.json

For Termux:
Save the following as a script (e.g., `start.sh`) and run it:

```bash
#!/usr/bin/env bash
$PREFIX/bin/ssserver -c .config.json
```


Documentation
-------------

You can find all the documentation in the [Wiki](https://github.com/developmentmachine/shadowsocks/wiki).

License
-------

Apache License







[Build Status]:      https://img.shields.io/travis/shadowsocks/shadowsocks/master.svg?style=flat
[PyPI]:              https://pypi.python.org/pypi/shadowsocks
[PyPI version]:      https://img.shields.io/pypi/v/shadowsocks.svg?style=flat
[Travis CI]:         https://travis-ci.org/shadowsocks/shadowsocks

