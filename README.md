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
