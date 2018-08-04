---
title: Configuring PingIdentity (SAML)
weight: 1200
---
_Available as of v2.0.7_

If your organization uses Ping Identity Provider (IdP) for user authentication, you can configure Rancher to allow your users to log in using their IdP credentials.

>**Prerequisites:**
>
>- You must have a [Ping IdP Server](https://www.pingidentity.com/) configured.
>- Export a `metadata.xml` file from your IdP Server. For more information, see the [PingIdentity documentation](https://documentation.pingidentity.com/pingfederate/pf83/index.shtml#concept_exportingMetadata.html).

1.	From the **Global** view, select **Security > Authentication** from the main menu.

1.	Select **PingIdentity**.

1.	Complete the **Configure Ping Account** form. Rancher can work with your Ping IdP that has Active Directory to manage the users and groups.
	
    1. **Display Name Field**: Enter the AD attribute that contains the display name of users (example: `displayName`).

	1. **User Name Field**: Enter the AD attribute that contains the user name/given name (example: `givenName`).
	
    1. **UID Field**: Enter an AD attribute that is unique to every user (example: `sAMAccountName`, `distinguishedName`).
	
    1. **Groups Field**: Make entries for managing group memberships (example: `memberOf`).
	
    1. **Rancher API Host**: Enter the URL for your Rancher Server.

	1. **Private Key** and **Certificate**: This is a key-certificate pair to create a secure shell between Rancher and your IdP. 
    
        You can generate one using an openssl command. For example:
    
        ```
        openssl req -x509 -newkey rsa:2048 -keyout myservice.key -out myservice.cert -days 365 -nodes -subj "/CN=myservice.example.com"
        ```
    1. **IDP-metadata**: The `metadata.xml` file that you [exported from your IdP server](https://documentation.pingidentity.com/pingfederate/pf83/index.shtml#concept_exportingMetadata.html).

 
1. After you complete the **Configure Ping Account** form, click **Authenticate with Ping**, which is at the bottom of the page. 

    Rancher redirects you to the IdP login page. Enter your AD credentials that are added to Ping IdP to validate your Rancher PingIdentity configuration.

    >**Note:** You may have to disable your popup blocker to see the IdP login page.

**Result:** Rancher is configured to work with PingIdentity. Your users can now sign into Rancher using their PingIdentity logins.