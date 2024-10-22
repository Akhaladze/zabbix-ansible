Here is Zabbix env deploy ansible playbooks collection
How you can use it:

1. Setup your zabbix env configuration:
   - set proper params in ./hosts file. All host must already have password less ssh connection (ssh-keygen && ssh-copy-id)
   - fix DB Users and Passwords, if it needed, in all used playbooks

Install Zabbix server
ansible-playbook -i hosts playbook.yml

Install Zabbix agents
ansible-playbook -i hosts playbook-agents.yml

# Integrate Zabbix with Grafana 
ansible-playbook -i hosts playbook-server-grafana.yml

# Or Another tested approch to add Grafana to Zabbix
ansible-playbook -i hosts playbook-server-grafana.yml

TO.DO.
- params via ENV : done
- test playbook  : done
- Discovery research & tests
- Implement MAC Address based client logical binding insted IP based client analitycs and Zabbix settings.
