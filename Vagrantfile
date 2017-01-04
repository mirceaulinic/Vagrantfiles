# -*- mode: ruby -*-
# vi: set ft=ruby :

VEOS_BOX = "vEOS-lab-4.15.5M-virtualbox"
IOSXR_BOX = "IOS-XRv-6.2.1-virtualbox"
JUNOS_BOX = "juniper/ffp-12.1X47-D20.7-packetmode"

Vagrant.configure(2) do |config|

  config.vm.define "base" do |base|
    base.vm.box = "hashicorp/precise64"
    base.vm.network :forwarded_port, guest: 22, host: 12200, id: 'ssh'
    base.vm.network "private_network", virtualbox__intnet: "link_1",
                                       ip: "10.0.1.100"
    base.vm.network "private_network", virtualbox__intnet: "link_2",
                                       ip: "10.0.2.100"
    base.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install lldpd -y
    SHELL
  end

  config.vm.define "eos" do |eos|
    eos.vm.box = VEOS_BOX

    eos.vm.network :forwarded_port, guest: 22, host: 12201, id: 'ssh'
    eos.vm.network :forwarded_port, guest: 443, host: 12443, id: 'https'

    eos.vm.network "private_network", virtualbox__intnet: "link_1", ip: "169.254.1.11", auto_config: false
    eos.vm.network "private_network", virtualbox__intnet: "link_2", ip: "169.254.1.11", auto_config: false
  end

  config.vm.define "vsrx" do |vsrx|
    vsrx.vm.box = JUNOS_BOX

    vsrx.vm.network :forwarded_port, guest: 22, host: 12202, id: 'ssh'
    vsrx.vm.network :forwarded_port, guest: 830, host: 12830, id: 'netconf'
    vsrx.vm.network :forwarded_port, guest: 80, host: 12280, id: 'http'

    vsrx.vm.network "private_network", virtualbox__intnet: "link_1",
                                        ip: "169.254.1.11", auto_config: false
    vsrx.vm.network "private_network", virtualbox__intnet: "link_2",
                                        ip: "169.254.1.11", auto_config: false
    vsrx.vm.network "private_network", virtualbox__intnet: "link_3",
                                        ip: "169.254.1.11", auto_config: false
    vsrx.vm.network "private_network", virtualbox__intnet: "link_4",
                                        ip: "169.254.1.11", auto_config: false
  end

  config.vm.define "vsrx2" do |vsrx|
    vsrx.vm.box = JUNOS_BOX

    vsrx.vm.network :forwarded_port, guest: 22, host: 12203, id: 'ssh'
    vsrx.vm.network :forwarded_port, guest: 80, host: 12281, id: 'http'

    vsrx.vm.network "private_network", virtualbox__intnet: "link_1",
                                        ip: "169.254.1.11", auto_config: false
    vsrx.vm.network "private_network", virtualbox__intnet: "link_2",
                                        ip: "169.254.1.11", auto_config: false
    vsrx.vm.network "private_network", virtualbox__intnet: "link_3",
                                        ip: "169.254.1.11", auto_config: false
    vsrx.vm.network "private_network", virtualbox__intnet: "link_4",
                                        ip: "169.254.1.11", auto_config: false
  end

  config.vm.define "gcre" do |gcre|
    gcre.vm.box = "google/gce"

    gcre.vm.network :forwarded_port, guest: 22, host: 12204, id: 'ssh'

    gcre.vm.network "private_network", virtualbox__intnet: "link_1",
                                        ip: "169.254.1.11", auto_config: false
    gcre.vm.network "private_network", virtualbox__intnet: "link_2",
                                        ip: "169.254.1.11", auto_config: false
  end

 config.vm.define "iosxr" do |iosxr|
    iosxr.vm.box = IOSXR_BOX

    iosxr.vm.network :forwarded_port, guest: 22, host: 12205, id: 'ssh'
    iosxr.vm.network :forwarded_port, guest: 57400, host: 12257, id: 'grpc'
    iosxr.vm.network :forwarded_port, guest: 38751, host: 12251, id: 'xml'
    iosxr.vm.network :forwarded_port, guest: 38752, host: 12252, id: 'ssl'

    iosxr.vm.network "private_network", virtualbox__intnet: "link_1",
                                    ip: "169.254.1.11", auto_config: false
    iosxr.vm.network "private_network", virtualbox__intnet: "link_2",
                                    ip: "169.254.1.11", auto_config: false
    iosxr.vm.network "private_network", virtualbox__intnet: "link_3",
                                    ip: "169.254.1.11", auto_config: false
    iosxr.vm.network "private_network", virtualbox__intnet: "link_4",
                                        ip: "169.254.1.11", auto_config: false
  end

end
