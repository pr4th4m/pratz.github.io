---
layout: post
title:  Custom ansible module
date:   2016-07-12 00:00:00
author: pratz
permalink: /custom-ansible-module
categories:
    - infrastructure-management
tags:
    - ansible
---

### How to write ansible custom modules
Ansible modules are easy way to interact between an existing application and ansible playbook. This blog covers how to write your own ansible module.


#### Module
- Create a python file called `greet.py` with following content

        def main():

            module = AnsibleModule(
                argument_spec = dict(
                    message = dict(required=True, type="str"),
                ),
                supports_check_mode=True
            )

            # get module params
            message = module.params.get("message")

            try:
                module.exit_json(changed=True, msg=message)
            except:
                module.fail_json(msg="It's bad not to greet someone")

        from ansible.module_utils.basic import AnsibleModule
        if __name__ == "__main__":
            main()

- File name `greet.py` is considered as ansible module.
- Arguments defined in ansible playbooks will be parsed by `AnsibleModule` class.
- Ansible module always returns json, for convenience ansible provides two methods, one for success and other for failure

                # For success
                module.exit_json(changed=True, msg=message)

                # For failure
                module.fail_json(msg="It's bad not to greet someone")


#### Usage

- Create an ansible playbook called `playbook.yml`

        touch playbook.yml


- Create directory `library` alongside `playbook.yml` and copy `greet.py` to `library`

        mkdir library
        cp greet.py library


- Now our directory structure should look like

        library
            |- greet.py
        playbook.yml


- We can now use `greet` module with our `playbook.yml`

        ---
        - hosts: localhost
          tasks:
          - name: Lets start greeting
            greet:
                message: "Good morning"


**Done !!** as simple as that ;)
