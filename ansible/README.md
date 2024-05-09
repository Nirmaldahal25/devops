## Running with taskbook
- The taskbook contains roles directory. That directory contains rolenames. The rolenames contains predefined folder names such as tasks, files, handlers which contains a main.yml file.
- In this taskbook, the create_user.yml file has to be executed before the main.yml file.
- Run `ansible-playbook create_user.yml --become --ask-become-pass -u <remote_user> --key-file <ssh_private_key>`. This will create ansible user who will have sudo permissions and it doesn't ask for password prompt.
- Run main.yml with ansible.cfg file, which will run tasks as a ansible remote user.
