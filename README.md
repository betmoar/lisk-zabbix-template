lisk-zabbix-template
=====================

Description
-----------

This is a basic template to get info from your LISK node. 

Monitoring information by now:

* Stats: Forging Enabled
* Stats: Blocks Forged
* Process: Memory Usage
* Process: Lisk Status
* Log: Received New Block
* Log: Fork Detected
* Log: Forged New Block
* Log: Failed Generate Block
* Log: Failed Common Block
* Api: Forging Status	
* Api: Rank
* Api: Productivity
* Api: Produced Blocks
* Api: Missed Blocks
* Api: Approval
* Trigger: LISK Detected a Fork on {HOST.NAME}
* Trigger: Warning Process LISK is not running {HOST.NAME}

Installation on a Zabbix Client
-------------------------------

Copy userparameter_lisk.conf to /etc/zabbix/zabbix_agentd.d/ - userparameter_lisk.conf must be updated if you want to use a different port than port 7000

Restart the zabbix-agent

Installation in the Zabbix Server
---------------------------------

In your Zabbix frontend: Configuration-Templates section, Import bottom in the right.

Choose the XML file (for server installation: lisk_zabbix_template.xml) and import it.

Apply this new template to your LISK servers. 


Template Config
------------

From your Zabbix Template view click on the "Template App Lisk Service"

Go to the Macros section and fill in the details

* {$GROUP} <- The zabbix groupname of your Lisk Servers
* {$LISK.LOG} <- Location of your Lisk log on your node
* {$PUBLICKEY} <- Your Lisk publicKey from your Forging account
* {$ADDRESS} <- Your Lisk address from your Forging account


Requirements
------------

Debian / Ubuntu / Raspbian
```
sudo apt-get install jq
```

RHEL / CentOS / Fedora
```
sudo yum install jq
```