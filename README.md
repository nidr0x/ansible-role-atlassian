# Ansible Role for Atlassian

Ansible Role for Atlassian JIRA and Confluence Installation.

Requirements
------------

This role is designed for Ansible 2.0 or higher.

Only tested in Ubuntu Server 14.04 LTS and Ubuntu Server 16.04 LTS.

The next steps will be add more logical into configurations file to allow multiple database engines depends on selection made by default config variables in Ansible.

Role Variables
--------------

Note: Not all variables are documented

Common

| Parameter       | Required      | Comments                          |
| -------------   |:-------------:| :------------:                     |
| nfs_is_enabled  | no |  Enable NFS for attachments       |
| jira_is_enabled | no      |  Enable JIRA installation         |
| confluence_is_enabled | no      |  Enable Confluence installation   |
| attachments_mount_filesystem | no      |  Filesystem for NFS (if exists)   |
| attachments_mount_src | no      |  Source host for NFS mount   |
| attachments_mount_path | no      |  Local mountpoint for NFS   |
| attachments_mount_options | no      |  Mountoptions for NFS (if is required)   |

JIRA

| Parameter           | Required      | Comments             |
| -------------       |:-------------:| :------------:        |
| jira_config_db_host | yes           | Database host        |
| jira_config_db_port | yes           | Database port        |
| jira_config_db_name | yes           | Database name        |
| jira_config_db_user | yes           | Database username    |
| jira_config_db_pass | yes           | Database passwords   |
| jira_config_db_type | yes           | Database engine (only postgresql, for the nonce)      |
| jira_config_db_params | yes         | Database driver      |
| jira_checksum | yes         | Checksum for JIRA download      |
| jira_version_download | yes         | Version for JIRA download      |


Confluence

| Parameter           | Required      | Comments                                                    |
| -------------       |:-------------:| :------------:                                               |
| confluence_config_db_host | yes           | Database host                                         |
| confluence_config_db_port | yes           | Database port                                         |
| confluence_config_db_name | yes           | Database name                                         |
| confluence_config_db_user | yes           | Database username                                     |
| confluence_config_db_pass | yes           | Database passwords                                    |
| confluence_config_db_type | yes           | Database engine (only postgresql, for the nonce)      |
| confluence_config_db_params | yes         | Database driver                                       |
| confluence_checksum | yes         | Checksum for Confluence download                                       |
| confluence_version_download | yes         | Version for Confluence download      |



Dependencies
------------

You will need to install ORACLE (JDK) or Java Run-time Environment (JRE). [Ansiblebit-oracle-java](https://github.com/ansiblebit/oracle-java) is battle-tested and works very well across some distros.

If you are planning to use in production, i recommend a Load Balancer (like haproxy or ALB -AWS-) or nginx/apache as a reverse proxy. 

Even JIRA supports MySQL 5.x, Oracle 11g, Microsoft SQL Server 2008 & 2012 and finally PostgreSQL 8.4 - 9.x, in this role only giving support to the last one.

# Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yml
- hosts: servers
  roles:
    - ansible-role-atlassian
```

## License

MIT / BSD