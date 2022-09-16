# Dreamhost-wpbackup
Ansible code for doing backups on Wordpress installations hosted on Dreamhost. This will back up both the directory files and the database

This will result in a tarball of the site's directory and a gzipped SQL file for the site's database being present in the __controlling node__.

This assumes a directory structure for Dreamhost's shared hosting plans and quick Wordpress setup per Dreamhost's tooling.

```
/home/site_shell_user
|-- mysite.mydomain
|   |-- wp-content
|   |   |-- plugins
|   |   `-- themes
|   `-- wp-config.php
|   `-- index.php
.
.
.
```

## Usage

### 1. Create an inventory file 

```ini
[websites]
mysite1.mydomain 
mysite2.mydomain
```

You may use variables for `remote_user` matching your Dreamhost's shell user.

### 2. Create a configuration file `ansible.cfg`

Use the provided sample to fill in the `remote_user` if all your sites are in the same shared host.

### 3. Run the playbook
`$ ansible-playbook -i inventory wp-backup.yml`
