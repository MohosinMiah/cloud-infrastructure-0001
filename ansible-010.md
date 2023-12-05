# Ansible 101 starter file

# How to add SSH file to host server to remote server
```
1) First create a key by keygen
ssh-keygen -t rsa -b 2048 -C "your_email@example.com"

2) Add a ssh copy to the remote server
ssh-copy-id mohosin@75.127.13.28

```
# Create inventory.ini
```
touch  inventory.ini
[myhosts]
75.127.13.28
```


# Create new file and content
```
ansible-playbook -i inventory.ini create_file.yml --ask-become-pass

touch create_file.yml
---
- name: Create a New File
  hosts: 75.127.13.28
  become: true  # Run tasks with elevated privileges
  tasks:
    - name: Create a new file
      file:
        path: /home/newfile.txt  # Specify the path and filename
        state: touch  # Ensure the file exists

    - name: Add content to the file
      blockinfile:
        path: /home/newfile.txt  # Specify the same path and filename
        block: |
          This is the content of the new file.
          You can add more lines here.
```
