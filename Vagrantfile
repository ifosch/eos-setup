# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.define 'debian' do |debian|
    debian.vm.box = 'natx/debian-stretch-amd64-desktop'
    debian.vm.provider 'virtualbox' do |vb|
      # Display the VirtualBox GUI when booting the machine
      vb.gui = true

      # Customize the amount of memory on the VM:
      vb.memory = '4096'
      vb.customize ["modifyvm", :id, "--vram", "32"]
    end
    debian.vm.provision 'shell', inline: <<-SHELL
      which sudo || \
          su - -c apt-get install sudo gksu && \
          sudo adduser vagrant sudo
      test -f /tmp/updated || \
          sudo apt-get update && \
          sudo DEBIAN_FRONTEND=noninteractive apt-get -y upgrade && \
          touch /tmp/updated
      git version &> /dev/null || \
          sudo DEBIAN_FRONTEND=noninteractive apt-get -y install \
          git-core \
          python-pip \
          libcurl4-openssl-dev \
          python-dev
      ansible --version &> /dev/null || \
          sudo pip install \
          ansible \
          pycurl \
          pyYAML \
          argcomplete
      sudo mkdir -p /etc/ansible &> /dev/null
      sudo bash -c '
        echo localhost ansible_connection=local > /etc/ansible/hosts
      '
      cd /vagrant
      sudo ansible-playbook setup.yml --extra-vars "user=vagrant"
    SHELL
  end

  config.vm.define 'debian-testing' do |debian|
    debian.vm.box = 'natx/debian-testing-amd64-desktop'
    debian.vm.provider 'virtualbox' do |vb|
      # Display the VirtualBox GUI when booting the machine
      vb.gui = true

      # Customize the amount of memory on the VM:
      vb.memory = '4096'
      vb.customize ["modifyvm", :id, "--vram", "32"]
    end
    debian.vm.provision 'shell', inline: <<-SHELL
      which sudo || \
          su - -c apt-get install sudo gksu && \
          sudo adduser vagrant sudo
      test -f /tmp/updated || \
          sudo apt-get update && \
          sudo DEBIAN_FRONTEND=noninteractive apt-get -y upgrade && \
          touch /tmp/updated
      git version &> /dev/null || \
          sudo DEBIAN_FRONTEND=noninteractive apt-get -y install \
          git-core \
          python-pip \
          libcurl4-openssl-dev \
          python-dev
      ansible --version &> /dev/null || \
          sudo pip install \
          ansible \
          pycurl \
          pyYAML \
          argcomplete
      sudo mkdir -p /etc/ansible &> /dev/null
      sudo bash -c '
        echo localhost ansible_connection=local > /etc/ansible/hosts
      '
      cd /vagrant
      sudo ansible-playbook setup.yml --extra-vars "user=vagrant"
    SHELL
  end

end
