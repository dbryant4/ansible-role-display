# Display Role

[![Build
Status](https://travis-ci.org/dbryant4/ansible-role-display.svg)](https://travis-ci.org/dbryant4/ansible-role-display)

## Description

This role sets up a Raspberry Pi to display a webpage automatically on
boot and with no screen saver. This should also work for any Debian
based system. This is useful for creating cheap display boards which
show a [dashing dashboard](http://dashing.io/) for example.

## Provides

1. A Raspberry pi which will display a webpage
2. A VNC server will also be setup for remote management

## Requires

1. Ansible 1.6 or higher
2. Raspberry Pi (possibly other Debian based systems)
3. Internet connectivity to download tesseract source

## Variables

- display_rotate_display - if set to true, the Raspberry Pi will boot
  with the screen rotated 90 degrees clockwise.
- display_vnc_password - the password to set for the VNC password.
  This role will not change an existing password.
- display_chromium_urls - array of URLs for Chromium to load in
  individual tabs. To rotate between the tabs, the user must install an
  extension.

### Changing Variable Values

To Change the value of variables, create a file in `host_vars/` or `group_vars/` or define variables in the playbook.

There are other options for changing variable values. See [Ansible
Variable
Documentation](http://docs.ansible.com/playbooks_variables.html) for
more ideas.

## Usage

Include this role in your plays and set variables as desired.

```yaml
---
  hosts: display-pis
  vars:
    display_chromium_urls:
      - "http://google.com"
  roles:
    - display
```

## Tests
This role includes Travis CI tests and a Vagrantfile. To run tests
locally, run `vagrant up`
