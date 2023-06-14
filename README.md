# Microsoft Dynamics 365 Business Central connector
Repository for the Microsoft Dynamics 365 Business Central connector

The current connector is using the API as part of the wider Microsoft Graph API, this is still in beta, but seems to work. When doing `sesam upload/authentication` using sesam-py, first time you use the authorization screen to send a request for approval the Azure AD admin (Henrik/support), and then after it's approved, you have to do `upload/authenticate` again. The second time, all the secrets should be picked up and uploaded to your node successfully. 

A note/caveat on the API
------------------------

Currently, this connector uses several undocumented MS Graph APIs (and the documented ones are in "beta" and has been since 2019).
This means that it could stop working, and there's no support from MS if they do.

How to obtain an "account_id"
-----------------------------

Most of the pipes in this connector need an "account_id" which is really a "CompanyID" from the "companies" pipe.
To get it, do a `sesam upload` (possibly twice) and then run the "xxxxxx-companies-collect" pipe and copy the "id" 
from the only entity  it produces. Enter this as "account_id" in .authconfig.


# Datatypes
## Currencies
Minimal object:
```
{
  "amountDecimalPlaces": "2:2",
  "amountRoundingPrecision": 0.01,
  "code": "TD",
  "displayName": "Test dollar",
  "symbol": "$"
}
```

## Employee
Minimal object:
```
{
  "addressLine1": "677 Fifth Avenue",
  "birthDate": "1973-12-12",
  "employmentDate": "2001-06-01",
  "givenName": "Annette",
  "jobTitle": "Secretary",
  "mobilePhone": "4564-4564-7831",
  "number": "AH",
  "personalEmail": "ah@contoso.com",
  "phoneNumber": "4465-4899-4643",
  "status": "Active",
  "surname": "Hill"
}
```
