# Ansible Infrastructure Monitoring and Logging Stack

This repository contains Ansible playbooks for setting up a comprehensive monitoring and logging infrastructure across Ubuntu and CentOS servers. The project implements various monitoring and logging solutions including Nagios, Prometheus, and the ELK (Elasticsearch, Logstash, Kibana) stack, along with LAMP stack deployments.

## Features

- **Monitoring Solutions**:
  - Nagios setup for both Ubuntu and CentOS servers
  - Prometheus monitoring system deployment
  
- **Logging Stack**:
  - Logstash for log processing and forwarding
  - Kibana for log visualization and analysis
  
- **Web Stack**:
  - LAMP (Linux, Apache, MySQL, PHP) stack deployment for both Ubuntu and CentOS

## Prerequisites

- Ansible installed on the control node
- Target servers running Ubuntu or CentOS
- SSH access to target servers
- Proper network connectivity between servers

## Project Structure

```
.
├── ansible.cfg          # Ansible configuration file
├── config.yml          # Main playbook configuration
├── inventory           # Inventory file with server definitions
├── roles/             # Contains role-specific configurations
└── files/             # Additional files needed for deployment
```

## Server Configuration

The project is configured to work with the following server groups:

- **Ubuntu Servers**: 192.168.56.16
- **CentOS Servers**: 192.168.56.14
- **ELK Stack**: Deployed on 192.168.56.16

## Usage

1. Ensure your inventory file is properly configured with your server IPs
2. Run the main playbook:
   ```bash
   ansible-playbook -i inventory config.yml
   ```

3. To run specific components using tags:
   ```bash
   # For Logstash deployment
   ansible-playbook -i inventory config.yml --tags logstash
   
   # For Kibana deployment
   ansible-playbook -i inventory config.yml --tags kibana
   
   # For LAMP stack deployment
   ansible-playbook -i inventory config.yml --tags ls
   ```

## Automated Tasks

- Automatic package management and system updates
- Configuration of monitoring tools
- Setup and configuration of logging infrastructure
- LAMP stack deployment and configuration

## Notes

- The playbook includes automatic system updates for both Ubuntu and CentOS servers
- Package management is handled differently for Ubuntu (apt) and CentOS (dnf/yum)
- Prometheus is configured with version 2.43.0
- GPG keys are automatically retrieved for ELK stack components

## Contributing

Feel free to submit issues and enhancement requests!
