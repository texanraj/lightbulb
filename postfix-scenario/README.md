Ansible Certification: Postfix/Squirrelmail Scenario
----------------------------------------------------

Basic Requirements
==================

- Vagrant 1.7.2 or later, with VirtualBox
- A control machine with Ansible 1.9.x or later

Components Provided
===================

- 2 Ubuntu LTS hosts/Vagrantfile
- Skeleton roles for relevant mail components
- Basic configuration files (in the config directory)
- Variable file with users and their passwords to add as system users on the MTA host
- Ansible inventory

Practical Exam Requirements
===========================

- A base playbook named "site.yml" will configure all servers in an idempotent fashion.
- The base playbook will call roles to apply common configuration to all servers
- Common configuration shall include:
  - NTP installed and running on all servers
  - fail2ban configured for all hosts correctly for relative ports to host
- All tunable configuration entries listed in group_vars/* will be templated correctly
  in the appropriate configuration files.
- The base playbook will call a common role to configure users/groups/basic configuration of OS
  - Users included in the vault.yml file should be system users, using the provided passwords for mail/ssh/shell access (You will need to generate the hash for the user module)
  - Vault file should be vaulted with the password "ansible1"
- The base playbook will call a mail/mta role to install postfix on one server
- The mail/mta role also installs dovecot imapd on the postfix server
- The base playbook will also install squirrelmail on a second host, configured to utilize mail services on the first host
- A second playbook will implement a rolling upgrade (1 server at a time) to do a system patch/upgrade and to upgrade squirrelmail
- The playbooks will run by logging in as "vagrant" (already specified in ansible.cfg)
  but sudoing to root, by passing -s to the ansible-playbook command line.
- all mail/web services share a self-generated ssl cert and are properly configured for ssl. Domain name of your choosing.

Scoring
=======

The resulting playbooks and associated content will be scored based on the following
criteria:

- Satisfaction of the practical exam requirements above
- Appropriate use of Ansible modules
- Adherence to Ansible best practices and role layout
- Clarity and readability of tasks and playbooks

Instructions
============

1. Launch the VMs with "vagrant up"
2. Run: "ansible-playbook sanity.yml" and verify connectivity to the VMs and
   to update the Yum/apt caches.
3. Implement a series of playbooks, roles, and templated config files to satisfy the
   requirements above.
4. Additional instructions exist in the various skeleton playbooks, role files, etc.
   These are market with the string "FIXME". Please read the contents carefully, and
   make sure that you have addressed all the FIXME sections throughout.
4. Create a tar or zip file of the resulting content and email to
   certification@ansible.com for scoring.
