lsblk
mount /dev/sr0 /mnt
ls /mnt
rpm -ivh  /mnt/Packages/vsftpd-3.0.2-21.el7.x86_64.rpm
systemctl restart vsftpd 

systemctl enable vsftpd


mkdir  /var/ftp/dvd
vim  /etc/fstab

/dev/sr0                             /var/ftp/dvd              iso9660    defaults        0 0
:wq!


mount /var/ftp/dvd/
df -h
ls /var/ftp/dvd
ftp://192.168.122.1/
cd /etc/yum.repos.d/

ll
vim dvd.repo

[RHEL7]
name=all rhel7 packages
baseurl=ftp://192.168.122.1//dvd/
enable=1
gpgcheck=0
:wq!
yum clean all
cd

yum install qemu-kvm libvirt virt-manager -y

systemctl status libvirtd
virsh list
virsh list --all
virt-manager
