gitlab-ci-server
===============

This demo isnt done, probably never will be, just holds some ideas and scripts.

A gitlab "Continuous Integration"-ish server.  This vagrant virtualbox app can be used to compare jenkins and gitlab-ci apps.  Infrastructure as software FTW!  Also, this seems to go faster if you throw about 2 GB of RAM into the Vagrantfile.


Try it out!
-----------
*Bring up the virtualmachine and provision the server*

    $ vagrant up

_Point your browser at_

    Jenkins: http://localhost:8080/
    GitLab: http://localhost:8000/
    GitLab-CI: TBD

_Cleaning up_

    $ vagrant destroy

_To manually clean up stray VMs_

    $ VBoxManage list vms
    $ VBoxManage unregistervm flask-app-server –delete

####Requires:
* [Vagrant](http://www.vagrantup.com/) -- `sudo apt-get install vagrant` 1.2.2
* [VirtualBox](https://www.virtualbox.org/wiki/Downloads/) -- `sudo apt-get install virtualbox-4.2`

####Built On:
* [ansible](https://github.com/ansible/ansible/) -- provisioner loaded up first
* [gitlab] (http://gitlab.org/) -- Self hosted Git management software
* [jenkins] (http://jenkins-ci.org/) -- An extendable open source continuous integration server

####TODO:
* Test tingtun/ansible-playbook-gitlab
* run on a different platform to confirm all is working with different dev env.

####Issues:
* ICTO/ansible-jenkins didn't run the first time, might have been timing w/ RAM.
* If GitLab gives you: "502 Bad Gateway":
    * GitLab script is janky and didn't start right:

    $ rm /home/git/gitlab/tmp/sockets/gitlab.socket
    $ /etc/init.d/gitlab stop
    $ /etc/init.d/gitlab start

    * Increase your RAM.

####Notes:
* bootstrap.sh does a one-time install of ansible to get the ball rolling
* GitLab username: admin@local.host
* GitLab password: 5iveL!fe

####My workflow:
* git config --global user.name 'Your Name'
* git config --global user.email your@email
* git pull
* edit some code
* git add <new files>
* git commit -am 'fixed some bugs'
* git push -u origin master

####Thanks to:
* [ansible-playbook-gitlab] (https://github.com/tingtun/ansible-playbook-gitlab)
* [ansible-jenkins](https://github.com/ICTO/ansible-jenkins)


Contributing
------------

1. Fork it.
2. Create a branch (`git checkout -b my_new_feature`)
3. Commit your changes (`git commit -am "Added Cool Thing"`)
4. Push to the branch (`git push origin my_new_feature`)
5. Open a [Pull Request][1]
6. Enjoy a few plumphelmets while you wait cuz I've never done this before.

[1]: http://github.com/ubergarm/gitlab-jenkins-ci-server/pulls

