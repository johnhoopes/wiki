<!-- TITLE: Regin -->
<!-- SUBTITLE: A quick summary of Regin -->

# Information
Author: NSA
Timeline:  per wikipedia 2003 -> 2018.  
Highlights: 
* Modular
* Own encrypted file system in one file
* 
# References
https://en.wikipedia.org/wiki/Regin_(malware)
https://media.kasperskycontenthub.com/wp-content/uploads/sites/43/2018/03/08070305/Kaspersky_Lab_whitepaper_Regin_platform_eng.pdf

# Stage 1 - Loader
the ZeroAccess gang implemented a very similar loading mechanism

All the stage 1 modules for 64-bit systems were signed with fake digital certificates. The two fake certificates we identified are supposed to belong to Microsoft Corporation and Broadcom Corporation. During the infection phase, the attackers inject a trusted CA in the certificates chain, which instructs the system to trust their signatures.

