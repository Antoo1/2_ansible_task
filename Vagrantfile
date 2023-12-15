MACHINES = {
  # VM name "kernel update"
  :"nginx" => {
              # VM box
              :box_name => "ubuntu/focal64",
              # IP addr
              :ip_addr => '192.168.56.150',
              # VM CPU count
              :cpus => 1,
              # VM RAM size (Mb)
              :memory => 200,
            }
}

Vagrant.configure("2") do |config|
  MACHINES.each do |boxname, boxconfig|
    # Disable shared folders
    config.vm.synced_folder ".", "/vagrant", disabled: true
    # Apply VM config
    config.vm.define boxname do |box|
      # Set VM base box and hostname
      box.vm.box = boxconfig[:box_name]
      box.vm.host_name = boxname.to_s

      box.vm.network "private_network", ip: boxconfig[:ip_addr]
      
      # VM resources config
      box.vm.provider "virtualbox" do |v|
        # Set VM RAM size and CPU count
        v.memory = boxconfig[:memory]
        v.cpus = boxconfig[:cpus]
      end
    end
  end
end
