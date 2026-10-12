# how-to-add-a-federated-identity-on-microsoft-entra-id
This lab allows users to use their Google account to sign in to your directory. 

**Step 1: Configure Google as an identity provider (IdP)**
Sign in with your Google account at console.developers.google.com. Accept the terms of the service when prompted to do so. 

Click on Create project and fill in the necessary info: 

<img width="1560" height="862" alt="image" src="https://github.com/user-attachments/assets/0ad54baa-7d2b-4c9d-9a85-85047e518868" />

In the left menu, select OAuth consent screen under APIs & Services and select the Get Started button. Complete the following Project Configuration settings: 

a. App Information
b. Audience (Internal or External): If you select Internal, it'll only be available to users within your organization, while External will be avaialble to any user with a Google account 
c. Contact information

Once complete, select the Create button to continue.

Select the Create OAuth client button. Configure the following on the page: 

a. Application type: I chose Web Application.

b. Name: I left it as is for the web application. 

c. Within the Authorized JavaScript origins, select the + Add URI button and add this URL: https://microsoftonline.com 

d. Add three URIs within the Authorized redirect URIs: 

  First URI: https://microsoftonline.com
  Second URI: https://login.microsoftonline.com/te/**tenant ID**/oauth2/authresp
  Third URI: https://login.microsoftonline.com/te/**tenant ID**/oauth2/authresp
Note: Replace the "**tenant ID**" in the 2nd and 3rd URI with your tenant ID. To copy your tenant ID, go to Overview on Entra ID. 

Then select "Create"

Download the JSON file containing the Client ID and Client Secret for later use. 

<img width="830" height="754" alt="image" src="https://github.com/user-attachments/assets/474a90d3-1620-45b0-b90d-687c218c82da" />

**Step 2: Add a test user**
Go to Audience on the left menu > In the Test Users section of the page, choose + Add Users > Enter the Gmail account you are using for this lab. Then save.

**Step 3: Add authorized domain to Branding**

From the menu on the left, select the Branding item. Scroll to the very bottom of the page. In the Authorized domains section, add the domain microsoftonline.com. In the Developer contact information, add the email address you are using for this lab. Select Save: 

<img width="1112" height="703" alt="image" src="https://github.com/user-attachments/assets/be2ae409-0662-4be0-b46e-dbf3af33d842" />

**Step 4: Configure Azure to work with an external identity provider**

In the left navigation menu, under Entra ID, select External Identities > select All identity providers and select "configure" to make Google as an identity provider: 

<img width="1577" height="755" alt="image" src="https://github.com/user-attachments/assets/8079ee24-6f38-4fb4-8b77-fe8096693b0b" />

Add the client ID and Client secret from the JSON file you saved in step 1: 

<img width="1164" height="683" alt="image" src="https://github.com/user-attachments/assets/46eef3d4-428a-4383-bebc-d1f1a68f3d85" />

And now the Google account is configured to work as an IdP: 

<img width="1038" height="523" alt="image" src="https://github.com/user-attachments/assets/83a03490-0379-4472-9be8-5375cd5d98ff" />

**Step 5: Invite your test user account**
In the left navigation menu, under Entra ID, select Users > Open the All users menu item, then select + New User > Select Invite external user from the dropdown menu. Enter the information for the Gmail account you set up as a test user for the Google App in step 2. Select Review & Invite, then select Invite.

Open the Microsoft Invitation on behalf of in the Inbox. Select the Accept invitation link in the message. Once complete, the new account will see My Apps. 

**Step 6: Access Microsoft 365 with your Google account**
Once you have finished the external user invite process in step 5, log in to login.microsoftonline.com on a private tab. Select sign-in options > choose sign in to work or school account > enter your tenant domain name > enter the Google email address to have access to the Microsoft portal. 


