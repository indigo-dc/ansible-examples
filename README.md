#Example Ansible Playbooks for Onedata Services


> Playbooks in this repostory use newly developed roles, that for a moment are
> experimental and not intended for production use. Feel free to use playbooks
> for evaluation, development, testing, and report bugs in this repository.

This repository contains example Ansible playbooks showcasing installation of Onedata services:
- (playbook-onezone.yml)[playbook-onezone.yml] installs and configures Onezone instance
- (playbook-oneprovider.yml)[playbook-oneprovider.yml] installs and configures Oneprovider instance
- (playbook-onezone-letsencrypt.yml)[playbook-onezone-letsencrypt.yml] installs, configures Onezone instance and setups proper certificates using letsencrypt
- (playbook-oneprovider-letsencrypt.yml)[playbook-oneprovider-letsencrypt.yml] installs, configures Oneprovider instance and setups proper certificates using letsencrypt

## Dependencies
~~~
ansible 2.2.0 or newer
~~~

## Bootstraping
In order to use playbooks you need to install required ansible roles using ansible-galaxy:
~~~
ansible-galaxy install -r requirements.yml
~~~
or, if you would like to have sources (recomended if you want to customize configuration of Onedata services prior to executing playbooks) of the roles avilable in the directory of this repository execute:
~~~
./bootstrap.sh
~~~

## Using Playbooks
In order to use playbooks you need to either have properly setup Ansible inventory, or use `~/.ssh/config` together with private key autentication. Assuming you are able to login to an example zone machine using a command ~ssh my-zone~ (mind no ports or users, just an alias from `~/.ssh/config`), you can install Onezone on an example *my-zone* machine with command:
~~~
ansible-playbook -i 'my-zone,' playbook-oneprovider.yml
~~~
similarlly you can install provider:
~~~
ansible-playbook -i 'my-prov,' playbook-oneprovider.yml
~~~