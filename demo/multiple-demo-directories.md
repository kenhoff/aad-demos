# Setting up multiple directories for demo purposes

Sometimes, setting up multiple directories for concurrent use is necessary, be it for demonstration, training, or testing use. It's not a trivial matter, but hopefully these steps will make the process more transparent. 

## Demo Setup

- create an MSA
- set up an azure subscription
  - (recommended) use an internal subscription
  - use the MSDN subscription
  - pay for/activate a trial azure subscription
- assign the MSA as the service admin for the subscription
- create a parent directory 
  - choose the name carefully - the users will be named after this directory
- create 200 users in that directory
  - recommended that this be done in bulk
  - set the user passwords, and set them to never expire
- assign each of those users as a coadmin of that azure subscription
- with each user, log in and create a directory
- (optional) activate the Azure AD trial for each directory
- (optional) configure each directory to your specifications

## Demo Walkthrough

- log in with one of the users
