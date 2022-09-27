# Operation

## Operation Syntax

After the configuration have been updated and the credentials are set (using the --credential operation), the program is ready to run. To run the utility, use the following operation syntax:

```smartemail.exe ((--msal (--renewMsalToken (--renewTokenSilent | --doNotSaveAccount))) | ((-server:[value]) (-port:[value]) --[pop|imap] (--[ssl|tls1_1|tls1_2])) (--delete)```

:::info Note 

[|] indicates mutually exclusive options.

:::

## Operation Arguments

The SMArt Email (Smartemail.exe) supports the following arguments:

| Argument | Required? | Value |
| -------- | --------- | ----- |
| -server | Y | Use this argument to define the email server IP address or hostname. You may specify this also directly in the configuration file. |
| -port | Y | Use this argument to define the port number for the email server. It defaults to standard ports and can also be specified in the configuration file. | 
| --pop | Y | Use this argument to define a POP email protocol. |
| --imap | Y | Use this argument to define an IMAP email protocol. |
| --ssl | N | Use this argument to use SSL 3.0 with a selected mail protocol. The port number has to apply to this level of encryption; otherwise, the communication will not be established. |
| --tls1_1 | N | Use this argument to use TLS 1.1 with a selected mail protocol. The port number has to apply to this level of encryption; otherwise, the communication will not be established. |
| --tls1_2 | N | Use this argument to use TLS 1.2 with a selected mail protocol. The port number has to apply to this level of encryption; otherwise, the communication will not be established. |
| --delete | N |Use this argument if you want to delete emails after processing. This option only works when using the IMAP email protocol. |
| --msal | Y | Use this argument to define a MSAL email protocol. |
| --renewMsalToken | N | Used to interactively acquire a new token and/or assign a different account to be used by SMArtEmail. |
| --renewTokenSilent | N | Used in conjunction with --renewMsalToken, if the refresh token is still valid (~1 week) this can be used to refresh the token and keep it alive longer. |
| --doNotSaveAccount | N | Used in conjunction with --renewMsalToken, if you would like to prevent storing a token to an account on this machine. Typically used to prevent saving an access token to an Administrator's email. |