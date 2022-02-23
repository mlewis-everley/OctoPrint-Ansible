OctoPrint-Ansible
=================

Ansible playbooks to install OctoPrint on a Raspberry Pi. These playbooks assume you have
python 3 installed, and it's aliased to `python3`.

Installation
------------

The recommended way to install ansible is via a [virtualenv](https://virtualenv.pypa.io/en/latest/installation.html#):

    cd /path/to/OctoPrint-Ansible
    virtualenv -p python3 .
    ./bin/pip install -r requirements

**NOTE:** These docs require **virtualenv** to be installed via pipx on your host machine. To do this,
run: `pipx install virtualenv`

Create User
-----------
This is an optional step if you want to create a new user and not use the 
built in **pi** user

```bash
$ ./bin/ansible-playbook create_user.yml -i "<RPi IP Address>," --user pi --ask-pass --ask-su-pass
```

Note, once you create the custom user, the `ansible-playbook` commands can be 
simplified by exclusing the `--user`, `--ask-pass` and `--ask-su-pass` options 
can be removed if your username matches the username you are executing from 
match and your public key added to the authorized keys list

Setup static ip
---------------
This is an optional step if you prefer to have a static IP address

```bash
$  ./bin/ansible-playbook setup_static_ip.yml -i "<RPi IP Address>," --user <username> --ask-pass --ask-su-pass
```

Install OctoPrint
-----------------
Run the following command and follow the initial prompts.
```bash
$  ./bin/ansible-playbook install_octoprint.yml -i "<RPi IP Address>," --user <username> --ask-pass --ask-su-pass
```

**NOTE:** You must add at least one `,` to the list of hosts, even if only using a single IP 