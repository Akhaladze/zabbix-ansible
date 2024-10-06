Here is Zabbix env deploy ansible playbooks collection
How you can use it:

1. Setup your zabbix env configuration:
   - set proper params in ./hosts file. All host must already have password less ssh connection (ssh-keygen && ssh-copy-id)
   - fix DB Users and Passwords, if it needed, in all used playbooks

Install Zabbix server
ansible-playbook -i hosts playbook.yml

Install Zabbix agents
ansible-playbook -i hosts playbook-agents.yml

#Integrate Zabbix with Grafana 
grafana_zabbix_playbook.yml

TO.DO.
- params via ENV
- test playbook
