Vagrant.configure('2') do |config|
  config.vm.box = 'obnox/fedora23-64-lxc'
  config.vm.hostname = 'ansible-role-cockpit-fedora-23'
  config.vm.network "forwarded_port", guest: 80, host: 8080

  config.vm.synced_folder '.', '/vagrant', disabled: true
  config.vm.synced_folder '.', '/vagrant/ansible-role-cockpit'

  config.vm.provision 'shell' do |s|
    s.keep_color = true
    s.path = 'tests/init.sh'
  end
end
