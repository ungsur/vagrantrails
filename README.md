# vagrantrails
This is a Vagrant Box that starts a Centos 7 image and installs ruby 2.2.2 and rails 5.0.1
Dependencies include:

vagrant 
virtualbox

vagrant plugin install vagrant-vbguest
vagrant plugin install vagrant-librarian-chef-nochef
vagrant plugin install vagrant-chef-zero
vagrant plugin install vagrant-berkshelf
vagrant plugin install vagrant-omnibus
vagrant plugin install vagrant-rsync-back
vagrant plugin install vagrant-share


This creates a vagrant machine which syncs /vagrant on the guest machine to src/ on the host machine. 

After the dependencies are installed, clone the repo, then run vagrant up from the repo directory.
Once the machine is up, run vagrant rsync-auto to automatically rsync from the repo/src directory to /vagrant on the guest box.

To rsync from the guest /vagrant directory to the repo/src directory, run vagrant rsync-back


