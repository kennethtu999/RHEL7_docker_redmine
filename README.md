# install docker and redmine on RHEL 7
POT

1. run command
```
vagrant up
vagrant provision
```
1. browser open http://127.0.0.1:12345
1. finish

## Non internet connected machine
### save
```
sudo docker pull ubuntu
sudo docker save -o ubuntu_image.docker ubuntu
```

### load  
```
sudo docker load ubuntu_image.docker
```

### ref
https://serverfault.com/questions/701248/downloading-docker-image-for-transfer-to-non-internet-connected-machine
