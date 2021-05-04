Vagrant.configure("2") do |config|
  config.vm.box = "k3os.box"
  #config.vm.guest = "linux"
  #config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.hostname = "rke-k3os"

  config.ssh.username = 'rancher'
  config.ssh.password = 'rancher'

  config.vm.provider :vmware_esxi do |esxi|
    esxi.esxi_hostname = 'esxi'
    esxi.esxi_username = 'root'
    esxi.esxi_password = 'file:./esxi_password'
    esxi.esxi_virtual_network = ['VM Network']
    esxi.esxi_disk_store = 'datastore'
    esxi.guest_name = "rke-k3os"
    esxi.guest_memsize = 3072
    esxi.guest_numvcpus = 2
    esxi.guest_boot_disk_size = 30
    esxi.guest_mac_address = [ '00:50:56:aa:d9:aa' ]
    esxi.guest_guestos = 'ubuntu-64'
    esxi.guest_nic_type = 'vmxnet3'
    esxi.debug = 'false'

  end #end of provider

end
