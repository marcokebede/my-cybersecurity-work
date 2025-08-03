OffensiveTools THM - Web Enumeration & Flag Capture

This short project shows how I used gobuster and curl to enumerate a target site and find a hidden JavaScript file that contained a flag. Good practice for basic recon skills in a CTF-style web challenge.

 Objective

Enumerate the website www.offensivetools.thm, find hidden or interesting directories/files, and extract the flag.

 Tools Used

gobuster for brute-force directory and file discovery

curl to inspect content manually

Wordlist: /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt

 Steps I Took

Initial Directory Scan:

Started with basic gobuster scan:


gobuster dir -u "http://www.offensivetools.thm" -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x .php,.js

This revealed several directories like /home, /media, /templates, and most importantly:

/secret (Status: 301)

Focused on the /secret Directory:

I ran gobuster again inside /secret:


gobuster dir -u "http://www.offensivetools.thm/secret" -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x .php,.js
Results included:


/content (301)

/uploads (301)

/flag.js (200)

Manually Accessed the Flag File:

Since /flag.js had a 200 OK response, I grabbed its content with curl:


curl http://www.offensivetools.thm/secret/flag.js
Output:

THM{ReconWasASuccess}

 What I Practiced

Brute-forcing hidden paths with file extensions

Recognizing status codes (like 403, 301, 200)

Following redirection logic

Manually reviewing potential flag files

 Final Flag

THM{ReconWasASuccess}
