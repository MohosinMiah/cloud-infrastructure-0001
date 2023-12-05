# Ansible 101 starter file

# Create new file and content
```
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
