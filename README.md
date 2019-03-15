# Gitlab-CE

Gitlab Community Edition installation

## Getting Started

### Installing Ansible

```sh
$ sudo apt-add-repository ppa:ansible/ansible -y -u
$ sudo apt update -y && sudo apt install ansible -y
$ sudo chown -R $USER:$USER /etc/ansible
```

### Prerequisites

* Gitlab dependencies installing in second and third task in first play
    * cURL
    * openSSH server
    * CA-certificates

## Usage

### Hosts

By default Ansible hosts (inventory) file is stored as /etc/ansible/hosts, but you can define any other file in `ansible.cfg` file.

### Running playbook

Make sure that your inventory (hosts file) is defined.
Take note of variables - these also need to be defined.

```yaml
- hosts: host

  roles:
    - { role: syzmekk.gitlab }
```

### Templates

* *gitlab.j2* - a Gitlab config file, based in */etc/gitlab* as *gitlab.rb*. It is being set twice, because of bootstrap run.

## Acknowledgments

- Playbook tested on Ubuntu xenial (16.04)
- `ENVIRONMENT_URL` sets an environment variable to the system, but only for current task (according to [Gitlab documentation](https://about.gitlab.com/install/#ubuntu))
