\# Network Scan Investigation



\## 1. Detection Summary



Suricata detected suspicious inbound network traffic targeting a database

service on the Ubuntu 16.04 endpoint.



\- \*\*Detection:\*\* ET SCAN Suspicious inbound to PostgreSQL port 5432

\- \*\*Signature ID:\*\* 2010939

\- \*\*Source IP:\*\* 192.168.56.101

\- \*\*Destination IP:\*\* 192.168.56.104

\- \*\*Affected Agent:\*\* vtcsec

\- \*\*Alert Severity:\*\* 2

\- \*\*Alert Category:\*\* Potentially Bad Traffic

\- \*\*Action:\*\* Allowed



\## 2. Investigation



The source IP `192.168.56.101` belongs to the authorized Kali Linux

machine used within the lab environment.



A controlled Nmap SYN scan was performed against the Ubuntu 16.04

endpoint at `192.168.56.104` to test the Suricata detection capability.



Suricata generated multiple ET SCAN alerts during the scan, including

detections for database and other commonly targeted service ports.



The alert was subsequently forwarded through Suricata's `eve.json`

log to the Wazuh agent and displayed in the Wazuh Threat Hunting

interface.



\## 3. Analysis



The activity is consistent with network reconnaissance/port scanning.



Because the source system was an authorized lab machine and the scan

was intentionally performed as part of security testing, the activity

does not represent an unauthorized attack in this scenario.



The Suricata detection itself is considered a \*\*True Positive\*\* because

the network scanning activity actually occurred and was correctly

identified.



\## 4. Disposition



\*\*True Positive — Authorized Security Testing\*\*



The alert was not escalated as a real security incident because the

activity was intentionally generated within the controlled laboratory

environment.



\## 5. Analyst Conclusion



The investigation demonstrates that Suricata successfully detected

network reconnaissance activity and that the resulting security event

was forwarded to Wazuh for centralized monitoring and investigation.



This validates the Suricata → eve.json → Wazuh detection pipeline

within the lab.



\## 6. Evidence



\- `07-suricata-scan-alerts.png` — Suricata detection log showing network scan alerts

\- `08-wazuh-suricata-alert.png` — Wazuh alert generated from suricata telemetry

\- `09-network-scan-investigation.png` — Wazuh event details used to investigate the network scan

