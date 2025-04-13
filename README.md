# README.md
# Employee Management Application Deployment

This Ansible project automates the deployment of the Employee Management application to AWS free tier instances.

## Architecture

- **App Server**: Ubuntu EC2 t2.micro instance running Java Spring Boot application
- **DB Server**: Ubuntu EC2 t2.micro instance running PostgreSQL database

## Prerequisites

- Ansible 2.9+
- Two AWS EC2 t2.micro instances with Ubuntu (free tier eligible)
- SSH access to both EC2 instances

## Directory Structure

- `inventory/`: Contains inventory files for server management
- `playbooks/`: Contains deployment playbooks
- `roles/`: Contains modular roles for each component
- `group_vars/`: Contains variables for server groups

## How to Use

1. Update the inventory file with your AWS instance details:
   ```
   # Edit inventory/hosts.ini and replace IP addresses with your actual EC2 IPs
   ```

2. Update the variables in group_vars to match your environment:
   ```
   # Edit group_vars/all.yml, app_servers.yml, and db_servers.yml
   ```

3. Run the main playbook to deploy everything:
   ```
   ansible-playbook -i inventory/hosts.ini playbooks/main.yml
   ```

4. For subsequent application updates, use the dedicated deployment playbook:
   ```
   ansible-playbook -i inventory/hosts.ini playbooks/deploy_app.yml
   ```

## Security Notes

For production use, please:
1. Use Ansible Vault to encrypt sensitive information
2. Restrict PostgreSQL access to only allow connections from your app server
3. Use private subnets for the database with proper security groups

## Performance Considerations

This deployment is optimized for AWS free tier with:
- Reduced Java memory settings (-Xms256m -Xmx512m)
- Optimized PostgreSQL configuration for low memory environments
- Connection pool settings appropriate for t2.micro instances# ansible-employee-management
# ansible-employee-management
# ansible-employee-management
