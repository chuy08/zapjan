Vagrant.configure(2) do |config|
  config.vm.provider :virtualbox do |v|
    v.name = "veronica_#{Time.now.strftime('%Y%m%d%H%M%S')}"
  end

  config.vm.box = 'bento/ubuntu-16.04'
  config.vm.box_check_update = true

  config.vm.hostname = 'veronica'
  config.vm.network "forwarded_port", guest: 80, host: 8080

  config.vm.define "veronica" do |dev|
  end

  config.vm.provision :shell, inline: <<-SHELL
    apt-get update
    apt-get -y install apache2

  SHELL

  config.vm.synced_folder 'html', '/var/www/html' 

  #config.vm.provision :salt do |salt|
  #  salt.minion_config = 'minion'
  #  salt.run_highstate = true
  #  salt.verbose = true
  #  salt.bootstrap_options = '-F -P -c /tmp' # Vagrant issue #6029 and #5973
  #end
end
