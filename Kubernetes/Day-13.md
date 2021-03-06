<div align="center">
  <h1> How to setup MULTI-NODE K8S CLUSTER on AWS </h1>
</div>

## At master nodes
Give root power to user -
``` 
sudo su - root
``` 
Install docker
``` 
yum install docker -y
``` 
Enable docker
``` 
systemctl enable docker --now
``` 
Configure YUM 
``` 
cat <<EOF | sudo tee /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-\$basearch
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
EOF
``` 
Install kubadm and kubelet
``` 
yum install kubeadm 
yum install kubelet
``` 
Enable kubelet
``` 
systemctl enable --now kubelet
``` 
Pull the image from docker hub
``` 
kubeadm config images pull
``` 
Check driver of docker
``` 
docker info | grep -i cgroup
Cgroup Driver: cgroupfs
``` 
Change the driver from cgroupfs  to  systemd
``` 
cat  /etc/docker/daemon.json
{
   "exec-opts": ["native.cgroupdriver=systemd"]
}
docker info | grep -i cgroup
Cgroup Driver: systemd
``` 
 
Now, restart docker
``` 
systemctl restart docker
``` 
For routing       
``` 
yum install iproute-tc
``` 
Set the bridge routing to 1 using
``` 
echo "1" > /proc/sys/net/bridge/bridge-nf-call-iptables
``` 
As we are using t2-micro of aws which gives 1CPU and 1GB ram...Now, we can initialize master by ignoring CPU and Mem       
``` 
kubeadm init --pod-network-cidr=10.240.0.0/16 --ignore-preflight-errors=NumCPU --ignore-preflight-errors=Mem
``` 
After initializing, it give us some commands that we need to run for making the nodes as worker/slave....
``` 
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
``` 

## At worker nodes
Give root power to user -
``` 
sudo su - root
``` 
Install docker
``` 
yum install docker -y
``` 
Enable docker
``` 
systemctl enable docker --now
``` 
Configure YUM 
``` 
cat <<EOF | sudo tee /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-\$basearch
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
EOF
``` 
Install kubadm and kubelet
``` 
yum install kubeadm 
yum install kubelet
``` 
Enable kubelet
``` 
systemctl enable --now kubelet
``` 
Check driver of docker
``` 
docker info | grep -i cgroup
Cgroup Driver: cgroupfs
``` 
Change the driver from cgroupfs  to  systemd
``` 
cat  /etc/docker/daemon.json
{
   "exec-opts": ["native.cgroupdriver=systemd"]
}
docker info | grep -i cgroup
Cgroup Driver: systemd
``` 
 
Now, restart docker
``` 
systemctl restart docker
``` 
## At Master node
we have to create a token so that worker nodes can join the master node.
``` 
kubeadm token create  --print-join-command
``` 
Now if we run kubectl get nodes , then we will find nodes are not ready....so we need to make overlay connection between master and worker. Now, we use Flannel plugin .
``` 
kubectl apply  -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml
``` 

## At workers nodes
Use the join cmd given by master node so that worker can connect....

## At Master node
Now, run the command and get the nodes....
``` 
kubectl get nodes
``` 
<br>

**Blog link** : https://www.thesocialcomment.com/blog/---MULTI-NODE-K8S-CLUSTER-ON-AWS---?pid=601cd7d4b53e2a647cc8ff30
