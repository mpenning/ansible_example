## Overview

These examples were built using ansible version 2.9.2.

## Managing Cisco IOS in a playbook

- To run `cisco-playbook.yaml` with the `ios_command` module and ask for passwords before connecting:

```python
# iterate over hosts in inventory.ini and save 'show runn' as a file for each
ansible-playbook -i inventory.ini -k -K cisco-playbook.yaml
```

## Managing Linux in a playbook

- To run `linux-playbook.yaml` and ask for passwords before connecting:
  - This `linux-playbook` runs a command using the `command` module
  - This `linux-playbook` runs another command using the `shell` module

```python
# This goes through localhost and saves 'sudo ls -la' as a file
ansible-playbook -i inventory.ini -k -K linux-playbook.yaml
```

## Using ansible directly from the command-line (without a playbook)

- To run a `ping` from a switch with the `raw` module
  - `-k -K` asks for passwords before connecting
  - `-v` outputs command ouput to the screen
  - `-m` specifies the module to be used
  - The `raw` module is not the only way to run ansible commands without a playbook

```python
ansible sw3 -v -i inventory.ini -k -K -m raw -a "ping 4.2.2.2"
```

