# This is the Ansible Configuration of the example Kubernetes Cluster Setup published on https://www.guschlbauer.dev/kubernetes-cluster


The most simple Kubernetes Cluster consists of one Kubernetes-Master, which manages an arbitrary amount of Kubernetes-Nodes (Workers).


**1. Infrastructure Setup**
* Choose your Hardware and Operating System
Since I’m a huge fan of Raspberry Pi’s, in my case I used three Raspberry Pi’s with Raspbian as an operating system (kube-master01, kube-node01 and kube-node02) for my Cluster Setup.
Connect the hosts to the network infrastructure and assign a static IP for easy access.
* Enable SSH with Public-Key-Authentication to provide root SSH access from the Kubernetes Master to your Nodes.
Log into the future Kubernetes-Master Node and create a key-pair using ssh-keygen.
Copy the public key into the /root/.ssh/authorized_keys file of each Kubernetes nodes (master + workers)
* Test the SSH connection from your Kubernetes-Master to each Worker-Node using
ssh root@[IP] -i [private key]

**2. Install Ansible**

Install ansible on Kubernetes-Master executing
`sudo apt-get install -y ansible. `
Check that the installed version is higher than Ansible 2.2 using
`ansible --version`.

**3. Kubernetes Cluster Configuration and Setup**

*  Once the Ansible is installed checkout this repo. 
*  Modify your hosts.
*  Execute `ansible-playbook cluster.yml`

As the last step of the Kubernetes Cluster Setup, the available nodes can be checked using `kubectl get nodes`.

# References & Credits

This example is based on https://github.com/rak8s/rak8s.git