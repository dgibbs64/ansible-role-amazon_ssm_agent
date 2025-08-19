# amazon_ssm_agent

An [Ansible](https://www.ansible.com) role that ensures <a href="https://docs.aws.amazon.com/systems-manager/">Amazon SSM Agent</a> is installed on EC2 instances.

<p align="center">
<a href="https://app.codacy.com/gh/dgibbs64/ansible-role-amazon_ssm_agent"><img src="https://img.shields.io/codacy/grade/1a892d499efd4dabb73beffa8d64ed01?logo=codacy&style=flat-square" alt="Codacy grade"></a>
<a href="https://github.com/dgibbs64/ansible-role-amazon_ssm_agent/actions/workflows/molecule.yml"><img alt="GitHub Workflow Status" src="https://img.shields.io/github/actions/workflow/status/dgibbs64/ansible-role-amazon_ssm_agent/molecule.yml?label=molecule&logo=ansible&style=flat-square"></a>
<a href="https://galaxy.ansible.com/dgibbs64/amazon_ssm_agent"><img alt="GitHub tag (latest by date)" src="https://img.shields.io/github/v/tag/dgibbs64/ansible-role-amazon_ssm_agent?color=EE0000&label=release&logo=ansible&style=flat-square"></a>
<a href="https://github.com/dgibbs64/ansible-role-amazon_ssm_agent/blob/main/LICENSE.md"><img src="https://img.shields.io/github/license/gameservermanagers/docker-steamcmd?style=flat-square" alt="MIT License"></a>
</p>

## About

<a href="https://docs.aws.amazon.com/systems-manager/">Amazon SSM Agent</a> is a management agent that can be installed on EC2 instances to enable AWS Systems Manager capabilities. This role will install or remove the Amazon SSM Agent.

> note: For Ubuntu AMI's, the Amazon SSM Agent is already installed by default. However this role will still ensure the agent is installed and running.

This role can only check if Amazon SSM Agent is installed and install it if not. Update functionality is handled by AWS Systems Manager. Amazon SSM Agent can be auto updated by enabling _Auto update SSM Agent_ in `AWS Systems Manager > Fleet Manager > Settings > Agent auto update > Auto update SSM Agent`. Full guide found <a href="https://docs.aws.amazon.com/systems-manager/latest/userguide/ssm-agent-automatic-updates.html">here</a>.

This role uses <a href="https://docs.ansible.com/ansible/latest/collections/amazon/aws/ec2_metadata_facts_module.html">amazon.aws.ec2_metadata_facts</a>. Please ensure the <a href="https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html">EC2 metadata endpoint</a> is setup on your control node.

## Requirements

Requires an AWS account to use the Amazon SSM features.

### Supported Distros

- AlmaLinux >= 8
- AmazonLinux 2023
- CentOS >= 8
- Debian >= 10
- Fedora >= 39
- OracleLinux >= 8
- Redhat Enterprise Linux >= 8
- Rocky Linux >= 8
- Ubuntu >= 20.04

## Role Variables

By default, this role will install the Amazon SSM Agent if not already installed.

To customize the configuration, you can set the following variables:

```yaml
# Agent state present|absent
amazon_ssm_agent_state: "present"
# Force install of SSM Agent
amazon_ssm_agent_force_install: false
```

## Dependencies

```yaml
community.general
amazon.aws
```

## Example Playbook

```yaml
---
- name: Netdata
  hosts: all
  roles:
    - dgibbs64.amazon_ssm_agent
```

## License

MIT

## Author Information

- [Daniel Gibbs](https://danielgibbs.co.uk)
