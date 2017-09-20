Mac Development Ansible Playbook (RoR)
=========

This playbook instals local dev environment on macOS.
Playbook is inspired by [geerlingguy.mac-dev-playbook](https://github.com/geerlingguy/mac-dev-playbook).

Requirements and Installation
------------

To run with vagrant use:

```
vagrant up
ansible-playbook -i inventory.ini main.yml
```

To run locally use:
```
ansible-playbook -i local.ini main.yml -c local
```

To provision macOS:

1. `xcode-select --install`
2. Install Ansible
  ```
  sudo easy_install pip
  sudo pip install ansible
  ```
3. ~~Generate ssh key: `cd ~/.ssh && ssh-keygen`~~ *(ansibled)*
4. ~~Configure .gitconfig~~ *(ansibled)*
  ```
  git config --global user.name "bob"
  git config --global user.email "bob@gmail.com"
  ```
5. Configure github: `cat ~/.ssh/id_rsa.pub | pbcopy`
6. Copy playbook
  ```
  git clone git@github.com:tuykin/mac-dev-playbook.git
  ```
7. `ansible-playbook -i inventory.ini main.yml`


Role Variables
--------------

Whole list of settable variables (except the list of for rvm_io.ruby) you can see in `vars.yml`:

```
git_user_name: 'Bob Marley'
git_user_email: 'bob_marley@gmail.com'

projects_path: '~/projects'
project_name: 'my_super_project'
project_path: "{{ projects_path }}/{{ project_name }}"
repo_url: 'git@github.com:kinley/mkdev.git'

rvm_gemset: 'ruby-2.4.1@my-super-project'
```

Dependencies
------------

`rvm_io.ruby` role is required, but I've included it into repo.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

[Anvar Tuykin](linkedin.com/in/anvar-tuykin-2616b866/), 2017 (originally inspired by [geerlingguy.mac-dev-playbook](https://github.com/geerlingguy/mac-dev-playbook))