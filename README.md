# Update CentOS/RHEL

Copyright (C) 2019 Dmitriy Prigoda <deamon.none@gmail.com> 
This script is free software: Everyone is permitted to copy and distribute verbatim copies of 
the GNU General Public License as published by the Free Software Foundation, either version 3
of the License, but changing it is not allowed.

Tested on:
- CentOS 8 
- Ansible = 2.9.5

For group update install CentOS/RHEL using Ansible
--------------------------------------------------
*Project structure: Update-CentOS-RHEL*


This project is hosted at:

  * https://github.com/D34m0nN0n3/ansible-update-os/

For the latest version, to contribute, and for more information, please visit
the project pages.

To clone the current master branch run:

```
git clone https://github.com/D34m0nN0n3/ansible-update-os.git
```
### Run Playbook
To run this playbook, you must:
1. Make sure that there is network access from the management server to the managed nodes on port 22 (ssh). It is described in detail in the documentation: `Connection methods` and` Ansible passing sudo`.
2. There is an account with administrator rights from which the connection will be made.
3. Create an `inventory` file with the appropriate groups and variables defined. *An example inventory can be found in: [inventory/hosts.example](inventory/hosts.example)*

An example run with the password of the user under which we connect to the managed hosts:
```
bash
# Go to the project folder:
> cd ansible-update-os
# Run playbook:
> ansible-playbook -i inventory/hosts playbooks/01-main.yml --ask-pass --become --ask-become-pass
```
#### Keys
Key                 |INFO
--------------------|------------------------------------------------------------------
-i                  |Необходимо указать путь к файлу `inventory`
-v or -vv           |Повышает информативность вывода, нужен для анализа ошибок
--become            |Предоставляет повышение полномочий через `sudo` УЗ при подключение
--ask-pass          |Запрашивает пароль УЗ под которой будет выполнен сценарий
--ask-become-pas    |Запрашивает пароль УЗ при запуске `sudo`

*At startup and at runtime, a log file is generated for error analysis [logs/ansible-log.log](logs/ansible-log.log). File size depends on the verbose level and the number of script runs.*

## Documentations ANSIBLE:
- [Ansible installation guide](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)
- [Ansible Documentations](https://docs.ansible.com/)
- [Ansible Vault](https://docs.ansible.com/ansible/latest/user_guide/vault.html)
- [Connection methods](https://docs.ansible.com/ansible/latest/user_guide/connection_details.html)
- [Ansible passing sudo](https://8gwifi.org/docs/ansible-sudo-ssh-password.jsp)
- [Manages packages with the yum package manager](https://docs.ansible.com/ansible/latest/modules/yum_module.html)
