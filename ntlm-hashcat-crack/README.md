

This lab demonstrates how to crack NTLM password hashes using Hashcat,

one of the most powerful GPU-accelerated password recovery tools. The objective was to recover the plaintext password from a given NTLM hash using a dictionary attack with the popular rockyou.txt wordlist.

Tools Used Hashcat: Command-line password cracker supporting many hashing algorithms.

RockYou Wordlist: A widely-used dictionary of leaked passwords.

Linux Terminal: Used to execute commands and analyze output.

Step-by-Step Process Identify Hash Type 

The NTLM hash was detected based on its format. NTLM corresponds to Hashcat mode 1000.

Prepare the Hash File Saved the target NTLM hash in a text file named hash1.txt.

Run Hashcat Executed the cracking process with the following command:

hashcat -m 1000 -a 0 hash1.txt /usr/share/wordlists/rockyou.txt

Crack Success

Hashcat successfully cracked the hash:

Hash: e78870e25a5c[...]

Recovered Password: Trustno1

Speed: ~1.5 million hashes per second

Wordlist: rockyou.txt

Runtime: 2 seconds

Verified Result Displayed cracked password using: hashcat --show -m 1000 ~/Hashing-Basics/Task-6/hash1.txt

Hashcat cracked NTLM hash

Lessons Learned

NTLM hashes are fast to compute and thus vulnerable to dictionary attacks.

Importance of strong, unique passwords that aren’t in common wordlists.

How to identify and attack different hash types using correct Hashcat modes.

Next Steps

Explore cracking more secure hashes like bcrypt and SHA512.

Try hybrid attacks combining dictionaries and brute force.

Test salted hashes and understand their defensive advantages.
