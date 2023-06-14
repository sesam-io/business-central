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
  "code": "NOK"
}
```

## Customers
Note that ``displayName`` is not actually required by the API, but without a ``displayName`` it will not show up in the UI.

Minimal object:
```
{
  "displayName": "Some customer"
}
```

## Employee
Minimal object:
```
{
  "givenName": "Ante",
  "surname": "Testson"
}
```

## Paymentterms
Minimal object:
```
{

}
```

## Paymentmethods
Minimal object:
```
{

}
```

## Vendors
Minimal object:
```
{
  "displayName": "Leverandør 2"
}
```


