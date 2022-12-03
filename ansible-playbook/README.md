# Usage

* check playbook syntax

  `ansible-lint site.yml`
* run playbook only for certain group (`osds` in this case)

  `ansible-playbook site.yml -i inventory.yml -l osds`
* run complete playbook for all hosts

  `ansible-playbook site.yml -i inventory.yml`
