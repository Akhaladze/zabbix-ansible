Here is Zabbix env deploy ansible playbooks collection
How you can use it:

1. Setup your zabbix env configuration:
   - set proper params in ./hosts file. All host must already have password less ssh connection (ssh-keygen && ssh-copy-id)
   - change DB UserName and DBPassword, IP addesses of zabbix server, allowed subnets for clients and many other params in zabbix-server.env
   - change zabbix agnets params in zabbix-client.env
   - change IP Sec Server and IP Sec client params in ipsec.env
   - change server,clients hosts to ./hosts
2. Start installation process following next steps, one-by-one

# Install Zabbix server
ansible-playbook -i hosts playbook-zabbix-agent-70.yml

# Install IP SEC server
ansible-playbook -i hosts playbook-ipsec-server.yml

# Integrate Zabbix with Grafana 
ansible-playbook -i hosts playbook-server-grafana.yml


# Install Zabbix agents
ansible-playbook -i hosts playbook-agent-70.yml

# Install IP SEC client
ansible-playbook -i hosts playbook-ipsec-client.yml


TO.DO.
- params via ENV : done
- test playbook  : done
- Discovery research & tests: done
- Implement MAC Address based client logical binding insted IP based client analitycs and Zabbix settings: in progress

Note:
ansible-playbook -i inventory_file playbook.yml --extra-vars "server_ip=YOUR_SERVER_IP psk_key=YOUR_PSK"
