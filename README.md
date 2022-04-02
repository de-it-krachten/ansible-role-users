[![CI](https://github.com/de-it-krachten/ansible-role-users/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-users/actions?query=workflow%3ACI)


# ansible-role-users

Creates local users & groups


Platforms
--------------

Supported platforms

- Red Hat Enterprise Linux 7<sup>1</sup>
- Red Hat Enterprise Linux 8<sup>1</sup>
- CentOS 7
- RockyLinux 8
- AlmaLinux 8<sup>1</sup>
- Debian 10 (Buster)
- Debian 11 (Bullseye)
- Ubuntu 18.04 LTS
- Ubuntu 20.04 LTS

Note:
<sup>1</sup> : no automated testing is performed on these platforms

Role Variables
--------------
<pre><code>
# List of users to create
users: []

# List of groups to create
grps: []

# List of users to delete
users_rm: []

# List of groups to delete
grps_rm: []
</pre></code>


Example Playbook
----------------

<pre><code>
- name: sample playbook for role 'users'
  hosts: all
  vars:
    grps: [{'name': 'user1', 'gid': 2000}, {'name': 'user2', 'gid': 2001}, {'name': 'group1', 'gid': 3000}, {'name': 'group2', 'gid': 3001}]
    users: [{'name': 'user1', 'uid': 2000, 'group': 'user1'}, {'name': 'user2', 'uid': 2001, 'group': 'group2', 'shell': '/bin/sh', 'sshkey': 'ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQC5rUvo3sZrPcKYmezty1kOUX61jF03EyDJ8DVcmU4heTpTm35/UhltfcJkYPNUChpLJelfm1y+d4MKSJPsBcRmbep3757xUCqQYej9itwpBY0n2XzdurR6uJh1cFfiynsKFnDbr/pqOatY/GedFMVABMtdMf9zJDfYpfEzvDxbN1hpMq+/dJTs+5EjAjgon0mNZ1925tyMQdNpFTl/M/B04utNqQfcM1f5UozIT1o6YNJcNH5tp7B/mkpj4c3WR4ZPmMcLrvycSP1Nzrb7cmtTlxR2nSXANRnQhMJCHEORyBn3aFI62SJXwQxbKt1fX9UaiFZpHDJ1IqsFc56lylNGcBJK8vCCJwkscFbMnLbBGwAD+ozo4Vt/2MVHhXDFtO84rfz7Nr+J55imJnxE4BS44xm6eaF+7G+NZZGvxQEdKV/o9rpjXFeSGO+LW7qVzva2biA+l3sw6N+suzklhuNxdKQ9Q4JMwNoyDhNr4Bk1fZePSxwWC28eChXln9Vzkv8=', 'sudo': True}]
  tasks:
    - name: Include role 'users'
      include_role:
        name: users
</pre></code>
