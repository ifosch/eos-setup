# `rvm` Role

This role installs RVM.

## Requirements

This requires the variable `user` to be setup.

## Role Variables

- `rvm_install_mode`: Defines which install mode for RVM is chosen. Defaults to `single_user`. Another choice might be `multi_user`.
- `rubies`: Defines a list of all rubies to be installed.

## Dependencies

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

## License

BSD

## Author Information

Ignasi Fosch
