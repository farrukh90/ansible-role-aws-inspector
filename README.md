# Ansible Role: AWS Inspector

[![CI](https://github.com/geerlingguy/ansible-role-aws-inspector/workflows/CI/badge.svg?event=push)](https://github.com/geerlingguy/ansible-role-aws-inspector/actions?query=workflow%3ACI)

Installs [AWS Inspector](https://aws.amazon.com/inspector/) (awsagent) on RedHat/CentOS or Debian/Ubuntu.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    aws_inspector_url: "https://d1wk0tztpsntt1.cloudfront.net/linux/latest/install"
    aws_inspector_installer_dest: /tmp/aws_inspector_agent_installer

URL from which inspector installer will be downloaded, and temporary directory where installer will be stored.

    awsagent_state: started
    awsagent_enabled: true

Control the `awsagent` service; by default, for Amazon Inspector to work correctly, you must have `awsagent` running on any server you want inspected.

There is also a handler, `restart awsagent`, which can be used to restart the agent.

    aws_inspector_role_test_mode: false

Set this to `true` if testing or using this role outside of an EC2 instance (e.g. if testing in CI or building a server in a different cloud environment).

There is also support for proxy configuration:

    aws_inspector_proxy_enabled: false
    aws_inspector_https_proxy: 127.0.0.1:8080
    aws_inspector_http_proxy: 127.0.0.1:8080
    aws_inspector_no_proxy: 169.254.169.254

Set `aws_inspector_proxy_enabled` to `true` and configure the rest of `*_proxy` variables to create a `/etc/init.d/awsagent.env` file that will enable proxy support.


## Dependencies

None.

## Example Playbook

    - hosts: ec2-instances
      roles:
        - geerlingguy.aws-inspector

## License

MIT / BSD

## Author Information

This role was created in 2017 by [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).
