cntlm
=========

<img src="https://docs.ansible.com/ansible-tower/3.2.4/html_ja/installandreference/_static/images/logo_invert.png" width="10%" height="10%" alt="Ansible logo" align="right"/>
<a href="https://travis-ci.org/robertdebock/ansible-role-cntlm"><img src="https://travis-ci.org/robertdebock/ansible-role-cntlm.svg?branch=master" alt="Build status" align="left"/></a>

Install and configure cntlm on your system.

<img src="https://img.shields.io/ansible/role/d/25457"/>
<img src="https://img.shields.io/ansible/quality/25457"/>

Example Playbook
----------------

This example is taken from `molecule/resources/playbook.yml`:
```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - robertdebock.cntlm
```

The machine you are running this on, may need to be prepared.
```yaml
---
- name: Prepare
  hosts: all
  become: yes
  gather_facts: no

  roles:
    - robertdebock.bootstrap
    - robertdebock.buildtools
```

Also see a [full explanation and example](https://robertdebock.nl/how-to-use-these-roles.html) on how to use these roles.

Role Variables
--------------

These variables are set in `defaults/main.yml`:
```yaml
---
# defaults file for cntlm

# The version of CNTLM to install.
cntlm_version: 0.92.3

# What release to install.
cntlm_release: 1

# Where to download CNTLM from.
cntlm_download_mirror: netcologne.dl.sourceforge.net

# CNTLM authenticate to the proxy, set a username, password and domain.
cntlm_username: changeme
cntlm_password: changeme
cntlm_domain: example.com
cntlm_proxy: changeme.example.com:3128

# To what port should CNTLM listen?
cntlm_listen: 3128

# When you've got a password hash, you may fill it in here.
cntlm_passntlmv2: 1234567890abcdef

# What hosts to omit in the proxy.
cntlm_noproxy: localhost
```

Requirements
------------

- Access to a repository containing packages, likely on the internet.
- A recent version of Ansible. (Tests run on the current, previous and next release of Ansible.)

The following roles can be installed to ensure all requirements are met, using `ansible-galaxy install -r requirements.yml`:

```yaml
---
- robertdebock.bootstrap
- robertdebock.buildtools
- robertdebock.service

```

This role uses the following modules:
```yaml
---
- apt
- command
- copy
- dnf
- get_url
- import_role
- package
- service
- shell
- systemd
- template
- unarchive
- yum
```

Context
-------

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/cntlm.png "Dependency")


Compatibility
-------------

This role has been tested on these [container images](https://hub.docker.com/):

|container|tag|allow_failures|
|---------|---|--------------|
|alpine|latest|no|
|alpine|edge|yes|
|debian|stable|yes|
|debian|unstable|yes|
|debian|latest|no|
|centos|7|no|
|centos|latest|no|
|fedora|latest|no|
|fedora|rawhide|yes|
|ubuntu|rolling|yes|
|ubuntu|devel|yes|
|ubuntu|latest|no|

This role has been tested on these Ansible versions:

- ansible~=2.7
- ansible~=2.8
- git+https://github.com/ansible/ansible.git@devel

The indicator '\~=' means [compatible with](https://www.python.org/dev/peps/pep-0440/#compatible-release). For example 'ansible\~=2.8' would pick the latest ansible-2.8, for example ansible-2.8.6.

Exceptions
----------

Some variarations of the build matrix do not work. These are the variations and reasons why the build won't work:

| variation                 | reason                 |
|---------------------------|------------------------|
| EL | No package matching 'bison' found available, installed or updated |

Included version(s)
-------------------

This role [refers to a version](https://github.com/robertdebock/ansible-role-cntlm/blob/master/defaults/main.yml) released by Mavey on SOURCEFORGE. Check the released version(s) here:
- [cntlm](https://sourceforge.net/projects/cntlm/files/).

This version reference means a role may get outdated. Monthly tests occur to see if [bit-rot](https://en.wikipedia.org/wiki/Software_rot) occured. If you however find a problem, please create an issue, I'll get on it as soon as possible.

Testing
-------

[Unit tests](https://travis-ci.org/robertdebock/ansible-role-cntlm) are done on every commit and periodically.

If you find issues, please register them in [GitHub](https://github.com/robertdebock/ansible-role-cntlm/issues)

To test this role locally please use [Molecule](https://github.com/ansible/molecule):
```
pip install molecule
molecule test
```

To test on Amazon EC2, configure [~/.aws/credentials](https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/credentials.html) and set a region using `export AWS_REGION=eu-central-1` before running `molecule test --scenario-name ec2`.

There are many specific scenarios available, please have a look in the `molecule/` directory.

License
-------

Apache-2.0


Author Information
------------------

[Robert de Bock](https://robertdebock.nl/)
