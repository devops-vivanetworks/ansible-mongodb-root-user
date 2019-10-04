# ansible-mongo-root-user #
Create root users for MongoDB.
This role creates user with root privilege and sets the password using value passed via playbook. If user already exists, it's password will be updated to match the one passed via playbook.

## Requirements ##
- pymongo installed on remote hosts

## Role Variables ##

This variable is not declared neither in defaults or vars, but must be passed externally
- name: login_password
  desc: password for root user

### Defaults ###

- name: login_host
  value: localhost
  desc: Host to login into
- name: login_port
  value: 27017
  desc: Port to login into
- name: login_database
  value: admin
  desc: Database used for authentication
- name: login_user
  value: root
  desc: User used for authentication

### Vars ###

- name: default_database
  value: "admin"
  desc: Default database to create users in if alternative value not provided
- name: default_state
  value: "present"
  desc: Default state of the user if alternative value not provided
- name: default_update_password
  value: "always"
  desc: Default behaviour when changing password of the user if alternative not provided

## Dependencies ##

    - role: https://github.com/traveloka/ansible-pymongo

## Example Playbook ##
    - hosts: servers
      roles:
        - role: ansible-mongo-root-user
          login_password: rahasia007
