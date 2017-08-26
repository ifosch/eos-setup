# Debian - Elementary OS setup

## Introduction

Back in 2011, there were not many ultrabooks with memory and processing power enough to support the development setup and environment I could use when attending conferences and events, or working remotely.
The only option I found it was a MacBook Air, so I bought it.
I was decided to install Linux, even while for that time, it was not very easy, but I was adviced to try out MacOS.
It was nice enough, simple, and, even most important to me, supposed very light work and effort, just adopting some tools and get used to the new keyboard and hardware.
Anyway, deep inside, a part of me was willing to go back to Linux, a little bit.
That's why when I found easier to install Linux in a MacBook, I decided to prepare an automated setup for my local environment.

With this playbook I setup the following in my setup:

  - Caffeine Plus
  - Calibre :white_check_mark:
  - Conda
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
  - LibreOffice :white_check_mark:
  - OpenJDK Java JRE 8 :white_check_mark:
  - Pidgin :white_check_mark:
  - Pwgen :white_check_mark:
  - Remmina (RDP client) :white_check_mark:
  - RVM
  - Spotify :white_check_mark:
  - Slack (Scudcloud) :white_check_mark:
  - [Spacemacs](https://github.com/syl20bnr/spacemacs#linux-distros) :white_check_mark:
  - Telegram Desktop :white_check_mark:
  - Terminator :white_check_mark:
  - Thefuck
  - UNetBootIn
  - [Zeal (Dash clone)](http://zealdocs.org/) :white_check_mark:

## Requirements:

  - Fresh Debian Stretch or EOS Freya setup
  - When using Debian Stretch, `sudo` needs to be installed and setup.
    Use these commands, and log out and in back:

        su -
        apt-get install sudo gksu
        adduser <your_username> sudo

  - Run:

        sudo apt-get update && sudo apt-get -y upgrade
        sudo apt-get -y install git-core python-pip \
          libcurl4-openssl-dev python-dev
        sudo pip install ansible pycurl pyYAML argcomplete
        mkdir -p src/github.com/ifosch/eos-setup
        git clone https://github.com/ifosch/eos-setup.git \
          src/github.com/ifosch/eos-setup
        sudo mkdir -p /etc/ansible
        sudo bash -c '
          echo localhost ansible_connection=local >> /etc/ansible/hosts
        '
        exit

## To make it work:

    cd src/github.com/ifosch/eos-setup
    sudo ansible-playbook setup.yml --extra-vars "user=${USER}"
