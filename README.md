# Simple NTP service with Ansible

This project uses Ansible to provision a small EC2 instance and configure it as an NTP server using Chrony. It is designed to be a simple example of automating the deployment of a time synchronization service in AWS.

## Overview

The playbook:

- creates a VPC, subnet, internet gateway, route table, and security group
- launches an Ubuntu EC2 instance
- installs Chrony on the instance
- fetches recommended NTP pool servers for a chosen region/zone
- writes the Chrony configuration files
- enables and starts the Chrony service

## Files

- `ntp.yml` - main Ansible playbook
- `roles/init` - role that performs the infrastructure and NTP setup
- `roles/init/vars/main.yml` - default variables for the deployment
- `roles/init/templates/chrony.conf.j2` - Chrony configuration template
- `roles/init/templates/ubuntu-ntp-pools.sources.j2` - NTP source list template

## Requirements

- Ansible installed on your local machine
- AWS credentials configured for the AWS CLI or environment variables
- Access to the `amazon.aws` and `community.general` Ansible collections
- An AWS account with permission to create EC2 networking resources

## Configuration

Edit the variables in `roles/init/vars/main.yml` to match your environment, including:

- AWS region
- VPC and subnet CIDRs
- key pair name
- EC2 instance type and AMI
- NTP pool zone

## Usage

Run the playbook:

```bash
ansible-playbook ntp.yml
```

This will provision the infrastructure and configure the NTP service automatically.

## Notes

The role installs Chrony and configures it to use NTP sources from the NTP Pool project, which is suitable for a lightweight and reliable NTP setup.

This project is intended as a basic example and can be extended for production use with stricter security, monitoring, and deployment practices.

## Author
BlackMagic-Master
Szymon G.