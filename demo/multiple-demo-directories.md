<!---
Owner:          kenhoff
Owner DL:       adiampm
Last Reviewed:  2015.02.23
--->

# Setting up multiple demo directories

Sometimes setting up multiple directories for concurrent use is necessary, either for demonstration, training, or testing. It's not a trivial matter; there's a complicated combination of subscriptions, admins, and licenses that are needed. These steps will make the process more transparent. 

Because a user must be associated with an Azure Subscription in order to sign into the Azure Management Portal, and it is impractical and insecure to create a large number of Azure Subscriptions, we will be creating one Azure Subscription with every demo admin as a co-administrator of that Azure Subscription.

If you run into issues, or you'd like guidance with the process, feel free to get in touch at kenhoff@microsoft.com.

## Demo Setup

Note: "Parent" and "Child" directories are functionally identical. Conceptually, each demo directory is a "child" directory, while all of the admins are mastered in the "parent" directory.

- [create an MSA](https://signup.live.com)
- set up an azure subscription - 3 options:
  - (recommended) use an [internal subscription](https://azuremsregistration.cloudapp.net/Default.aspx)
  - use the [MSDN subscription](http://azure.microsoft.com/en-us/pricing/member-offers/msdn-benefits/)
  - pay for/activate a [trial azure subscription](http://azure.microsoft.com/en-us/pricing/free-trial/) (credit card needed)
  - note that it will be possible for each of the demo directory admins to create azure resources (will incur costs)
    - to avoid this, it's possible to use a $0 subscription, but you'll have to contact Eran Dvir about that
- assign the MSA as the service admin for the subscription
  - at https://account.windowsazure.com, Subscriptions -> <your subscription> -> Edit subscription details -> set Service Administrator to the MSA's email
- sign into the [management portal](https://manage.windowsazure.com/) with the MSA
- create a parent directory (New -> App Services -> Active Directory -> Directory -> Custom Create)
  - choose the name carefully - the users will be named after this directory
- create 200 users in that parent directory
  - you'll need to use [LCA-approved fictitious names](https://microsoft.sharepoint.com/sites/lcaweb/Pages/Applications/FictitiousNameFinder.aspx)
  - (recommended) this can be [done in bulk](http://blogs.technet.com/b/heyscriptingguy/archive/2014/08/04/use-powershell-to-create-bulk-users-for-office-365.aspx) 
  - set the user passwords (recommended: ```Microsoft123!``` - your users will be typing this a lot, and it's more useful to be easy than secure), and set them to never expire
- assign each of those users as a coadmin of that azure subscription (Azure Management Portal -> Settings -> Administrators -> Add)
- with each user, log in and create a child directory
  - if you need to be able to log into a different management portal (e.g. O365, Intune), then you'll need to create an additional global admin in the child directory
- (optional) activate the Azure AD trial for each child directory (Azure Management Portal -> (your child directory) -> Licenses -> Activate)
- (optional) configure each child directory to your specifications
  - check out some of the other [demo scripts available](/demo)

## Demo Walkthrough

- log in with one of the admin users and note that only the child directory can be accessed
- provide your users with the credentials to access the demo directories
