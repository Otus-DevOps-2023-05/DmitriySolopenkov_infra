# DmitriySolopenkov_infra
DmitriySolopenkov Infra repository

## Bastion homework

```bash
ssh -J appuser@158.160.106.57 appuser@10.128.0.9
```

```bash
vim ~/.ssh/config
```

```bash
Host bastion
    HostName 158.160.106.57
    User appuser
    IdentityFile ~/.ssh/appuser

Host someinternalhost
    ProxyJump appuser@158.160.106.57
    HostName 10.128.0.9
    User appuser
    IdentityFile ~/.ssh/appuser
```

```bash
vim ~/.bashrc
```

```bash
alias someinternalhost='ssh someinternalhost'
```


bastion_IP = 158.160.106.57
someinternalhost_IP = 10.128.0.9

testapp_IP = 158.160.123.103
testapp_port = 9292

```bash
yc compute instance create \
 --name reddit-app \
 --hostname reddit-app \
 --memory=4 \
 --create-boot-disk image-folder-id=standard-images,image-family=ubuntu-1604-lts,size=10GB \
 --network-interface subnet-name=default-ru-central1-a,nat-ip-version=ipv4 \
 --metadata serial-port-enable=1 \
 --metadata-from-file user-data=cloud-init.conf

```
