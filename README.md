andrewrothstein.git
=========
[![Build Status](https://travis-ci.org/andrewrothstein/ansible-git.svg?branch=master)](https://travis-ci.org/andrewrothstein/ansible-git)

Installs and configures git.
On Linux it installs a global configuration /etc/gitconfig
On OSX it installs ~/.gitconfig

Requirements
------------

See [meta/main.yml](meta/main.yml)

Role Variables
--------------

> Note: 
> * If git_installer is toggled from Homebrew (brew) to either source, which builds program from released package, or Package Manager (pkg), please make sure the executable is re-linked if you want to leverage the Homebrew version: `brew unlink git && brew link git`
> * If `git_installer == 'source'` developers should install the following ansible role: [andrewrothstein.git_build](https://github.com/andrewrothstein/ansible-git_build)

See [defaults/main.yml](defaults/main.yml). With v3.0.0+ of the role
each mapping needs to have a UID associated with it.

Dependencies
------------

See [meta/main.yml](meta/main.yml).

Example Playbook
----------------

Important that each URL mapping rule have a UUID

```yml
- hosts: servers
  roles:
    - role: andrewrothstein.git
	  git_config_protocol_map:
	    - uid: '93f2b82088e744739a4cfb8a3df68925'
		  url: 'ssh://git@github.com'
		  insteadOf : 'git://github.com'
		- uid: '5446806d328f42dc8be2e6d1e6139aa8'
		  url: 'https://'
		  insteadOf : 'git://'
```

License
-------

MIT

Author Information
------------------

Andrew Rothstein <andrew.rothstein@gmail.com>
