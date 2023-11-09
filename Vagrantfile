Vagrant.configure("2") do |config|

#-----------------------------------------------------------#
#----------------------ROUTER-------------------------------#
#-----------------------------------------------------------#

    config.vm.define :router do |router|
      router.vm.box = "debian/bookworm64"
      router.vm.hostname = "Router"
      router.vm.synced_folder ".", "/vagrant", disabled: true

# Red Publica.
      router.vm.network :public_network,
       :dev => "br0",
       :mode => "bridge",
       :type => "bridge",
       use_dhcp_assigned_default_route: true

# Red Privada Intra.
      router.vm.network :private_network,
        :libvirt__network_name => "red-intra",
        :libvirt__dhcp_enabled => false,
        :ip => "10.0.0.1",
        :libvirt__forward_mode => "veryisolated"
    end

#-----------------------------------------------------------#
#----------------------WEB----------------------------------#
#-----------------------------------------------------------#

    config.vm.define :web do |web|
      web.vm.box = "debian/bookworm64"
      web.vm.hostname = "Web"
      web.vm.synced_folder ".", "/vagrant", disabled: true

# Red Privada Intra.

      web.vm.network :private_network,
        :libvirt__network_name => "red-intra",
        :libvirt__dhcp_enabled => false,
        :ip => "10.0.0.2",
        :libvirt__forward_mode => "veryisolated"

#Red Datos.

      web.vm.network :private_network,
        :libvirt__network_name => "red-datos",
        :libvirt__dhcp_enabled => false,
        :ip => "10.0.0.5",
        :libvirt__forward_mode => "veryisolated"

    end
#-----------------------------------------------------------#
#----------------------BD-----------------------------------#
#-----------------------------------------------------------#
      config.vm.define :bd do |bd|
       bd.vm.box = "debian/bookworm64"
       bd.vm.hostname = "Web"
       bd.vm.synced_folder ".", "/vagrant", disabled: true

# Red Privada Intra.

      bd.vm.network :private_network,
        :libvirt__network_name => "red-intra",
        :libvirt__dhcp_enabled => false,
        :ip => "10.0.0.3",
        :libvirt__forward_mode => "veryisolated"

#Red Datos. 

      bd.vm.network :private_network,
        :libvirt__network_name => "red-datos",
        :libvirt__dhcp_enabled => false,
        :ip => "10.0.0.6",
        :libvirt__forward_mode => "veryisolated"

    end

# Maquina cliente
config.vm.define :cliente do |cliente|
      cliente.vm.box = "debian/bookworm64"
      cliente.vm.hostname = "cliente"
      cliente.vm.synced_folder ".", "/vagrant", disabled: true
# Agregar una interfaz de red privada
cliente.vm.network :private_network,
      :libvirt__network_name => "red-intra",
      :libvirt__dhcp_enabled => false,
      :ip => "10.0.0.4",
      :libvirt__forward_mode => "veryisolated"

    end

  end

