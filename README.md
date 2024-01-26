# kalilinux-on-gcloud-with-gui-and-virtualization

Goal is to install windows on google cloud platform in trial period.


Create ubuntu/debian instance with any machine type and do not boot up. Just stop it after creating instance.


Open gcloud terminal and run below command (Which make image copy of vm with VMX enabled)
```
gcloud compute images create nested-(name of instance)-image \
--source-disk=(name of instance) --source-disk-zone=us-west4-b \
 --licenses="https://www.googleapis.com/compute/v1/projects/vm-options/global/licenses/enable-vmx"
```
 
Now delete the vm and create new one with same configuration

Create new machine again 
Insted of selecting the os select import and select the exporetd image file.


Run below command to check if VMX is enabled or not
```
grep -cw vmx /proc/cpuinfo
```
# Configure kali 
```
sudo -i 
```
```
cd /etc/apt 
```
```
nano sources.list 
```
(delete all the deb files here and paste this)
```
deb http://http.kali.org/kali kali-rolling main contrib non-free non-free-firmware
```
```
apt update
```

(if face any error than do this) 
```

wget http://http.kali.org/kali/pool/main/k/kali-archive-keyring/kali-archive-keyring_2022.1_all.deb
```
```

dpkg -i kali-archive-keyring_2022.1_all.deb
```


# now install gui (am going for kali, you can choose any either ubuntu or any debian)
```
apt upgrade 
```
```
apt install -y kali-linux-default
```
```
apt install kali-desktop-xfce
```
```
reboot
```
```
vncserver 
```
