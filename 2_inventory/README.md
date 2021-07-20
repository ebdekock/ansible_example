# All
ansible all -i hosts -m ping

# Groups
ansible db -i hosts -m ping
ansible mysql -i hosts -m ping
ansible web -i hosts -m ping

# Hosts
ansible web1 -i hosts -m ping
ansible mysql1 -i hosts -m ping
