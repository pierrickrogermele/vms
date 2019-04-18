# vi: ft=ruby sw=0 ts=2 et fdm=marker

# Main {{{1
################################################################

Vagrant.configure(2) do |config|
  
  # averell {{{2
  ################################################################
  
  config.vm.define "averell" do |averell|
    averell.vm.box = "generic/freebsd12"
    averell.vm.hostname = "averell"
    averell.vm.provider :virtualbox do |vb|
      vb.name = 'averell'
    end
    averell.vm.provision "Install Python.", type: "shell", privileged: true, inline: "pkg install -y python" # Needed by Ansible
    averell.vm.provision :ansible do |ansible|
      ansible.extra_vars = {
        ansible_python_interpreter: "python3"
      }
      ansible.playbook = "provisioning/playbook.yml"
    end
  end
  
  # rantanplan {{{2
  ################################################################
  
  config.vm.define "rantanplan" do |rantanplan|
    rantanplan.vm.box = "ubuntu/trusty64"
  end
  
end
