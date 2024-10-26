Here is Zabbix env deploy ansible playbooks collection
How you can use it:

1. Setup your zabbix env configuration:
   - set proper params in ./hosts file. All host must already have password less ssh connection (ssh-keygen && ssh-copy-id)
   - change DB UserName and DBPassword, IP addesses of zabbix server, allowed subnets for clients and many other params in zabbix-server.env
   - change zabbix agnets params in zabbix-client.env
   - change IP Sec Server and IP Sec client params in ipsec.env
   - change server,clients hosts to ./hosts
2. Start installation process following next steps, one-by-one

- 2.1. Install Zabbix server
   ansible-playbook -i hosts playbook-zabbix-server-70-nginx-mysql.yml

- 2.2. Install IP SEC server
   ansible-playbook -i hosts playbook-ipsec-server.yml

- 2.3 Integrate Zabbix with Grafana 
   ansible-playbook -i hosts playbook-zabbix-server-add-grafana.yml


- 2.4 Install Zabbix agents
   ansible-playbook -i hosts playbook-zabbix-agent-70.yml

- 2.5 Install IP SEC client
   ansible-playbook -i hosts playbook-ipsec-client.yml


3. Test installed components 
   ansible-playbook -i hosts playbook-zabbix-tests.yml

4. TO.DO.
   - params via ENV : done
   - test playbook  : done
   - Discovery research & tests: done
   - Implement MAC Address based client logical binding insted IP based client analitycs and Zabbix settings: in progress

FAQ:
Q: how to use vars from cli?
A: ansible-playbook -i inventory_file playbook.yml --extra-vars "server_ip=YOUR_SERVER_IP psk_key=YOUR_PSK"
