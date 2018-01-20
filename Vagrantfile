# Defaults for config options defined in CONFIG
$num_instances = 3
$instance_name_prefix = "docker"
$vm_gui = false
$vm_memory = 512
$vm_cpus = 1
$ip_prefix = "172.17.0."
$forwarded_ports = {}

Vagrant.configure("2") do |config|
  config.ssh.insert_key = false
  config.vm.box = "centos/7"
  if defined? VagrantPlugins::HostManager
    config.hostmanager.enabled = true
    config.hostmanager.manage_host = true
    config.hostmanager.manage_guest = true
    config.hostmanager.ignore_private_ip = false
    config.hostmanager.include_offline = false
  end
  (1..$num_instances).each do |i|
    config.vm.define vm_name = "%s-%02d" % [$instance_name_prefix, i] do |config|
      config.vm.hostname = vm_name

      $forwarded_ports.each do |guest, host|
        config.vm.network "forwarded_port", guest: guest, host: host, auto_correct: true
      end

      config.vm.provider :virtualbox do |vb|
        vb.gui = $vm_gui
        vb.memory = $vm_memory
        vb.cpus = $vm_cpus
      end

      ip = $ip_prefix + "#{i+10}"
 
      config.vm.network :private_network, ip: ip
      config.vm.provision "shell", path: "install_docker.sh"
      instances = $num_instances.to_s
    end
  end
end
