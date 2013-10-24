# Local virtual environments

## Vagrant

We are using vagrant for building up local VMs on top of Virtual Box. It's useful
for testing.

For more information on using vangrant refer to the home page, has really good
documentation [http://vagrantup.com](http://vagrantup.com).

### Vagrant Omnibus to update the version of chef.

Vagrant comes with a relatively old version of chef by default and will most
probably cause problems with the cookbooks you want to run. Vagrant Omnibus helps
solve this: https://github.com/schisamo/vagrant-omnibus

````vagrant plugin install vagrant-omnibus````

Usage on the context of our project:

- You'll need to install [Virtual Box](https://www.virtualbox.org/)

To run the vms go to the folder where the Vagrant file is located
(dev_ops/dev_vms) and run:

Important: If this is the first time you instantiate the VM it will take time since
the box image template used by vagrant for create the new VM is not in you local
vangrant installation, so this time it will download it and install the generic
box on your machine, next time you want to use that box is going to be available
and won't consume extra time.

````vagrant up````

This will run the boxes configured in the vagrant file (please refer to the file for
details of which ports are binded and the configuration of those vms)


That's it, after running that you should have running VMs as specified in the
vagrant file, provisioned with the tools specified in the vagrant file
(under the chef solo section)

## Chef (chef-solo)

We are using chef-solo for installing and bootstraping the VMs after starting them.
Luckily vagrant has a built in integration with chef-solo.
For more details refer to
[http://docs.opscode.com/chef_solo.html](http://docs.opscode.com/chef_solo.html).

## Chef cookbooks on this directory

For managing the chef cookbooks on this directory we are using librarian.
Please refer to the docs in the "doc" folder of this project.