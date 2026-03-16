# SSH-Log-Analysis-using-Splunk-for-Security-Monitoring
Analyzed SSH authentication logs using Splunk in an Ubuntu Linux environment to monitor login activities and detect suspicious behavior. Implemented SPL queries, dashboards, and alerts to identify failed login attempts, brute-force attacks, and unauthorized access, supporting basic SOC monitoring and incident investigation.

## Project Overview

This project demonstrates how SSH authentication logs can be analyzed
using Splunk to detect suspicious login activity. Logs generated from an
Ubuntu Linux system are ingested into Splunk to monitor SSH login
attempts, detect brute-force attacks, and identify unauthorized access
attempts. The project simulates basic Security Operations Center (SOC)
monitoring.

## Objectives

-   Monitor SSH login activity from system logs
-   Detect failed login attempts and brute-force attacks
-   Identify suspicious IP addresses and unauthorized access
-   Create dashboards and alerts for security monitoring
-   Perform basic incident investigation using log data

## Tools and Technologies

-   Splunk
-   Ubuntu Linux
-   OpenSSH
-   Linux authentication logs (/var/log/auth.log)
-   Splunk Search Processing Language (SPL)

## Workflow

1.  SSH authentication logs are generated on the Ubuntu system.
2.  Logs are stored in `/var/log/auth.log`.
3.  Log files are ingested into Splunk.
4.  SPL queries are used to analyze login activity.
5.  Dashboards visualize authentication events.
6.  Alerts are triggered for suspicious activity.

## Log Source

Linux SSH authentication logs:

`/var/log/auth.log`

These logs include: - Successful SSH logins - Failed login attempts -
Invalid user login attempts - Source IP addresses

## Example SPL Queries

### Failed SSH Login Attempts

index=ssh_logs "Failed password" \| stats count by src_ip \| sort -count

### Successful SSH Logins

index=ssh_logs "Accepted password" \| stats count by user, src_ip

### Detect Possible Brute Force Attack

index=ssh_logs "Failed password" \| stats count by src_ip \| where count
\> 10

## Dashboard Features

-   Failed SSH login attempts
-   Successful login attempts
-   Top attacking IP addresses
-   Authentication activity trends

## Alerts

Alerts can be configured to detect: - Multiple failed login attempts
from the same IP - Repeated authentication failures - Possible
brute-force attacks

## Skills Demonstrated

-   SIEM log analysis
-   Security monitoring with Splunk
-   Linux log investigation
-   Basic SOC analyst workflow
-   Threat detection using log data

## Use Case

This project shows how SSH authentication logs can be monitored in a
SIEM platform to identify potential security threats and support SOC
analyst incident detection and investigation.

