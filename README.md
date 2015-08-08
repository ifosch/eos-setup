# Elementary OS setup

## Introduction

Back in 2011, there were not many ultrabooks with memory and processing power enough to support the development setup and environment I could use when attending conferences and events, or working remotely.
The only option I found it was a MacBook Air, so I bought it.
I was decided to install Linux, even while for that time, it was not very easy, but I was adviced to try out MacOS.
It was nice enough, simple, and, even most important to me, supposed very light work and effort, just adopting some tools and get used to the new keyboard and hardware.
Anyway, deep inside, a part of me was willing to go back to Linux, a little bit.
That's why when I found easier to install Linux in a MacBook, I decided to prepare an automated setup for my local environment.

With this playbook I setup the following in my elementary OS installation:

  - BTSync
  - Caffeine Plus
  - Calibre
  - Dropbox
  - Firefox
  - Gimp
  - Github Hub
  - Google Chrome (with hangouts)
  - Google Go
  - Htop
  - Heroku Toolbelt
  - Ipcalc
  - KeepassX
  - LibreOffice
  - NVM
  - OpenJDK Java JRE 7
  - Pidgin
  - Pwgen
  - Remmina
  - RVM
  - Spotify
  - Telegram Desktop
  - Terminator
  - Thefuck
  - UNetBootIn
  - [Zeal (Dash clone)][http://zealdocs.org/]

## Requirements:

  - Fresh EOS Freya setup
  - Run:

        sudo apt-get update && sudo apt-get -y upgrade
        sudo apt-get install git-core python-pip python-pycurl
        sudo pip install ansible
        mkdir -p src/github.com/ifosch
        git clone https://github.com/ifosch/eos-setup.git !$
        sudo -s
        echo localhost ansible_connection=local >> /etc/ansible/hosts
        exit

## To make it work:

    cd src/github.com/ifosch/eos-setup
    sudo ansible-playbook setup.yml
