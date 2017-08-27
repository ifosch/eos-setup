# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.define 'debian' do |debian|
    vbox = VagrantPlugins::ProviderVirtualBox::Driver::Meta.new
    if vbox.version.include?('4.3')
      debian.vm.box = 'natx/debian-testing-amd64-desktop-vb4330'
    else
      debian.vm.box = 'natx/debian-testing-amd64-desktop'
    end
    debian.vm.provider 'virtualbox' do |vb|
      # Display the VirtualBox GUI when booting the machine
      vb.gui = true

      # Customize the amount of memory on the VM:
      vb.memory = '2048'
    end
    debian.vm.provision 'shell', inline: <<-SHELL
      which sudo || su - -c apt-get install sudo gksu \
                 && su - -c adduser vagrant sudo
      test -f /tmp/updated || sudo apt-get update && sudo apt-get -y upgrade \
                           && touch /tmp/updated
      git version > /dev/null || sudo apt-get -y install git-core python-pip \
                                                 libcurl4-openssl-dev \
                                                 python-dev
      ansible --version > /dev/null || sudo pip install ansible pycurl pyYAML \
                                                        argcomplete
      sudo mkdir -p /etc/ansible 2> /dev/null
      sudo bash -c '
        echo localhost ansible_connection=local > /etc/ansible/hosts
      '
      cd /vagrant
      sudo ansible-playbook setup.yml --extra-vars "user=vagrant"
    SHELL
  end

end
