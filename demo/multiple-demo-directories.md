<!---
Owner:          kenhoff
Owner DL:       adiampm
Last Reviewed:  2015.02.23
--->

# Setting up multiple demo directories

Sometimes setting up multiple directories for concurrent use is necessary, either for demonstration, training, or testing. It's not a trivial matter; there's a complicated combination of subscriptions, admins, and licenses that are needed. These steps will make the process more transparent. 

If you run into issues, or you'd like guidance with the process, feel free to get in touch at kenhoff@microsoft.com.

## Demo Setup

Difference between parent and child directories: no technical difference, just conceptual

- create an MSA
- set up an azure subscription
  - (recommended) use an [internal subscription](https://azuremsregistration.cloudapp.net/Default.aspx)
  - use the [MSDN subscription](http://azure.microsoft.com/en-us/pricing/member-offers/msdn-benefits/)
  - pay for/activate a [trial azure subscription](http://azure.microsoft.com/en-us/pricing/free-trial/) (credit card needed)
  - note that it will be possible for each of the demo directory admins to create azure resources (will incur costs)
    - to avoid this, it's possible to use a $0 subscription, but you'll have to contact Eran Dvir about that
- assign the MSA as the service admin for the subscription
- sign into the management portal with the MSA
- create a parent directory 
  - choose the name carefully - the users will be named after this directory
- create 200 users in that parent directory
  - (recommended) this can be done in bulk (powershell link)
  - set the user passwords (recommended: ```Microsoft123!```), and set them to never expire
- assign each of those users as a coadmin of that azure subscription
- with each user, log in and create a child directory
  - if you need to be able to log into a different management portal (e.g. O365, Intune), then you'll need to create an additional global admin in the child directory
- (optional) activate the Azure AD trial for each child directory
- (optional) configure each child directory to your specifications

## Demo Walkthrough

- log in with one of the admin users and note that only the child directory can be accessed
