# install docker and redmine on RHEL 7
technical verification

1. run command
```
vagrant up
vagrant provision
```

2. browser open http://127.0.0.1:12345
3. finish

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
