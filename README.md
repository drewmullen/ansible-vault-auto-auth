Role Name
=========

Installs and configures vault agent for auto auth using an approle. Just set the app and namespace (or dont). Auto Auth is a vault tool that can maintain a token.

Requirements
------------

- systemd based linux
- approle enabled and defined (assign the name value to `app`))

Role Variables
--------------

### vault_agent_start:

- Default: true

### agent_remove_secret:

- Set to false if you want the secret_id to remain on the machine
- Default: true

### role_id_dir:

- Default: /tmp

### secret_id_dir:

- Default: /tmp

### token_dir:

- Default: /tmp

### namespace:

- Default: "{{ lookup('env', 'VAULT_NAMESPACE') | default('') }}"

### vault_log_level:

- Default: undefined

Example
-------

---

- hosts: localhost
  connection: local
  become: true
  tasks:
    - import_role:
        name: vault-auto-auth
      vars:
        app: example_approle
        namespace: parent_ns/child_ns


License
-------

MIT

Author Information
------------------

Drew Mullen
mullen.drew@gmail.com
www.drewbuntu.com

