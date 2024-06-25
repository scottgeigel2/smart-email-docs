# Installation

## Requirements

Before beginning the installation, ensure that the system requirements are met. The supported software include:

* Any supported version of Windows with .NET Framework 4.8 installed.
* A supported version of the MSLSAM installed on the machine.

## New Installation

Complete the procedure in this section for installation of the SMArt Email utility.

### To install the utility for **POP** and **IMAP**:

1. Log in to the Windows machine as a Local Administrator.

:::info Note

The Local Administrator account used should be a domain user that is included as a Batch User in OpCon. This is the user that the MSAL token is created for and should be the account that runs any SMArt Email Job in OpCon.

:::

2. Download the SMArt Email utility installation file from the [files.smatechnologies.com](https://files.smatechnologies.com/)  site.
3. Enter your valid username and password and click Login.
4. Navigate to **Root Folder/SMArt Email**.
5. Double-click the **SMA OpCon SMArt Email Install.exe**. The Select Language screen displays.
6. Select the desired language for the installation screens and click **OK**. The Welcome screen displays.
7. Click **Next**. The Destination Folder screen displays.
8. Choose your Destination Folder and click **Next**. The **Configure SMA MSGIN Directory** screen displays.
9. Choose the path to the SAM's MSGIN directory where external events are submitted or accept the default path.
10. Click **Next**. The **Configure OpCon User** screen displays.
11. *(Required)* Enter the OpCon user used to submit external events.
12. *(Required)* Enter the password of the OpCon user used to submit external events.
13. Click **Next**. The **Configure Email Server** displays.
14. Select the protocol used to connect to your email server: **IMAP** or **POP**.
15. Select the encryption level used to connect to your email server: **SSL**, **TLS1_1**, or **TLS1_2**.
16. Enter the name of the email server to connect.
17. Enter the port number.
18. *(Required)* Enter the user used to connect to the email server.
19. *(Required)* Enter the password used to connect to the email server.

:::info Note 

You can configure both the External Event authentication information and the Email Server connection information during install or after install by updating your configuration file. Refer to [Utility Configuration](./configuration) to learn more about modifying the configuration file.

:::

20. Click **Next**. The **Setup Type** screen displays.
21. Select the Complete option and click **Next**. The **Ready to Install the Program** screen displays.
22. Click **Install**.
23. Wait while the installation completes. This may take a few minutes.
24. Click **Finish** on the **InstallShield Wizard Completed** screen.


### To install the utility for **MSAL**:

1. Log in to the Windows machine as a Local Administrator.
2. Download the SMArt Email utility installation file, version 20 or above, from the [files.smatechnologies.com](https://files.smatechnologies.com/)  site.
3. Enter your valid username and password and click Login.
4. Navigate to **Root Folder/SMArt Email**.
5. Double-click the **SMA OpCon SMArt Email Install.exe**. The Select Language screen displays.
6. Select the desired language for the installation screens and click **OK**. The Welcome screen displays.
7. Click **Next**. The Destination Folder screen displays.
8. Choose your Destination Folder and click **Next**. The **Configure SMA MSGIN Directory** screen displays.
9. Choose the path to the SAM's MSGIN directory where external events are submitted or accept the default path.
10. Click **Next**. The **Configure OpCon User** screen displays.
11. *(Required)* Enter the OpCon user used to submit external events.
12. *(Required)* Enter the password of the OpCon user used to submit external events.
13. Click **Next**. The **Configure Email Server** displays.
14. Select **MSAL**.

#### Setup if the SMArtEmail email account also has administrator privileges for Outlook
1. Click **Next**
2. A web browser will take you to a Microsoft Login Page, select your SMArtEmail account
3. Review the claims requested and click the checkbox to give administrator consent 

#### Setup if an Administrator needs to grant access for the SMArtEmail email account
1. Click the checkbox that says "Do Not Associate or Store Account"
2. A web browser will take you to a Microsoft Login Page, select your SMArtEmail account
3. Review the claims requested and click the checkbox to give administrator consent 
4. Open a command prompt and navigate to SMArtEmail's installation directory
5. Run: SMArtEmail.exe --renewMsalToken
6. A web browser will take you to a Microsoft Login Page, select your SMArtEmail account


## Upgrade Installation
To upgrade the SMArt Email utility, simply install the new package to the same directory as the previous installation. The installation package will preserve your configuration files automatically.

## Silent Mode

To learn how to install the SMArt Email utility in silent mode, refer to [Silent Mode](https://help.smatechnologies.com/opcon/core/installation/components#silent-mode) in the **OpCon Installation** online help.
