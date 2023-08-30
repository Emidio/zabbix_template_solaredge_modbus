# Zabbix template for SolarEdge inverter (using modbus)

This is a very simple way to monitor your PowerWall directly without relying on the Tesla website. This work is really simple and rough - I just needed it to debug my system, quick and dirty.

You need to enable MODBUS over TCP in your SolaEdge inverter - this option is not enabled by default.
Install on zabbix server solaredge_modbus (python needed, install it if missing):

https://github.com/nmakel/solaredge_modbus

pip3 install solaredge_modbus

You need to copy the two scripts in your externalscripts zabbix folder, adjust path in solaredge_mbus.sh. Remember to give execution permissions to the .sh script.

Import Zabbix template. Create a new host (doesn't matter interface, I set SNMP), assign the template, set the correct macros:

* {$SOLAREDGE_ID}        Your Solaredge installation ID (the one you see loggin in the monitoring website after registration).
* {$SOLAREDGE_APIKEY}    Generate it from the SolaEdge monitoring website after loggin in.
* {$SOLAREDGE_IP}        Your SolaEdge inverter IP address.

Tested using Zabbix 6.2, Powerwall 2 and SolarEdge HD-Wawe SE6000H. Dashboards in Grafana using Zabbix plugin by Alexander Zobnin.
