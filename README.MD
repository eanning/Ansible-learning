# Ansible Navigator
# When you run ansible-navigator run by default it starts a container with Podman and runs your playbook in the container
# Container immage = Execution Environment (EE) -> contains ansible-core, Python + Python libries, and set of ansible conent colections ( like ansible.posix and community general)
# EE = everything Ansible needs is inside, so playbook behaves the same on any machine


ansible-playbook example.yml = ansible-navigator run example.yml
ansible-doc ansible.builtin.copy = ansible-navigator doc ansible.builtin.copy
ansible-inventory --list = ansible-navigator inventory --list
ansible-config dump = ansible-navigator config 
                      ansible-navigator collections
                      ansible-navigator images
                      ansible-navigator replay

# Two modes: Interactive vs stdout
# Interactive mode (default) opens a full-screen text interface (TUI) that you navigate with the keyboard
ansible-navigator run example.yml
# stdout (-m stdout) prints plain output to the terminal
ansible-navigator run example.yml -m stdout

# Interactive mode
# 0-9 = select row 
# :12 = select row 12 or higher 
# Esc = Go back one screen
# :q or :quit = Quit navigator
# :help = show help
# :stdout or :st = show plain playbook output in run mode
# pgup / pgdown = scroll
# :doc <module> = open docs for a module from anywhere
# :collections / :images / :inventory / : /config = jump to those views


Options like --ask-vault-pass / --syntax-check / --check will work as normal

# Ansible configuration file
ansible-navigator settings --sample > ansible-navigator.yml
ansible-navigator settings --sample --ee false > ansible-navigator.yml
nsible-navigator settings --effective --ee false

# Exam Workflow
1. Go to your project directory ( cd /home/student/ansible)
2. Create ansible.cfg and the inventory 
3. Create the navigator config
4. Check the inventory is correct
5. Install required collections/roles into the project 
6. Check the collections are available 
7. Write the playbooks and check syntax
8. Run the playbook
9. Run again to confirm idempotence 
