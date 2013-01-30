These are the steps I took to create this box:

0. Found a great resource on vagrant, chef & librarian:
http://blog.base2.io/2012/05/01/vagrants-and-chefs-and-librarians-oh-my/#.UQlD6Uq6BYg

1. Installed a Vagrant base box (and tested upping it):
``
  $ vagrant box add precise32 http://files.vagrantup.com/precise32.box
  $ vagrant init precise32
  $ vagrant up
``

2. Prepared librarian:
``
  $ librarian-chef init
``

3. Updated the Cheffile to install apt, build-essentials, rvm, git and postgres

4. Updated the Vagrantfile to use Chef (chef_solo) and listed the cookbooks I wanted to use.

5. Installed cookbooks
``
  $ librarian-chef install
``

6. Turned off the VM and launched it again:
``
  $ vagrant halt
  $ vagrant up
``

7. Chef processed the recipes and installed the packages.