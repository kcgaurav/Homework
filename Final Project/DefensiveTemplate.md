# Blue Team: Summary of Operations

## Table of Contents
- Network Topology
- Description of Targets
- Monitoring the Targets
- Patterns of Traffic & Behavior
- Suggestions for Going Further

### Network Topology

The following machines were identified on the network:
- ELK
  - **Operating System**: Ubuntu
  - **Purpose**: Elasticsearch and Kibana
  - **IP Address**: 192.168.1.100

- CAPSTONE
  - **Operating System**: Ubuntu
  - **Purpose**: Web Server
  - **IP Address**: 192.168.1.105

- KALI
  - **Operating System**: Kali
  - **Purpose**: Pentesting
  - **IP Address**: 192.168.1.90
 
- TARGET 1
  - **Operating System**: Debian GNU/Linux
  - **Purpose**: WordPress
  - **IP Address**:192.168.1.110

### Description of Target

The target of this attack was: `Target 1` (192.168.1.110).

Target 1 is an Apache web server and has SSH enabled, so ports 80 and 22 are possible ports of entry for attackers. As such, the following alerts have been implemented:

### Monitoring the Targets

Traffic to these services should be carefully monitored. To this end, we have implemented the alerts below:

Excessive HTTP Errors:
  - **Metric**: WHEN count() GROUPED OVER top 5 'http.response.status_code' IS ABOVE 400 FOR THE LAST 5 minutes
  - **Threshold**: Above 400
  - **Vulnerability Mitigated**: Enumeration 
  - **Reliability**: This aleat creats high reliabilitiy because measuring error codes 400 and above will filter any responses.


HTTP Request Size Monitor:
  - **Metric**: WHEN sum() of http.request.bytes OVER all documents IS ABOVE 3500 FOR THE LAST 1 minute
  - **Threshold**: Above 3500
  - **Vulnerability Mitigated**: Code Injection
  - **Reliability**: This alert creates medium reliabilitiy because there is a possibility of large non malicious HTTP request traffic.

CPU Usage Monitor:
  - **Metric**: WHEN max() OF system.process.cpu.total.pct OVER all documents IS ABOVE 0.5 FOR THE LAST 5 minutes
  - **Threshold**: Above 0.5
  - **Vulnerability Mitigated**: malicious activities
  - **Reliability**: This alert is high reliabilitiy because this help determine where to improve on CPU usage.

_TODO Note: Explain at least 3 alerts. Add more if time allows._

### Suggestions for Going Further (Optional)

- Each alert above pertains to a specific vulnerability/exploit. Recall that alerts only detect malicious behavior, but do not stop it. For each vulnerability/exploit identified by the alerts above, suggest a patch. E.g., implementing a blocklist is an effective tactic against brute-force attacks. It is not necessary to explain _how_ to implement each patch.

The logs and alerts generated during the assessment suggest that this network is susceptible to several active threats, identified by the alerts above. In addition to watching for occurrences of such threats, the network should be hardened against them. The Blue Team suggests that IT implement the fixes below to protect the network:
- Vulnerability 1
  - **Patch**: TODO: E.g., _install `special-security-package` with `apt-get`_
  - **Why It Works**: TODO: E.g., _`special-security-package` scans the system for viruses every day_
- Vulnerability 2
  - **Patch**: TODO: E.g., _install `special-security-package` with `apt-get`_
  - **Why It Works**: TODO: E.g., _`special-security-package` scans the system for viruses every day_
- Vulnerability 3
  - **Patch**: TODO: E.g., _install `special-security-package` with `apt-get`_
  - **Why It Works**: TODO: E.g., _`special-security-package` scans the system for viruses every day_
