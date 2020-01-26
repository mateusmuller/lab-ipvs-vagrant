Vagrant.configure("2") do |config|
    (1..2).each do |i|
        config.vm.define "web_#{i}" do |web|
            web.vm.box = "centos/7"
            web.vm.network "public_network", bridge: "enp8s0", ip: "192.168.0.12#{i}"
            web.vm.provision "shell", path: "httpd_#{i}.sh"
        end
    end
  
    (1..2).each do |i|
        config.vm.define "lb_ipvsadm_#{i}" do |lb_ipvsadm|
            lb_ipvsadm.vm.box = "centos/7"
            lb_ipvsadm.vm.network "public_network", bridge: "enp8s0", ip: "192.168.0.12#{i+2}"
            lb_ipvsadm.vm.provision "shell", path: "lb_ipvsadm.sh"
        end
    end
end