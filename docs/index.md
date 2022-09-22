---
slug: '/'
sidebar_label: 'Smart Email Overview'
---

# SMA Smart Email Utility 

The SMArt Email utility periodically checks a user's email to send OpCon events. Based on the contents of a configuration file, masks can be checked against the Subject of each email. If the Subject line of an email matches one of the predefined masks, an event will be generated.
 
The SMArt Email utility:

* Leverages TLS 1.1 and 1.2 security in its messaging
* Supports multiple-line matching in the subject line or within the body of an email using regular expressions
* Allows you to choose whether or not to download the processed emails
* Allows you to select whether to download attachments and generate events based on attachment names.

## Scope

This online help provides basic and advanced, conceptual and procedural information for running the SMArt Email utility.

## Audience

This online help is written for users with a working knowledge of the email server configuration and a basic understanding of automated job scheduling concepts.

## Microsoft Compliance

To meet compliance as a Microsoft Certified Development Partner, SMA Technologies has standardized on storing application data files in the ProgramData directory by default when you install to the system drive. For more information, refer to [Determining Installation Locations](https://help.smatechnologies.com/opcon/core/installation/system-requirements#determining-installation-locations) in the OpCon Installation online help.

## Windows File Names

Some systems will not allow long file names (e.g., ```C:\Program Files\OpConxps\```). To work around this, revert to method 8.3. In this method, the 7th character becomes a tilde followed by a 1 (e.g., ```C:\Progra~1\OpConxps\```).