# OpenStack Installation
We are using CentOS Linux release 8.3.2011 on this Lab.

```bash
$ sudo cat /etc/centos-release
$ CentOS Linux release 8.3.2011
```

Configure selinux to Permissive mode:

```bash
$ sudo sed -i 's/^SELINUX=.*/SELINUX=permissive/g' /etc/selinux/config
$ sudo setenforce 0
```

Reboot to take effect
```bash
$ sudo reboot
```

Prerequisites:
```bash
$ sudo dnf install network-scripts -y
$ sudo systemctl disable firewalld
$ sudo systemctl stop firewalld
$ sudo systemctl disable NetworkManager
$ sudo systemctl stop NetworkManager
$ sudo systemctl enable network
$ sudo systemctl start network
```

Add the OpenStack Ussuri release repository:
```bash
$ sudo dnf update -y
$ sudo dnf config-manager --enable powertools
$ sudo dnf install -y centos-release-openstack-ussuri
```

If you want to check available Openstack release, use below command:
```bash
$ sudo dnf search centos-release-openstack
```

Update system:
```bash
$ sudo dnf update -y
```

Install packstack package and generate answer file (for Configuration):
```bash
$ sudo dnf install -y openstack-packstack
$ sudo packstack --gen-answer-file=packstack-answer.txt
```

Edit packstack-answer file:
[packstack-answer](https://github.com/luthfanfauzi/Openstack_Lab/blob/main/packstack-answer.txt)

Install Openstack with Packstack:
```bash
$ sudo packstack --answer-file=packstack-answer.txt | tee packstack.log
```
