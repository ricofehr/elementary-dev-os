
Vagrant.configure("2") do |config|
    # always use vagrant insecure key
    config.ssh.insert_key = false
    # forward ssh agent
    config.ssh.forward_agent = true

    check_guest_additions = false
    functional_vboxsf = false

    config.vm.box = "elementary-dev"

    config.vm.define :dev, primary: true do |machine|
      machine.vm.hostname = "devstation"
      machine.vm.provider "virtualbox" do |v|
          v.name = "devstation"
          v.memory = 4096
          v.cpus = 2
          v.gui = true
      end
    end

    config.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/elementary-dev.yml"
      ansible.verbose = true

      ansible.extra_vars = {
        ansible_os_family: 'Debian',
        ansible_distribution: 'Ubuntu',
        ansible_distribution_release: 'bionic',
        ansible_pkg_mgr: 'apt',
        keyboard_layout: 'fr'
      }
    end
end
