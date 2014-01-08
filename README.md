ansible_cloudstack_rpmbuild
===========================

Ansible playbooks for configuring a host to build CloudStack RPMs or Debs. 

Rationale
=========
I typically do a number of tests when Apache CloudStack gets close to release, and one of those is ensuring
that RPMs can be built. (there is a CI job that does this as well). I could build these on a my local machine, but 
there is all manner of cruft and potential assumptions on my local machines that a non-CloudStack developer might 
not have so I bring up a fresh CentOS VM. I have historically run puppet to get all of the prereqs, but that 
involves me either having puppet preinstalled/configured or installing it manually - plus I wanted to learn about 
Ansible, so this allows me to have a bare VM and still get my deployment ready in a timely manner. Hopefully others 
will find it helpful. 

Usage
======


Defining hosts
---------------
I typically define my hosts and set some variables in /etc/ansible/hosts 

  [rpmbuilders]
  foo-23-21-16-253.compute-1.davidcloudstack.com
  [rpmbuilders:vars]
  ansible_ssh_private_key_file=~/.ssh/david.pem
  [debbuilders]
  foo-54-237-56-170.compute-1.davidcloudstack.com
  [debbuilders:vars]
  ansible_ssh_private_key_file=~/.ssh/david.pem

The [rpmbuilders] and [debbuilders] sections define the hosts to be used. The :vars section merely sets the ssh key to use. 

Putting ansible to work
------------------------

After the config file is set up, merely execute ansible-playbook ./rpmbuilder.yml or ansible-playbook ./debbuilder.yml

Keep in mind package generation can frequently take some time. It's not uncommon for 45 minutes to elapse for a full build. 
Be patient, have a pot or two of coffee.
