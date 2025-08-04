OffensiveTools.thm - Virtual Host Enumeration

In this task, I performed virtual host (vhost) enumeration on the target domain offensivetools.thm to discover subdomains and identify which hosts respond with a valid HTTP 200 status.

Steps and commands used:

Used gobuster for vhost enumeration with a large DNS wordlist:


gobuster vhost -u http://offensivetools.thm -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-110000.txt --domain offensivetools.thm --append-domain > vhost_output.txt

Filtered the results for hosts responding with status code 200:


grep "Status: 200" vhost_output.txt

Removed duplicate entries differing only in case to count unique valid vhosts.

Findings:

Discovered 4 unique virtual hosts responding with HTTP 200:

forum.offensivetools.thm

store.offensivetools.thm

www.offensivetools.thm

secret.offensivetools.thm

This enumeration helps identify valid subdomains that could be further investigated for vulnerabilities or sensitive content.

