# X.509 Certificate Analysis with Splunk

This project demonstrates how to identify and verify the most recent X.509 certificate using Splunk logs from a CTF challenge.

## Overview

I used Splunk to pivot from the `x509` log to the `files` log using the certificate `id` as a reference, in order to find the correct SHA1 fingerprint of the most recent certificate.

## Commands Used

```splunk

index=ctf path=x509 example.com
This returned certificate metadata, including the id field (e.g., FNZ7Z22WzAofFQvsZf).


index=ctf path=files fuid=FNZ7Z22WzAofFQvsZf
This let me pivot to the files log and extract the SHA1 hash.

Result
Final SHA1 hash:

19594b811f9f867db68efabcc7135852e63fd7da
