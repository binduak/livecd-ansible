Building Custom CentOS 6.8 LiveCD With Ansible
==============================================

Initial work and step-by-step instructions are available in the blog post: [Building Custom CentOS 6.4 LiveCD With Ansible](http://gr360ry.github.io/blog/2013/11/28/building-custom-centos-6-dot-4-livecd-with-ansible/)

Master branch is being used to build a minimal live cd system, while the desktop branch is being used to build a full desktop live cd.

## Requirements:
1. CentOS 6.X machine or virtual machine.
2. livecd-tools, git, python-argparse, python-jinja2, screen and ansible – all packages available in EPEL repository.

Install EPEL repository if not already installed:

    # yum -y install http://dl.fedoraproject.org/pub/epel/6/i386/epel-release-6-8.noarch.rpm

Install required packages:

    # yum -y install livecd-tools git ansible python-argparse screen python-jinja2

Clone livecd-ansible repository:

    $ git clone https://github.com/kalxas/livecd-ansible.git -b desktop
    
Add your custom ansible roles, modify centos6-desktop.yml and generate the CD:

    $ cd livecd-ansible
    $ ./generate_config.py centos6-desktop.yml
    $ sudo -s
    # livecd-creator -c centos6-desktop.ks --cache=cache -f centos6-desktop

Many thanks to Gregory for his initial work!
