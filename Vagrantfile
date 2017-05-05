Vagrant.configure(2) do |config|

  config.vm.box = "thussain/rhel7"

  config.vm.hostname = "rhel7-docker-reedmine"

  config.ssh.pty = true

  config.vm.network :forwarded_port, guest: 3000, host: 12345

  config.vm.provision "shell", inline: <<-SHELL
    wget https://test.docker.com/builds/Linux/x86_64/docker-17.05.0-ce-rc3.tgz
    tar xzvf docker-17.05.0-ce-rc3.tgz
    sudo cp docker/* /usr/bin/
    sudo dockerd &
    sudo sleep 10s
    sudo docker run -d --name some-postgres -e POSTGRES_PASSWORD=secret -e POSTGRES_USER=redmine postgres
    sudo docker run -d -p 3000:3000 --name some-redmine --link some-postgres:postgres redmine
  SHELL
end
