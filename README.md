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

In order to create the SIEM Dashbaord we use Splunk Dashboard Studio. Splunk Dashboard Studio provides tools to customize dashboards in Splunk, such as designing your dashboard's layout, colors, images, and more.

We created the Dashboard by using Splunk SPL Commands to search specific events in the events dataset. The scope of SPL includes data searching, filtering, modification, manipulation, insertion, and deletion.
![SOC_2023-11-08 at 11 03 50+0530_Splunk](https://github.com/MOUSSADOUNDA/setup-Splunk-SIEM-for-anomalies-detection/assets/129728703/9f22fede-6a29-40ed-94ce-7d4b3ce1ab02)

The potential threat machine is a metasploitable2 machine with the address 192.168.150.129. Lets suppose that machine is trying unauthorized ssh connection
![meta](https://github.com/MOUSSADOUNDA/setup-Splunk-SIEM-for-anomalies-detection/assets/129728703/6e5f5aa3-fec4-4442-94ff-679893125ed7)

We can see that the metasploitable machine is trying an SSH connection with the Ubuntu server and was not able to connect because the SSH server on the ubuntu server have a Key-based authentication
![sp_2](https://github.com/MOUSSADOUNDA/setup-Splunk-SIEM-for-anomalies-detection/assets/129728703/8e1bc1a2-d5d3-4483-8de6-ddcd17ffe231)

