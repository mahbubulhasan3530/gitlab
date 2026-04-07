```
sudo vim /etc/docker/daemon.json 
{
    "insecure-registries": ["192.168.168.168","my-home.com"],
    "dns": ["8.8.8.8","8.8.4.4","1.1.1.1"],
    "storage-drive": "overlay2"
}
```