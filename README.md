[![CI](https://github.com/de-it-krachten/ansible-role-users/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-users/actions?query=workflow%3ACI)


# ansible-role-users

Creates local users & groups



## Dependencies

#### Roles
None

#### Collections
- ansible.posix

## Platforms

Supported platforms

- Red Hat Enterprise Linux 7<sup>1</sup>
- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- CentOS 7
- RockyLinux 8
- RockyLinux 9
- OracleLinux 8
- OracleLinux 9
- AlmaLinux 8
- AlmaLinux 9
- SUSE Linux Enterprise 15<sup>1</sup>
- openSUSE Leap 15
- Debian 11 (Bullseye)
- Debian 12 (Bookworm)
- Ubuntu 20.04 LTS
- Ubuntu 22.04 LTS
- Fedora 37
- Fedora 38

Note:
<sup>1</sup> : no automated testing is performed on these platforms

## Role Variables
### defaults/main.yml
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




## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'users'
  hosts: all
  become: 'yes'
  vars:
    grps:
      - name: user1
        gid: 2000
      - name: user2
        gid: 2001
      - name: group1
        gid: 3000
      - name: group2
        gid: 3001
    users:
      - name: user1
        uid: 2000
        group: user1
      - name: user2
        uid: 2001
        group: group2
        shell: /bin/sh
        authorized_key: ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQC5rUvo3sZrPcKYmezty1kOUX61jF03EyDJ8DVcmU4heTpTm35/UhltfcJkYPNUChpLJelfm1y+d4MKSJPsBcRmbep3757xUCqQYej9itwpBY0n2XzdurR6uJh1cFfiynsKFnDbr/pqOatY/GedFMVABMtdMf9zJDfYpfEzvDxbN1hpMq+/dJTs+5EjAjgon0mNZ1925tyMQdNpFTl/M/B04utNqQfcM1f5UozIT1o6YNJcNH5tp7B/mkpj4c3WR4ZPmMcLrvycSP1Nzrb7cmtTlxR2nSXANRnQhMJCHEORyBn3aFI62SJXwQxbKt1fX9UaiFZpHDJ1IqsFc56lylNGcBJK8vCCJwkscFbMnLbBGwAD+ozo4Vt/2MVHhXDFtO84rfz7Nr+J55imJnxE4BS44xm6eaF+7G+NZZGvxQEdKV/o9rpjXFeSGO+LW7qVzva2biA+l3sw6N+suzklhuNxdKQ9Q4JMwNoyDhNr4Bk1fZePSxwWC28eChXln9Vzkv8=
        sudo: true
      - name: user3
        uid: 2002
        group: group2
        shell: /bin/sh
        authorized_keys:
          - ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQC5rUvo3sZrPcKYmezty1kOUX61jF03EyDJ8DVcmU4heTpTm35/UhltfcJkYPNUChpLJelfm1y+d4MKSJPsBcRmbep3757xUCqQYej9itwpBY0n2XzdurR6uJh1cFfiynsKFnDbr/pqOatY/GedFMVABMtdMf9zJDfYpfEzvDxbN1hpMq+/dJTs+5EjAjgon0mNZ1925tyMQdNpFTl/M/B04utNqQfcM1f5UozIT1o6YNJcNH5tp7B/mkpj4c3WR4ZPmMcLrvycSP1Nzrb7cmtTlxR2nSXANRnQhMJCHEORyBn3aFI62SJXwQxbKt1fX9UaiFZpHDJ1IqsFc56lylNGcBJK8vCCJwkscFbMnLbBGwAD+ozo4Vt/2MVHhXDFtO84rfz7Nr+J55imJnxE4BS44xm6eaF+7G+NZZGvxQEdKV/o9rpjXFeSGO+LW7qVzva2biA+l3sw6N+suzklhuNxdKQ9Q4JMwNoyDhNr4Bk1fZePSxwWC28eChXln9Vzkv8=
  tasks:
    - name: Include role 'users'
      ansible.builtin.include_role:
        name: users
</pre></code>
