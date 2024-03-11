# CVE-2024-21762-Checker
This script performs vulnerability scanning for CVE-2024-21762, a Fortinet SSL VPN remote code execution vulnerability. It checks whether a given server is vulnerable to this CVE by sending specific requests and analyzing the responses.
For more information, [see this Bishop Fox blog post](https://bishopfox.com/blog/cve-2024-21762-vulnerability-scanner-for-fortigate-firewalls)
Date of published exploit: **2024/02/28**
Vulnerable vesions: **FortiOS 6.0 to 7.4.2**
| FortiOS Version | Affected Versions    | Recommended Action         |
|-----------------|----------------------|----------------------------|
| FortiOS 7.6     | Not affected         | Not Applicable             |
| FortiOS 7.4     | 7.4.0 through 7.4.2  | Upgrade to 7.4.3 or above  |
| FortiOS 7.2     | 7.2.0 through 7.2.6  | Upgrade to 7.2.7 or above  |
| FortiOS 7.0     | 7.0.0 through 7.0.13 | Upgrade to 7.0.14 or above |
| FortiOS 6.4     | 6.4.0 through 6.4.14 | Upgrade to 6.4.15 or above |
| FortiOS 6.2     | 6.2.0 through 6.2.15 | Upgrade to 6.2.16 or above |
| FortiOS 6.0     | 6.0 all versions     | Migrate to a fixed release |

## Usage
The script supports two modes of operation:
Single check: You can provide a hostname and port as command-line arguments to check a single host.
```
python3 check-cve-2024-21762.py <IP> <PORT>
```
Mass scanning: You can provide a file containing a list of host URLs in the format hostname:port, and the script will scan each host listed in the file.
```
python3 check-cve-2024-21762.py host_URL.txt # <IP|Hostname>:<PORT>
```
For each host, the script sends two POST requests: a control request and a check request. Based on the responses received, it determines whether the server is vulnerable or patched. The output includes color-coded status messages for easy identification: Vulnerable status is displayed in red, while Patched status is displayed in green. Additionally, it provides warning messages if the server does not appear to be a Fortinet SSL VPN interface or if the connection fails.

