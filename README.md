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
## Company
Read-only, represents the tenant. Contains company ID which is required for fetching other datatypes.


## Currencies
Insert:

Minimal object:
```
{
  "code": "NOK"
}
```

Update:

```
  "$based_on_properties": [
    "amountDecimalPlaces",
    "amountRoundingPrecision",
    "code",
    "displayName",
    "symbol",
    "lastModifiedDateTime",
    "id"
  ],
```

## Customers
Note that ``displayName`` is not actually required by the API, but without a ``displayName`` it will not show up in the UI.

Insert:

Minimal object:
```
{
  "displayName": "Some customer"
}
```

Update:
```
    "$based_on_properties": [
        "type",
        "blocked",
        "currencyCode",
        "currencyId",
        "displayName",
        "email",
        "id",
        "lastModifiedDateTime",
        "number",
        "paymentMethodId",
        "paymentTermsId",
        "shipmentMethodId",
        "taxAreaDisplayName",
        "taxAreaId",
        "taxLiable",
        "taxRegistrationNumber"
       ],
```

## Countriesregions
Update:
```
    "$based_on_properties": [
        "addressFormat",
        "code",
        "displayName",
        "id",
        "lastModifiedDateTime"
       ]
```

Insert:

Minimal object:
```
{
  "code": "EB"
}
```

## Dimensions
Does not support updates or inserts.

## Dimensionvalues
Does not support updates or inserts.


## Employee
Minimal object:
```
{
  "givenName": "Ante",
  "surname": "Testson"
}
```

## Paymentterms
Insert:

Minimal object:
```
{
   "code": "3 DAGER"
}
```

Update:
```
    "$based_on_properties": [
      "calculateDiscountOnCreditMemos",
      "code",
      "discountPercent",
      "displayName",
      "dueDateCalculation",
      "id",
      "lastModifiedDateTime"
    ]
```

## Paymentmethods
Insert:

Minimal object:
```
{
  "code": "ACCOUNT",
  "displayName": "Betaling",
}
```

Update:
```
    "$based_on_properties": [
      "code",
      "displayName",
      "id",
      "lastModifiedDateTime"
    ]
```

## Vendors
Insert:

Minimal object:
```
{
  "displayName": "Leverandør 2"
}
```

Update:
```
    "$based_on_properties": [
      "balance",
      "blocked",
      "currencyCode",
      "currencyCode",
      "currencyId",
      "displayName",
      "id",
      "lastModifiedDateTime",
      "number",
      "paymentMethodId",
      "paymentTermsId",
      "taxLiable"
    ]
```


## Salesorders
Insert:

Minimal object:
```
  {
    "customerNumber": "50000"
  }
```


Update:
```
  "$based_on_properties": [
    "billToCustomerId",
    "billToCustomerNumber",
    "billToName",
    "currencyCode",
    "currencyId",
    "id",
    "customerName",
    "customerNumber",
    "customerId",
    "discountAmount",
    "discountAppliedBeforeTax",
    "email",
    "externalDocumentNumber",
    "fullyShipped",
    "number",
    "orderDate",
    "partialShipping",
    "paymentTermsId",
    "pricesIncludeTax",
    "requestedDeliveryDate",
    "salesperson",
    "shipToContact",
    "shipToName",
    "status",
    "totalAmountExcludingTax",
    "totalAmountIncludingTax",
    "totalTaxAmount"
  ]
```

## Salesorderlines
Insert:

Minimal object:
```
  {
    "itemId": "d66eb5d3-55e9-ed11-8850-6045bdc8c1cc",
    "lineType": "Item"  
  }
```

Update:
```
    "$based_on_properties": [
      "description",
      "accountId",
      "amountExcludingTax",
      "amountIncludingTax",
      "discountAmount",
      "discountAppliedBeforeTax",
      "discountPercent",
      "documentId",
      "id",
      "invoiceDiscountAllocation",
      "invoiceQuantity",
      "invoicedQuantity",
      "itemId",
      "lineType",
      "netAmount",
      "netAmountIncludingTax",
      "netTaxAmount",
      "quantity",
      "sequence",
      "shipQuantity",
      "shipmentDate",
      "shippedQuantity",
      "taxCode",
      "taxPercent",
      "totalTaxAmount",
      "unitOfMeasureId",
      "unitPrice"
    ]
```

## Items
Insert:

Minimal object:
```
  {
    "displayName": "Test",
    "itemCategoryId": "c46eb5d3-55e9-ed11-8850-6045bdc8c1cc",
    "type": "Inventory"
  }
```

Update:
```
    "$based_on_properties": [
      "type",
      "baseUnitOfMeasureId",
      "blocked",
      "displayName",
      "id",
      "inventory",
      "itemCategoryCode",
      "itemCategoryId",
      "lastModifiedDateTime",
      "number",
      "priceIncludesTax",
      "taxGroupId",
      "unitCost",
      "unitPrice"
    ],
```

## Itemcategories

Insert:

Minimal object:
```
  {
    "code": "TEST",
    "displayName": "Test"
  }
```

Update:
```
    "$based_on_properties": [
      "code",
      "displayName",
      "id",
      "lastModifiedDateTime"
    ]
```