# Configuration

## SMArt Email Configuration

Once you have completed the SMArt Email utility installation, the next step is configuration.

### Third-Party Email Configuration  

In preparation to use the SMArt Email utility, you may need to do a bit of third-party email information gathering and/or configuration.

####  Email Protocols

In order to leverage the SMArt Email utility, you will need to know which email protocol you use. The utility supports IMAP and POP email protocols.

#### Email Provider Settings

#### Microsoft Exchange Server

If you are using Microsoft Exchange Server, you will need to make sure that it is configured to use IMAP or POP protocol.

#### Gmail

If you are using Gmail, you will need to configure it to allow other applications (third-party apps) to connect to Gmail.

#### Encryption Levels

You will also need to know which encryption level you use. The utility supports SSL 3.0, TLS 1.1, and TLS 1.2 encryption levels.

#### Ports

Depending on the email protocol and the encryption level, you can set the port to 993, 465, 564, or any other acceptable port number.

### OpCon Configuration

Be sure that the external event credentials are configured using the command syntax and that the path to the MSGIN directory is configured in the INI file.

### Utility Configuration

####  Modifying Credentials

During installation, you should have already set both the OpCon and mailbox credentials. However, should you need to modify either set of credentials after installation, you can use the --credentials operation to do so.

#### Credential Syntax

To modify the credentials, use the following syntax:
smartemail.exe --credentials -user:[value] -password:[value] -opconuser:[value] -opconpassword:[value] (-inifile:[value])

### Credentials Arguments

The SMArt Email (Smartemail.exe) supports the following arguments:

| Argument | Required | Value |
| -------- | -------- | ----- |
| -credentials | Y | This parameter sets the user credentials and encrypts the username and passwords in the configuration file. The utility must run using this parameter only the first time in order to complete the configuration. This parameter sets the user credentials for the email server and OpCon user credentials as well. |
| -user | Y | This parameter is used in conjunction with the --credentials. It defines the username for the email inbox that will be monitored by the SMArt Email utility. |
| -password | Y | This parameter is used in conjunction with the --credentials. It defines the password for the email inbox that will be monitored by the SMArt Email utility. |
| -opconuser | Y | This parameter is used in conjunction with the --credentials. It defines the OpCon username that will run the events triggered by SMArt Email utility. |
| -opconpassword | Y | This parameter is used in conjunction with the --credentials. It defines the OpCon password for the user that will run the events triggered by SMArt Email utility. | 
| -inifile | N | This is an optional parameter used to specify a different configuration file. The default configuration file is SMArtEmail.ini, which is installed in the C:\ProgramData\OpConxps\SMArt Email directory. <br></br><br></br> Note: The root OpConxps data folder is likely hidden. To access this directory, type C:\ProgramData in your File Explorer address bar. | 

#### Updating Configuration Settings

Before moving on to the operation of the utility, you should update the settings in the SMArtEmail.ini file. All settings in the configuration file apply to the machine on which the file resides. The tables in this section describe all the configurable settings in the SMArtEmail.ini file.

##### General Settings

