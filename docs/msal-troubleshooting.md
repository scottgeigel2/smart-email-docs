# MSAL Troubleshooting

The MSAL option will only work for email servers hosted by Microsoft. A private Exchange server will still need to use IMAP and POP.
If a mistake occurs with setting up SMArtEmail, that leads to Permission Errors, then you may need to reset and retry the setup.

## Remove SMArtEmail from your Enterprise Applications
1. Go to portal.azure.com
2. Navigate to Enterprise Applications and select SMArtEmail
3. Go to the properties blade
4. Click the delete button and remove SMArtEmail

## Clear the MSAL Token Cache
1. Navigate to your AppData\Local (e.g. C:\Users\myUser\AppData\Local\)
2. Delete the file msal.smatechnologies.cache

## If SMArtEmail is not used frequently

The Token SMArtEmail acquires should be renewable for up to a week but the expiration will reset every time SMArtEmail connects to your account. If SMArtEmail does not run frequently, you can setup a job in OpCon to run: SMArtEmail.exe --msal --renewMsalToken --renewTokenSilent.
This will prevent you from needing to go through interactive authorization again.