
boxes = [
    {
        :name => "k8smaster",
        :eth1 => "192.168.8.10",
        :mem => "1536",
        :cpu => "2"
    },
     {
        :name => "k8smode",
        :eth1 => "192.168.8.11",
        :mem => "1536",
        :cpu => "2"
    },
]

Vagrant.configure("2") do |config|

    #config.vm.box = "bento/ubuntu-16.04"
    config.vm.box = "ubuntu/xenial64"
     boxes.each do |opts|
      config.vm.define opts[:name] do |config|
        config.vm.hostname = opts[:name]
        config.vm.provider "virtualbox" do |v|
          v.customize ["modifyvm", :id, "--memory", opts[:mem]]
          v.customize ["modifyvm", :id, "--cpus", opts[:cpu]]
        end
        config.vm.network :private_network, ip: opts[:eth1]
        config.ssh.private_key_path = ["~/.ssh/id_rsa", "~/.vagrant.d/insecure_private_key"]
        config.ssh.insert_key = false
        config.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/authorized_keys"
      end
  end
end

  

#  MASTER
# -----
# sudo swapoff -a
# sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
# curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
# sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
# sudo apt-get update
# sudo apt-get install docker-ce   
# sudo usermod -aG docker $USER
# sudo systemctl enable docker
# logout + relog
# sudo apt-get update && sudo apt-get install -y apt-transport-https
# curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
# En root
# cat <<EOF >/etc/apt/sources.list.d/kubernetes.list
# deb http://apt.kubernetes.io/ kubernetes-xenial main
# EOF

# sudo kubeadm init --apiserver-advertise-address 192.168.8.10 --token 54c315.78a320e33baaf27d
# mkdir -p $HOME/.kube
# sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
# sudo chown $(id -u):$(id -g) $HOME/.kube/config
# sudo  sysctl net.bridge.bridge-nf-call-iptables=1
# export kubever=$(kubectl version | base64 | tr -d '\n')
# kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$kubever"

#  SLAVE
# -----
# sudo swapoff -a
# sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
# curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
# sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
# sudo apt-get update
# sudo apt-get install docker-ce   
# sudo usermod -aG docker $USER
# sudo systemctl enable docker
# -> faire test de pull (besoin potentiel de reboot de la vm à confirmer)
# logout + relog
# sudo apt-get update && sudo apt-get install -y apt-transport-https
# sudo curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
# En root
# cat <<EOF >/etc/apt/sources.list.d/kubernetes.list
# deb http://apt.kubernetes.io/ kubernetes-xenial main
# EOF

# user normal
# sudo apt-get update
# sudo apt-get install -y kubelet kubeadm kubectl
# sudo kubeadm join --token 54c315.78a320e33baaf27d 192.168.8.10:6443 --discovery-token-unsafe-skip-ca-verification

# attention au

# root@k8smaster:~# more /etc/docker/daemon.json

# {

  # "exec-opts": ["native.cgroupdriver=cgroupfs"]

# }

 

 

 

 

# 10.96.0.0/12

# 10.244.0.0/16

 

# printf -v no_proxy1 '%s,' 10.244.{1..255}.{1..255};

# printf -v no_proxy2 '%s,' 10.96.{1..255}.{1..255};

# export NO_PROXY=localhost,127.0.0.1,192.168.8.10,${no_proxy1}

 

 

 

# --cgroup-driver=system

 

# kubelet cgroup driver: "cgroupfs" is different from docker cgroup driver: "systemd"

 

# [native.cgroupdriver=systemd])