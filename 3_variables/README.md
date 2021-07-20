# Undefined
ansible db -m debug -a 'var=not_a_var' -i hosts

# Precedence, lowest to highest
ansible web -m debug -a 'var=web_version' -i hosts
ansible db -m debug -a 'var=db_version' -i hosts
ansible db -m debug -a 'var=db_version' -i hosts --extra-vars db_version=90000

# Gather facts
ansible web -m setup -i hosts
