
workers = {
  "k3osn5" => [k3os.box, 2, 3072, 30, "192.168.2.125", "192.168.60.125", "00:50:56:aa:d9:aa", "00:50:56:aa:d9:a1" ],
  "k3osn6" => [k3os.box, 2, 3072, 30, "192.168.2.126", "192.168.60.126", "00:50:56:aa:d9:bb", "00:50:56:aa:d9:b1" ],
}


Vagrant.configure("2") do |config|

  # building worker nodes
  workers.each do | (name, cfg) |
    box, numvcpus, memory, storage, nodeip1, nodeip2, macaddr1, macaddr2 = cfg

    config.vm.define name do |machine|
      machine.vm.box = box
      machine.vm.hostname = name

      machine.vm.provider :vmware_esxi do |esxi|
        esxi.esxi_hostname = 'esxi'
        esxi.esxi_username = 'root'
        esxi.esxi_password = 'file:./esxi_password'
        esxi.esxi_virtual_network = ['VM Network', 'internal-60']
        esxi.esxi_disk_store = 'datastore'
        esxi.guest_memsize = memory
        esxi.guest_numvcpus = numvcpus
        esxi.guest_boot_disk_size = storage
        esxi.guest_mac_address = [ macaddr1, macaddr2 ]
        esxi.guest_guestos = 'centos-64'
        esxi.guest_nic_type = 'vmxnet3'
        esxi.debug = 'false'
        
      end #end of provider
    end #end of machine
  end #end of each loop

end #end of vagrant
