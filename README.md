# Debian - Elementary OS setup

## Introduction

Back in 2011, there were not many ultrabooks with memory and processing power enough to support the development setup and environment I could use when attending conferences and events, or working remotely.
The only option I found it was a MacBook Air, so I bought it.
I was decided to install Linux, even while for that time, it was not very easy, but I was adviced to try out MacOS.
It was nice enough, simple, and, even most important to me, supposed very light work and effort, just adopting some tools and get used to the new keyboard and hardware.
Anyway, deep inside, a part of me was willing to go back to Linux, a little bit.
That's why when I found feasible to install Linux in a MacBook, I decided to prepare an automated setup for my local environment.

With this playbook I setup the following in my setup:

  - Caffeine Plus
  - Calibre :white_check_mark:
  - Conda :white_check_mark:
  - [Docker](www.docker.com) :white_check_mark:
  - Dropbox :white_check_mark:
  - Firefox :white_check_mark:
  - Gimp :white_check_mark:
  - Github Hub :white_check_mark:
  - Google Chrome (with hangouts) :white_check_mark:
  - Google Go :white_check_mark:
  - Htop :white_check_mark:
  - Heroku Toolbelt :white_check_mark:
  - Ipcalc :white_check_mark:
  - KeepassX :white_check_mark:
  - [Keybase](www.keybase.com) :white_check_mark:
  - LibreOffice :white_check_mark:
  - [NVM](https://github.com/creationix/nvm.git) :white_check_mark:
  - OpenJDK Java JRE 8 :white_check_mark:
  - [Packer](https://www.packer.io) :white_check_mark:
  - Pidgin :white_check_mark:
  - Pwgen :white_check_mark:
  - Remmina (RDP client) :white_check_mark:
  - RVM :white_check_mark:
  - Spotify :white_check_mark:
  - Slack (Scudcloud) :white_check_mark:
  - [Spacemacs](https://github.com/syl20bnr/spacemacs#linux-distros) :white_check_mark:
  - Telegram Desktop :white_check_mark:
  - Terminator :white_check_mark:
  - Thefuck :white_check_mark:
  - [Vagrant](www.vagrantup.com) :white_check_marker:
  - [VirtualBox 5.1](https://download.docker.com/linux/debian/gpg) :white_check_mark:
  - [Zeal (Dash clone)](http://zealdocs.org/) :white_check_mark:

## Requirements:

  - Fresh Debian Stretch or newer, or EOS Freya setup
  - When using Debian Buster, or previous, `sudo` needs to be installed and setup.
    Use these commands, and log out and in back:

        su -
        apt-get install sudo gksu
        adduser ${USER} sudo
        newgrp sudo
        newgrp ${USER}

  - Run:

        sudo apt-get update && sudo apt-get -y upgrade
        sudo apt-get -y install git-core python3-pip \
          libcurl4-openssl-dev python-dev libssl-dev
        sudo pip3 install ansible pycurl pyYAML argcomplete
        mkdir -p src/github.com/ifosch/eos-setup
        git clone https://github.com/ifosch/eos-setup.git \
          src/github.com/ifosch/eos-setup
        sudo mkdir -p /etc/ansible
        sudo bash -c '
          echo localhost ansible_connection=local ansible_python_interpreter=/usr/bin/python3 >> /etc/ansible/hosts
        '
        exit
        
## Your setup

In order to adjust this for your setup, you can remove or add any software, by removing or adding the role name in the `setup.yml`.

If you are interested in writing new roles, you must remember to include a `prepare_repos.yml` task file in the role, or the `common` role will fail.

## To make it work:

    cd src/github.com/ifosch/eos-setup
    sudo ansible-playbook setup.yml --extra-vars "user=${USER}"

When using Debian Buster, reboot after this finished.
