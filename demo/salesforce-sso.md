<!---

Owner:		liviodlc
Owner DL:	adiampm
Last Reviewed:	2015.02.20

--->


# SSO to Salesforce with user provisioning

description

## Demo Setup

### Creating a Salesforce Demo Account

Rather than creating a “real” Salesforce account, it’s far easier and faster to create a developer account that behaves like a real account.

Of course there are a few caveats with respect to how many licenses you have:

**(image)**

You’re limited to one regular Salesforce user, but you have plenty of Chatter Free users.

1.	Go to https://developer.salesforce.com/
2.	Click Sign-up to create a new account, and follow the steps for creating and verifying your account.
3.	Once your account has been activated, go to https://www.salesforce.com/ and Log in
	a.	Note: Sign into salesforce.com, as opposed to developer.salesforce.com
4.	Under Administer, go to Domain Management > My Domain
**(image)**
5.	Choose a domain name for your demo account. It will be in the format of http://mydomain-dev-ed.my.salesforce.com
6.	You can now treat your developer account like a Salesforce account 


### Populating your Salesforce Account with Users

Several options:

1.	If you have an Azure AD tenant filled with users, you can set up automatic user provisioning to Salesforce:
https://msdn.microsoft.com/en-us/library/azure/dn308593.aspx#BKMK_ConfiguringAccountSync
2.	If you only need a handful of users, you can add them manually with their “Add Multiple Users” feature:
https://help.salesforce.com/HTViewHelpDoc?id=users_adding_multiple.htm&language=en_US

### Connecting your Salesforce Account to Azure AD

1.	Follow this guide:
https://msdn.microsoft.com/en-us/library/azure/dn308593.aspx#BKMK_ConfiguringAccountSync
2.	Now you need to assign users to the app. In the Azure Management Portal, you can do this by going to Your Directory > Applications > Salesforce > Users.
3.	Designate one user who will be used in the demo. Make sure you have the login credentials for that user. Assign that user to Salesforce.




## Demo Walkthrough

### Admin Side: show the current configuration

1.	In the Azure Management portal, go to Your Directory > Applications > Salesforce.
2.	On the Quick Start screen for Salesforce, click on “Configure single sign-on”. Walk through the pages of the wizard (which have already been filled out), and talk about how it’s been configured.
  a.	First page shows that we’re using federation-based SSO
  b.	Second page specified the sign-on URL for our Salesforce account.
  c.	Third page shows the configurations that had to be made on the Salesforce side to allow for SSO.
  d.	Exit the wizard.
3.	Click on “configure user provisioning”
  a.	First page shows the admin credentials that are used by Azure AD to provision and deprovision users into our Salesforce account.
  b.	Second page allows us to subscribe to email notifications for urgent provisioning errors.

### End-User Side: show SSO in action

1.	Go to http://myapps.microsoft.com
2.	Sign in as the end-user that you designated earlier for the demo.
3.	Click on the Salesforce icon to get SSO to Salesforce.
