Vagrant.configure(2) do |config|

  config.vm.box = "thussain/rhel7"

  config.vm.hostname = "rhel7-docker-redmine"

  config.ssh.pty = true

  config.vm.network :forwarded_port, guest: 3000, host: 12345

  config.vm.synced_folder ".", "/vagrant", disabled: false

  config.vm.provision "shell", inline: <<-SHELL
    wget https://test.docker.com/builds/Linux/x86_64/docker-17.05.0-ce-rc3.tgz
    tar xzvf docker-17.05.0-ce-rc3.tgz
    sudo cp docker/* /usr/bin/
    sudo dockerd &
    sudo sleep 10s

    mkdir -p /srv/docker/redmine/postgresql
    mkdir -p /srv/docker/redmine/redmine
    sudo chcon -Rt svirt_sandbox_file_t /srv/docker/redmine/postgresql
    sudo chcon -Rt svirt_sandbox_file_t /srv/docker/redmine/redmine

    sudo docker run -d --name some-postgres -v /srv/docker/redmine/postgresql:/var/lib/postgresql/data  -e POSTGRES_PASSWORD=secret -e POSTGRES_USER=redmine postgres
    sudo docker run -d -p 3000:3000 --name some-redmine  -v /srv/docker/redmine/redmine:/usr/src/redmine/files --link some-postgres:postgres redmine
  SHELL
end