| [General] Settings | Default | Description |
| ------------------ | ------- | ----------- |
| MSGINDirectory | %PROGRAMDATA%\OpConxps\SAM\MSGIN | This parameter defines the path to which the SMArt Email will write the events. |
| OpConUser | Blank | This parameter defines the OpCon user with privileges to create Notification Events. |
| OpConUserPassword | Blank | This parameter defines the external event password for the defined OpConUser. |
| DeleteEmails | Match | This parameter deletes emails after processing. Three different settings are allowed. <br></br><br></br> - Values: Match, All, or None |
| DownloadEmails | True | This parameter downloads all the processed emails to a specific location if set to "TRUE." <br></br><br></br> - Values: True or False |
| DownloadFolder | %PROGRAMDATA%\OpConxps\SMArt Email\Received | This parameter defines the path to a folder the SMArt Email uses for processing emails that match one of the masks defined in the Smartemail.ini file. <br></br><br></br> Note: For best practices, it is recommended that you periodically clean up this folder using the SMADirectory utility. For more information, refer to [SMADirectory](https://help.smatechnologies.com/opcon/core/utilities/Command-line-Utilities/SMADirectory) in the Utilities online help. |
| ExitCodeForNoMatchingEmails | 0 | This parameter defines the exit code when no matching emails are found. <br></br><br></br> Note: Users who have already modified their job failure criteria to allow exit code 3 will not need to modify their jobs. Those users who want the job to fail when no matching emails are found will want to modify this setting to some non-zero value. New users and those upgrading SMArt Email will not need to modify the INI configuration file and can choose the default during install. |
| UseLastRunDate | True	| This parameter, if set to "TRUE," tracks then saves the most recently received email it processes in the LastRunDate value after each run. <br></br><br></br> - Values: True or False |
| LastRunDate | Blank | This value specifies the time stamp of the last email processed each time the program executes. On subsequent runs, only emails received on or after this date will be processed. <br></br><br></br> Note: If users wish to re-process emails from a certain date range, they can override this value by entering a valid date and time. For example:
1/1/2017 12:30:00 AM |

#### Mail Settings

The mail settings should be set up using the --credentials program switch since the utility requires the username and password to be encrypted. You should be able to refer to these values set up in the INI file after running the command appropriately.

| [Mail] Settings | Default	| Description |
| --------------- | ------- | ----------- |
| User | Blank | This parameter is used in conjunction with the --credentials program switch. It defines the username for the email inbox that will be monitored by the SMArt Email. |
| Password | Blank | This parameter is used in conjunction with the --credentials. It defines the password for the email inbox that will be monitored by the SMArt Email. |
| Server | Blank | This value should be the name of the email server to connect. <br></br><br></br> Note: If using TLS/SSL security, the value here should match the hostname of the certificate. Otherwise, you may receive a system error warning that the server certificate verification failed and that the connection aborted. |
| EmailProtocol | Blank | This value can be IMAP or POP. | 
| SecurityProtocol | Blank | - This value can be SSL, SSL2, TLS1, TLS1_1, or TLS1_2. <br></br><br></br> - The value specified here will serve as a minimum to meet during security protocol negotiation. The utility will attempt to negotiate with the highest available protocol above the defined minimum and fail only if it does not connect. <br></br><br></br> - The negotiations will be as follows: <br></br><br></br> --- For SSL - Try TLS options first, then connect with SSL3 if that does not succeed. <br></br> --- For SSL2 - Try TLS options first, then connect with SSL3 or SSL2 if that does not succeed. <br></br> --- For TLS1 - Allow TLS1.0 or above <br></br> --- For TLS1_1 - Allow TLS1.1 or above <br></br> --- For TLS1_2 - Allow only TLS1.2 |
| Port | Blank | This value should be the number of the port. Based on the EmailProtocol and SecurityProtocol, your port can change. | 
| SelfSignedCertificate | True | This parameter, if set to "TRUE," allows a self-signed certificate to be accepted. <br></br><br></br> - Values: True or False |

#### Audit Settings

The audit settings are used to configure audit log file format and event notification during the program processing. This section allows the configuration of audit logs based on acceptance or rejection. This section is completely optional and can be skipped if desired.

| [Audit] Settings | Default | Description |
| ---------------- | ------- | ----------- |
| AuditAcceptLogFile | Audit.log | This parameter is used to specify the log file to which accepted emails are logged. |
| LogAccepts | False | This parameter indicates whether or not to log accepted emails to the file. <br></br><br></br> -Values: True or False |
| LogAcceptFormat | SMArt Email - Message Accepted - From: [[SENDER]] Subject: [[SUBJECT]] | This is the format of the log message for an accepted email. |
| NotifyOnAccepts | False | This parameter indicates whether or not an email should be sent back to the initiator when there are strings defined in the configured SubjectLineMasks that match the subject line. <br></br><br></br> - Values: True or False |
| NotifyOnAcceptSubject	| SMArt Email - Message Accepted - From: [[SENDER]] Subject: [[SUBJECT]] | This is the subject of notification email that is sent on an accepted email. |
| NotifyOnAcceptBody | Email message was accepted and generated event: [[EVENT]] | This the body of notification email that is sent on an accepted email. |
| NotifyOnAcceptTo | [[SENDER]] | This is the recipient list for the accepted email notifications. <br></br><br></br> - For multiple users, use a semi-colon-separated list format. |
| AuditRejectLogFile | Audit.log | This parameter is used to specify the log file to which rejected emails are logged. |
| LogRejects | False | - This parameter indicates whether or not to log rejected emails to the file. An email is only considered rejected in 2 scenarios: <br></br><br></br> - The subject of the email matched one of the configurations, but for some other reason it did not generate a match. For example, the sender was not in the allowed list, the time was not in the allowed time frame, or it had no attachments to generate events for when ProcessAttachments is true. <br></br><br></br> - The email matched 0 configurations. <br></br><br></br> - Values: True or False |
| LogRejectFormat | SMArt Email - Message Rejected - From: [[SENDER]] Subject: [[SUBJECT]] | This is the format of the log message for a rejected email. |
| NotifyOnRejects | False | This parameter indicates whether or not an email should be sent back to the initiator when there are no strings defined in the configured SubjectLineMasks that match the subject line. <br></br><br></br> - Values: True or False |
NotifyOnRejectSubject | SMArt Email - Message Rejected - From: [[SENDER]] Subject: [[SUBJECT]] | This is the subject of the notification email that is sent on a rejected email. |
| NotifyOnRejectBody | Email message sent on [[DATE]] was rejected for reason: [[REASON]] | This is the body of notification email that is sent on a rejected email. |
| NotifyOnRejectTo | [[SENDER]] | This is the recipient list for rejected email notifications. <br></br><br></br> - For multiple users, use a semi-colon-separated list format. |
| RejectTimeframeMessage | Message received outside timeframe | This is the message to be used in the [[REASON]] token if an email is rejected due to its time frame. |
| RejectSenderMessage | Invalid Sender | This is the message to be used in the [[REASON]] token if the sender is not in the configured AllowedSenders list. |
| RejectNoMatchingSubjectMessage | No matching subjects found | This is the message to be used in the [[REASON]] token if the email does not match any existing configurations in the INI file. |
| RejectNoAttachmentMessage | No matching attachments found | This is the message to be used in the [[REASON]] token if the email does not have any attachments or any matching attachment, yet ProcessAtachment is TRUE and the Subject of the email matches.| 
| RejectEvent | N/A	| This parameter is used to generate an event when an email is rejected. Add here the event along with tokens from the email. If no value is present, it will not generate events on rejects. |
| LogOpConEvents | N/A | This parameter indicates whether or not the events generated by email should be logged. <br></br><br></br> - Values: True or False |
OpConEventLogFile | N/A	| This is parameter is used to specify the file name and path of the file to log events. |
| LogOpConEventFormat | Generated Event: [[Event]] | This is the format of the logged events. |

#### Tokens Settings

The tokens settings are used to define custom tokens that can be used throughout the [Configuration] section to avoid duplication of information.

| [Tokens] Settings	| Default | Description |
| ----------------- | ------- | ----------- | 
| Name | N/A | This parameter allows you to set the value of your custom token so it can be referenced in the configurations. |


#### Configuration# Settings

The Configuration section of the file contains one configuration section for each mask and event(s) to send. Name each section with the syntax [Configuration#].

| [Configuration#] Settings | Description |
| ------------------------- | ----------- |
| SubjectLineMask | This is the mask to search for on the subject line using regular expressions. |
| Event <br></br>Event2 <br></br> Event3 | - This should be one or more valid OpCon external event specification(s). <br></br><br></br> - SMArt Email supports a special token named [[SENDER]]. If you place this token in your event, SMArt Email will resolve the token to the name of the sending address from the email that caused the event to send. <br></br><br></br> - Note: Do not include the external user event credentials at the end of the event because the SMArt Email utility will automatically append the credentials that were entered during the initial credential set up. |
| AllowedSenders | This is a list of one or more semicolon-separated email addresses. <br></br><br></br> - Only when the sender is included in this list will this event be processed. <br></br><br></br> - Use "ALL" to use no filtering. <br></br><br></br> - Rejected emails will be logged to SMArtEmailRejections.log. <br></br><br></br> - To allow all users for a specific domain, use "any" as the email address. <br></br> --- For example, any@yourorg.com. |
| AllowedTimeFrame | - This is a 24-hour clock representation of when an email will be allowed for this configuration. <br></br><br></br> - The first four digits represent the hours and minutes of the beginning time. <br></br><br></br> - The last four digits represent the hours and minutes of the ending time. <br></br><br></br> - For example, 0000-2359 represents a time-frame of 12:00 AM through 11:59 PM. <br></br><br></br> - Rejected emails will be logged to SMArtEMailRejections.log. |
| ProcessBody | - This is an optional argument. <br></br><br></br> - This argument is supported for both Plain Text and HTML-formatted emails. <br></br><br></br> - The default value (if not specified) is "NO." A value of "NO" will force SMArt Email to operate in "classic" mode. Only the subject line is analyzed. <br></br><br></br> - This directive specifies that the body of the email should be included in the lines to be processed. It works in conjunction with QualifyingSubjectLine to determine exactly how the email is handled. If ProcessBody is set to "YES," the following processing is done: <br></br> --- If QualifyingSubjectLine is empty (or blank), each line in the body is evaluated against SubjectLineMask in addition to comparing the subject line against SubjectLineMask. Matches to the subject line or to line(s) in the body of the email can generate events. <br></br> --- If QualifyingSubjectLine contains a value, the subject line is compared to QualifyingSubjectLine. If the subject line is like QualifyingSubjectLine, each line in the body of the email is then compared against SubjectLineMask. Testing the subject line against QualifyingSubjectLine does NOT generate events. It is just to "filter out" unwanted matches between email bodies and mask lines. |
| QualifyingSubjectLine | - This is an optional argument. <br></br><br></br> - The default value (if not specified) is "". Refer to **ProcessBody** (above) to learn how this is used. |
| AttachmentMask | - This is an optional argument. <br></br><br></br> - This is the mask to search for an attachment name using regular expressions. |
| ProcessAttachments | This "true/false" switch should be used when you want to generate events based on **AttachmentMask**. |

### Configuration Examples to Generate Events

Provided in this section are configuration examples for generating different events.

#### Example for Generating an Event based on Subject

:::tip Example

This configuration will process any incoming emails from all senders all day. The program will try to match the email **subject** with "Test". If any email matches them, the program will generate an external event in OpCon.

```

[General]
MSGINDirectory=%PROGRAMDATA%\OpConxps\SAM\MSGIN
OpConUser=
OpConUserPassword=
DeleteEmails=MATCH
DownloadEmails=TRUE
DownloadFolder=%PROGRAMDATA%\OpConxps\SMArt Email\Received
 
[Mail]
User=
Password=
Server=
EmailProtocol=
SecurityProtocol=
Port=
 
[Audit]
AuditAcceptLogFile=Audit.log
LogAccepts=FALSE
LogAcceptFormat=SMArt Email - Message Accepted - From: [[SENDER]] Subject: [[SUBJECT]]
NotifyOnAccepts=FALSE
NotifyOnAcceptSubject=SMArt Email - Message Accepted - From: [[SENDER]] Subject: [[SUBJECT]]
NotifyOnAcceptBody=Email message was accepted and generated event: [[EVENT]]
NotifyOnAcceptTo=[[SENDER]]
 
AuditRejectLogFile=Audit.log
LogRejects=FALSE
LogRejectFormat=SMArt Email - Message Rejected - From: [[SENDER]] Subject: [[SUBJECT]]
NotifyOnRejects=FALSE
NotifyOnRejectSubject=SMArt Email - Message Rejected - From: [[SENDER]] Subject: [[SUBJECT]]
NotifyOnRejectBody=Email message sent on [[DATE]] was rejected for reason: [[REASON]]
NotifyOnRejectTo=[[SENDER]]
RejectTimeframeMessage=Message received outside timeframe
RejectSenderMessage=Invalid Sender
RejectNoMatchingSubjectMessage=No matching subjects found
RejectNoAttachmentMessage=No matching attachments found
RejectEvent=N\A
LogOpConEvents=N\A
OpConEventLogFile=N\A
LogOpConEventFormat=Generated Event: [[Event]]
 
[Tokens]
ADMINEMAIL=admin@anycompany.com
 
#---------------------------------
# Configuration events definitions
#---------------------------------
 
[Configuration1]
SubjectLineMask=Test
Event=$CONSOLE:DISPLAY,the test passed
AllowedSenders=[[ADMINEMAIL]]
AllowedTimeFrame=0000-2400

```

:::

#### Example for Generating an Event based on Attachment

:::tip Example

This configuration will process any incoming emails from all senders all day. The program will try to match the email **subject** with "Test" and the name of any **attachment** with "SMArtEmail Test". If both conditions are met, then the program will download the emails and generate an external event in OpCon.

```

[General]
MSGINDirectory=%PROGRAMDATA%\OpConxps\SAM\MSGIN
OpConUser=
OpConUserPassword=
DeleteEmails=NONE
SendRejectionNotice=FALSE
SendAcceptedNotice=FALSE
DownloadEmails=TRUE
DownloadFolder=%PROGRAMDATA%\OpConxps\SMArt Email\Received
 
[Mail]
User=
Password=
Server=
EmailProtocol=
SecurityProtocol=
Port=
 
[Audit]
AuditAcceptLogFile=Audit.log
LogAccepts=FALSE
LogAcceptFormat=SMArt Email - Message Accepted - From: [[SENDER]] Subject: [[SUBJECT]]
NotifyOnAccepts=FALSE
NotifyOnAcceptSubject=SMArt Email - Message Accepted - From: [[SENDER]] Subject: [[SUBJECT]]
NotifyOnAcceptBody=Email message was accepted and generated event: [[EVENT]]
NotifyOnAcceptTo=[[SENDER]]
 
AuditRejectLogFile=Audit.log
LogRejects=FALSE
LogRejectFormat=SMArt Email - Message Rejected - From: [[SENDER]] Subject: [[SUBJECT]]
NotifyOnRejects=FALSE
NotifyOnRejectSubject=SMArt Email - Message Rejected - From: [[SENDER]] Subject: [[SUBJECT]]
NotifyOnRejectBody=Email message sent on [[DATE]] was rejected for reason: [[REASON]]
NotifyOnRejectTo=[[SENDER]]
RejectTimeframeMessage=Message received outside timeframe
RejectSenderMessage=Invalid Sender
RejectNoMatchingSubjectMessage=No matching subjects found
RejectNoAttachmentMessage=No matching attachments found
RejectEvent=N/A
LogOpConEvents=N/A
OpConEventLogFile=N/A
LogOpConEventFormat=Generated Event: [[Event]]
 
[Tokens]
ADMINEMAIL=admin@anycompany.com
 
#---------------------------------
# Configuration events definitions
#---------------------------------
 
[Configuration1]
SubjectLineMask=Test
Event=$CONSOLE:DISPLAY,the test passed
AllowedSenders=[[ADMINEMAIL]]
AllowedTimeFrame=0000-2400
AttachmentMask=SMArtEmail Test
ProcessAttachments=True

```

:::

#### Example for Generating an Event based on Body

:::tip Example

This configuration will process any incoming emails from all senders all day. The program will try to match the email **subject** with "Test". Additionally, the program will try to match **each and every line in the body** of the email with the word "Test". If both conditions are met, then the program will generate an external event in OpCon.
 
``` 
[General]
MSGINDirectory=%PROGRAMDATA%\OpConxps\SAM\MSGIN
OpConUser=
OpConUserPassword=
DeleteEmails=MATCH
SendRejectionNotice=FALSE
SendAcceptedNotice=FALSE
DownloadEmails=TRUE
DownloadFolder=%PROGRAMDATA%\OpConxps\SMArt Email\Received
 
[Mail]
User=
Password=
Server=
EmailProtocol=
SecurityProtocol=
Port=
 
[Audit]
AuditAcceptLogFile=Audit.log
LogAccepts=FALSE
LogAcceptFormat=SMArt Email - Message Accepted - From: [[SENDER]] Subject: [[SUBJECT]]
NotifyOnAccepts=FALSE
NotifyOnAcceptSubject=SMArt Email - Message Accepted - From: [[SENDER]] Subject: [[SUBJECT]]
NotifyOnAcceptBody=Email message was accepted and generated event: [[EVENT]]
NotifyOnAcceptTo=[[SENDER]]
 
AuditRejectLogFile=Audit.log
LogRejects=FALSE
LogRejectFormat=SMArt Email - Message Rejected - From: [[SENDER]] Subject: [[SUBJECT]]
NotifyOnRejects=FALSE
NotifyOnRejectSubject=SMArt Email - Message Rejected - From: [[SENDER]] Subject: [[SUBJECT]]
NotifyOnRejectBody=Email message sent on [[DATE]] was rejected for reason: [[REASON]]
NotifyOnRejectTo=[[SENDER]]
RejectTimeframeMessage=Message received outside timeframe
RejectSenderMessage=Invalid Sender
RejectNoMatchingSubjectMessage=No matching subjects found
RejectNoAttachmentMessage=No matching attachments found
RejectEvent=N/A
LogOpConEvents=N/A
OpConEventLogFile=N/A
LogOpConEventFormat=Generated Event: [[Event]]
 
[Tokens]
ADMINEMAIL=admin@anycompany.com
 
#---------------------------------
# Configuration events definitions
#---------------------------------
 
[Configuration1]
SubjectLineMask=Test
Event=$CONSOLE:DISPLAY,the test passed
AllowedSenders=[[ADMINEMAIL]]
AllowedTimeFrame=0000-2400
ProcessBody=Yes
```

:::

#### Regular Expressions

SMArt Email supports "masks" as part of the Subject line that can be captured and used in the event. You can create the mask using Regular Expression in the SMArtEmail.ini file. To get started, you need to know that:

* An expression in parenthesis is "captured" for use in the event and will replace the string [[1]] in the event. The second expression in parenthesis will replace [[2]] and so on.
    * Expressions in parentheses can be numbers or strings. For example:
        * The expression \S+ will match one white-space delimited word.
        * The expression [0-9]+ will capture a number with one or more digits and a decimal.

:::tip Example

If the mask is:
```OpCon/xps: (\S+) total = ([0-9]+\.[0-9]+)```

If an email was received that had a subject line that looked like:
```OpCon/xps: ACHBalanceTotal total = 149926.22```

The first captured argument would be ```(\S+)``` or ```"ACHBalanceTotal"```.
The second captured argument would be ([0-9]+\.[0-9]+) or ```"149926.22"```.

If the event to generate was defined as:
```$TOKEN:SET,[[1]],[[2]]```

The event that would be sent to OpCon would look like:
```$TOKEN:SET,ACHBalanceTotal,149926.22```

:::

### Job Output

All information produced by the job is available in the job output and can be retrieved using the View Job Output feature. For more information, refer to Viewing Job Output in the Enterprise Manager online help.