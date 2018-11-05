rbenv
=========

This role installs and configures [rbenv](https://github.com/rbenv/rbenv).

Requirements
------------

No special requirements; note that this role requires root access, so either run it in a playbook with a global `become: yes`, or invoke the role in your playbook like:

    - hosts: app_server
      roles:
        - role: bithium.rbenv
          become: yes

Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml` and `vars/main.yml`):

 * Packages to install for each OS: `rbenv_packages`:

        rbenv_packages:
          - git

 * Repository to download sources from:

        rbenv_repo: "https://github.com/rbenv/rbenv"

 * Installation path: `rbenv_root: "/opt/rbenv"`

 * Installation version: `rbenv_version: master`

 * Plugins to install:

        rbenv_plugins:
          - rbenv_plugin/ruby-build
          - rbenv_plugin/rbenv-vars

Where each entry is the variable name that contains the configuration for installing the plugin.

 * ruby-build plugin install configuration:

```yaml
rbenv_plugin/ruby_build:
  name: ruby-build
  repo: https://github.com/rbenv/ruby-build.git
  version: master
  packages:
    Debian:
      - build-essential
      - curl
      - git
      - libcurl4-openssl-dev
      - libffi-dev
      - libreadline-dev
      - libssl-dev
      - libxml2-dev
      - libxslt1-dev
      - zlib1g-dev
```

 * rbenv-vars plugin install configuration:

```yaml
rbenv_plugin/rbenv-vars:
  name: rbenv-vars
  repo: https://github.com/rbenv/rbenv-vars.git
  version: master
```

Dependencies
------------

No dependencies.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables
passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: rbenv, x: 42 }

License
-------

Apache 2.0

Author Information
------------------

[Bithium S.A.](https://www.bithium.com/)
