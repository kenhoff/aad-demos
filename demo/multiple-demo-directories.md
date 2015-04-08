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

### Creating the parent directory
- Email Eran Dvir - ask him for a 1-user IUR key.
- Navigate to http://aka.ms/activateAAD and begin the sign up process. This will create the parent directory, the global admin of your parent directory, and make the parent directory the default directory of a $0 Azure subscription.
  - You may want to choose your directory name carefully; your users will have to sign in with usernames like admin123@superlongdirectoryname.onmicrosoft.com  

#### Alternative method:

- [create an MSA](https://signup.live.com)
- set up an azure subscription - 3 options:
  - (recommended) use an [internal subscription](https://azuremsregistration.cloudapp.net/Default.aspx)
  - use the [MSDN subscription](http://azure.microsoft.com/en-us/pricing/member-offers/msdn-benefits/)
  - pay for/activate a [trial azure subscription](http://azure.microsoft.com/en-us/pricing/free-trial/) (credit card needed)
  - note that it will be possible for each of the demo directory admins to create azure resources (will incur costs)
    - to avoid this, it's possible to use a $0 subscription, but you'll have to contact Eran Dvir about that
- assign the MSA as the service admin for the subscription
  - at https://account.windowsazure.com, Subscriptions -> {your subscription} -> Edit subscription details -> set Service Administrator to the MSA's email
- sign into the [management portal](https://manage.windowsazure.com/) with the MSA
- create a parent directory (New -> App Services -> Active Directory -> Directory -> Custom Create)
  - choose the name carefully - the users will be named after this directory
 
### Creating the users in your parent directory (which will be the admins for the child directory)

- create 200 users in that parent directory
  - you'll need to use [LCA-approved fictitious names](https://microsoft.sharepoint.com/sites/lcaweb/Pages/Applications/FictitiousNameFinder.aspx)
  - (recommended) this can be [done in bulk](http://blogs.technet.com/b/heyscriptingguy/archive/2014/08/04/use-powershell-to-create-bulk-users-for-office-365.aspx) 
  - set the user passwords (recommended: ```Microsoft123!``` - your users will be typing this a lot, and it's more useful to be easy than secure), and set them to never expire

### Making those users able to log into the Azure Management Portal

- assign each of those users as a coadmin of that azure subscription (Azure Management Portal -> Settings (left navigation) -> Administrators -> Add)
 
### Creating the child directory for each child admin

- with each user, log in and create a child directory

#### Additional step: creating another admin to log into other management portals  

  - if you need to be able to log into a different management portal (e.g. O365, Intune), then you'll need to create an additional global admin in the child directory
  
### Activating trials on each directory
- (optional) activate the Azure AD trial for each child directory (Azure Management Portal -> {your child directory} -> Licenses -> Activate)
- [o365](https://microsoft.sharepoint.com/teams/office365demos/Lists/Demo%20Account%20Extension%20Requests/Item/newifs.aspx?List=32418e74-18aa-48e4-a257-b061e0c7ab4d&Source=https%3A%2F%2Fmicrosoft%2Esharepoint%2Ecom%2Fteams%2Foffice365demos%2FLists%2FDemo%20Account%20Extension%20Requests&Web=f9ec1306-1519-4a4d-a132-a5077e9f900e&InitialTabId=Ribbon%2ERead&VisibilityContext=WSSTabPersistence#InplviewHashdc12fa55-37ed-4b7e-bc8e-75640c2a74e7=ShowInGrid%3DTrue)

### Configuring each directory with the right data and enabled features

- (optional) configure each child directory to your specifications
  - check out some of the other [demo scripts available](/demo)
- verify your corp domain: [msinterface](http://msinterface/form.aspx?ID=3890)
<!---
[4/8/2015 3:39 PM] Andreas Kjellman: 
DNS configuration instructions for MSInterface
 
1.       Please visit http://msinterface/form.aspx?ID=3890 (if this opens up the home page, please try clicking the link again)
2.       In the “Request Categories” dropdown choose “Non AD Integrated (Internet Facing) Request” 
3.      Enter “GFS-Domains” in the “MSIdentity Application Name” field
4.      Complete the required fields marked with *
5.      Once you have completed the form, click “Submit Form”
--->


## Demo Walkthrough

- log in with one of the admin users and note that only the child directory can be accessed
- provide your users with the credentials to access the demo directories
