# Microsoft Dynamics 365 Business Central connector
Repository for the Microsoft Dynamics 365 Business Central connector

The current connector is using the API as part of the wider Microsoft Graph API, this is still in beta, but seems to work. When doing `sesam upload/authentication` using sesam-py, first time you use the authorization screen to send a request for approval the Azure AD admin (Henrik/support), and then after it's approved, you have to do `upload/authenticate` again. The second time, all the secrets should be picked up and uploaded to your node successfully. 
