# azcore
AzerothCore installation script.

This guide is based on: [https://www.azerothcore.org/wiki/debian12-install-guide#debian-setup](https://www.azerothcore.org/wiki/debian12-install-guide#debian-setup)

Set your password in the `inventory.yml` file, or uncomment the lines in `server-install.yml` file so you'll be asked every time.

To prevent accidental upload of password, use the command: `git update-index --assume-unchanged inventory.yml` 
This prevents the file from being tracked. After installation is completed, it's still a good idea to remove your password as it's stored in plain text.

```yml
# inventory.yml
ansible_sudo_pass: <password>
```

```yml
# server-install.yml
become: true
become_method: sudo

vars_prompt:
  - name: ansible_become_password
    prompt: Please enter the sudo password
    private: true
```

To install the server including bots, run the command:

```shell 
ansible-playbook azcore/server-install.yml
```
