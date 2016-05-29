lisk-zabbix-template
=====================

Description
-----------

This is a basic template to get info from your LISK node. 

Monitoring information by now:

* Api: Approval Percentage
* Api: Delegate Rank
* Api: Forging Status
* Api: Missed Blocks
* Api: Node Productivity
* Api: Produced Blocks
* Api: Status Sync [Blocks]
* Api: Status Sync [Height]
* Log: Received New Block (timestamped blocks from app.log)
* Log: Fork Detected (logs.log)
* Log: Forged New Block (logs.log)
* Log: Failed Generate Block (logs.log)
* Log: Failed Common Block (logs.log)
* Process: Memory Usage
* Process: Lisk Status
* Cluster: Forging Enabled (aggregated check)
* Stats: Avg Blocks Per Minute
* Trigger: Api: Missed Block on {HOST.NAME}
* Trigger: Cluster: Forging Nodes > 1
* Trigger: Log: Failed Generate Block on {HOST.NAME}
* Trigger: Log: Fork Detected on {HOST.NAME}
* Trigger: Process: Lisk is not running on {HOST.NAME}
* Trigger: Stats: Lisk Block Height on {HOST.NAME} is unchanged for last 10 minutes

Todo:
* Better included graphs and a extend monitoring screen
* What else?

Installation on a Zabbix Client
-------------------------------

Copy userparameter_lisk.conf to /etc/zabbix/zabbix_agentd.d/ - userparameter_lisk.conf must 
be updated if you want to use a different port than port 8000

Restart the zabbix-agent

Installation in the Zabbix Server
---------------------------------

In your Zabbix frontend: Configuration-Templates section, Import bottom in the right.

Choose the XML file (for server installation: lisk_zabbix_template.xml) and import it.

Apply this new template to your LISK servers. 


Template Config
---------------

From your Zabbix Template view click on the "Template App Lisk Service"

Go to the Macros section and fill in the details where needed

* {$LISK.ADDRESS} <- Your Lisk address from your Forging account
* {$LISK.APPLOG} <- Location of your Lisk app.log on your node
* {$LISK.FORGING} <- Used for aggregated check # nodes forging enabled (dont change!)
* {$LISK.LOG} <- Location of your Lisk logs.log on your node
* {$LISK.PORT} <- The port LISK is running on (default 8000 for mainnet)
* {$LISK.PUBLICKEY} <- Your Lisk publicKey from your Forging account
* {$ZABBIX.GROUP} <- The zabbix groupname of your Lisk Servers


Requirements on your Lisk node
------------------------------

Debian / Ubuntu / Raspbian
```
sudo apt-get install jq
```

RHEL / CentOS / Fedora
```
sudo yum install jq
```