# Ansible playbook which installs Jenkins behind Apache HTTP web-server

## devops-bootstrap.yml playbook:

1. Generating ssh-keys on host machine. The public key will be sent to nodes, the private key will be used to access them from host.


## inventory - a file with servers, which should be provisioned.
Group and group's variables are used.  

## provision.yml playbook:

List of roles:

1. **common** - provides system updates.
2. **create_user** - creates "devops:devops" user, uploads key for ssh-connection, configures sudoers, disables requiretty setting for this user.
3. **java** - installs java-openjdk.
4. **jenkins** - installs Jenkins, creates user jenkins:jenkins, configures systemd to start Jenkins, starts Jenkins and prints the init password to console.
5. **httpd** - installs httpd service, configures httpd to forward requests to Jenkins (using VirtualHost config).

All roles gather facts about configured software on the system.  
  
Handlers, templates and default variables are used.
