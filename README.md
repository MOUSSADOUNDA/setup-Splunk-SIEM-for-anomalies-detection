# setup-Splunk-SIEM-for-anomalies-detection
This project aim to setup Splunk Enterprise in order to detect anomalies in a specific server. Splunk will be collecting logs from the ubuntu server including: Authentication logs, Suricata IDS/IPS logs, System logs.
This is a an architecture of our use case scenario 
![arch_Splunk](https://github.com/MOUSSADOUNDA/setup-Splunk-SIEM-for-anomalies-detection/assets/129728703/da1e441f-ff81-4f1e-878a-1b15401a72a4)

First and foremost, we install Splunk Enterprise on the local machine, then we configure a Receive data port (9997) on the local Splunk Server. This enable the sever to receive data from remote servers
![s_1](https://github.com/MOUSSADOUNDA/setup-Splunk-SIEM-for-anomalies-detection/assets/129728703/1acb6f45-4f71-43c4-a482-41c2a6bb6cb7)

To allow remote connection, we create windows firewall inboud rule that allow the port 9997
![s_2](https://github.com/MOUSSADOUNDA/setup-Splunk-SIEM-for-anomalies-detection/assets/129728703/25db0f0d-6f2d-4d56-bf44-2ade1277b41d)

Data will be collected from the Ubuntu server to the Splunk server. To do so, we install Splunk universal forwarder on the ubuntu server and set up the admin credentials
![s_3](https://github.com/MOUSSADOUNDA/setup-Splunk-SIEM-for-anomalies-detection/assets/129728703/56990ca6-0c19-4e68-855a-d455b3eaa2f8)

We enable boot start in order to start Universal forwarder at each boot of Ubuntu server
![s_0](https://github.com/MOUSSADOUNDA/setup-Splunk-SIEM-for-anomalies-detection/assets/129728703/01129e90-0fdb-415d-bfe4-509fd2d03c78)

Now we add log sources to the Splunk forwaerder including:
/var/log/auth.log
/var/log/syslog
/var/log/suricata/fast.log
![s_00](https://github.com/MOUSSADOUNDA/setup-Splunk-SIEM-for-anomalies-detection/assets/129728703/718da19a-8e88-4a60-820e-7e9ed902ecf3)
![auth](https://github.com/MOUSSADOUNDA/setup-Splunk-SIEM-for-anomalies-detection/assets/129728703/8b21fbbd-8133-4d3c-8b7d-3562bd5c7175)

After all the configuration are done, we are receive data from the Ubuntu server called "moussa"
![sp_1](https://github.com/MOUSSADOUNDA/setup-Splunk-SIEM-for-anomalies-detection/assets/129728703/fcebb2b1-4bdc-4aa2-bb97-3199273a5dcf)
