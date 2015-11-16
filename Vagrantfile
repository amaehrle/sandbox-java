# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = 'ubuntu/trusty64'

  config.vm.synced_folder './workspace', '/home/vagrant/workspace'

  config.vm.provider "virtualbox" do |vb|
    # vb.gui = true
    vb.memory = '2048'
    vb.cpus = '2'
#    vb.vram = '128'
#    vb.audio = 'coreaudio'
#    vb.audiocontroller = 'ac97'
#    vb.clipboard =  'bidirectional'
  end

  # config.vm.provision "shell", inline: <<-SHELL
  #   sudo apt-get update
  # SHELL

  config.librarian_chef.cheffile_dir = "chef"

  config.vm.provision 'chef_solo' do |chef|
    # chef.log_level = :debug
    chef.cookbooks_path = ['chef/cookbooks', 'chef/site-cookbooks']
    chef.run_list = [
      'recipe[apt]',
      'recipe[preinstall]',
      'recipe[git]'
    ]

#     chef.run_list = [
# #      'recipe[sandbox::rvm]',
# #      'recipe[sandbox::heroku]',
# #      'recipe[sandbox::packages]',
# #      'recipe[sandbox::wkhtmltopdf]',
#       'recipe[sandbox::java]'
# #      'recipe[rvm::user]'
#     ]
  end
end
