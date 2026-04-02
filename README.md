# Splunk Detection Engineering Home Lab



A home lab where I simulated real-world cyberattacks against a Windows machine and used Splunk to detect them. The goal was to understand how defenders think, how to read logs, spot suspicious activity, and build dashboards that tell the story of an attack.

The lab runs on three virtual machines in a private network. A Linux host runs Splunk and acts as the central log server. A Windows 10 machine acts as the target endpoint, sending all of its logs to Splunk in real time using Sysmon and the Splunk Universal Forwarder. A Kali Linux machine is used to launch attacks against Windows. When an attack happens, it shows up in the logs and can be detected using custom Splunk queries and dashboards.

Over the course of the project I simulated six attacks. A network port scan, an RDP brute force, a reverse shell delivered through a fake webpage, a scheduled task set to run malware on startup, a registry modification for persistence, and a hidden backdoor admin account. For each one I wrote detection logic in Splunk, built a dashboard to visualize the activity, and documented the full process including every problem I ran into and how I solved it. I feel the problems I faced are common problems that every Defender faces at least once at the start  of their journey and I hope that this will help them understand and solve these problems

Building the detection side turned out to be far more interesting than running the attacks. Windows does not log most security events by default, which means attacks are invisible unless you explicitly configure audit policies first. Sysmon fills in the gaps that native Windows logging misses, particularly around network connections and process behavior. The most important lesson was that good detection depends entirely on knowing what normal looks like — once a baseline was established, anything unusual stood out immediately.

For the full technical breakdown of each attack, detection query, and troubleshooting step, see the weekly documentation files in the Weekly Documentation folder.





Repository Structure



Splunk\_Detection\_Engineering\_Lab/

├── README.md

├── architecture/

│   └── lab\_architecture.png

├── Weekly Documentation/

│   ├── week1\_documentation.md

│   ├── week2\_documentation.md

│   ├── week3\_documentation.md

│   └── week4\_documentation.md

└── Configuration/

&#x20;   ├── sysmon\_config.xml

&#x20;   ├── inputs.conf

&#x20;   └── outputs.conf



