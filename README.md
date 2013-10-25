ansible_cloudstack_rpmbuild
===========================

Ansible playbook for configuring a host to build CloudStack RPMs

Rationale
=========
I typically do a number of tests when Apache CloudStack gets close to release, and one of those is ensuring
that RPMs can be built. (there is a CI job that does this as well). I could build these on a my local machine, but 
there is all manner of cruft and potential assumptions that a non-CloudStack developer might not have so I bring up a 
fresh CentOS VM. I have historically run puppet to get all of the prereqs, but that involves me either having puppet 
preinstalled/configured or installing it manually - plus I wanted to learn about Ansible, so this allows me to have 
a bare VM and still get my deployment ready in a timely manner. Hopefully others will find it helpful. 
