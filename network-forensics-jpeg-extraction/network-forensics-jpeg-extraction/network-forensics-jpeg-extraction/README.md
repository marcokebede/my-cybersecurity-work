Network Forensics: Extracting a JPEG from HTTP Traffic

Challenge Overview

This lab focused on analyzing captured network traffic to extract a JPEG image transferred over HTTP. The goal was to locate and reconstruct a file from a .pcapng capture using Wireshark and validate its integrity using hashing tools. The exercise was conducted in a TryHackMe virtual lab environment.

Tools and Techniques Used

Wireshark: For analyzing packet captures and reconstructing reassembled TCP streams carrying HTTP data.

GtkHash: Used to generate hash values (MD5, SHA1, SHA256, CRC32) of the extracted image for validation.

TryHackMe VNC lab: Provided the virtual environment and traffic capture for analysis.

Step-by-Step Process

Opened the file Exercise.pcapng in Wireshark.

Applied display filters to locate HTTP traffic, especially responses with JPEG content.

Identified a packet with an HTTP 200 OK response containing a JPEG JFIF file.

Observed the presence of the JPEG signature in the data stream (0xffd8) and confirmed successful reassembly of TCP segments.

Exported the reassembled payload as an image file named wireshark-extracted-jpg.

Opened GtkHash and loaded the extracted file.

Generated and recorded the following hash values:

MD5: 911cd574a42865a956c...

SHA1: 40eea6565acd5a8e39b...

SHA256: 99958e145afe69a59b0...

CRC32: 65d2xxxx (partial)



Lessons Learned


How to analyze and reconstruct HTTP-transferred files using Wireshark.

Use of file signatures (magic bytes) in identifying file types from network traffic.

Importance of TCP stream reassembly for file recovery.

Basics of verifying data integrity using cryptographic hashes.

Next Steps


Use tshark or NetworkMiner to automate file extraction from PCAPs.

Practice carving and identifying other file types like PDFs and executables.

Compare extracted hashes against public threat intel or malware databases.




