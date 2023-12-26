---
title: "Install Kubernetes on AWS EC2"
excerpt: "Easy tutorial on how to setup Kubernetes on 4 EC2 Instances using kubeadm"
---
I have seen a lot tutorials online on how to install Kubernetes on AWS EC2 and all of them are unessecarilly complicated. Kubernetes is a simple platform with a bad reputation of being difficult to understand because of how many options it gives its users. That's why I have created a small tutorial of how you can install Kubernetes in the simplest way I can think of with the least amount of resources. The only requirements are some basic AWS EC2 knowledge of how to spin up EC2 instances and setup Security Groups.

Provision 4 EC2 Instances with Ubuntu 20.04 and an allow everything security group for simplicity.

Install docker on all EC2 instances with:
```
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```

SSH into all EC2 Instances and setup all the required modules and iptable config for Kubernetes:
```
sudo modprobe br_netfilter

cat <<EOF | sudo tee /etc/modules-load.d/k8s.conf
br_netfilter
EOF

cat <<EOF | sudo tee /etc/sysctl.d/k8s.conf
net.bridge.bridge-nf-call-ip6tables = 1
net.bridge.bridge-nf-call-iptables = 1
EOF
```

Install KubeAdm, Kubelet and Kubectl:
```
sudo curl -fsSLo /usr/share/keyrings/kubernetes-archive-keyring.gpg https://packages.cloud.google.com/apt/doc/apt-key.gpg

echo "deb [signed-by=/usr/share/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list

sudo apt-get update
sudo apt-get install -y kubelet kubeadm kubectl
sudo apt-mark hold kubelet kubeadm kubectl
```

Specify systemd as the cgroup driver in docker, this should be automatic but doesn't for some reason for docker in AWS Ubuntu:
```
sudo sh -c 'echo "{
"exec-opts": ["native.cgroupdriver=systemd"]
}" > /etc/docker/daemon.json'

sudo systemctl daemon-reload
sudo systemctl restart docker
```

Setup your Kubernetes master with KubeAdm init and pod-cidr that canal needs:

```
sudo kubeadm init --pod-network-cidr=10.244.0.0/16
```

Setup the Kubernetes workers with the command in the kubeadm init output.

Setup kubeconfig on the master:
```
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
```

You can copy this kubeconfig on your own machine in `~/.kube/config` to operate the cluster from your local machine.

Install the Kubernetes CNI:
```
curl https://docs.projectcalico.org/manifests/canal.yaml -O
kubectl apply -f canal.yaml
```

We are using canal because it is the most reliable one with AWS Ubuntu in my experience.

Your cluster is ready to be used!