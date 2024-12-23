Here is Zabbix env deploy ansible playbooks collection
How you can use it:

1. Setup your zabbix env configuration:
   - set proper params in ./hosts file. All host must already have password less ssh connection (ssh-keygen && ssh-copy-id)
   - change DB UserName and DBPassword, IP addesses of zabbix server, allowed subnets for clients and many other params in zabbix-server.env
   - change zabbix agnets params in zabbix-client.env
   - change IP Sec Server and IP Sec client params in ipsec.env
   - change server,clients hosts to ./hosts
2. Start installation process following next steps, one-by-one

# Install with All-In-One Master playbook for Zabbix Server, IPSEC, Grafana, add hosts, plugins and dashboards.
   RUN: ansible-playbook -i hosts  playbook-master-server.yml

# Install with All-In-One Master playbook for Zabbix Agent, IPSEC Client.
   RUN: ansible-playbook -i hosts  playbook-master-client.yml

Or use it separetly

- 2.1. Install Zabbix server
   RUN: ansible-playbook -i hosts playbook-zabbix-server-70-nginx-mysql.yml

- 2.2. Install IP SEC server
   RUN: ansible-playbook -i hosts playbook-ipsec-server.yml

- 2.3 Integrate Zabbix with Grafana 
   RUN: ansible-playbook -i hosts playbook-zabbix-server-add-grafana.yml


- 2.4 Install Zabbix agents
   RUN: ansible-playbook -i hosts playbook-zabbix-agent-70.yml

- 2.5 Install IP SEC client
   RUN: ansible-playbook -i hosts playbook-ipsec-client.yml


1. Test installed components 
   RUN: ansible-playbook -i hosts playbook-zabbix-tests.yml

2. TO.DO.
   - params via ENV : done
   - test playbook  : done
   - Discovery research & tests: done
   - Implement MAC Address based client logical binding insted IP based client analitycs and Zabbix settings: in progress
   - Dashboards: brainstorm session: which params we need
   - Alerting: brainstorm session: params, triggers
   - Logging

FAQ:
Q: how to use vars from cli?
A: ansible-playbook -i inventory_file playbook.yml --extra-vars "server_ip=YOUR_SERVER_IP psk_key=YOUR_PSK"
