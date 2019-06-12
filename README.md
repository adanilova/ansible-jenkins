Ansible Role: Jenkins CI
=====================
Installs Jenkins CI and Docker with pipeline support on RHEL/CentOS servers. Also install the jenkins-cli.jar and plagins for jenkins. No authorization requared, no manual configuration needed.
Add new jobs to: roles/jenkins/files/

Dependencies
---------------
Ansible >= 2.0

Requirements
---------------
  - java-1.8.0-openjdk
  - wget
  - http://vault.centos.org/centos/7.3.1611/extras/x86_64/Packages/container-selinux-2.9-4.el7.noarch.rpm
  - git

Role Variables
---------------
*General variables*
*path:/ansible-jenkins/roles/jenkins/defaults/main.yml*
| Name              | Default Value       | Description          |
|-----------------------|---------------------|----------------------|
| `jenkins_port` | `8085` | Self Explanatory |
|`jenkins_user` |jenkins|Self Explanatory|
|`jenkins_group` |jenkins|Self Explanatory|
|`jenkins_home` |/var/lib/jenkins|Self Explanatory|
|`tomcat_dir` |/var/lib/jenkins/jobs/mytomcat|Self Explanatory|

Example Playbook
---------------
```yaml
- name: "Apply the jenkins role to the jenkins nodes"
  hosts: vagrant
  become: yes
  roles:
    - jenkins
  tags:
    - jenkins
```
Go
---------------
```sh
$ ansible-playbook playbook.yml -i inventories/test/hosts
```
Author Information
---------------
This role was created in 2019 [Anastasia Danilova](https://www.linkedin.com/in/anastasia-danilova-1b7966101/).

Vagrant
---------------
To use Vagrantfile:
* Create new `ssh-key`, name it `vagrant` and put it to `~/.ssh/` directory
```sh
$ ssh-keygen
```

* Add information about `key`, `vagrant user` and `vagrant host` to `~/.ssh/config`
```sh
Host vagrant 192.168.13.13
    HostName 192.168.13.13
    IdentityFile ~/.ssh/vagrant
    User vagrant
```
* Run `vagrant up`
* Go to Jenkins UI: http://192.168.13.13:8085/ and run the build for `mytomcat`
* Test your application: http://192.168.13.13:8085/sample
* Jenkinsfile and Dockerfile a [here](https://github.com/adanilova/tomcat-app)

This role was created in 2019 by [Anastasia Danilova](https://www.linkedin.com/in/anastasia-danilova-1b7966101/)
